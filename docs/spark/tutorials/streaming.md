---
title: Streaming estruturado com .NET para tutorial apache spark
description: Neste tutorial, você aprende a usar o .NET para Apache Spark for Spark Structured Streaming.
author: mamccrea
ms.author: mamccrea
ms.date: 12/04/2019
ms.topic: tutorial
ms.openlocfilehash: 125ef834da8e42c99c8080a3d5414a7927ce7636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79186506"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a>Tutorial: Streaming estruturado com .NET para Apache Spark

Este tutorial ensina como invocar o Spark Structured Streaming usando .NET para Apache Spark. O Spark Structured Streaming é o suporte da Apache Spark para processar fluxos de dados em tempo real. Processamento de fluxo significa analisar dados ao vivo enquanto são produzidos.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
>
> * Criar e executar um aplicativo .NET para Apache Spark
> * Use o netcat para criar um fluxo de dados
> * Use funções definidas pelo usuário e SparkSQL para analisar dados de streaming

## <a name="prerequisites"></a>Pré-requisitos

Se este é o seu primeiro aplicativo .NET para Apache Spark, comece com o [tutorial Getting Started](get-started.md) para se familiarizar com o básico.

## <a name="create-a-console-application"></a>Criar um aplicativo de console

1. No prompt de comando, execute os seguintes comandos para criar um novo aplicativo de console:

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   O `dotnet` comando `new` cria uma `console` aplicação de tipo para você. O `-o` parâmetro cria um diretório chamado *mySparkStreamingApp* onde seu aplicativo é armazenado e o preenche com os arquivos necessários. O `cd mySparkStreamingApp` comando altera o diretório para o diretório de aplicativos que você acabou de criar.

1. Para usar o .NET para Apache Spark em um aplicativo, instale o pacote Microsoft.Spark. No console, execute o seguinte comando:

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a>Estabeleça e conecte-se a um fluxo de dados

Uma maneira popular de testar o processamento de fluxo é através **do netcat**. o netcat (também conhecido como *nc*) permite que você leia e escreva para conexões de rede. Você estabelece uma conexão de rede com o netcat através de uma janela de terminal.

### <a name="create-a-data-stream-with-netcat"></a>Crie um fluxo de dados com netcat

1. [Baixar netcat](https://sourceforge.net/projects/nc110/files/). Em seguida, extraia o arquivo do zip download e apêndice o diretório que você extraiu para a variável de ambiente "PATH".

2. Para iniciar uma nova conexão, abra um novo console e execute o seguinte comando que se conecta ao host local na porta 9999.

   No Windows:

   ```console
   nc -vvv -l -p 9999
   ```

   No Linux:

   ```console
   nc -lk 9999
   ```

   Seu programa Spark ouve a entrada digitada neste prompt de comando.

### <a name="create-a-sparksession"></a>Criar uma SparkSession

1. Adicione as `using` seguintes instruções adicionais à parte superior do arquivo *Program.cs* no *mySparkStreamingApp*:

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. Adicione o seguinte `Main` código ao seu `SparkSession`método para criar um novo . A Sessão spark é o ponto de entrada para programar o Spark com a API Dataset e DataFrame.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   Chamar o objeto *de faísca* criado acima permite que você acesse a funcionalidade do Spark e do DataFrame durante todo o seu programa.

### <a name="connect-to-a-stream-with-readstream"></a>Conecte-se a um fluxo com ReadStream()

O `ReadStream()` método `DataStreamReader` retorna um que pode ser usado `DataFrame`para ler dados de streaming em como um . Inclua as informações do host e da porta para dizer ao seu aplicativo Spark onde esperar seus dados de streaming.

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a>Registre uma função definida pelo usuário

Você pode usar UDFs, *funções definidas pelo usuário,* em aplicativos Spark para realizar cálculos e análises em seus dados.

Adicione o seguinte `Main` código ao seu método `udfArray`para registrar um UDF chamado .

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

Este UDF processa cada string que recebe do terminal netcat para produzir uma matriz que inclui a seqüência original (contida em *str),* seguida pela seqüência original concatenada com o comprimento da seqüência original.

Por exemplo, entrar no *hello world* no terminal netcat produz uma matriz onde:

* matriz\[0] = Olá mundo
* matriz\[1] = Olá mundo 11

## <a name="use-sparksql"></a>Use SparkSQL

Use sparkSQL para executar várias funções nos dados armazenados em seu DataFrame. É comum combinar UDFs e SparkSQL para aplicar um UDF a cada linha de um DataFrame.

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

Este trecho de código aplica *udfArray* a cada valor em seu DataFrame, o que representa cada string lida do seu terminal netcat. Aplique o método <xref:Microsoft.Spark.Sql.Functions.Explode%2A> SparkSQL para colocar cada entrada de sua matriz em sua própria linha. Finalmente, <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> use para colocar as colunas que você produziu no novo array *dataframeDF.*

## <a name="display-your-stream"></a>Exibir seu fluxo

Use <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> para estabelecer características da sua saída, como imprimir resultados para o console e exibir apenas a saída mais recente.

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a>Execute seu código

O streaming estruturado no Spark processa dados através de uma série de pequenos **lotes.**  Quando você executa seu programa, o prompt de comando onde você estabelece a conexão netcat permite que você comece a digitar. Cada vez que você pressiona a tecla Enter após digitar dados nesse prompt de comando, a Spark considera sua entrada um lote e executa o UDF.

### <a name="use-spark-submit-to-run-your-app"></a>Use o spark-submit para executar seu aplicativo

Depois de iniciar uma nova sessão netcat, `spark-submit` abra um novo terminal e execute seu comando, semelhante ao seguinte comando:

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> Certifique-se de atualizar o comando acima com o caminho real para o seu arquivo de jarro Microsoft Spark. O comando acima também pressupõe que seu servidor netcat está sendo executado na porta localhost 9999.

## <a name="get-the-code"></a>Obter o código

Este tutorial usa o [exemplo StructuredNetworkCharacterCount.cs,](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) mas existem outros três exemplos de processamento de fluxo completo no GitHub:

* [StructuredNetworkWordCount.cs:](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)contagem de palavras em dados transmitidos de qualquer fonte
* [StructuredNetworkWordCountWindowed.cs:](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs)contagem de palavras com dados com lógica de janelas
* [StructuredKafkaWordCount.cs:](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)contagem de palavras em dados transmitidos de Kafka

## <a name="next-steps"></a>Próximas etapas

Avance para o próximo artigo para saber como implantar seu aplicativo .NET para Apache Spark no Databricks.
> [!div class="nextstepaction"]
> [Tutorial: Implante um aplicativo .NET para Apache Spark no Databricks](databricks-deployment.md)
