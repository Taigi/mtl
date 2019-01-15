# Multi-Task Learning project
Unofficial implimitation of Multi-task learning using uncertainty to weigh losses for scene geometry and semantics [[arXiv](https://arxiv.org/abs/1705.07115)].

## Results
### Examples
|        Input        | Label <br>segmentation  |Instance <br>segmentation|       Depth         |
|:-------------------:|:-------------------:|:-------------------:|:-------------------:|
|<img width="200px" src='inputs/Pedestrian_crossing_0.png'>|<img src='results/resNet_label_instance_disp/label_Pedestrian_crossing_0.png' width="200px">|<img src='results/resNet_label_instance_disp/instance_Pedestrian_crossing_0.png' width="200px">|<img src='results/resNet_label_instance_disp/disp_Pedestrian_crossing_0.png' width="200px">|
|<img width="200px" src='inputs/Pedestrian_crossing_1.png'>|<img src='results/resNet_label_instance_disp/label_Pedestrian_crossing_1.png' width="200px">|<img src='results/resNet_label_instance_disp/instance_Pedestrian_crossing_1.png' width="200px">|<img src='results/resNet_label_instance_disp/disp_Pedestrian_crossing_1.png' width="200px">|
|<img width="200px" src='inputs/bicycle_0.png'>|<img src='results/resNet_label_instance_disp/label_bicycle_0.png' width="200px">|<img src='results/resNet_label_instance_disp/instance_bicycle_0.png' width="200px">|<img src='results/resNet_label_instance_disp/disp_bicycle_0.png' width="200px">|
|<img width="200px" src='inputs/bicycle_1.png'>|<img src='results/resNet_label_instance_disp/label_bicycle_1.png' width="200px">|<img src='results/resNet_label_instance_disp/instance_bicycle_1.png' width="200px">|<img src='results/resNet_label_instance_disp/disp_bicycle_1.png' width="200px">|
|<img width="200px" src='inputs/bus_0.png'>|<img src='results/resNet_label_instance_disp/label_bus_0.png' width="200px">|<img src='results/resNet_label_instance_disp/instance_bus_0.png' width="200px">|<img src='results/resNet_label_instance_disp/disp_bus_0.png' width="200px">|
|<img width="200px" src='inputs/bus_1.png'>|<img src='results/resNet_label_instance_disp/label_bus_1.png' width="200px">|<img src='results/resNet_label_instance_disp/instance_bus_1.png' width="200px">|<img src='results/resNet_label_instance_disp/disp_bus_1.png' width="200px">|
|<img width="200px" src='inputs/parking_0.png'>|<img src='results/resNet_label_instance_disp/label_parking_0.png' width="200px">|<img src='results/resNet_label_instance_disp/instance_parking_0.png' width="200px">|<img src='results/resNet_label_instance_disp/disp_parking_0.png' width="200px">|
|<img width="200px" src='inputs/parking_1.png'>|<img src='results/resNet_label_instance_disp/label_parking_1.png' width="200px">|<img src='results/resNet_label_instance_disp/instance_parking_1.png' width="200px">|<img src='results/resNet_label_instance_disp/disp_parking_1.png' width="200px">|
|<img width="200px" src='inputs/truck_0.png'>|<img src='results/resNet_label_instance_disp/label_truck_0.png' width="200px">|<img src='results/resNet_label_instance_disp/instance_truck_0.png' width="200px">|<img src='results/resNet_label_instance_disp/disp_truck_0.png' width="200px">|
|<img width="200px" src='inputs/truck_1.png'>|<img src='results/resNet_label_instance_disp/label_truck_1.png' width="200px">|<img src='results/resNet_label_instance_disp/instance_truck_1.png' width="200px">|<img src='results/resNet_label_instance_disp/disp_truck_1.png' width="200px">|

### Single vs. Dual vs. All
Task quantitative result per epoch

|Label segmentation   |Instance segmentation|       Depth         |
|:-------------------:|:-------------------:|:-------------------:|
|<img src='images/graphs/label.png' width="280px">|<img src='images/graphs/instance.png' width="280px">|<img src='images/graphs/disp.png' width="280px">|

Compression to paper quantitative results

|                            |     |        |      |Label segmentation   |Instance segmentation|       Depth         |
|----------------------------|:---:|:------:|:----:|:-------------------:|:-------------------:|:-------------------:|
|loss                        |Label|Instance|Depth |IoU [%]              |RMS error            |RMS error            |
|Label only                  |V    |X       |X     |0.4345/ <span style="color:blue"> 43.1 </span>          |X                    |X                    |
|Instance only               |X    |V       |X     |X                    |3.4128/4.61(paper)          |X                    |
|Depth only                  |V    |X       |V     |X|X|0.7005/0.783|
|Unweighted sum of losses    |0.333|0.333   |0.333 |43.6(paper)|3.92(paper)|0.786(paper)|
|Approx. optimal weights     |0.8  |0.05    |0.15  |46.3(paper)|3.92(paper)|0.799(paper)|
|2 task uncertainty weighting|V    |V       |X|0.4298/46.5(paper)|3.3185/3.73(paper)|X|
|2 task uncertainty weighting|V    |X       |V|0.4327/46.2(paper)|X|0.7118/0.714(paper)|
|2 task uncertainty weighting|X    |V       |V|X|3.2853/3.54(paper)|0.7166/0.744(paper)|
|3 task uncertainty weighting|V    |V       |V|0.4287/46.6(paper)|3.3183/3.91(paper)|0.7102/0.702(paper)|

## Setup

**Inferene:**<br>
1. Download the pre-trained network folder ([resNet_label_instance_disp](https://drive.google.com/drive/folders/1gjhkFlxH0OEsOVD1YFaxrM_fWfpH1eEv?ogsrc=32)) and save it in `trained_nets`.
2. Download the pre-trained resNet-101 folder ([res_net_101_ckpt](https://drive.google.com/drive/folders/1gjhkFlxH0OEsOVD1YFaxrM_fWfpH1eEv?ogsrc=32)) and save it in the main project folder.
3. Put yor wanted input images in `inputs`.
4. Run `inference.py`.
4. Your results will be saved in `results`.




