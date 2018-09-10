---
title: Histórico de versão do .NET Core
description: Consulte a linha do tempo para obter as versões do tempo de execução do .NET Core, do SDK do .NET Core, do compilador C# e do compilador VB.NET.
ms.date: 07/26/2018
ms.openlocfilehash: 90fd4ba57620a3a005f2148c0335a76a6fa54a30
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519059"
---
# <a name="net-core-version-history"></a>Histórico de versão do .NET Core

Os números de versão do .NET Core são difíceis de entender porque o SDK do .NET Core e o tempo de execução do .NET Core são lançados em cadências diferentes. As diferentes cadências ocorreram porque a equipe foi forçada a fazer apenas duas das três ações a seguir:

1. Lançar de forma independente, especificamente permitindo que as ferramentas, o C# e o VB avancem com mais rapidez do que o tempo de execução do .NET Core.
2. Manter o alinhamento nos números de versão entre o SDK do .NET Core e o tempo de execução do .NET Core.
3. Usar o controle de versão semântico para o SDK do .NET Core e o tempo de execução do .NET Core.

A 2.0.0 forçou o alinhamento de versão e seguiu sem problemas para uma única versão. Em dezembro de 2017 o SDK do .NET Core tinha uma versão de recurso, sem nenhuma versão correspondente no tempo de execução do .NET Core. A equipe optou pelas metas 1 e 3, perdendo o alinhamento entre o tempo de execução e o SDK do .NET Core. Várias versões do SDK do .NET Core 2.1.x foram lançadas antes do tempo de execução do .NET Core 2.1. Como o SDK não é compatível com as versões posteriores, essas versões do SDK 2.1.x não puderam ser direcionadas ao tempo de execução do .NET Core 2.1. A equipe respondeu a essa confusão considerável mudando para as metas 1 e 2, abandonando o controle de versão semântico descrito em [Controle de versão do .NET Core](index.md#versioning-details).

Devido ao tempo da decisão de abandonar o controle de versão semântico, houve versões de transição nos intervalos de número de versão 2.1.10x e 2.1.20x, que também não podem ser direcionados ao tempo de execução do .NET Core 2.1.

Os dois primeiros dígitos dos números de versão são realinhados com a versão 2.1.0 do tempo de execução do .NET Core e a versão 2.1.300 do SDK do .NET Core.

Informações detalhadas sobre as versões dos componentes individuais, incluindo versões do compilador de estrutura e de linguagem podem ser encontradas na [página de downloads do .NET Core](https://www.microsoft.com/net/download/dotnet-core/current). Para obter informações detalhadas sobre as versões anteriores, selecione a versão solicitada na [página de arquivos mortos de download do .NET Core](https://www.microsoft.com/net/download/archives). Informações detalhadas sobre suporte podem ser encontradas no artigo que descreve a [Política de suporte do .NET](https://www.microsoft.com/net/Support/Policy) oficial.