# EC528_Fall21_Project
EC528: Cloud Computing. 
Project Name: Scaling remote sensing data processing in the Cloud with Ray.

Project Description 

1. Vision and Goals Of The Project:

Our project aims to extensively research and test Python libraries to improve on the current prototype that is actively being used by our client. A main vision is to have a working new prototype that performs faster computation for processing the data collected from the remote sensing system. High level goals for the project include:

* Identify current system performace and the system's bottlenecks.
* Explore Python's computation libraries. 
* Thoroughly test each of these libraries' performance and comapare with current execution.
* Integrate the more effective libraries into the system.

2. Users/Personas Of The Project:

The end users of the projects are research scientists who study remote sensing images datasets. The project will be open source and available to the community.

The personas of the project other than the end users will be the developers who work on the different components of the end to end data processing pipeline, from pre-processing, to model building and inference.

Each developers working on their respective components can change their system, and the internals of their part of the pipeline. 

#There will also be a system wide administrator that can make changes to the system level configuration affecting different parts of the end to end pipeline.

#This section describes the principal user roles of the project together with the key characteristics of these roles. This information will inform the design and the user scenarios. A complete set of roles helps in ensuring that high-level requirements can be identified in the product backlog.

#Again, the description should be specific enough that you can determine whether user A, performing action B, is a member of the set of users the project is designed for.

3. Scope and Features Of The Project:

The Scope places a boundary around the solution by detailing the range of features and functions of the project. This section helps to clarify the solution scope and can explicitly state what will not be delivered as well.

It should be specific enough that you can determine that e.g. feature A is in-scope, while feature B is out-of-scope.

4. Solution Concept

The prototype consists of a platform built on Ray that takes Raw satelitte daqta images, turns them into time-series and feeds them into a linear regression model for analysis. This plaform will help researchers study local effects of climate change on ecosystems all over the world. It will allow for a better understanding of how the Earth's land cover, or the physical makeup of the land, changes over time.
Our final solution will be a scalable Python application for remote sensing data processing in the cloud. It will download real satellite image data fom web archives, transform it into time-series, and apply the linear regression model to identify land cover changes over large periods of time. 

This section provides a high-level outline of the solution.

Global Architectural Structure Of the Project:

This section provides a high-level architecture or a conceptual diagram showing the scope of the solution. If wireframes or visuals have already been done, this section could also be used to show how the intended solution will look. This section also provides a walkthrough explanation of the architectural structure.

Design Implications and Discussion:

This section discusses the implications and reasons of the design decisions made during the global architecture design.

5. Acceptance criteria

At the end of the project timeline the team should have substantial documentation on the performance of the various Python Libraries explored. The final prototype should also have one or more of these instegrated. Stretch goals are:

* Integration and perfromace reviews of all the libraries that can be explored
* Final performance of 2TB of data processed in 2 hours. 


6. Release Planning:

Release planning section describes how the project will deliver incremental sets of features and functions in a series of releases to completion. Identification of user stories associated with iterations that will ease/guide sprint planning sessions is encouraged. Higher level details for the first iteration is expected.

General comments

Remember that you can always add features at the end of the semester, but you can't go back in time and gain back time you spent on features that you couldn't complete.
