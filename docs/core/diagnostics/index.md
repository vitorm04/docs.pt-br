---
title: Visão geral das ferramentas de diagnóstico – .NET Core
description: Uma visão geral das ferramentas e das técnicas disponíveis para diagnosticar aplicativos .NET Core.
ms.date: 12/17/2019
ms.topic: overview
ms.openlocfilehash: 0a78ec6c88f5323104277cddea4480a5e13b4e41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399045"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>Quais ferramentas de diagnóstico estão disponíveis no .NET Core?

O software nem sempre se comporta como esperado, mas o .NET Core tem ferramentas e APIs que ajudarão você a diagnosticar esses problemas de maneira rápida e eficaz.

Este artigo ajuda a identificar as diversas ferramentas de que você precisa.

## <a name="managed-debuggers"></a>Depuradores gerenciados

[Os depuradores gerenciados](managed-debuggers.md) permitem que você interaja com seu programa. Pausar, executar incrementalmente, examinar e retomar fornecem informações sobre o comportamento do seu código. Um depurador é a primeira opção para diagnosticar problemas funcionais que podem ser facilmente reproduzidos.

## <a name="logging-and-tracing"></a>Log e rastreamento

[Registro e rastreamento](logging-tracing.md) são técnicas relacionadas. Eles se referem ao código de instrumentação para criar arquivos de log. Os arquivos registram os detalhes do que um programa faz. Esses detalhes podem ser usados para diagnosticar os problemas mais complexos. Quando aliados aos carimbos de data/hora, essas técnicas também são valiosas para as investigações de desempenho.

## <a name="unit-testing"></a>Teste de unidade

[O teste unitário](../testing/index.md) é um componente-chave da integração contínua e implantação de software de alta qualidade. Os testes de unidade são projetados para fornecer um aviso antecipado quando você interrompe algo.

## <a name="net-core-dotnet-diagnostic-global-tools"></a>.NET Core dotnet diagnóstico Global Tools

### <a name="dotnet-counters"></a>dotnet-counters

[dotnet-counters](dotnet-counters.md) é uma ferramenta de monitoramento de desempenho para monitoramento de saúde de primeiro nível e investigação de desempenho. Observa valores de contador <xref:System.Diagnostics.Tracing.EventCounter> de desempenho publicados através da API. Por exemplo, você pode monitorar rapidamente coisas como o uso da CPU ou a taxa de exceções que estão sendo lançadas no seu aplicativo .NET Core.

### <a name="dotnet-dump"></a>dotnet-dump

A ferramenta [dotnet-dump](dotnet-dump.md) é uma maneira de coletar e analisar dumps centrais do Windows e Linux sem um depurador nativo.

### <a name="dotnet-trace"></a>dotnet-trace

O Núcleo .NET inclui `EventPipe` o que é chamado de através do qual os dados de diagnóstico são expostos. A ferramenta [dotnet-trace](dotnet-trace.md) permite que você consuma dados interessantes de criação de perfil do seu aplicativo que podem ajudar em cenários onde você precisa criar aplicativos de causa em execução lenta.

## <a name="net-core-diagnostics-tutorials"></a>Tutoriais de diagnóstico do .NET Core

### <a name="debug-a-memory-leak"></a>Depurar um vazamento de memória

[Tutorial: Depurar um vazamento de memória](debug-memory-leak.md) passa por encontrar um vazamento de memória. A ferramenta [dotnet-counters](dotnet-counters.md) é usada para confirmar o vazamento e a ferramenta [dotnet-dump](dotnet-dump.md) é usada para diagnosticar o vazamento.
