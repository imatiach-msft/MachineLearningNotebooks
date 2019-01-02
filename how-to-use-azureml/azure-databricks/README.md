Azure Databricks is a managed Spark offering on Azure and customers already use it for advanced analytics. It provides a collaborative Notebook based environment with CPU or GPU based compute cluster. 

In this section, you will see sample notebooks on how to use Azure Machine Learning SDK with Azure Databricks. You can train a model using Spark MLlib and then deploy the model to ACI/AKS from within Azure Databricks. You can also use Automated ML capability (**public preview**) of Azure ML SDK with Azure Databricks. 

- Customers who use Azure Databricks for advanced analytics can now use the same cluster to run experiments with or without automated machine learning. 
- You can keep the data within the same cluster. 
- You can leverage the local worker nodes with autoscale and auto termination capabilities. 
- You can use multiple cores of your Azure Databricks cluster to perform simultenous training. 
- You can further tune the model generated by automated machine learning if you chose to. 
- Every run (including the best run) is available as a pipeline. 
- The model trained using Azure Databricks can be registered in Azure ML SDK workspace and then deployed to Azure managed compute (ACI or AKS) using the Azure Machine learning SDK.

**Create Azure Databricks Cluster:**

Select New Cluster and fill in following detail:
 - Cluster name: _yourclustername_
 - Databricks Runtime: Any 4.x runtime.
 - Python version: **3**
 - Workers: 2 or higher.  

These settings are only for using Automated Machine Learning on Databricks.
 - Max. number of **concurrent iterations** in Automated ML settings is **<=** to the number of **worker nodes** in your Databricks cluster.
 - Worker node VM types: **Memory optimized VM** preferred. 
 - Uncheck _Enable Autoscaling_


It will take few minutes to create the cluster. Please ensure that the cluster state is running before proceeding further.

**Install Azure ML SDK without Automated ML capability on your Azure Databricks cluster**

- Select Import library

- Source: Upload Python Egg or PyPI

- PyPi Name: **azureml-sdk[databricks]**

**Install Azure ML with Automated ML SDK on your Azure Databricks cluster**

- Select Import library

- Source: Upload Python Egg or PyPI

- PyPi Name: **azureml-sdk[automl_databricks]**

**For installation with or without Automated ML**

- Click Install Library

- Do not select _Attach automatically to all clusters_. In case you have selected earlier then you can go to your Home folder and deselect it.

- Select the check box _Attach_ next to your cluster name

(More details on how to attach and detach libs are here - [https://docs.databricks.com/user-guide/libraries.html#attach-a-library-to-a-cluster](https://docs.databricks.com/user-guide/libraries.html#attach-a-library-to-a-cluster) )

- Ensure that there are no errors until Status changes to _Attached_. It may take a couple of minutes.

**Note** - If you have the old build the please deselect it from cluster’s installed libs > move to trash. Install the new build and restart the cluster. And if still there is an issue then detach and reattach your cluster.

iPython Notebooks 1-4 have to be run sequentially after making changes based on your subscription. The corresponding DBC archive contains all the notebooks and can be imported into your Databricks workspace. You can the run notebooks after importing [databricks_amlsdk](Databricks_AMLSDK_1-4_6.dbc) instead of downloading individually.

Notebooks 1-4 are related to Income prediction experiment based on this [dataset](https://archive.ics.uci.edu/ml/datasets/adult) and demonstrate how to data prep, train and operationalize a Spark ML model with Azure ML Python SDK from within Azure Databricks. Notebook 6 is an Automated ML sample notebook.

For details on SDK concepts, please refer to [notebooks](https://github.com/Azure/MachineLearningNotebooks).

Learn more about [how to use Azure Databricks as a development environment](https://docs.microsoft.com/azure/machine-learning/service/how-to-configure-environment#azure-databricks) for Azure Machine Learning service.

You can also use Azure Databricks as a compute target for [training models with an Azure Machine Learning pipeline](https://docs.microsoft.com/machine-learning/service/how-to-set-up-training-targets#databricks).


**Please let us know your feedback.**