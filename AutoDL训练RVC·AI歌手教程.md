
# 1-从如下页面创建实例（预先准备好2元预算，如果数据量小（例如半小时）5毛也行）

https://www.codewithgpu.com/i/RVC-Project/Retrieval-based-Voice-Conversion-WebUI/RVC_WebUI

<img src="https://user-images.githubusercontent.com/129054828/236987373-d46723c2-66c7-4601-997f-b6227de5e8b1.png" width = "1000" height = "550" alt="" align=center />

<img src="https://user-images.githubusercontent.com/129054828/236987380-3ebe27cf-9873-4e10-a607-50d9273655c5.png" width = "1000" height = "300" alt="" align=center />


# 2-后台输入页面中的命令启动webui

jupyterlab->打开终端->ctrl+v黏贴命令

![2a](https://user-images.githubusercontent.com/129054828/236987803-3ae74d14-6654-4b70-81d4-75496cee6b18.png)

<img src="https://user-images.githubusercontent.com/129054828/236987810-4573a77f-027e-4b0e-805c-48d75003a37a.png" width = "500" height = "400" alt="" align=center />
<img src="https://user-images.githubusercontent.com/129054828/236987814-23e93c93-8c81-4892-8784-68e8e02dcb85.png" width = "600" height = "340" alt="" align=center />

# 3-启动完成后自定义服务进入前端页面

![3](https://user-images.githubusercontent.com/129054828/236988726-00a5d406-1ebc-4c3c-bc16-1fb7fd82f515.png)


# 4-（可选前置）使用HP2或HP5模型进行人声提取伴奏去除（HP5去除和声和伴奏幅度更大，但是主人声更容易丢失）。填写输入音频素材和输出人声文件夹的路径。

![4-前置-提取人声](https://user-images.githubusercontent.com/129054828/236988025-bd622125-d2a1-4023-af4c-15d66ad9b652.png)

# 5-上传训练集，填写实验名和上一步输出的训练集路径，点击一键训练

上传训练集：直接jupterlab左侧新建训练文件夹，从本地拖动文件进去，复制路径即可，但注意复制的路径不带/root/，要手工加上

![5a-上传训练集音频，本地文件拖动至目标文件夹即可](https://user-images.githubusercontent.com/129054828/236988372-cc950be3-7ffa-479d-905c-693c02f12bc0.png)
![5b-复制训练集路径](https://user-images.githubusercontent.com/129054828/236988378-9a884792-33ac-4805-a56a-34378873a8bb.png)

填写实验名，训练集路径，一键训练

![5c-一键训练](https://user-images.githubusercontent.com/129054828/236988492-41abad98-2b6d-4e89-bebf-2ea7cedc18f7.png)

这是训练完了

![5d-后台训练中-已训练完成](https://user-images.githubusercontent.com/129054828/237048384-f1433625-54ba-4bc5-b324-242d25158293.png)

# 6-下载推理用模型和索引

weights/xxx.pth

logs/xxx/added_xxxx.index

这2个文件需要备份。
