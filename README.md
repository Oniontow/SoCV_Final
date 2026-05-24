# SoCV_Final
SoCV Final Project -- RTL Verilog Debugger

## Overview
This project provides a notebook-based workflow for RTL Verilog debugging.

## Contents
- verilog_debugging_agent.ipynb: main notebook

## Requirements
- Kaggle Notebook environment
- GPU: T4 x2 (required)
- Internet: On (required)

## Kaggle Setup
1. Create a new Kaggle Notebook and upload this repository, or add it as a data source.
2. In the notebook settings, select GPU and choose T4 x2.
3. Turn Internet access On.
4. Open verilog_debugging_agent.ipynb and run cells from top to bottom.

## Flow Architecture
1. Environment setup installs required packages and downloads the GGUF model and sample data.
2. The model is loaded to GPU via llama-cpp-python and a helper function wraps chat inference.
3. Multiple specialized debug agents each scan the line-numbered RTL for a single error class.
4. A supervisor agent synthesizes findings and outputs a corrected, complete Verilog module.
5. The pipeline runs on all code*.v/vode*.v files and writes *_clean.v outputs.

## Model Choice
- Runtime: llama-cpp-python with GPU offload.
- Default GGUF model: Qwen3-14B-Claude-4.5-Opus-Distill.q8_0.gguf (downloaded in the notebook).
- You can replace the GGUF file with another model and adjust the load path if needed.

## Testbench
- The testbench uses CVSD past exam questions (archived problems).
- In informal evaluation, human reviewers typically found only about half of the injected errors.

## Notes
- If you run locally, you may need to adjust paths and dependencies to match your environment.

