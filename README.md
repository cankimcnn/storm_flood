# 河南省中小流域设计暴雨洪水自动查算

## 项目介绍
暂可用于河南省山丘区200平方公里以内的小流域设计暴雨洪水自动查算（采用推理公式法）。200~1000平方公里的山丘区、平原区计算程序敬请期待。

前端界面采用响应式布局，可支持移动端。

## 开发环境

python 3.6.8

第三方包详见 requirements.txt

### 环境安装步骤（推荐使用虚拟环境，指定 Python 3.6）

1. 确认已安装 Python 3.6（如路径为 `C:\Users\lovec\AppData\Local\Programs\Python\Python36\python.exe`）。
2. 在项目根目录下，使用 Python 3.6 创建虚拟环境：

```bash
C:\Users\lovec\AppData\Local\Programs\Python\Python36\python.exe -m venv env
```

3. 激活虚拟环境（Windows jincancan从此开始）：

```bash
env\Scripts\activate
```

4. 安装依赖包（jincancan已安装）：

```bash
pip install -r requirements.txt
```
5. 执行
```bash
python app.py
```
## 使用概述

当前用户名：admin， 密码：admin

### 1、输入流域参数：
* 中心坐标点（或者在内嵌的高德地图上选择坐标点）
* 流域面积 F 平方公里
* 干流长度 L 公里
* L 上面的平均比降 J

根据以上的流域参数，可自动查相关暴雨等值线图获取暴雨参数

### 2、设置设计频率并校核暴雨参数
如果是移动端或小屏幕使用，建议设计频率不超过6个，不然成果表可能会超出显示范围。

每个自动计算的参数之后均有原始等值线（或关系）图表，若发现暴雨参数异常，可查看原始图表，根据实际情况对以上自动获取的暴雨参数做校核调整

### 3、计算结果展示

## 各 Python 文件功能说明

### app.py
Web应用主入口，基于Flask，负责路由、参数处理、页面渲染和会话管理。

### cores/
- __init__.py：包标识，无实际内容。
- calc.py：暴雨洪水计算主类，封装各类计算属性和流程。
- calc_common.py：核心水文计算函数库，包括频率、雨量、洪峰流量等的计算。
- chart.py：暴雨参数、关系曲线等查图与相关计算。
- db_info.py：暴雨、水文等分区、等值线、关系曲线等信息的组织与数据库接口。
- hydrology.py：水文统计分布（如P-III型）相关计算。
- tables.py：数据库ORM定义，负责area、contour、relationship三类表的操作。
- topology.py：空间拓扑与点多边形关系、象限等空间辅助函数。
- trans.py：数据文件与数据库的转换、投影变换、批量导入等工具。
- utils.py：通用工具函数，如路径创建等。
- conf.py：投影参数配置，定义地图投影方式。

