# JBBC-Bayer-Bin-Correction-Net

软件明天发，权重还在训练完善

<img width="1314" height="1044" alt="6a3198f4db7b51579514ecc67ff8b7c4" src="https://github.com/user-attachments/assets/c32b6829-012f-4ed5-81c9-6299b50565d9" />

<!-- current-weights:start -->
## 当前权重

`model.pth` 为 JDN304061 初始化分支在 **60,000 步**的验证最优推理权重（2026-11-10 更新），采用纯 PyTorch `state_dict`，337 个张量、3,220,131 个参数，不含优化器或训练状态。

**兼容性：** 当前模型为 `JDNInitializedRGB`（Gaussian9 / PTC32，30 通道输入层），与此前的 5 通道随机初始化 JBBC 权重不兼容。输入为四平面 RGGB 打包 RAW，并需匹配尺度的噪声参数 α、β；输出为线性 RGB。推理实现随软件提供，此仓库当前仅提供权重。

固定 120 张 SB 开发照片、未裁值线性 RGB PSNR；均分沿用无噪声、ISO100、ISO1600、ISO12800 四项，ISO25600 单独报告。当前分支最优不代表所有历史分支的最高均分，也不是独立测试集排名。

| 条件 | PSNR / dB |
|---|---:|
| 四档均分 | 39.17419 |
| 无噪声 | 39.63875 |
| ISO100 | 39.88687 |
| ISO1600 | 39.32881 |
| ISO12800 | 37.84231 |
| ISO25600 | 37.05693 |

SHA-256：`889e4b412b4fd802ca3e6830efc650628f30056573d248e65fab43fb2599ecdb`

### 上游来源与权重许可

本权重经本项目 JDN304061 检查点继续训练，继承 SamsungLabs [unified-demosaicing](https://github.com/SamsungLabs/unified-demosaicing) 的 ESUM 实现及官方 ISO3200 预训练权重。上游作者：SaiKiran Tedla、Abhijith Punnappurath、Luxi Zhao、Michael S. Brown；Copyright (c) 2025 Samsung Electronics Co., Ltd.。引用：*Examining Joint Demosaicing and Denoising for Single-, Quad-, and Nona-Bayer Patterns*, ICCP 2025。

本项目修改包括 Gaussian9 幅度归一化、PTC32 噪声条件，以及普通 RGGB 同色四读平均后的联合重建训练。与上游原始权重不同，不代表三星认可或支持本项目。

本次发布的 `model.pth` 按 **CC BY-NC-SA 4.0** 提供，限非商业用途；再分发需署名、说明修改并遵守相同方式共享条件。完整许可与免责声明见 [WEIGHTS_LICENSE.txt](WEIGHTS_LICENSE.txt)，上游总许可见 [LICENSE.MD](https://github.com/SamsungLabs/unified-demosaicing/blob/main/LICENSE.MD)。上游部分源码文件头写 CC BY-NC 4.0，本次发布保留并遵守仓库总许可中的 NC-SA 条件；本权重许可不替代未来软件各组件的独立许可。
<!-- current-weights:end -->
