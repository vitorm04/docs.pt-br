---
title: Ferramentas de portabilidade para o .NET Core
description: Conheça algumas das ferramentas que você pode usar para portar para o .NET Core
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 98b3a29f2287414b2cd323f1cbf2225905592b26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157512"
---
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="39338-103">Ferramentas para ajudar com a portabilidade para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="39338-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="39338-104">As ferramentas listadas neste artigo podem ser úteis para portar:</span><span class="sxs-lookup"><span data-stu-id="39338-104">You may find the tools listed in this article helpful when porting:</span></span>

- <span data-ttu-id="39338-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - Uma cadeia de ferramentas que pode gerar um relatório de quão portátil seu código é entre .NET Framework e .NET Core:</span><span class="sxs-lookup"><span data-stu-id="39338-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - A toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:</span></span>
  - <span data-ttu-id="39338-106">Como uma [ferramenta de linha de comando](https://github.com/Microsoft/dotnet-apiport/releases)</span><span class="sxs-lookup"><span data-stu-id="39338-106">As a [command-line tool](https://github.com/Microsoft/dotnet-apiport/releases)</span></span>
  - <span data-ttu-id="39338-107">Como uma [extensão do Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span><span class="sxs-lookup"><span data-stu-id="39338-107">As a [Visual Studio extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span></span>
- <span data-ttu-id="39338-108">[Analisador de API do .NET](../../standard/analyzers/api-analyzer.md) – um analisador Roslyn que descobre possíveis riscos de compatibilidade para APIs C# em diferentes plataformas e detecta chamadas a APIs preteridas.</span><span class="sxs-lookup"><span data-stu-id="39338-108">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>

<span data-ttu-id="39338-109">Além disso, você pode tentar fazer a portabilidade de soluções menores ou projetos individuais para o formato de arquivo de projeto do .NET Core com a ferramenta [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017).</span><span class="sxs-lookup"><span data-stu-id="39338-109">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) tool.</span></span>

> [!WARNING]
> <span data-ttu-id="39338-110">CsprojToVs2017 é uma ferramenta de terceiros.</span><span class="sxs-lookup"><span data-stu-id="39338-110">CsprojToVs2017 is a third-party tool.</span></span> <span data-ttu-id="39338-111">Não há nenhuma garantia de que ela funcionará para todos os seus projetos, e isso pode causar alterações sutis no comportamento que dependem de você.</span><span class="sxs-lookup"><span data-stu-id="39338-111">There is no guarantee that it will work for all of your projects, and it may cause subtle changes in behavior that you depend on.</span></span> <span data-ttu-id="39338-112">CsprojToVs2017 deve ser usada como um _ponto de partida_ que automatize as funções básicas que podem ser automatizadas.</span><span class="sxs-lookup"><span data-stu-id="39338-112">CsprojToVs2017 should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="39338-113">Não é uma solução garantida para a migração de formatos de arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="39338-113">It is not a guaranteed solution to migrating project file formats.</span></span>
