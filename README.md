# EC528_Fall21_Project
EC528: Cloud Computing. 

Project Name: Scaling remote sensing data processing in the Cloud with Ray.

Team Members: Carmen Hurtado

Project Description 

## 1. Vision and Goals Of The Project:

Our project aims to extensively research and test multi-dimensional data processing Python libraries to improve on the current prototype of a remote sensing data processing system.
The system is actively being used by our client, while running on a Google Cloud Platform with significant performance bottlenecks.
A main vision is to have a working system that improves upon the existing prototype by performing faster computation for processing the data collected from the remote sensing system. High level goals for the project include:

* Identify current system performace and the system's bottlenecks.
* Explore Python's computation libraries. 
* Thoroughly test each of these libraries' performance and comapare with current execution, evaluating tradeoffs such as speed and memory.
* Integrate the more effective libraries into the system.
* Improve over the existing State Of The Art on remote scaling data processing

## 2. Users/Personas Of The Project:

The end users of the projects are research scientists who study remote sensing images datasets. The project will be open source and available to the community.

The personas of the project other than the end users will be the developers who work on the different components of the end to end data processing pipeline, from pre-processing, to model building and inference.

Each developers working on their respective components can change their system, and the internals of their part of the pipeline. 

<!--#There will also be a system wide administrator that can make changes to the system level configuration affecting different parts of the end to end pipeline.-->

<!--#This section describes the principal user roles of the project together with the key characteristics of these roles. This information will inform the design and the user scenarios. A complete set of roles helps in ensuring that high-level requirements can be identified in the product backlog.-->

<!--#Again, the description should be specific enough that you can determine whether user A, performing action B, is a member of the set of users the project is designed for.-->

## 3. Scope and Features Of The Project:

The project prototype, as of now, is hosted in the Google Cloud Platform. 

We will be deploying the project clusters of Mass Open Cloud (MOC).

The project will run initially with the existing prototype at the MOC. 

After the initial setup, we will profile the various processes of the pre-processing part of the pipeline, which uses the Python library, Xarray: a multidimensional array processing library.

By using analytics tools, our goal is to identify the bottlenecks of the pre-processing pipeline, and explore the areas where it can be improved upon.

We will implement, and profile other libraries other than Xarray, which might help us achieve better performance on the pre-processing step of the pipeline.

The final goal of the project is to create  a much faster, and scalabale end to end large scale remote sensing data processing pipeline running in the MOC.

## 4. Solution Concept

Our client will provide us with a working prototype consisting of a platform built on Ray that takes Raw satelitte data images, turns them into time-series and feeds them into a linear regression model for analysis. This plaform will help researchers study local effects of climate change on ecosystems all over the world. It will allow for a better understanding of how the Earth's land cover, or the physical makeup of the land, changes over time.
Our final solution will be an improved prototype of this system as a scalable Python application hosted on MOC. 

This section provides a high-level outline of the solution.

Global Architectural Structure Of the Project:

<img src="/images/diagram.jpg" style="height: 400px; width:400px;"/>

Design Implications and Discussion:

TO BE COMPLETED


## 5. Acceptance criteria

At the end of the project timeline the team should have substantial documentation on the performance of the various Python Libraries explored. The final prototype should also have one or more of these instegrated. Stretch goals are:

* Integration and perfromace reviews of all the libraries that can be explored
* Final performance of 2TB of data processed in 2 hours. 


## 6. Release Planning:

The team will split the project components in 4 high-level parts:

1. Deploy Ray on a small cluster on MOC and run the existing prototype of satellite data processing system.
2. Study the application to identify bottlenecks.
    * Research and compute the performance of various Python libraries.
3. Build a faster and more scalable prototype based on the previous findings.
4. Do a large-scale experiment on MOC using real satellite data from one of the Google archives and report end-to-end performance.

