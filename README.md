# EC528_Fall21_Project
BU ENG EC528: Cloud Computing. 

Project: Scaling Remote Sensing Data Processing In The Cloud With Ray.

Team Members: Carmen Hurtado, Pujan Paudel, Jean Marc Achkar.

Mentor: John Liagouris.

# Project Description 

## 1. Vision and Goals Of The Project:

As a starting point, we received a distributed application built with [Ray](https://docs.ray.io/en/latest/index.html) that is a working prototype to measure and study satellite images of the earth's surface. 

Our project aims to profile the current uses of Ray in the application to identify its end to end performance. 

The system is running on the Mass Open Cloud(MOC) platform with significant performance bottlenecks. Many of the current functionality of the data processing part of the pipeline will need to be tested to verify their implementation because of limited documentation. 

Our main vision is to have a working system that improves upon the existing prototype by performing faster computation for processing the data collected from the remote sensing system and that is more efficient on memory usage across the cluster. 

High level goals for the project include:
* Identify current system performace and the system's bottlenecks.
* Verify component implementation.
* Understand Python's computation libraries used (Xarray, Dask).
* Profile Ray application for bottelnecks in parallelization and processes distribution. 
* Improve over the existing State Of The Art on remote scaling data processing.

## 2. Users/Personas Of The Project:

The end users of the finalized prototype are research scientists at NASA JPL who study these remote sensing images datasets. However, the project will be open source and thus available to the community.

The personas of our project contribution to the working prototype other than the end users will be the developers who work on the different components of the end to end data processing pipeline, from pre-processing, to model building and inference. Our improvement will make the prototype developing and testing easier. Each developer working on their respective components can change their system, and the internals of their part of the pipeline while experiencing quicker results. 

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

We will profile other libraries other than Xarray, which might help us achieve better performance on the pre-processing step of the pipeline.

The final goal of the project is to document current prototype and create a much faster, and scalabale end to end large scale remote sensing data processing pipeline running in the MOC.

## 4. Solution Concept

Our client will provide us with a working prototype consisting of a platform built on Ray that takes Raw satelitte data images, turns them into time-series and feeds them into a linear regression model for analysis. This platform will help researchers study local effects of climate change on ecosystems. It will allow for a better understanding of how the Earth's land cover, or the physical makeup of the land, changes over time.
Our final solution will be an improved prototype of this system hosted on MOC. 
We put our focus on these major fixes:

1. Improve end-to-end time of data processing computation.
    - Instrument code to measure the perfromance. For this we use tools [Chrome Tracing](https://www.chromium.org/developers/how-tos/trace-event-profiling-tool), [Prometheus](https://prometheus.io/docs/introduction/overview/), [Jeager](https://docs.ray.io/en/latest/ray-tracing.html), [Ray Dashboard](https://docs.ray.io/en/latest/ray-dashboard.html).
    - Parallelize by worker activities in each node.

2. Diagnose memory blow up, propose a solution, and possibly implement it. 
    - Profile memory usage with [Python Memory Profiler](https://pypi.org/project/memory-profiler/).
    - Study more efficient approaches to Image Alignemnt (Which is the process that causes memory blow up).
    - Collaborate with another team from our mentor's class to solve this issue.

Global Architectural Structure Of the Application Prototype And The Project:

<img src="/images/diagram.jpg" style="height: 400px; width:600px;"/>

Design Implications and Discussion:

As it can be seen in the architecture diagram, our project addresses the need to scale, and improve the performance of the existing system before the linear regression model is applied from the data. Other components of the systems, including the model building, and the prediction are already scaled and efficient. One of the bottlenecks of the project is speeding up operations during the phase of pre-processing raw satelite images to time series. We will understand the current implementation of the pre-processing system, investigate where the expensive operations are happening, and determine how we can improve upon it by testing and instrumenting the current application. The second and biggest bottleneck is a memory blow up that happens in the chunking phase of the processing where the satellite images need to be aligned to form the true tile we want to study.  
The improvements and findings we will bring on this phase of the pipeline will alow the whole system to be end-to-end scalable. 

## 5. Acceptance criteria

Minimum goals for this project:
* At the end of the project timeline the team should have substantial documentation on the performance of the original application.
* In addition we will have extensive data results on how Ray could be completely optimized for this prototype.
* The team must have important findings on the bottlenecks of the application.
* There should be documentation about every step studied and every new implementation to the application. 
* The performance of the application must have improved, meaning the processing of the data takes less than 2 hours which was the time it took the original prototype. 

Stretch goals are:
* Fix memory blow up bottleneck. 


## 6. Release Planning:

The team will split the project components in 5 high-level parts:

1. Deploy Ray on a small cluster on MOC and run the existing prototype of satellite data processing system.
    * Build a cluster with a head node and multiple worker nodes.
    * Add the prototype to the cluster, one node at a time, and test the performance differences of using different amount of nodes for computations.
2. Study the application to identify bottlenecks.
    * Profile Ray as it is being used and identify any improvement opportunities.
        * Tools: [Ray Dashboard](https://docs.ray.io/en/latest/ray-dashboard.html), [Chrome Tracing](https://www.chromium.org/developers/how-tos/trace-event-profiling-tool), [Prometheus](https://docs.ray.io/en/latest/ray-metrics.html)  
    * Profile memory usage and propose improvements. 
        * Tools: [Python Memory Profiler](https://pypi.org/project/memory-profiler/)
3. Build a faster and more scalable prototype based on the previous findings.
    * Adjust the Ray settings of computational resources (Workers, vCPUS, etc) that proved to speed up the computations. 
    * Build an efficient algorithms to perform Image Alignement or find a library that perfroms better than Xarray. 
4. Do a large-scale experiment on MOC using real satellite data from one of the Google archives and report end-to-end performance.
    * After various experiments with big data sizes, note any discrepancies on performance.
5. Adjust solution per result of previous part.

## 7. Computing Resources
The systems needs to run on OpenStack either on MOC or NERC depending on support. 

## 8. Additional Learning Resources
- [Ray: A Distributed Framework for Emerging AI Applications - Academic Paper](https://www.usenix.org/system/files/osdi18-moritz.pdf)
- [xray + dask: out-of-core, labeled arrays in Python](http://stephanhoyer.com/2015/06/11/xray-dask-out-of-core-labeled-arrays/)
- [Prometheus Tool](https://prometheus.io/docs/introduction/overview/)
- [Jeager, OpenTelemetry, and Ray](https://docs.ray.io/en/latest/ray-tracing.html)
- [Xarray.concat](http://xarray.pydata.org/en/stable/generated/xarray.concat.html)

## 9. Demo Videos
- [Demo 1](https://github.com/carmenhg/EC528_Fall21_Project/blob/main/Demo%20Videos/EC528_Demo_1.mp4)
- [Demo 2](https://www.youtube.com/watch?v=okqhSW9OlmM)
- [Demo 3](https://www.youtube.com/watch?v=15Q9H4_5T5s)
- [Demo 4](https://www.youtube.com/watch?v=GG3KkTXrLek)
- [Demo 5](https://www.youtube.com/watch?v=acsXzN09634)
- [Project Wrap Up]()

## Important And Helpful Information
For a full documentation on this project follow [this link](https://github.com/carmenhg/EC528_Fall21_Project/wiki/1.-General-Information) to the Github Repo Wiki. 


