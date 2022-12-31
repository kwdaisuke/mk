
Kubeflow Pipelines concept


pipeline
In the context of KFP, a pipeline is a set of machine learning workflows defined in a directed acyclic graph (DAG). KFP uses Python to define Pipeline execution details and inputs (parameters). The defined Pipeline can be uploaded using the Web UI and shared within the organization.

Components
A Component is a unit of processing executed in a Pipeline. For example, data preprocessing and processing, model training, etc. When represented in a DAG graph, each node corresponds to a Component. Each Component runs on Kubernetes as a Docker container. Therefore, care must be taken to ensure that they are not executed in the same process.

Regarding the definition of Component
There are multiple ways to create a Component in KFP, all of which end up in Yaml format. This Yaml-formatted state is called a Component Definition. A Component definition contains three things:

Metadata: component name and description
Interface: inputs and outputs (names, data types, default values, etc.)
Implementation: Content of processing
See the official documentation for details.

Experiment
Experiment refers to a workspace accessible from the web UI. In Experiment, you can execute Pipeline with changed settings.

Run and Recurring Run
Run is the execution unit of Pipeline. You can check Pipeline status and execution logs from the Web UI. A Recurring Run is a Run that is executed periodically. Kubernetes CronJob is used as the backend, and execution time etc. are defined from the Web UI.

Artifact
Artifact shows the output by running the Component. Kubeflow provides appropriate visualization in UI depending on the type of artifact.

ML Metadata
The KFP backend stores Pipeline execution environment information in the Metadata Store. This information includes task status, artifact information, runtime parameters, etc. Please refer to the official documentation for details.

reference
Concepts - Kubeflow Pipelines Docs