AirflowでDAGやTaskの仕様を共有できるdoc_mdの使い方
この記事では、Airflowの機能の一つであるDAGやTaskの仕様を共有できるdoc_mdという機能があるのですが、その機能について紹介します。

なぜAirflowのDAGやTaskのドキュメントを書くか
なぜAirflowのDAGやTaskのドキュメントを書くかについてです。AirflowのDAGやTaskの内容は、コードを確認すれば把握はできます。また、Pythonで記述できるAirflowであれば、docstringなども一つの選択肢かもしれません。docstringであれば、専用のドキュメントツールみたいなのを立ち上げることもできるかもしれません。

しかし、GUIツールとして提供されているAirflowを使いこなすうえで、気軽にAirflow上でドキュメントを視覚的にわかりやすく確認することができることはそれだけでメリットがありますし、専用のドキュメントをホスティングする必要もありません。

加えて、Airflowのコードの修正と同時にドキュメントの修正をレビューできる点もメリットです。

書き方
以下は、書き方のサンプルコードです。


```python
from datetime import datetime, timedelta
from textwrap import dedent

# The DAG object; we'll need this to instantiate a DAG
from airflow import DAG

# Operators; we need this to operate!
from airflow.operators.bash import BashOperator
with DAG(
    'tutorial',
    # These args will get passed on to each operator
    # You can override them on a per-task basis during operator initialization
    default_args={
        'depends_on_past': False,
        'email': ['airflow@example.com'],
        'email_on_failure': False,
        'email_on_retry': False,
        'retries': 1,
        'retry_delay': timedelta(minutes=5),
        # 'queue': 'bash_queue',
        # 'pool': 'backfill',
        # 'priority_weight': 10,
        # 'end_date': datetime(2016, 1, 1),
        # 'wait_for_downstream': False,
        # 'sla': timedelta(hours=2),
        # 'execution_timeout': timedelta(seconds=300),
        # 'on_failure_callback': some_function,
        # 'on_success_callback': some_other_function,
        # 'on_retry_callback': another_function,
        # 'sla_miss_callback': yet_another_function,
        # 'trigger_rule': 'all_success'
    },
    description='A simple tutorial DAG',
    schedule_interval=timedelta(days=1),
    start_date=datetime(2021, 1, 1),
    catchup=False,
    tags=['example'],
) as dag:

    # t1, t2 and t3 are examples of tasks created by instantiating operators
    t1 = BashOperator(
        task_id='print_date',
        bash_command='date',
    )

    t2 = BashOperator(
        task_id='sleep',
        depends_on_past=False,
        bash_command='sleep 5',
        retries=3,
    )
    t1.doc_md = dedent(
        """\
    #### Task Documentation
    You can document your task using the attributes `doc_md` (markdown),
    `doc` (plain text), `doc_rst`, `doc_json`, `doc_yaml` which gets
    rendered in the UI's Task Instance Details page.
    """
    )

    dag.doc_md = __doc__  # providing that you have a docstring at the beginning of the DAG
    dag.doc_md = """
    This is a documentation placed anywhere
    """  # otherwise, type it like this
    templated_command = dedent(
        """
    {% for i in range(5) %}
        echo "{{ ds }}"
        echo "{{ macros.ds_add(ds, 7)}}"
    {% endfor %}
    """
    )

    t3 = BashOperator(
        task_id='templated',
        depends_on_past=False,
        bash_command=templated_command,
    )

    t1 >> [t2, t3]
```
上記のように、doc_mdを使うことで、ドキュメントを書くことができます。

表示内容
実際の表示方法は以下の通りです。

DAG
DAG

Task
Task

以上で、Airflowのdoc_mdの使い方は以上です。

参考
Tutorial - Airflow