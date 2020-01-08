---
title: Visão geral das ferramentas de diagnóstico – .NET Core
description: Uma visão geral das ferramentas e das técnicas disponíveis para diagnosticar aplicativos .NET Core.
author: sdmaclea
ms.author: stmaclea
ms.date: 12/17/2019
ms.topic: overview
ms.openlocfilehash: 20374c53769bf19901b042e0909175718665b523
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341475"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>Quais ferramentas de diagnóstico estão disponíveis no .NET Core?

O software nem sempre se comporta como esperado, mas o .NET Core tem ferramentas e APIs que ajudarão você a diagnosticar esses problemas de maneira rápida e eficaz.

Este artigo ajuda a identificar as diversas ferramentas de que você precisa.

## <a name="managed-debuggers"></a>Depuradores gerenciados

Os [depuradores gerenciados](managed-debuggers.md) permitem que você interaja com seu programa. Pausar, executar incrementalmente, examinar e retomar fornecem informações sobre o comportamento do seu código. Um depurador é a primeira opção para diagnosticar problemas funcionais que podem ser facilmente reproduzidos.

## <a name="logging-and-tracing"></a>Log e rastreamento

O [registro em log e o rastreamento](logging-tracing.md) são técnicas relacionadas. Eles se referem ao código de instrumentação para criar arquivos de log. Os arquivos registram os detalhes do que um programa faz. Esses detalhes podem ser usados para diagnosticar os problemas mais complexos. Quando aliados aos carimbos de data/hora, essas técnicas também são valiosas para as investigações de desempenho.

## <a name="unit-testing"></a>Teste de unidade

O [teste de unidade](../testing/index.md) é um componente fundamental da integração e da implantação contínuas de software de alta qualidade. Os testes de unidade são projetados para fornecer um aviso antecipado quando você interrompe algo.

## <a name="net-core-dotnet-diagnostic-global-tools"></a>Ferramentas globais de diagnóstico dotnet do .NET Core

### <a name="dotnet-counters"></a>dotnet-counters

[dotnet-os contadores](dotnet-counters.md) são uma ferramenta de monitoramento de desempenho para a investigação de desempenho e monitoramento de integridade de primeiro nível. Ele observa os valores do contador de desempenho publicados por meio da API <xref:System.Diagnostics.Tracing.EventCounter>. Por exemplo, você pode monitorar rapidamente coisas como o uso da CPU ou a taxa de exceções que estão sendo geradas em seu aplicativo .NET Core.

### <a name="dotnet-dump"></a>dotnet-dump

A ferramenta [dotnet-dump](dotnet-dump.md) é uma maneira de coletar e analisar despejos do Windows e do Linux Core sem um depurador nativo.

### <a name="dotnet-trace"></a>dotnet-trace

O .NET Core inclui o que é chamado de `EventPipe` por meio do qual os dados de diagnóstico são expostos. A ferramenta [dotnet-Trace](dotnet-trace.md) permite que você consuma dados de criação de perfil interessantes de seu aplicativo que podem ajudar em cenários em que você precisa ter a causa raiz dos aplicativos em execução lenta.

## <a name="net-core-diagnostics-tutorials"></a>Tutoriais de diagnóstico do .NET Core

### <a name="debug-a-memory-leak"></a>Depurar um vazamento de memória

[Tutorial: Depurar um vazamento de memória](debug-memory-leak.md) percorre a localização de um vazamento de memória. A ferramenta [dotnet-Counters](dotnet-counters.md) é usada para confirmar o vazamento e a ferramenta [dotnet-dump](dotnet-dump.md) é usada para diagnosticar o vazamento.
