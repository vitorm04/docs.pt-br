---
title: O que é o Apache Spark?
description: Conheça o Apache Spark e os cenários de big data.
ms.date: 10/15/2019
ms.topic: conceptual
ms.custom: mvc
ms.openlocfilehash: 653f355d09a045feabb3dee0f5737cb691cf2dc4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73458170"
---
# <a name="what-is-apache-spark"></a>O que é o Apache Spark?

[O Apache Spark](https://spark.apache.org/) é uma estrutura de processamento paralelo de código aberto que suporta processamento na memória para aumentar o desempenho de aplicativos que analisam big data. As soluções de big data são projetadas para lidar com dados muito grandes ou complexos para bancos de dados tradicionais. O Spark processa grandes quantidades de dados na memória, o que é muito mais rápido do que as alternativas baseadas em disco.

## <a name="common-big-data-scenarios"></a>Cenários comuns de big data

Você pode considerar uma arquitetura de big data se precisar armazenar e processar grandes volumes de dados, transformar dados não estruturados ou processar dados de streaming. Spark é um mecanismo de processamento distribuído de uso geral que pode ser usado para vários cenários de big data.

### <a name="extract-transform-and-load-etl"></a>ETL (extrair, transformar e carregar)

[Extrair, transformar e carregar (ETL)](/azure/architecture/data-guide/relational-data/etl) é o processo de coleta de dados de uma ou várias fontes, modificando os dados e movendo os dados para um novo armazenamento de dados. Existem várias maneiras de transformar dados, incluindo:

* Filtragem
* Classificação
* Agregar
* Adição
* Limpeza
* Deduplicação
* Validando

### <a name="real-time-data-stream-processing"></a>Processamento de fluxo de dados em tempo real

Streaming, ou em tempo real, dados são dados em movimento. Telemetria de dispositivos IoT, weblogs e clickstreams são todos exemplos de dados de streaming. Os dados em tempo real podem ser processados para fornecer informações úteis, como análise geoespacial, monitoramento remoto e detecção de anomalias. Assim como os dados relacionais, você pode filtrar, agregar e preparar dados de streaming antes de mover os dados para um dissipador de saída. O Apache Spark suporta [o processamento de fluxo de dados em tempo real](/azure/architecture/data-guide/big-data/real-time-processing) através do Spark [Streaming](https://spark.apache.org/streaming/).

### <a name="batch-processing"></a>Processamento em lotes

[O processamento em lote](/azure/architecture/data-guide/big-data/batch-processing) é o processamento de big data em repouso. Você pode filtrar, agregar e preparar conjuntos de dados muito grandes usando trabalhos de longa duração em paralelo.

### <a name="machine-learning-through-mllib"></a>Aprendizado de máquina através do MLlib

O aprendizado de máquina é usado para problemas analíticos avançados. Seu computador pode usar dados existentes para prever ou prever comportamentos futuros, resultados e tendências. A biblioteca de aprendizado de máquina da Apache Spark, [MLlib,](https://spark.apache.org/mllib/)contém vários algoritmos e utilitários de aprendizagem de máquina.

### <a name="graph-processing-through-graphx"></a>Processamento de gráficos através do GraphX

Um gráfico é uma coleção de nódulos conectados por bordas. Você pode usar um banco de dados gráfico se tiver dados hierárquicos ou dados com relacionamentos interconectados. Você pode processar esses dados usando a API [GraphX](https://spark.apache.org/graphx/) do Apache Spark.

### <a name="sql-and-structured-data-processing-with-spark-sql"></a>SQL e processamento de dados estruturados com Spark SQL

Se você estiver trabalhando com dados estruturados (formatados), você pode usar consultas SQL em seu aplicativo Spark usando [Spark SQL](https://spark.apache.org/sql/).

## <a name="apache-spark-architecture"></a>Arquitetura Apache Spark

O Apache Spark, que usa a arquitetura master/worker, tem três componentes principais: o driver, os executores e o gerenciador de cluster.

![Arquitetura Apache Spark](media/spark-architecture.png)

### <a name="driver"></a>Driver

O driver consiste em seu programa, como um aplicativo de console C# e uma sessão Spark. A sessão Spark pega seu programa e o divide em tarefas menores que são tratadas pelos executores.

### <a name="executors"></a>Executores

Cada executor, ou nó do trabalhador, recebe uma tarefa do motorista e executa essa tarefa. Os executores residem em uma entidade conhecida como cluster.

### <a name="cluster-manager"></a>Gerente de cluster

O gerenciador de cluster comunica-se com o driver e os executores para:

* Gerenciar a alocação de recursos
* Gerenciar divisão de programas
* Gerenciar a execução do programa

## <a name="language-support"></a>Suporte ao idioma

Apache Spark suporta as seguintes linguagens de programação:

* Scala
* Python
* Java
* SQL
* R
* .NET

## <a name="spark-apis"></a>APIs de faísca

O Apache Spark suporta as seguintes APIs:

* [Spark Scala API](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
* [Spark Java API](https://spark.apache.org/docs/2.2.0/api/java/index.html)
* [Spark Python API](https://spark.apache.org/docs/2.2.0/api/python/index.html)
* [Spark R API](https://spark.apache.org/docs/2.2.0/api/R/index.html)
* [Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), funções incorporadas

## <a name="next-steps"></a>Próximas etapas

Saiba como usar o Apache Spark no seu aplicativo .NET. Com .NET para Apache Spark, desenvolvedores com experiência .NET e lógica de negócios podem escrever consultas de big data em C# e F#.
> [!div class="nextstepaction"]
> [O que é .NET para Apache Spark](what-is-apache-spark-dotnet.md)
