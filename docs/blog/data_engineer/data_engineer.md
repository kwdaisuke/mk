# Data Engieer Architecture
Reading time: 5 minutes

<figure markdown>
  ![Image title](https://future.a16z.com/wp-content/uploads/2020/10/Blueprint-1_-Modern-Business-Intelligence-1.png)
</figure>

- There has been a surge of interest in the metrics layer, a system providing a standard set of definitions on top of the data warehouse. This has been hotly debated, including what capabilities it should have, which vendor(s) should own it, and what spec it should follow. So far, we’ve seen several credible pure-play products (like Transform and Supergrain), plus expansion into this category by dbt.
- **Reverse ETL** vendors have grown meaningfully, particularly Hightouch and Census. The purpose of these products is to update operational systems, like CRM or ERP, with outputs and insights derived from the data warehouse.
- Data teams are showing stronger interest in new applications to augment their standard dashboards, especially data workspaces (like Hex). Broadly speaking, new apps are likely the result of increasing standardization in cloud data warehouses — once data is cleanly structured and easy to access, data teams naturally want to do more with it.
- Data discovery and observability companies have proliferated and raised substantial amounts of capital (especially Monte Carlo and Bigeye). While the benefits of these products are clear — i.e. more reliable data pipelines and better collaboration — adoption is still relatively early, as customers discover relevant use cases and budgets. (Technical note: although there are several credible new vendors in data discovery — e.g. Select Star, Metaphor, Stemma, Secoda, Castor — we have excluded seed-stage companies from the diagram in general.)

<figure markdown>
  ![Image title](https://future.a16z.com/wp-content/uploads/2020/10/Blueprint-2_-Multimodal-Data-Processing-1.png)
</figure>

- There is growing recognition and clarity for the lakehouse architecture. We’ve seen this approach supported by a wide range of vendors (including AWS, Databricks, Google Cloud, Starburst, and Dremio) and data warehouse pioneers. The fundamental value of the lakehouse is to pair a robust storage layer with an array of powerful data processing engines like Spark, Presto, Druid/Clickhouse, Python libraries, etc.
- The **storage layer** itself is getting an upgrade. While technologies like Delta, Iceberg, and Hudi are not new, they are seeing accelerated adoption and are being built into commercial products. Some of these technologies (particularly Iceberg) also interoperate with cloud data warehouses like Snowflake. If heterogeneity is here to stay, this is likely to become a key part of the multimodal data stack.
- There may be an uptick in adoption taking place for stream processing (i.e., real-time analytical data processing). While first-generation technologies like Flink still haven’t gone mainstream, new entrants with simpler programming models (like Materialize and Upsolver) are gaining early adoption, and, anecdotally, usage of stream processing products from incumbents Databricks and Confluent has also started to accelerate.

<figure markdown>
  ![Image title](https://future.a16z.com/wp-content/uploads/2022/03/Blueprint-3_-Artificial-Intelligence-and-Machine-Learning.png)
</figure>

- The ML industry is consolidating around a data-centric approach, emphasizing sophisticated data management over incremental modeling improvements. This has several implications:
    - Rapid growth for data labeling (e.g. Scale and Labelbox) and growing interest in closed-loop data engines, largely modeled on Tesla’s Autopilot data pipelines.
    - Increased adoption for feature stores (e.g. Tecton), for both batch and real-time use cases, as a means to develop production-grade ML data in a collaborative way.
    - Revived interest in low-code ML solutions (like Continual and MindsDB) that at least partially automate the ML modeling process. These newer solutions focus on bringing new users (i.e. analysts and software developers) into the ML market.
- Use of **pre-trained models** is becoming the default, especially in NLP, and providing tailwinds to companies like OpenAI and Hugging Face. There are still meaningful problems to solve here around fine-tuning, cost, and scaling.
- Operations tools for ML (sometimes called MLops) are becoming more mature, built around **ML monitoring** as the most in-demand use case and immediate budget. Meanwhile, a raft of new operational tools — including, notably, **validation** and **auditing** — are appearing, with the ultimate market still to be determined.
- There is increased focus on how developers can seamlessly integrate ML models into applications, including through **pre-built APIs** (e.g. OpenAI), **vector databases** (e.g. Pinecone), and more opinionated frameworks.

Source: <https://future.a16z.com/emerging-architectures-modern-data-infrastructure/>