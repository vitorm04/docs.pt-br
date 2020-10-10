---
title: Conectar o .NET para Apache Spark aos hubs de eventos do Azure
description: Saiba como se conectar ao Hub de eventos do Azure do .NET local para Apache Spark instância.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 3956a8152feb743f205f29334f0d42b3165cb27b
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877826"
---
# <a name="connect-net-for-apache-spark-to-azure-event-hubs"></a><span data-ttu-id="038b7-103">Conectar o .NET para Apache Spark aos hubs de eventos do Azure</span><span class="sxs-lookup"><span data-stu-id="038b7-103">Connect .NET for Apache Spark to Azure Event Hubs</span></span>

<span data-ttu-id="038b7-104">Neste artigo, você aprenderá a conectar seu [.net para Apache Spark](https://github.com/dotnet/spark) aplicativo com os hubs de eventos do Azure para ler e gravar Apache Kafka fluxos.</span><span class="sxs-lookup"><span data-stu-id="038b7-104">In this article, you will learn how to connect your [.NET for Apache Spark](https://github.com/dotnet/spark) application with Azure Event Hubs to read and write Apache Kafka streams.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="038b7-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="038b7-105">Prerequisites</span></span>

1. <span data-ttu-id="038b7-106">Ter um namespace de hubs de eventos pronto com um hub de eventos, consulte [este documento](https://docs.microsoft.com/azure/event-hubs/event-hubs-create) para obter um guia passo a passo sobre como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="038b7-106">Have an Event Hubs Namespace ready with an event hub, refer to [this document](https://docs.microsoft.com/azure/event-hubs/event-hubs-create) for a step-by-step guide on how to do that.</span></span> <span data-ttu-id="038b7-107">Certifique-se de selecionar o tipo de preço padrão ao criar o namespace do hub de eventos.</span><span class="sxs-lookup"><span data-stu-id="038b7-107">Make sure to select the Standard Pricing tier while creating the Event Hub Namespace.</span></span>

## <a name="what-is-azure-event-hubs"></a><span data-ttu-id="038b7-108">O que são os Hubs de Eventos do Azure</span><span class="sxs-lookup"><span data-stu-id="038b7-108">What is Azure Event Hubs</span></span>

<span data-ttu-id="038b7-109">Os [hubs de eventos do Azure](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-about) são uma plataforma de streaming Big data e um serviço de ingestão de eventos.</span><span class="sxs-lookup"><span data-stu-id="038b7-109">[Azure Event Hubs](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-about) is a big data streaming platform and event ingestion service.</span></span> <span data-ttu-id="038b7-110">Trata-se de uma PaaS (plataforma como serviço) totalmente gerenciada, que pode ser facilmente integrada com o [Apache Kafka](https://kafka.apache.org/) para fornecer a você a experiência de Kafka de PaaS sem precisar gerenciar, configurar ou executar seus próprios clusters.</span><span class="sxs-lookup"><span data-stu-id="038b7-110">It is a fully managed Platform-as-a-Service (PaaS), that can easily integrate with [Apache Kafka](https://kafka.apache.org/) to give you the PaaS Kafka experience without having to manage, configure or run your own clusters.</span></span>

## <a name="connect-your-application-to-azure-event-hubs"></a><span data-ttu-id="038b7-111">Conectar seu aplicativo aos hubs de eventos do Azure</span><span class="sxs-lookup"><span data-stu-id="038b7-111">Connect your application to Azure Event Hubs</span></span>

1. <span data-ttu-id="038b7-112">Obtenha a cadeia de conexão dos Hubs de Eventos e o FQDN (nome de domínio totalmente qualificado) para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="038b7-112">Get the Event Hubs connection string and fully qualified domain name (FQDN) for later use.</span></span> <span data-ttu-id="038b7-113">Para obter instruções, confira [Obter uma cadeia de conexão dos Hubs de Eventos](https://docs.microsoft.com/azure/event-hubs/event-hubs-get-connection-string).</span><span class="sxs-lookup"><span data-stu-id="038b7-113">For instructions, see [Get an Event Hubs connection string](https://docs.microsoft.com/azure/event-hubs/event-hubs-get-connection-string).</span></span>
2. <span data-ttu-id="038b7-114">Defina as seguintes configurações com detalhes de seu namespace em seu código para começar a ler dos hubs de eventos para Kafka:</span><span class="sxs-lookup"><span data-stu-id="038b7-114">Set the following configurations with details from your namespace in your code to start reading from Event Hubs for Kafka:</span></span>
    1. <span data-ttu-id="038b7-115">Atualize **BOOTSTRAP_SERVERS** e **EH_SASL** em seu aplicativo da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="038b7-115">Update **BOOTSTRAP_SERVERS** and **EH_SASL** in your application like so:</span></span>

    ```csharp
    string BOOTSTRAP_SERVERS = "hostname:9093"; // 9093 is the port used to communicate with Event Hubs, see [troubleshooting guide](https://docs.microsoft.com/azure/event-hubs/troubleshooting-guide)
    string EH_SASL = "org.apache.kafka.common.security.plain.PlainLoginModule required username=\"$ConnectionString\" password=\"<CONNECTION_STRING>\";"; // Connection string obtained from Step 1
    ```

## <a name="read-from-azure-event-hub-stream"></a><span data-ttu-id="038b7-116">Ler do fluxo do hub de eventos do Azure</span><span class="sxs-lookup"><span data-stu-id="038b7-116">Read from Azure Event Hub stream</span></span>

<span data-ttu-id="038b7-117">Agora você pode iniciar o streaming com os hubs de eventos como faria com o Kafka.</span><span class="sxs-lookup"><span data-stu-id="038b7-117">You can now start streaming with Event Hubs as you would with Kafka.</span></span> <span data-ttu-id="038b7-118">Código de exemplo, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="038b7-118">Sample code as shown below:</span></span>

```csharp
SparkSession spark = SparkSession
    .Builder()
    .AppName("Connect Event Hub")
    .GetOrCreate();

DataFrame df = spark
    .ReadStream()
    .Format("kafka")
    .Option("kafka.bootstrap.servers", BOOTSTRAP_SERVERS)
    .Option("subscribe", "spark-test")
    .Option("kafka.sasl.mechanism", "PLAIN")
    .Option("kafka.security.protocol", "SASL_SSL")
    .Option("kafka.sasl.jaas.config", EH_SASL)
    .Option("kafka.request.timeout.ms", "60000")
    .Option("kafka.session.timeout.ms", "60000")
    .Option("failOnDataLoss", "false")
    .Load();

DataFrame dfWrite = df
    .WriteStream()
    .OutputMode("append")
    .Format("console")
    .Start();
```

## <a name="write-to-azure-event-hub-stream"></a><span data-ttu-id="038b7-119">Gravar no fluxo do hub de eventos do Azure</span><span class="sxs-lookup"><span data-stu-id="038b7-119">Write to Azure Event Hub stream</span></span>

<span data-ttu-id="038b7-120">Você também pode gravar nos hubs de eventos da mesma maneira, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="038b7-120">You can also write to Event Hubs in the same way, as shown below:</span></span>

```csharp
// df is the DataFrame to write

df.WriteStream()
    .Format("kafka")
    .Option("topic", topics)
    .Option("kafka.bootstrap.servers", BOOTSTRAP_SERVERS)
    .Option("kafka.sasl.mechanism", "PLAIN")
    .Option("kafka.security.protocol", "SASL_SSL")
    .Option("kafka.sasl.jaas.config", EH_SASL)
    .Option("checkpointLocation", "./checkpoint")
    .Start();
```

## <a name="run-your-application"></a><span data-ttu-id="038b7-121">Execute seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="038b7-121">Run your application</span></span>

<span data-ttu-id="038b7-122">Para executar seu .NET para Apache Spark aplicativo, você deve definir o `spark-sql-kafka-0-10` módulo como parte da definição de compilação em seu projeto do Spark, usando o `libraryDependency` no `build.sbt` para projetos SBT.</span><span class="sxs-lookup"><span data-stu-id="038b7-122">In order to run your .NET for Apache Spark application, you should define the `spark-sql-kafka-0-10` module as part of the build definition in your Spark project, using `libraryDependency` in `build.sbt` for sbt projects.</span></span> <span data-ttu-id="038b7-123">Para ambientes Spark como `spark-submit` (ou `spark-shell` ), você deve usar a `--packages` opção de linha de comando da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="038b7-123">For Spark environments such as `spark-submit` (or `spark-shell`) you should use the `--packages` command-line option like so:</span></span>

```bash
spark-shell --packages org.apache.spark:spark-sql-kafka-0-10_2.12:2.4.5
```

> [!NOTE]
> <span data-ttu-id="038b7-124">Certifique-se de incluir a versão do pacote de acordo com a versão do Spark em execução.</span><span class="sxs-lookup"><span data-stu-id="038b7-124">Make sure to include the package version in accordance with the version of Spark being run.</span></span>
