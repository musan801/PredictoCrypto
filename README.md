<h1>PredictoCrypto</h1>

<h3>Implementation Details</h3>

The aim of the project is to use Hadoop as a database and store all the data files on Hadoop and then retrieving those files into python application to develop and test the Cryptocurrency prediction model. The implementation of project is divided into two major parts:
1. Hadoop clusters setup and data storage 
2. Prediction model development in python

<h3>Hadoop clusters setup and data storage</h3>

Hadoop is a software framework from Apache Software Foundation that is used to store and process Big Data. It has two main components; Hadoop Distributed File System (HDFS), its storage system and MapReduce, its data processing framework. Hadoop has the capability to manage large datasets by distributing the dataset into smaller chunks across multiple machines and performing parallel computation on it .HDFS is composed of a master-slave architecture where the master node is called NameNode and slave node is called DataNode. The NameNode and its DataNodes form a cluster. NameNode acts like an instructor to DataNode while the DataNodes store the actual data.

![image](https://user-images.githubusercontent.com/55654110/149028213-82fe6227-89f7-4aa9-b3fc-56da437826e0.png)

Another component of Hadoop is known as YARN. The purpose of Yarn is to manage the resources and schedule/monitor jobs in Hadoop. Yarn consists of two main components, Resource Manager and Node Manager. The resource manager has the authority to allocate resources to various applications running in a cluster. The node manager is responsible for monitoring their resource usage (CPU, memory, disk) and reporting the same to the resource manager.

The HDFS system here is used for the purpose of storing data in this prediction model. The Hadoop configuration in this system is created with a single cluster, a data node and a name node. The name node is used for the purpose of tracking the file directory and placing the chunks for each file that are replicated across the DataNodes. To run a query on data, a MapReduce function is used which runs on each node against the input files and the reducers aggregate and organize the final output. The Hadoop is installed in the windows 10 system and the cluster is configured as a single cluster. All the data files consisting of the Cryptocurrency prices are stored in separate csv files. These csv files are then imported into the Hadoop system. The HDFS is in the Pseudo-Distributed Mode where the NameNode and the DataNode exist in the same machine and all the daemons run on the same machine.


<h3>Prediction model development</h3>
The prediction model is developed in python programming language as it has a lot of extensions, libraries and documentation available for support and is a good language for developing a prediction model. The aim of the model is to predict values of a particular Cryptocurrency taking the previous data into account and also show accuracy of the model so that the user can make an informed decision with all the information available.
The dataset is .cave files of 10 different Cryptocurrency selected from available Cryptocurrency on the basis of current trends and popularity. The dataset is a sequential data and changes its values with respect to time. Each .csv file of a particular currency has multiple rows of data which changes with time and shows the following attributes:

1. Date and time: date and time with one minute of increment.
2. Open: the opening price of the Cryptocurrency for the minute in any currency
3. Close: the closing price of the Cryptocurrency for the minute in any currency
4. High: the highest price of the Cryptocurrency for the minute in any currency
5. Low: the lowest price of the Cryptocurrency for the minute in any currency
6. Volume: the amount of coins traded(bought/sold) of the Cryptocurrency for the minute

All the above-mentioned attributes are very important for prediction and can help build a better model. All the other attributes present in the file were dropped before moving forward.
The .csv files were imported using Fastquant API; other APIs as yfinance, binance etc were also taken into consideration however, they allowed to fetch data only up to a limited period and that would not be enough to build a model.
After importing the data from API, the csv files were made and that data was stored in Hadoop Distributed file system. Once the data was stored on Hadoop cluster we need to retrieve that data in order to process and clean the data to build the model.
For this, our team is using Snakebite – it is a python package developed by spotify engineering to access HDFS and allow interaction between HDFS and python application. We have used it to retrieve the .csv files and use it in preparing our model. The data is sequential and changes with time so we are performing regression analysis on the data and hence trying to predict values the Cryptocurrency will have in the future.

Once the python application has access to the data we are using multiple libraries and extensions available in python to store & process the data. These are:

**1. Fastquant:** it can access historical stock and Cryptocurrency data very quickly and takes data from binance so it can be trusted.

**2. Pandas:** pandas is a library for python for data analysis and manipulation. We are using it as our data is a numerical time series data.

**3. Numpy:** Numpy is used for adding more support in python to process large, multidimensional arrays and matrices. It also gives ability to work and process these large datasets.

**4. Plotly:** Plotly allows nonchalant creation of graphs and plots in python from any given data set. We have used it to plot our prediction values on a graph for better representation of data.

**5. Sklearn:** Sci-Kit learn is a machine learning library which includes various features to create algorithms for models. We have used it for pre-processing of our data using MinMaxScaler.

**6. TensorFlow:** TensorFlow-Keras is also a machine learning and artificial intelligence library which enables us in building deep neural networks.
