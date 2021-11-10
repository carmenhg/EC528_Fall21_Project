# EC528_Fall21_Project
EC528: Cloud Computing. 

Project: Scaling remote sensing data processing in the Cloud with Ray.

Team Members: Carmen Hurtado, Pujan Paudel, Jean Marc Achkar.

Mentor: John Liagouris.

# Project Description 

## 1. Vision and Goals Of The Project:

Our project aims to extensively research and test multi-dimensional data processing Python libraries to improve on the current prototype of a remote sensing data processing system that uses Ray for computation parallelization. Furthermore, we aim to profile the current uses of Ray in the application to identify its end to end performance. 
The system is running on the MOC platform with significant performance bottlenecks.
Many of the current functionality of the data processing part of the pipeline will need to be tested to verify their implementation because of the lack of documentation. 
A main vision is to have a working system that improves upon the existing prototype by performing faster computation for processing the data collected from the remote sensing system. 
High level goals for the project include:

* Identify current system performace and the system's bottlenecks.
* Verify component implementation.
* Explore Python's computation libraries. 
* Thoroughly test each of these libraries' performance and comapare with current execution, evaluating tradeoffs such as speed and memory.
* Integrate the more effective libraries into the system.
* Profile Ray application for bottelnecks in parallelization and processes distribution. 
* Improve over the existing State Of The Art on remote scaling data processing.

## 2. Users/Personas Of The Project:

The end users of the finalized prototype are research scientists at NASA JPL who study these remote sensing images datasets. However, the project will be open source and thus available to the community.

The personas of our project contribution to the working prototype other than the end users will be the developers who work on the different components of the end to end data processing pipeline, from pre-processing, to model building and inference. Our improvement will make the prototype developing and testing easier. Each developer working on their respective components can change their system, and the internals of their part of the pipeline while experiencing quicker results. 

<!--#There will also be a system wide administrator that can make changes to the system level configuration affecting different parts of the end to end pipeline.-->

<!--#This section describes the principal user roles of the project together with the key characteristics of these roles. This information will inform the design and the user scenarios. A complete set of roles helps in ensuring that high-level requirements can be identified in the product backlog.-->

<!--#Again, the description should be specific enough that you can determine whether user A, performing action B, is a member of the set of users the project is designed for.-->

## 3. Scope and Features Of The Project:

The prototype is currently a distributed application built with [Ray](https://www.ray.io)
* A distributed framework for emerging AI applications.
* It uses remote objects, tasks, and actors to create threads that parallelize the Python code.
* Easy incorporation onto sequential Python code
* Easily manageable depending on computing resources available.

The raw image datasets are currently stored in the Google Cloud Platform. 

The existing prototype is currently running in the Mass Open Cloud (MOC).

Our project will run initially with the dev version of the existing prototype at MOC. 

After the initial setup, we will profile the existing uses of Ray as a whole while mostly focusing on the data pre-processing part on the pipeline. 

Various experiments will be run to profile the application's current implementation of data shuffling and chunking among node workers.

The next steps will be to profile the various processes which use the Python library [Xarray: a multidimensional array processing library](http://xarray.pydata.org/en/stable/getting-started-guide/quick-overview.html) and [Dask: a libarry for parallel computing in Python](https://docs.dask.org/en/latest/).

By using analytics tools, our goal is to identify the bottlenecks of the pre-processing pipeline, and explore the areas where it can be improved upon.

We will implement, and profile other libraries other than Xarray, which might help us achieve better performance on the pre-processing step of the pipeline.

The final goal of the project is to create  a much faster, and scalabale end to end large scale remote sensing data processing pipeline running in the MOC.

## 4. Solution Concept

Our client will provide us with a working prototype consisting of a platform built on Ray that takes Raw satelitte data images, turns them into time-series and feeds them into a linear regression model for analysis. This platform will help researchers study local effects of climate change on ecosystems all over the world. It will allow for a better understanding of how the Earth's land cover, or the physical makeup of the land, changes over time.
Our final solution will be an improved prototype of this system as a scalable Python application hosted on MOC. 

Global Architectural Structure Of the Project:

<img src="/images/diagram.jpg" style="height: 400px; width:600px;"/>

Design Implications and Discussion:

As it can be seen in the architecture diagram, our project addresses the need to scale, and improve the performance of the existing system before the linear 
regression model is applied from the data. Other components of the systems, including the model building, and the prediction are already scaled and efficient.
The major bottleneck of the project is speeding up operations during the phase of pre-processing raw satelite images to time series. We will understand the
current implementation of the pre-processing system, investigate where the expensive operations are happening, and determine how we can improve upon it by
testing and instrumenting other alternative approaches. 
The improvements we will bring on this phase of the pipeline will alow the whole system to be end-to-end scalable. 

## 5. Acceptance criteria

Minimum goals for this project:
* At the end of the project timeline the team should have substantial documentation on the performance of the various Python Libraries explored.
* The final prototype should also have one or more of these instegrated.
* In addition we will have extensive data results on how Ray is being completely optimized for this prototype.

Stretch goals are:
* Integration and perfromace reviews of all the libraries that can be explored
* Final performance of 2TB of data processed in 2 hours. 


## 6. Release Planning:

The team will split the project components in 5 high-level parts:

1. Deploy Ray on a small cluster on MOC and run the existing prototype of satellite data processing system.
    * Build a cluster with a head node and multiple worker nodes.
    * Add the prototype to the cluster, one node at a time, and test the performance differences of using different amount of nodes for computations.
2. Study the application to identify bottlenecks.
    * Profile Ray as it is being used and identify any improvement opportunities.
        * Tools: [Ray Dashboard](https://docs.ray.io/en/latest/ray-dashboard.html), [Chrome Tracing](https://www.chromium.org/developers/how-tos/trace-event-profiling-tool), [Prometheus](https://docs.ray.io/en/latest/ray-metrics.html)  
    * Research and compute the performance of various Python libraries.
3. Build a faster and more scalable prototype based on the previous findings.
    * Integrate any libraries that proved to be faster for processing the Raw Image Data.
    * Adjust the Ray settings of computational resources (Workers, vCPUS, etc) that proved to speed up the computations. 
4. Do a large-scale experiment on MOC using real satellite data from one of the Google archives and report end-to-end performance.
    * After various experiments with big data sizes, note any discrepancies on performance.
5. Adjust solution per result of previous part.

## 7. Computing Resources
The systems needs to run on OpenStack either on MOC or NERC depending on support. 

## 8. Additional Learning Resources
- [Ray: A Distributed Framework for Emerging AI Applications - Academic Paper](https://www.usenix.org/system/files/osdi18-moritz.pdf)
- [xray + dask: out-of-core, labeled arrays in Python](http://stephanhoyer.com/2015/06/11/xray-dask-out-of-core-labeled-arrays/)
- [Prometheus Tool](https://prometheus.io/docs/introduction/overview/)
- 
- 

## 9. Demo Videos
- [Demo 1](https://github.com/carmenhg/EC528_Fall21_Project/blob/main/Demo%20Videos/EC528_Demo_1.mp4)
- [Demo 2](https://www.youtube.com/watch?v=okqhSW9OlmM)
- [Demo 3](https://www.youtube.com/watch?v=15Q9H4_5T5s)
- [Demo 4]()




