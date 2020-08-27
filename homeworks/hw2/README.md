# Assignment 2

## Overview
In this assignment, you will be asked to run the spatial queue-based dynamic traffic assignment on a hypothesized Berkeley Hills fire evacuation setting. You will be provided with:
* a base network inputs file: [berkeley_edges.csv](https://raw.githubusercontent.com/UCB-CE170a/Fall2020/master/traffic_data/north_berkeley_edges_clean.csv) and [berkeley_nodes.csv](https://raw.githubusercontent.com/UCB-CE170a/Fall2020/master/traffic_data/north_berkeley_nodes_clean.csv). Note that you will need to modify this to reflect your contraflow strategy.
* od inputs file: [od_10pn.csv](https://raw.githubusercontent.com/UCB-CE170a/Fall2020/master/traffic_data/od_10pn.csv). This travel demand input file assumes that there are 10 vehicles originating from each node in the evacuation area.

## Instruction
Take a moment to download and examine the [berkeley_edges.csv](https://raw.githubusercontent.com/UCB-CE170a/Fall2020/master/traffic_data/north_berkeley_edges_clean.csv) road links file. Notice that each road link has several attributes, including `lanes`, `capacity`, `fft`, etc. For example, the two road links with `link_id` = 457 and 462 are two directions of same road (Marin Avenue) between Santa Barbara Road and Spruce Street. If you are to implement contraflow here, you can either increase the number of lanes of 462 (the downhill direction) to 3 and reduce the number of lanes of its opposite direction to 1, or increase the number of lanes of 462 (the downhill direction) to 4 and reduce the number of lanes of its opposite direction to 0.

Capacity is calculated based on the number of lanes, assuming 1900 vehicles/(lane * hour). One thing you should pay attention to is, if you set the number of lanes to 0, then its free-flow travel time `fft` must be set to a very large number larger than `1e8` to reflect the road is no longer passable. Otherwise vehicles will still plan their routes using the closed link, even though they can never go through it.

|link_id  | start_node_id| end_node_id  |  type   | length  |maxmph   |lanes    | capacity| fft         | ... |
|---------|--------------|--------------|---------|---------|---------|---------|---------|-------------|-----|
|457      |157           |158           |tertiary |89.454   |25.0     |2        |3800     |8.0041292304 |-----|
|462      |158           |157           |tertiary |89.454   |25.0     |2        |3800     |8.0041292304 |-----|

In this assignment, you need to run the code with [berkeley_edges.csv](https://raw.githubusercontent.com/UCB-CE170a/Fall2020/master/traffic_data/north_berkeley_edges_clean.csv) as the base case. Then you need to modify [berkeley_edges.csv](https://raw.githubusercontent.com/UCB-CE170a/Fall2020/master/traffic_data/north_berkeley_edges_clean.csv) to reflect the changes in network (capacity, lanes and fft) after implementing contraflow at your chosen road links. The total length of contraflow links (both side of two-way roads combined) should not be longer than 3 miles (the `length` in the [berkeley_edges.csv](https://raw.githubusercontent.com/UCB-CE170a/Fall2020/master/traffic_data/north_berkeley_edges_clean.csv) has unit of `meter`).


## Submission
Your submissions consist of two parts:
1. September 30th, 10:00 am PDT: 
    * A CSV file, which is based on [berkeley_edges.csv](https://raw.githubusercontent.com/UCB-CE170a/Fall2020/master/traffic_data/north_berkeley_edges_clean.csv) but with modified `lanes`, `capacity` and `fft` to reflect your contraflow strategy, named `contraflow_edges_[your_name].csv`.
    * A CSV file containing the numbers of arrived vehicles at each time step, named `arrival_counts_[your_name].csv`. Template provided in 
    ** Note 1: do not make other changes to the simulation except from the `lanes`, `capacity` and `fft` in the `berkeley_edges.csv` file.
    ** Note 2: GSI will validate your arrival count results based on the `contraflow_edges_[your_name].csv` that you provide. We will show the most effective contraflow operations during the class on October 1st.
2. October 8th, 2:00 pm PDT:
    * Report outlining your findings through the assginment. The report should include at least a map (with legned, scale, north point, title, and background map). You are encouraged, though not required, to change the code to test, e.g., the impact of rerouting or staged evacuation and include the findings in your report.

## Evaluation
You will be evaluated by the following criteria:
1. The `contraflow_edges_[your_name].csv`: the total length of contraflow affected links (both the increased and reduced side) should be between 2 to 3 miles.
2. The `contraflow_edges_[your_name].csv`: when you increase the lanes or capacity on one side of the road, the capacity and number of lanes on the opposite side should reduce accordingly.
3. The `contraflow_edges_[your_name].csv`: when the number of lanes is 0, the free flow time `fft` should be at least `1e8`.
4. The `contraflow_edges_[your_name].csv`: the code should be able to run with this new input file.
5. You will **NOT** be evaluated by the single measure effectiveness of your contraflow strategy, so you can be creative in designing your strategy. Hopefully we will be able to review a diverse range of scenarios in the class.
6. Quality of report.

Click the icon below to start:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/UCB-CE170a/Fall2020/blob/master/homeworks/hw2/Assignment2.ipynb)
