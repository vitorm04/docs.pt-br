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
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="030dd-103">Ferramentas para ajudar com a portabilidade para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="030dd-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="030dd-104">As ferramentas listadas neste artigo podem ser úteis para portar:</span><span class="sxs-lookup"><span data-stu-id="030dd-104">You may find the tools listed in this article helpful when porting:</span></span>

- <span data-ttu-id="030dd-105">[Analisador de portabilidade .net](../../standard/analyzers/portability-analyzer.md) – um ferramentas que pode gerar um relatório de quão portátil seu código está entre .NET Framework e .NET Core:</span><span class="sxs-lookup"><span data-stu-id="030dd-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - A toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:</span></span>
  - <span data-ttu-id="030dd-106">Como uma [ferramenta de linha de comando](https://github.com/Microsoft/dotnet-apiport/releases)</span><span class="sxs-lookup"><span data-stu-id="030dd-106">As a [command-line tool](https://github.com/Microsoft/dotnet-apiport/releases)</span></span>
  - <span data-ttu-id="030dd-107">Como uma [extensão do Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span><span class="sxs-lookup"><span data-stu-id="030dd-107">As a [Visual Studio extension](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span></span>
- <span data-ttu-id="030dd-108">[Analisador de API do .NET](../../standard/analyzers/api-analyzer.md) – um analisador Roslyn que descobre possíveis riscos de compatibilidade para APIs C# em diferentes plataformas e detecta chamadas a APIs preteridas.</span><span class="sxs-lookup"><span data-stu-id="030dd-108">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>
- <span data-ttu-id="030dd-109">[try – Convert](https://www.nuget.org/packages/try-convert/) – uma ferramenta global do .NET Core que pode converter um projeto ou uma solução completa para o SDK do .net, incluindo a movimentação de aplicativos da área de trabalho para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="030dd-109">[try-convert](https://www.nuget.org/packages/try-convert/) - A .NET Core global tool that can convert a project or entire solution to the .NET SDK, including moving desktop apps to .NET Core.</span></span> <span data-ttu-id="030dd-110">Não é recomendável se você tiver uma compilação mais complicada estabelecida (como tarefas personalizadas, destinos ou importações) e rejeitar muitos tipos de projeto que são incompatíveis com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="030dd-110">It is not recommended if you have a more complicated build established (such as custom tasks, targets, or imports), and it rejects many project types that are incompatible with .NET Core.</span></span>
