---
title: Ferramentas de portabilidade para o .NET Core
description: Conheça algumas das ferramentas que você pode usar para portar para o .NET Core
author: cartermp
ms.date: 05/03/2020
ms.openlocfilehash: d0cf0abf206950beb34556ca3ba7243d8cad241e
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795580"
---
# <a name="tools-to-help-with-porting-to-net-core"></a>Ferramentas para ajudar com a portabilidade para o .NET Core

As ferramentas listadas neste artigo podem ser úteis para portar:

- [Analisador de portabilidade .net](../../standard/analyzers/portability-analyzer.md) – um ferramentas que pode gerar um relatório de quão portátil seu código está entre .NET Framework e .NET Core:
  - Como uma [ferramenta de linha de comando](https://github.com/Microsoft/dotnet-apiport/releases)
  - Como uma [extensão do Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [Analisador de API do .NET](../../standard/analyzers/api-analyzer.md) – um analisador Roslyn que descobre possíveis riscos de compatibilidade para APIs C# em diferentes plataformas e detecta chamadas a APIs preteridas.
- [try – Convert](https://www.nuget.org/packages/try-convert/) – uma ferramenta global do .NET Core que pode converter um projeto ou uma solução completa para o SDK do .net, incluindo a movimentação de aplicativos da área de trabalho para o .NET Core. Não é recomendável se você tiver uma compilação mais complicada estabelecida (como tarefas personalizadas, destinos ou importações) e rejeitar muitos tipos de projeto que são incompatíveis com o .NET Core.
