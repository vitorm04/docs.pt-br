---
title: Ferramentas de portabilidade para o .NET Core
description: Conheça algumas das ferramentas que você pode usar para portar para o .NET Core
author: cartermp
ms.date: 05/03/2020
ms.openlocfilehash: b8678ec72fe5d910d5f8cff4768106e7496f9276
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406122"
---
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="bda0b-103">Ferramentas para ajudar com a portabilidade para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="bda0b-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="bda0b-104">As ferramentas listadas neste artigo podem ser úteis para portar:</span><span class="sxs-lookup"><span data-stu-id="bda0b-104">You may find the tools listed in this article helpful when porting:</span></span>

- <span data-ttu-id="bda0b-105">[Analisador de portabilidade .net](../../standard/analyzers/portability-analyzer.md) – um ferramentas que pode gerar um relatório de quão portátil seu código está entre .NET Framework e .NET Core:</span><span class="sxs-lookup"><span data-stu-id="bda0b-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - A toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:</span></span>
  - <span data-ttu-id="bda0b-106">Como uma [ferramenta de linha de comando](https://github.com/Microsoft/dotnet-apiport/releases)</span><span class="sxs-lookup"><span data-stu-id="bda0b-106">As a [command-line tool](https://github.com/Microsoft/dotnet-apiport/releases)</span></span>
  - <span data-ttu-id="bda0b-107">Como uma [extensão do Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span><span class="sxs-lookup"><span data-stu-id="bda0b-107">As a [Visual Studio extension](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span></span>
- <span data-ttu-id="bda0b-108">[Analisador de compatibilidade de plataforma](../../standard/analyzers/platform-compat-analyzer.md) – um analisador de Roslyn que informa os desenvolvedores quando eles usam APIs específicas da plataforma de sites de chamada em que a API pode não estar disponível.</span><span class="sxs-lookup"><span data-stu-id="bda0b-108">[Platform compatibility analyzer](../../standard/analyzers/platform-compat-analyzer.md) - A Roslyn analyzer that informs developers when they use platform-specific APIs from call sites where the API might not be available.</span></span>
- <span data-ttu-id="bda0b-109">[.NET API Analyzer](../../standard/analyzers/api-analyzer.md) – um analisador de Roslyn que pode ajudar a detectar problemas de compatibilidade de plataforma em aplicativos e bibliotecas de plataforma cruzada.</span><span class="sxs-lookup"><span data-stu-id="bda0b-109">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that can help detect platform compatibility issues in cross-platform apps and libraries.</span></span>
- <span data-ttu-id="bda0b-110">[try – Convert](https://www.nuget.org/packages/try-convert/) – uma ferramenta global do .NET Core que pode converter um projeto ou uma solução completa para o SDK do .net, incluindo a movimentação de aplicativos da área de trabalho para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bda0b-110">[try-convert](https://www.nuget.org/packages/try-convert/) - A .NET Core global tool that can convert a project or entire solution to the .NET SDK, including moving desktop apps to .NET Core.</span></span> <span data-ttu-id="bda0b-111">Não é recomendável se você tiver uma compilação mais complicada estabelecida (como tarefas personalizadas, destinos ou importações) e rejeitar muitos tipos de projeto que são incompatíveis com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bda0b-111">It is not recommended if you have a more complicated build established (such as custom tasks, targets, or imports), and it rejects many project types that are incompatible with .NET Core.</span></span>
