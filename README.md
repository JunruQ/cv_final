# Computer Vision: Object Reconstruction and Novel View Synthesis

本仓库包含两个神经场重建方法的使用示例：**TensoRF** 和 **Gaussian Splatting**。分别对应各自的数据准备方式和训练、测试脚本。

---

## 📁 数据准备

### TensoRF

请将数据按如下结构放入仓库目录：

```
.
├── data/
│   ├── mages/                      # 注意拼写为 mages（TensoRF 中 colmap2nerf.py 的一个小错误）
│   ├── transforms_train.json
│   ├── transforms_val.json
│   └── transforms_test.json
```

⚠️ 由于 `colmap2nerf.py` 脚本中的小错误，请确保将 `images/` 文件夹重命名为 `mages/`。

---

### Gaussian Splatting

请将数据按如下结构放置：

```
.
├── data/
│   ├── images/                     # 包含输入图像
│   └── sparse/                     # COLMAP 输出的 sparse 模型
```

---

## 🚀 训练与测试

### TensoRF

- 启动训练：

```bash
python train.py --config configs/your_own_data.txt
```

- 训练完成后将自动生成测试结果。

---

### Gaussian Splatting

- 启动训练：

```bash
python train.py -s data/ --eval --checkpoint_iterations 30000
```

- 测试渲染：

```bash
python render.py -m output/<folder_name>/
```

- 评估结果：

```bash
python metrics.py -m output/<folder_name>/
```

---

## 📌 说明

- 若使用自己的数据，推荐先通过 COLMAP 对图像进行重建，再生成对应的 `transforms_*.json` 或 `sparse/` 文件夹。
- 更多详细参数请参考各自方法的官方文档或源码注释。

---

欢迎提交 Issue 或 PR 以优化数据处理或兼容性问题。🎉
