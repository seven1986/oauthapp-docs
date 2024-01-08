# Azure

???+ note "提示"

    1，需先购买Azure Blob[^1] 和Azure OpenAI[^2] 服务。

## 说明

- [x] Azure Blob 存储

- [x] Azure OpenAI

## 配置项

### OpenAI 模型的部署名称 

配置用于OpenAI的特定模型的部署名称。这个配置项可以让您选择使用特定版本或部署的模型，以满足您的需求。

### OpenAI 最大响应数 

配置OpenAI API的最大响应数。这个配置项决定了在单个API调用中，OpenAI将返回的最大响应数量。

这些令牌在提示(包括系统消息、示例、消息历史记录和用户查询)和模型响应之间共享。一个令牌大约是典型英文文本的 4 个字符。

### OpenAI 资源名称 

配置OpenAI服务的资源名称，以便连接到Azure上托管的OpenAI服务。
例如终结点是：https://oauthapp.openai.azure.com，则填写：oauthapp

### OpenAI 状态惩罚 

配置OpenAI模型生成文本时的状态惩罚参数。这个参数影响着生成的文本风格，可以用于控制文本的一致性和逻辑性。
介于 -2.0 和 2.0 之间的数字。
正值会根据它们到目前为止在文本中的现有频率来惩罚新令牌，从而降低模型逐字重复同一行的可能性。

### OpenAI 频率损失 

配置OpenAI模型生成文本时的频率损失参数。这个参数用于平衡生成文本中的新颖性和一致性。
介于 -2.0 和 2.0 之间的数字。
正值会根据它们到目前为止在文本中的现有频率来惩罚新令牌，从而降低模型逐字重复同一行的可能性。

### OpenAI Top P 

配置OpenAI模型生成文本时的Top P参数。这个参数用于控制生成文本时概率分布的截断阈值，从而限制生成文本的多样性。

介于 0.001 和 1 之间的数字。与温度类似，这控制随机性但使用不同的方法。
所以 0.1 意味着只考虑包含前 10% 概率质量的令牌。 我们通常建议更改此设置或温度，但不要同时更改这两者。

### OpenAI 温度 

配置OpenAI模型生成文本时的温度参数。这个参数用于控制生成文本的多样性，较高的温度会产生更多的随机性。

介于 0 和 2 之间。 较高的值意味着模型将承担更多风险。
对于更具创意的应用程序，请尝试将值设为 0.9，对于具有明确定义答案的应用程序，将值设为 0 (argmax sampling) 。
我们通常建议更改此设置或 top_p，但不要同时更改这两者。
参考值：
1.2 荒谬
1.1 离谱
1 创造性
0.7 平衡
0.2 准确
0.1 专业
0 死板

### OpenAI 提示词 

配置用于OpenAI模型的提示词，这些提示词可以影响生成文本的方向和内容。默认的提示词。

### OpenAI 密钥

配置连接到OpenAI服务所需的密钥，以便访问和使用OpenAI API。

### AzureBlob存储 

配置连接到Azure Blob服务所需的密钥。

## 截图

![](https://docs.oauthapp.com/doc_appsetting_azure/1.png){ loading=lazy }

[^1]:Azure Blob：
    Azure Blob 存储是一种云存储服务，用于存储和管理大量非结构化数据，例如图像、音频、视频和文本文件。通过Azure Blob 存储，您可以方便地上传、下载和管理数据，同时享受高可用性和可扩展性的优势。

    [https://azure.microsoft.com/zh-cn/products/storage/blobs/](https://azure.microsoft.com/zh-cn/products/storage/blobs/)

[^2]:Azure OpenAI：
    Azure OpenAI是基于Azure平台提供的人工智能服务，可用于自然语言处理任务。它提供了各种预训练的模型和API，以支持文本生成、语言理解和对话等任务。

    [https://azure.microsoft.com/zh-cn/products/cognitive-services/openai-service/](https://azure.microsoft.com/zh-cn/products/cognitive-services/openai-service/)