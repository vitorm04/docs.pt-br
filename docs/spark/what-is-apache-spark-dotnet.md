---
title: O que é o .NET para o Apache Spark?
description: Saiba mais sobre o .NET para Apache Spark, uma estrutura de análise de Big Data gratuita de software livre e multiplataforma que usa o Spark em qualquer lugar em que você escreva o código .NET.
author: mamccrea
ms.topic: overview
ms.date: 10/15/2019
ms.openlocfilehash: 12fccd478cedaccf455043feb3afa7b12221bf0e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73458195"
---
# <a name="what-is-net-for-apache-spark"></a>O que é o .NET para o Apache Spark?

[Apache Spark](what-is-spark.md) é um mecanismo de processamento distribuído de uso geral para análise sobre grandes conjuntos de dados - tipicamente terabytes ou petabytes de dados. Com o .NET para Apache Spark, o suporte gratuito, de código aberto e multiplataforma .NET para a popular estrutura de análise de big data de código aberto, agora você pode adicionar o poder do Apache Spark aos seus aplicativos de big data usando idiomas que você já conhece.

## <a name="why-choose-net-for-apache-spark"></a>Por que escolher .NET para Apache Spark?

.NET para Apache Spark capacita desenvolvedores com experiência .NET ou bases de código para participar no mundo da análise de big data. .NET para Apache Spark fornece APIs de alto desempenho para usar Spark de C# e F#. Com C# e F#, você pode acessar:

* DataFrame e SparkSQL para trabalhar com dados estruturados.
* Streaming estruturado do Spark para trabalhar usando dados de streaming.
* Spark SQL para escrever consultas com sintaxe SQL.
* Integração de aprendizado de máquina para treinamento e previsão mais rápidos (ou seja, use .NET para Apache Spark ao lado [de ML.NET](https://dot.net/ml)).

O .NET para Apache Spark está em conformidade com o .NET Standard, uma especificação formal das APIs do .NET comuns em implementações do .NET. Isso significa que você pode usar o .NET para Apache Spark em qualquer lugar em que você escreva código .NET, permitindo que você reutilize todo o conhecimento, as habilidades, o código e as bibliotecas que você já tem como um desenvolvedor do .NET.

O .NET para Apache Spark é executado no Windows, no Linux e no macOS usando o .NET Core. Ele também é executado no Windows usando o .NET Framework. Você pode implantar seus aplicativos em todos os principais provedores de nuvem, incluindo Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks e Databricks na AWS.

## <a name="net-for-apache-spark-architecture"></a>.NET para arquitetura Apache Spark

A vinculação da língua C#/ F# ao Spark está escrita em uma nova camada de interop Spark que oferece extensibilidade mais fácil. Esta nova camada de Interop Spark foi escrita usando as melhores práticas para extensão de linguagem e otimiza para interop e desempenho. A longo prazo, essa extensibilidade pode ser usada para adicionar suporte para outras línguas em Spark.

> [!div class="mx-imgBorder"]
> ![.NET para arquitetura Apache Spark](media/dotnet-spark-architecture.png)

Você pode aprender sobre o suporte interop para extensões de linguagem Spark a partir da [proposta](https://issues.apache.org/jira/browse/SPARK-26257).

## <a name="net-for-apache-spark-performance"></a>.NET para o desempenho do Apache Spark

Quando comparado com Python e Scala usando o [benchmark TPC-H,](http://www.tpc.org/tpch/)o .NET para Apache Spark tem um bom desempenho na maioria dos casos e é 2x mais rápido que o Python quando o desempenho da função definido pelo usuário é crítico. Há um esforço contínuo para melhorar e avaliar o desempenho.

Para fazer seu próprio benchmarking, consulte os benchmarks disponíveis no [.NET para Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).

## <a name="net-for-apache-spark-roadmap"></a>.NET para Apache Spark roadmap

Conheça os planos de curto e longo prazo do .NET oficial [para o roteiro do Apache Spark.](https://github.com/dotnet/spark/blob/master/ROADMAP.md)

## <a name="net-foundation"></a>.NET Foundation

O projeto .NET para Apache Spark faz parte do [.NET Foundation.](https://www.dotnetfoundation.org/)

## <a name="contributions"></a>Contribuições

A equipe do .NET para Apache Spark incentiva contribuições, tanto em problemas do GitHub quanto em solicitações de pull. Primeiro, procure um [problema existente](https://github.com/dotnet/spark/issues). Se você não conseguir encontrar um problema existente, [abra um novo problema](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).

## <a name="next-steps"></a>Próximas etapas

Experimente .NET para Apache Spark.
> [!div class="nextstepaction"]
> [Tutorial: Comece com .NET para Apache Spark](./tutorials/get-started.md)
