---
title: Conectar o .NET para Apache Spark aos hubs de eventos do Azure
description: Saiba como se conectar ao Hub de eventos do Azure do .NET local para Apache Spark instância.
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: c8fd10992e63674032af4148e0673a5330d9086c
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223963"
---
# <a name="connect-net-for-apache-spark-to-azure-event-hubs"></a><span data-ttu-id="3e6de-103">Conectar o .NET para Apache Spark aos hubs de eventos do Azure</span><span class="sxs-lookup"><span data-stu-id="3e6de-103">Connect .NET for Apache Spark to Azure Event Hubs</span></span>

<span data-ttu-id="3e6de-104">Neste artigo, você aprenderá a conectar seu [.net para Apache Spark](https://github.com/dotnet/spark) aplicativo com os hubs de eventos do Azure para ler e gravar Apache Kafka fluxos.</span><span class="sxs-lookup"><span data-stu-id="3e6de-104">In this article, you will learn how to connect your [.NET for Apache Spark](https://github.com/dotnet/spark) application with Azure Event Hubs to read and write Apache Kafka streams.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3e6de-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="3e6de-105">Prerequisites</span></span>

<span data-ttu-id="3e6de-106">Ter um namespace de hubs de eventos pronto com um hub de eventos.</span><span class="sxs-lookup"><span data-stu-id="3e6de-106">Have an Event Hubs Namespace ready with an event hub.</span></span> <span data-ttu-id="3e6de-107">Para obter um guia passo a passo, consulte [início rápido: criar um hub de eventos usando portal do Azure](/azure/event-hubs/event-hubs-create).</span><span class="sxs-lookup"><span data-stu-id="3e6de-107">For a step-by-step guide, refer to [Quickstart: Create an event hub using Azure portal](/azure/event-hubs/event-hubs-create).</span></span> <span data-ttu-id="3e6de-108">Certifique-se de selecionar o tipo de preço padrão ao criar o namespace do hub de eventos.</span><span class="sxs-lookup"><span data-stu-id="3e6de-108">Make sure to select the Standard Pricing tier while creating the Event Hub Namespace.</span></span>

## <a name="what-is-azure-event-hubs"></a><span data-ttu-id="3e6de-109">O que são os Hubs de Eventos do Azure</span><span class="sxs-lookup"><span data-stu-id="3e6de-109">What is Azure Event Hubs</span></span>

<span data-ttu-id="3e6de-110">Os [hubs de eventos do Azure](/azure/event-hubs/event-hubs-about) são uma plataforma de streaming de Big data e um serviço de ingestão de eventos.</span><span class="sxs-lookup"><span data-stu-id="3e6de-110">[Azure Event Hubs](/azure/event-hubs/event-hubs-about) is a big-data streaming platform and event-ingestion service.</span></span> <span data-ttu-id="3e6de-111">Trata-se de uma PaaS (plataforma como serviço) totalmente gerenciada que pode ser facilmente integrada com [Apache Kafka](https://kafka.apache.org/) para fornecer a você a experiência de Kafka de PaaS sem precisar gerenciar, configurar ou executar seus próprios clusters.</span><span class="sxs-lookup"><span data-stu-id="3e6de-111">It is a fully managed Platform-as-a-Service (PaaS) that can easily integrate with [Apache Kafka](https://kafka.apache.org/) to give you the PaaS Kafka experience without having to manage, configure, or run your own clusters.</span></span>

## <a name="connect-your-application-to-azure-event-hubs"></a><span data-ttu-id="3e6de-112">Conectar seu aplicativo aos hubs de eventos do Azure</span><span class="sxs-lookup"><span data-stu-id="3e6de-112">Connect your application to Azure Event Hubs</span></span>

1. <span data-ttu-id="3e6de-113">Obtenha a cadeia de conexão dos Hubs de Eventos e o FQDN (nome de domínio totalmente qualificado) para uso posterior.</span><span class="sxs-lookup"><span data-stu-id="3e6de-113">Get the Event Hubs connection string and fully qualified domain name (FQDN) for later use.</span></span> <span data-ttu-id="3e6de-114">Para obter instruções, confira [Obter uma cadeia de conexão dos Hubs de Eventos](/azure/event-hubs/event-hubs-get-connection-string).</span><span class="sxs-lookup"><span data-stu-id="3e6de-114">For instructions, see [Get an Event Hubs connection string](/azure/event-hubs/event-hubs-get-connection-string).</span></span>
2. <span data-ttu-id="3e6de-115">Defina as seguintes configurações com detalhes de seu namespace em seu código para começar a ler dos hubs de eventos para Kafka:</span><span class="sxs-lookup"><span data-stu-id="3e6de-115">Set the following configurations with details from your namespace in your code to start reading from Event Hubs for Kafka:</span></span>
    1. <span data-ttu-id="3e6de-116">Atualize **BOOTSTRAP_SERVERS** e **EH_SASL** em seu aplicativo da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="3e6de-116">Update **BOOTSTRAP_SERVERS** and **EH_SASL** in your application like so:</span></span>

    ```csharp
    string BOOTSTRAP_SERVERS = "hostname:9093"; // 9093 is the port used to communicate with Event Hubs, see [troubleshooting guide](https://docs.microsoft.com/azure/event-hubs/troubleshooting-guide)
    string EH_SASL = "org.apache.kafka.common.security.plain.PlainLoginModule required username=\"$ConnectionString\" password=\"<CONNECTION_STRING>\";"; // Connection string obtained from Step 1
    ```

## <a name="read-from-azure-event-hub-stream"></a><span data-ttu-id="3e6de-117">Ler do fluxo do hub de eventos do Azure</span><span class="sxs-lookup"><span data-stu-id="3e6de-117">Read from Azure Event Hub stream</span></span>

<span data-ttu-id="3e6de-118">Agora você pode iniciar o streaming com os hubs de eventos como faria com o Kafka.</span><span class="sxs-lookup"><span data-stu-id="3e6de-118">You can now start streaming with Event Hubs as you would with Kafka.</span></span> <span data-ttu-id="3e6de-119">Código de exemplo, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="3e6de-119">Sample code as shown below:</span></span>

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

## <a name="write-to-azure-event-hub-stream"></a><span data-ttu-id="3e6de-120">Gravar no fluxo do hub de eventos do Azure</span><span class="sxs-lookup"><span data-stu-id="3e6de-120">Write to Azure Event Hub stream</span></span>

<span data-ttu-id="3e6de-121">Você também pode gravar nos hubs de eventos da mesma maneira, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="3e6de-121">You can also write to Event Hubs in the same way, as shown below:</span></span>

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

## <a name="run-your-application"></a><span data-ttu-id="3e6de-122">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="3e6de-122">Run your application</span></span>

<span data-ttu-id="3e6de-123">Para executar seu .NET para Apache Spark aplicativo, defina o `spark-sql-kafka-0-10` módulo como parte da definição de compilação em seu projeto do Spark, usando o `libraryDependency` no `build.sbt` para projetos SBT.</span><span class="sxs-lookup"><span data-stu-id="3e6de-123">In order to run your .NET for Apache Spark application, define the `spark-sql-kafka-0-10` module as part of the build definition in your Spark project, using `libraryDependency` in `build.sbt` for sbt projects.</span></span> <span data-ttu-id="3e6de-124">Para ambientes do Spark, como `spark-submit` (ou `spark-shell` ), use a `--packages` opção de linha de comando da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="3e6de-124">For Spark environments such as `spark-submit` (or `spark-shell`), use the `--packages` command-line option like so:</span></span>

```bash
spark-shell --packages org.apache.spark:spark-sql-kafka-0-10_2.12:2.4.5
```

> [!NOTE]
> <span data-ttu-id="3e6de-125">Certifique-se de incluir a versão do pacote de acordo com a versão do Spark em execução.</span><span class="sxs-lookup"><span data-stu-id="3e6de-125">Make sure to include the package version in accordance with the version of Spark being run.</span></span>
