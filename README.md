# 🧩 ConeDent AI Metrix 安装说明  
**—— T-Mamba 牙科 CBCT 分割插件（基于 3D Slicer）**

---
### 📹 插件演示视频

👉 [点击此处观看演示视频](./demo_20240519.mp4)


## 一、🌱 环境要求

| 组件           | 要求说明                                           |
|----------------|----------------------------------------------------|
| 🖥 操作系统     | Windows / Linux / macOS（推荐：WSL 或原生 Linux）   |
| 🐍 Python       | Python 3.9（建议使用 Conda 虚拟环境）              |
| ⚙️ GPU支持      | 支持 NVIDIA CUDA（建议 CUDA 11.8）                 |
| 🧠 框架         | PyTorch ≥ 2.0.1，TorchVision ≥ 0.15.2              |
| 🧊 3D Slicer    | 建议版本 ≥ 5.2（安装 Scripted Module 插件）       |
| 📦 环境管理工具 | 推荐使用 Anaconda                                 |

---

## 二、🛠 安装 T-Mamba 依赖环境

### 1. 安装 Anaconda  
👉 官网地址：[https://www.anaconda.com](https://www.anaconda.com)

---

### 2. 创建并激活 Conda 虚拟环境  

```bash
conda create -n cbct python=3.9 -y
conda activate cbct
```

---

### 3. 安装依赖库  

你可以使用以下命令一键安装：

```bash
pip install -r requirements.txt
```

或者逐条安装（仅供参考）：

```bash
pip install \
    batchgenerators==0.25 \
    einops==0.7.0 \
    matplotlib==3.4.3 \
    ml_collections==0.1.1 \
    monai==1.3.0 \
    nibabel==5.2.0 \
    nni==3.0 \
    numpy==1.24.1 \
    opencv_python==4.8.1.78 \
    Pillow==10.2.0 \
    pydensecrf==1.0rc3 \
    scipy==1.11.4 \
    SimpleITK==2.2.1 \
    Surface_Distance_Based_Measures==0.1 \
    tifffile==2023.7.10 \
    timm==0.9.12 \
    torch==2.0.1+cu118 \
    torchtoolbox==0.1.8.2 \
    torchvision==0.15.2+cu118 \
    tqdm==4.65.0
```

---

## 三、🚀 插件使用说明（简略）

1. 启动 3D Slicer，点击菜单 `Edit > Application Settings > Modules`，添加插件路径。
2. 进入插件名为 “**ConeDent AI Metrix**” 的模块。
3. 按照界面提示：
   - 选择输入 CBCT 文件（`.nii.gz` 或 `.nrrd`）
   - 设置输出路径
   - 点击“执行”开始推理，等待完成。

---

## 四、🎯 设计重点与难点

- **Slicer集成与模型解耦**：将重模型计算逻辑与 Slicer 插件结构解耦，实现前端与后端清晰分离，方便维护与拓展。
- **路径与格式兼容性**：需支持医学图像常见格式（NIfTI, NRRD），并保证输入输出路径稳定传递。
- **跨平台推理适配**：考虑 Windows / WSL / Linux 等系统环境的兼容性，尤其是路径格式与环境激活方式差异。
- **大型模型资源控制**：T-Mamba 模型参数庞大，加载时需避免卡死 UI，故采用异步命令触发运行。
- **使用门槛降低**：尽可能通过图形化简化操作步骤，使医学用户无需编程背景也能完成操作。




