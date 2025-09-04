---
title: 'Solve the issue of "TqdmWarning: IProgress not found"'
date: 2025-04-19 21:43:11 +0800
categories: [issue]
tags: [transformers, hugging-face, tqdm]
---
## Description

When using models from Hugging Face, we typically import the libraries with from transformers import *. However, doing so often triggers the warning: "TqdmWarning: IProgress not found. Please update Jupyter and ipywidgets."

## Solution

To resolve this, simply use the following command to update ipywidgets:

```shell
pip install ipywidgets -U
```
