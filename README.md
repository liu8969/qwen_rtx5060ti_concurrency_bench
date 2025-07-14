# qwen_rtx5060ti_concurrency_bench
# 使用`https://github.com/liu8969/VllmTester`得到测试结果
# 5060ti 16gb 单卡 qwen3 14b awq
## vllm 最佳启动参数
~~~
vllm serve \
/home/liu/.cache/modelscope/hub/models/Qwen/Qwen3-14B-AWQ \
  --host 0.0.0.0 \
  --port 8000 \
  --served-model-name Qwen3-14B-AWQ \
  --trust-remote-code \
  --max-model-len 20000 \
  --max_num_seqs=64 \
  --block-size 16  \
  --dtype float16 \
  --gpu-memory-utilization 0.85\
  
~~~
## 结果
### 32并发
~~~
🚀 启动 vLLM 压力测试
├─ 模型: Qwen3-14B-AWQ
├─ 端点: http://localhost:8000/v1/completions
├─ 请求数: 256
├─ 并发数: 32
├─ 最大token数: 512
├─ 温度: 0.7
└─ Top-p: 0.95

📋 示例提示:
  1. 解释量子纠缠的概念
  2. 写一首关于秋天的诗
  3. 如何提高深度学习模型的准确率？
  ... 和另外 253 个提示

📊 测试结果:
├─ 总时间: 128.56秒
├─ 成功: 256/256
├─ 失败: 0/256
├─ 总token数: 119504
├─ 请求吞吐量: 1.99 请求/秒
└─ Token吞吐量: 929.56 token/秒


~~~
### 64并发
~~~
🚀 启动 vLLM 压力测试
├─ 模型: Qwen3-14B-AWQ
├─ 端点: http://localhost:8000/v1/completions
├─ 请求数: 256
├─ 并发数: 64
├─ 最大token数: 512
├─ 温度: 0.7
└─ Top-p: 0.95

📋 示例提示:
  1. 解释量子纠缠的概念
  2. 写一首关于秋天的诗
  3. 如何提高深度学习模型的准确率？
  ... 和另外 253 个提示

📊 测试结果:
├─ 总时间: 133.78秒
├─ 成功: 256/256
├─ 失败: 0/256
├─ 总token数: 120662
├─ 请求吞吐量: 1.91 请求/秒
└─ Token吞吐量: 901.96 token/秒


~~~
### 96并发
~~~
🚀 启动 vLLM 压力测试
├─ 模型: Qwen3-14B-AWQ
├─ 端点: http://localhost:8000/v1/completions
├─ 请求数: 256
├─ 并发数: 96
├─ 最大token数: 512
├─ 温度: 0.7
└─ Top-p: 0.95

📋 示例提示:
  1. 解释量子纠缠的概念
  2. 写一首关于秋天的诗
  3. 如何提高深度学习模型的准确率？
  ... 和另外 253 个提示

📊 测试结果:
├─ 总时间: 148.96秒
├─ 成功: 256/256
├─ 失败: 0/256
├─ 总token数: 120400
├─ 请求吞吐量: 1.72 请求/秒
└─ Token吞吐量: 808.27 token/秒

~~~
