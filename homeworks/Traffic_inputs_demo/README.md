# Traffic Inputs Demonstrations

[This notebook](Traffic_inputs_demo.ipynb) covers various aspects related to the preparation stage of building a traffic simulation model. Most of the content are not necessary, but could be helpful, for Quizzes 3, 4 and Assignment 2. In addition, if you would like to conduct traffic simulation for another case study in the future, the topics covered here may be useful in helping you to set up the model.

### Topics
* Network:
  * Retrieving road network from OpenStreetMap (OSM) with interatively or via command line.
  * Retrieving cleaned road network using [OSMnx](https://geoffboeing.com/2016/11/osmnx-python-street-networks/).
* Demand:
  * Selecting nodes within a given zone (e.g., selecting origin nodes given an evacuation area).
  * Constructing a origin-destination list.
* Shortest path:
  * Constructing a graph object using [sp](http://github.com/cb-cities/sp.git).
  * Retrieving the shortest path on a road network graph between given origin and destination using the [sp](http://github.com/cb-cities/sp.git).
  * Note: this exercise does not cover how to write a code implementing the Dijkstra's Algorithm.

Click the icon below to start:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/UCB-CE170a/Fall2020/blob/master/homeworks/Traffic_inputs_demo/Traffic_inputs_demo.ipynb)



