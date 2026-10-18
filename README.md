# manbo-models

漫波阅读器（[A11EvEnn/manbo-reader](https://github.com/A11EvEnn/manbo-reader)）端侧 AI 模型的分发仓。模型二进制**不进主仓 git**，一律以本仓 Release 资产分发；客户端按「代码内置描述表（精确字节数 + SHA-256）」验收，多源 URL 回退。

## 模型清单

| 模型 | 文件 | 字节数 | SHA-256 | 首发 Release |
|---|---|---|---|---|
| 漫画上色（MindSpore Lite FP16） | `manga-colorize-fp16.ms` | 61590528 | `3057493683518f4093edde039168b2263fae8907d56c8c3a910ffd3f699e8a5c` | `model-pack-v1.0.0` |
| OCR 日文文本检测（MindSpore Lite） | `det.ms` | 4201696 | `983762914c892284db593589373a44ff9c23dda16f912148a613aa82b3b5bd9f` | `rawfile-pack-v1.0.0` |
| OCR 日文词典 | `japan_dict.txt` | 17332 | `1dcfcb41eec90576a945b3084f22ade11ced506e24f14879245b071698f308e8` | `rawfile-pack-v1.0.0` |
| OCR 日文文本识别（MindSpore Lite） | `rec.ms` | 9991360 | `a2be71d2ff05e00105ecb10b58fe8954f912fe7676fec07afb76c48485a425f4` | `rawfile-pack-v1.0.0` |

> 上色模型的上游来源与许可条款：🌟存疑（主仓历史引入，未留下 provenance 记录；补证后更新此处）。

## 下载地址规则

```
https://github.com/Rainbow609/manbo-models/releases/download/<tag>/<fileName>
```

## 发布流程

1. 新模型或新版本：本地计算 `stat` 字节数与 `shasum -a 256`；
2. `gh release create <tag> --repo Rainbow609/manbo-models <file>` 上传资产；
3. 回填本表与客户端 `ModelRegistry` 描述表（字节数/SHA-256/URL 数组）；
4. 客户端随版本发布生效（无远端 manifest，模型更新 = App 发版）。
