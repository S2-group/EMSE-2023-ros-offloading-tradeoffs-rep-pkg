# Empirical Evaluation of Computation Offloading Strategies in Robotic Systems

This repository contains raw data outputs and complete data analysis of the results obtained in the empirical experiments conducted with the purpose of evaluation 
of computation offloading strategies in ROS-based systems. The experiments are conducted as a part of a Computer Science MSc thesis at Vrije Universiteit Amsterdam.

The repository consists of three main directories:
- **figures**: bar chart figures in *pdf* format created as outputs of data analysis. All figures in this direcotory are imported in the thesis paper, where they are thoroughly explained;
- **raw_data**: raw outputs of the experiments in *csv* format. The entire content of this direcotory is the direct output of the experiment conducted via the Robot Runner experiment orchestration tool. For tool configuration and further details, the reader is referred to [this](https://github.com/minana96/robot-runner) GitHub repository;
- **statistical_tests**: R project containing the source code of R markdown notebooks in *Rmd* format, along with the HTML visualisation of the notebooks in 
*nb.html* format. Notebooks document the complete data analysis process and the R source code used for statistical analysis. The analysis is conducted with R version 4.1.1 on Ubuntu 18.04.5.

## Repository structure

Each of the three main directories is structured in the subdirectories which represent the independent experiments conducted in the study:
- **unknown_map_experiment**: experiment that evaluates the effect of computation offloading strategies on performance and energy efficiency of ROS-based systems. 
To that aim, SLAM, navigation and object recognition are either offloaded or executed on-board the robot. The tasks are implemented in [gmapping](http://wiki.ros.org/gmapping), [move_base](http://wiki.ros.org/move_base) and [find_object_2d](http://wiki.ros.org/find_object_2d) ROS packages, respectfully;
- **known_map_experiment**: experiment that evaluates the effect of computation offloading strategies on performance and energy efficiency of ROS-based systems. 
To that aim, localisation, navigation and object recognition are either offloaded or executed on-board the robot. The tasks are implemented in [amcl](http://wiki.ros.org/amcl), [move_base](http://wiki.ros.org/move_base) and [find_object_2d](http://wiki.ros.org/find_object_2d) ROS packages, respectfully;
- **resolution_effect**: experiment that evaluates the effect of *image resolution* parameter on performance and energy efficiency of ROS-based systems;
- **frame_rate_effect**: experiment that evaluates the effect of *image frame rate* parameter on performance and energy efficiency of ROS-based systems;
- **particles_effect**: experiment that evaluates the effect of *particles* parameter in *gmapping* on performance and energy efficiency of ROS-based systems;
- **temporal_updates_effect**: experiment that evaluates the effect of *temporalUpdate* parameter in *gmapping* on performance and energy efficiency of ROS-based systems;
- **velocity_samples_effect**: experiment that evaluates the effect of *vx_samples* and *vth_samples* parameters in *local_planner* plugin in *move_base* (implemented in [dwa_local_planner](http://wiki.ros.org/dwa_local_planner) ROS package) on performance and energy efficiency of ROS-based systems;
- **sim_time_effect**: experiment that evaluates the effect of *sim_time* parameter in *local_planner* plugin in *move_base* (implemented in [dwa_local_planner](http://wiki.ros.org/dwa_local_planner) ROS package) on performance and energy efficiency of ROS-based systems.

## Raw data outputs

As noted above, each subdirectory in *raw_data* directory contains raw *Robot Runner* data outputs for each of the eight experiments. The structure of each subdirectory is as follows:

    <experiment subdirectory>
     .
     |
     |--- run_1/                                        The results for run 1 of the experiment
     |      |--- find_object_2d_results.csv
     |      |--- move_base_results.csv
     |      |--- network.csv
     |      |--- power.csv
     |      |--- resources.csv
     |
     |
     ...
     |
     |
     |--- run_<n>/                                      The results for run <n> of the experiment                                                      
     |      |--- find_object_2d_results.csv
     |      |--- move_base_results.csv
     |      |--- network.csv      
     |      |--- power.csv
     |      |--- resources.csv
     |
     |
     |
     |--- run_table.csv                                 Aggregated experiment results


Outputs of the independent experiment runs are contained within dedicated folders (*run_1* to *run_<n>*, whereas n stands for 80 in *unknown_map_experiment* and *known_map_experiment*, but 20 in *resolution_effect*, *frame_rate_effect*, *particles_effect*, *temporal_updates_effect*, *velocity_samples_effect* and *sim_time_effect* experiments). Each run directory contains outputs of five different profilers in *csv* format. For further details regarding profilers and their purpose, the reader is referred to [this](https://github.com/minana96/robot-runner) GitHub repository. The aggregated results per experiment run are represented within *run_table.csv* file. The statistical data analysis is conducted on the results in *run_table.csv* file for each respective experiment.
  
## Data analysis
  
As noted above, each subdirectory in *statistical_tests* directory contains R notebooks with complete statistical analysis for each of the eight experiments. The structure of each subdirectory is as follows:  

    <experiment subdirectory>
     .
     |
     |--- CPU_usage.Rmd                           Average CPU usage                                       
     |
     |--- Detection_result_delay.Rmd              Average object detection result delay
     |
     |--- Detection_time.Rmd                      Average object detection time
     |
     |--- Energy.Rmd                              Total energy consumption
     |
     |--- Extraction_time.Rmd                     Average feature extraction time
     | 
     |--- Mission_execution_time.Rmd              Total mission execution time
     |
     |--- Navigation_time.Rmd                     Average navigation time
     |
     |--- Number_of_packets.Rmd                   Total number of network packets
     |
     |--- RAM_utilisation.Rmd                     Average RAM utilisation
     |
     |--- Size_of_packets.Rmd                     Total size of network packets

      
The statistical analysis for each of the ten dependent experiment variables, containing R source code for statistical analysis accompanied with rational and explanation in R markdown, is organised within separate R notebook, in *Rmd* format. Each R notebook is also available as HTML output in *nb.html* format for visualisation in Web browsers.
  
