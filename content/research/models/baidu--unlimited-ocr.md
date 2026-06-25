---
title: "Baidu Unlimited-OCR"
org: baidu
model_id: baidu/Unlimited-OCR
date: 2026-06-19
tags:
  - huggingface
  - image-text-to-text
  - baidu
  - vision-language
  - ocr
  - document-parsing
  - pdf-parsing
  - multilingual
  - deepseek-v2
  - custom-code
downloads: 70743
likes: 869
license: mit
pipeline: image-text-to-text
source: https://huggingface.co/baidu/Unlimited-OCR
---

# Baidu Unlimited-OCR

**One-shot long-horizon document parsing** — vision-language OCR model from Baidu (PaddlePaddle team). Aimed at pushing [DeepSeek-OCR](https://github.com/deepseek-ai/DeepSeek-OCR) further by extending "one-shot" parsing to longer documents and multi-page inputs.

## What it does

- Single-image document parsing (two configs: `gundam` and `base`)
- Multi-page document parsing across multiple images in a single forward pass
- PDF parsing via PDF→image conversion + multi-page mode
- Schema-constrained decoding (via the DeepSeek-OCR no-repeat-n-gram logit processor) to prevent output loops on long sequences
- Max sequence length: **32,768 tokens**

## Architecture

Custom transformers model based on the **DeepSeek V2** backbone (`configuration_deepseek_v2.py` in the repo). The repo ships:

- Vision encoder (`deepencoder.py`)
- Multi-modal model (`modeling_unlimitedocr.py`, `modeling_deepseekv2.py`)
- Conversation template (`conversation.py`)

The model is implemented with **trust_remote_code** — you must opt in to load it. Tested on `python 3.12.3 + CUDA 12.9` with `torch==2.10.0`, `transformers==4.57.1`.

## Release timeline

| Date | Event |
|---|---|
| 2026-06-22 | Initial release on Hugging Face and GitHub |
| 2026-06-23 | Paper posted to arXiv (`2606.23050`); mirrored on ModelScope as `PaddlePaddle/Unlimited-OCR` |
| 2026-06-24 | HF Spaces demo live (courtesy of AK) |

## Notable tags / metadata

- **Pipeline**: `image-text-to-text`
- **License**: MIT (open-weight, commercial-friendly)
- **Languages**: multilingual
- **Architecture**: DeepSeek V2 backbone with custom vision encoder and OCR-specific decoding
- **Use case**: long-horizon OCR / document parsing — addresses the "one-shot" limit of prior OCR models

## How to use

```python
from transformers import AutoModel, AutoTokenizer
import torch

model_name = 'baidu/Unlimited-OCR'
tokenizer = AutoTokenizer.from_pretrained(model_name, trust_remote_code=True)
model = AutoModel.from_pretrained(
    model_name,
    trust_remote_code=True,
    use_safetensors=True,
    torch_dtype=torch.bfloat16,
).eval().cuda()

# Single image, gundam config
model.infer(tokenizer, prompt='<image>document parsing.',
            image_file='your_image.jpg', base_size=1024,
            image_size=640, crop_mode=True, max_length=32768,
            no_repeat_ngram_size=35, ngram_window=128, save_results=True)
```

The model also ships an [SGLang server recipe](https://huggingface.co/baidu/Unlimited-OCR) for production serving.

## Benchmarks

No quantitative benchmark tables are published in the model card. The repo points to the [arXiv paper](https://arxiv.org/abs/2606.23050) ("Unlimited OCR Works") for evaluation details. The model's value proposition — long-horizon one-shot parsing — is showcased in the `assets/long-horizon-ocr.gif` demo in the repo.

## See also

- [[welcome]]
- Paper: https://arxiv.org/abs/2606.23050
- GitHub: https://github.com/baidu/Unlimited-OCR
- Demo: https://huggingface.co/spaces/baidu/Unlimited-OCR
