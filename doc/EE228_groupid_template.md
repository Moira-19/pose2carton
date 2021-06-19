# Pose2Carton

EE228 课程大作业，利用3D骨架控制3D卡通人物（https://github.com/Moira-19/pose2carton）

数据组别：32

数据类型：20组匹配


# maya环境配置

由于本次实验只匹配模型，未进行蒙皮，故不需安装maya。


# 匹配流程

（1）transfer.py是关节点匹配主函数。其中，每一对配对i:j,表示待匹配模型的关节点i对应给定模型的关节点j，一一对应，至少10个，至多取决于待匹配模型关节点数。第一遍可随机匹配关节点（至少10个），运行transfer.py，输出关节点对应名称与序号；

```python
manual_model_to_smpl = {0:0,1:1,2:2,3:3,4:4,5:5,6:6,7:7,8:8,9:9,10:10}
```

（2）得到输出的关节点对应的名称与序号后，将待匹配模型的关节点与给定模型的关节点一一对应；

（3）再次运行transfer.py，将关节点匹配上；

（4）vis.py实现可视化，输出匹配结果.pkl，将匹配情况存为图像和mp4。修改好vis.py结果文件存储路径，运行即可生成匹配.png和.mp4，若图片和视频中两个模型动作一致，则匹配成功。

```python
#transfer_one_frame("samples/Ch14_nonPBR.txt", use_online_model=True)
transfer_one_sequence("fbx/7527.txt", "info_seq_5.pkl", use_online_model=False)
```


# 新增脚本说明

vis.py在未完全确认关节点完全匹配正确、模型动作一致时，可以稍作修改，先不生成图像视频，只打开visualizer窗口观察，具体操作即注释掉：

```python
line96 | visualizer.capture_screen_image(vis_save_path, True)
```

便可快速运行vis.py观察匹配是否正确，方便及时纠错，提高效率。若匹配成功需要生成图像视频，取消注释即可。



# 项目结果

以待匹配模型7527.fbx为例：

![image](../img/80.png)


