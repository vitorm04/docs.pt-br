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
# <a name="connect-net-for-apache-spark-to-azure-event-hubs"></a>Conectar o .NET para Apache Spark aos hubs de eventos do Azure

Neste artigo, você aprenderá a conectar seu [.net para Apache Spark](https://github.com/dotnet/spark) aplicativo com os hubs de eventos do Azure para ler e gravar Apache Kafka fluxos.

## <a name="prerequisites"></a>Pré-requisitos

1. Ter um namespace de hubs de eventos pronto com um hub de eventos, consulte [este documento](https://docs.microsoft.com/azure/event-hubs/event-hubs-create) para obter um guia passo a passo sobre como fazer isso. Certifique-se de selecionar o tipo de preço padrão ao criar o namespace do hub de eventos.

## <a name="what-is-azure-event-hubs"></a>O que são os Hubs de Eventos do Azure

Os [hubs de eventos do Azure](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-about) são uma plataforma de streaming Big data e um serviço de ingestão de eventos. Trata-se de uma PaaS (plataforma como serviço) totalmente gerenciada, que pode ser facilmente integrada com o [Apache Kafka](https://kafka.apache.org/) para fornecer a você a experiência de Kafka de PaaS sem precisar gerenciar, configurar ou executar seus próprios clusters.

## <a name="connect-your-application-to-azure-event-hubs"></a>Conectar seu aplicativo aos hubs de eventos do Azure

1. Obtenha a cadeia de conexão dos Hubs de Eventos e o FQDN (nome de domínio totalmente qualificado) para uso posterior. Para obter instruções, confira [Obter uma cadeia de conexão dos Hubs de Eventos](https://docs.microsoft.com/azure/event-hubs/event-hubs-get-connection-string).
2. Defina as seguintes configurações com detalhes de seu namespace em seu código para começar a ler dos hubs de eventos para Kafka:
    1. Atualize **BOOTSTRAP_SERVERS** e **EH_SASL** em seu aplicativo da seguinte forma:

    ```csharp
    string BOOTSTRAP_SERVERS = "hostname:9093"; // 9093 is the port used to communicate with Event Hubs, see [troubleshooting guide](https://docs.microsoft.com/azure/event-hubs/troubleshooting-guide)
    string EH_SASL = "org.apache.kafka.common.security.plain.PlainLoginModule required username=\"$ConnectionString\" password=\"<CONNECTION_STRING>\";"; // Connection string obtained from Step 1
    ```

## <a name="read-from-azure-event-hub-stream"></a>Ler do fluxo do hub de eventos do Azure

Agora você pode iniciar o streaming com os hubs de eventos como faria com o Kafka. Código de exemplo, conforme mostrado abaixo:

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

## <a name="write-to-azure-event-hub-stream"></a>Gravar no fluxo do hub de eventos do Azure

Você também pode gravar nos hubs de eventos da mesma maneira, conforme mostrado abaixo:

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

## <a name="run-your-application"></a>Execute seu aplicativo.

Para executar seu .NET para Apache Spark aplicativo, você deve definir o `spark-sql-kafka-0-10` módulo como parte da definição de compilação em seu projeto do Spark, usando o `libraryDependency` no `build.sbt` para projetos SBT. Para ambientes Spark como `spark-submit` (ou `spark-shell` ), você deve usar a `--packages` opção de linha de comando da seguinte forma:

```bash
spark-shell --packages org.apache.spark:spark-sql-kafka-0-10_2.12:2.4.5
```

> [!NOTE]
> Certifique-se de incluir a versão do pacote de acordo com a versão do Spark em execução.
