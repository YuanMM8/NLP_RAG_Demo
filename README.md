# Retrieval Augmented Generation (RAG) Intro Project 🤖🔍📝

**RAG教学示例项目**  本demo演示了RAG的基本流程。使用了[LlamaIndex](https://github.com/run-llama/llama_index)框架，也欢迎使用其它框架如[LangChain](https://www.langchain.com/)等进行实验。

## Project Structure 📂

- `README.md`: 项目总览
- `Intro of Retrieval Augmented Generation (RAG) and application demos_Henry.pdf`: 实验背景知识介绍

- **code**:  文件夹下包含三个教学实验，三个实验均有各自对应的.ipynb,.py以及.sh，可直接运行；同时提供了在[KDD CUP 2024 CRAG:Comprehensive Rag Benchmark](https://www.aicrowd.com/challenges/meta-comprehensive-rag-benchmark-kdd-cup-2024)的训练集上的测试以及结果评测脚本。
  - `1_Basic_RAG_Pipeline`: 基础的pipeline演示；
  - `2_Sentence_window_retrieval`: 理解句子窗口与基础pipeline的差异；
  - `3_Auto-merging_Retrieval`: 理解自动合并检索对生成结果带来的改进；
  - `model_response.py`: 提供了API访问和本地部署LLM两种方式，选择本地部署的同学可以进一步改造代码，使用`vllm`框架加速推理；
  - `crag.sh`: [KDD CUP 2024 CRAG:Comprehensive Rag Benchmark](https://www.aicrowd.com/challenges/meta-comprehensive-rag-benchmark-kdd-cup-2024)训练集的测试脚本；
  - `metric.py`: 评测脚本，计算模型生成内容与标答的BLEU和Rouge-l指标；
- **data**: 实验所需的语料，包括：
  - `Henry.txt`: 示例文件 `Henry.txt`
  - [KDD CUP 2024 CRAG:Comprehensive Rag Benchmark](https://www.aicrowd.com/challenges/meta-comprehensive-rag-benchmark-kdd-cup-2024)训练集。为方便使用，进行了简单的html标签去除，并提供全量2735条数据和200条子集。

## Getting Started 🚀

1. 克隆或下载项目仓库到本地：
```shell
  git clone https://github.com/ZhaoFangkun1/NLP_RAG_Demo.git
```

2. 阅读`Intro of Retrieval Augmented Generation (RAG) and application demos_Henry.pdf`文件，了解RAG基本原理和实验背景知识

3. 准备环境：
```shell
  conda create -n rag python=3.10
  conda activate rag
  pip install llama_index
  pip install llama-index-embeddings-huggingface
```

4. 进入`code`文件夹，依次运行三种实验脚本
```shell
cd code
1. sh Basic_RAG_Pipeline.sh
2. sh Sentence_window_retrieval.sh
3. sh Auto-merging_Retrieval.sh
```

5.更改数据为[CRAG](https://www.aicrowd.com/challenges/meta-comprehensive-rag-benchmark-kdd-cup-2024)数据集进行测试，同时也可尝试其它的数据集
```shell
sh crag.sh
python metric.py
```

## 附加说明 
1. 项目主体来自[Retrieval-Augmented-Generation-Intro-Project](https://github.com/HenryHengLUO/Retrieval-Augmented-Generation-Intro-Project/blob/main/README.md)。本项目对llama_index的最新版本进行了适配。
1. 一些免费的API申请地址如：[百度千帆](https://console.bce.baidu.com/qianfan/overview)、[阿里云](https://help.aliyun.com/zh/dashscope/developer-reference/?spm=a2c4g.11186623.0.0.644e9b6em7thMV)等。当前的demo使用了百度千帆提供的Yi-34B-Chat的接口(限时免费)，需要自行申请API Key和Secret Key，并在代码中相应位置替换。
2. 鼓励尝试更先进的chunk策略、检索召回以及重排算法。
3. 如需要进行模型训练，可自行将当前数据集进行切分：
   - BGE检索以及重排模型的微调，可参考 https://github.com/FlagOpen/FlagEmbedding/blob/master/examples/finetune/README.md
   - LLMs的further-pretrain以及SFT，对模型框架不做限制。可参考原始的[megatron-lm](https://github.com/NVIDIA/Megatron-LM)框架，以及阿里进行二次封装之后的[Pai-Megatron-Patch](https://github.com/alibaba/Pai-Megatron-Patch),[llama-factory](https://github.com/hiyouga/LLaMA-Factory)等。


