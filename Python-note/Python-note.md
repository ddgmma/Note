# 1.Python里的类

## 什么是类（Class）

* **类就像是一张汽车的设计图纸**
* 它描述了汽车应该有什么特征（如颜色、品牌、型号）和功能（如启动、加速、刹车）
* 设计图纸本身不是一辆真正的车，它只是告诉工厂如何制造汽车

## 什么是对像（Object）

* **对象是按照设计图纸实际造出来的汽车**
* 它是真实存在的，你可以看到、触摸、驾驶它
* 每辆汽车都是根据同样的设计图纸制造的，但每辆车的具体信息可能不同（比如一辆是红色宝马，另一辆是蓝色奔驰）

**原课程视频：**https://www.bilibili.com/video/BV1Jgf6YvE8e/?p=28&spm_id_from=333.1007.top_right_bar_window_history.content.click&vd_source=61cb9c3e4f6ef179a6e53d726700a1b1

## Python创建虚拟环境

```bash
# 1. 创建虚拟环境（项目根目录执行）；“.venv”是虚拟环境名称，可以修改
python -m venv .venv 

# 2. 激活环境
# macOS/Linux:
source .venv/bin/activate
# Windows (CMD):
venv\Scripts\activate.bat
# Windows (PowerShell):
venv\Scripts\Activate.ps1
```

