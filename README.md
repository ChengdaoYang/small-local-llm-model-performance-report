# small-local-llm-model-performance-report

This is part of a larger private project which intend to use cost effective llm to label statistical relationship between data in a graph. the test result could for useful for many individual with a single GPU set up and limited VRAM. all three model could be fitted into a 3060ti with 12gb ram and run on 100% GPU, and the Modelfile are provided. 
<img width="714" height="65" alt="image" src="https://github.com/user-attachments/assets/fe7041ef-3f21-4d08-bfc7-11b3f1be594c" />
# Model Setup and RAM Usage

| Model             | Context (ctx) | Predict (prd) | RAM Usage | Processor| 
|------------------|---------------|---------------|-----------|-----------|
| Qwen-3 8B        | 16384         | 8192          | 7.7 GB    | 100% GPU  | 
| Mistral-12B      | 8192          | 6144          | 8.5 GB    | 100% GPU  | 
| Deepseek-R1 14B  | 8192          | 6144          | 8.7 GB    | 100% GPU  |  


it seem the qwen8b is sufficient to call the tool given a limited tool set, and deepseek-r1 14b is sufficient to label the quantitative relationship. and for general relationship label qwen3 is adaqute and fast.
see report below:
# Summary Table – All Tests

| Model             | RAM Usage (GB) | Math Score | Coding Score | Step-by-Step Reasoning | Tool Order Rating | Maximum Profit             | Notes                                           |
|------------------|----------------|-----------|--------------|-----------------------|-----------------|------------------------|------------------------------------------------|
| DeepSeek-R1 14B   | 8.7            | 5/5       | 5/5          | 5/5                   | 2/5             | 3366.8 @ (66.67,10)        | Best math & coding, tool-call order weak      |
| Qwen-3 8B         | 7.7            | 4/5       | 5/5          | 3/5                   | 5/5             | 3320 @ (20,36)             | Very good tool-call sequencing, verbose outputs |
| Mistral-12B       | 8.5            | 1/5       | 1/5          | 4/5                   | 3/5             | 260 @ (20,40) ❌              | Poor math/coding, readable output, tool-call sequencing mediocre |

