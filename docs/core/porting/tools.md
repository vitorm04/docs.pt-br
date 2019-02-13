---
title: Ferramentas de portabilidade para o .NET Core
description: Conheça algumas das ferramentas que você pode usar para portar para o .NET Core
author: cartermp
ms.author: mairaw
ms.date: 12/07/2018
ms.openlocfilehash: 88e3edb0442b3326a77323fe4b6396f3eb1ca767
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904862"
---
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="c2f57-103">Ferramentas para ajudar com a portabilidade para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="c2f57-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="c2f57-104">As ferramentas listadas neste artigo podem ser úteis para portar:</span><span class="sxs-lookup"><span data-stu-id="c2f57-104">You may find the tools listed in this article helpful when porting:</span></span>

* <span data-ttu-id="c2f57-105">[Analisador de Portabilidade do .NET](../../standard/analyzers/portability-analyzer.md), uma cadeia de ferramentas que pode gerar um relatório sobre o grau de portabilidade do código entre o .NET Framework e .NET Core:  Como uma [ferramenta de linha de comando](https://github.com/Microsoft/dotnet-apiport/releases) Como uma [extensão do Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span><span class="sxs-lookup"><span data-stu-id="c2f57-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md), a toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:  As a [command line tool](https://github.com/Microsoft/dotnet-apiport/releases) As a [Visual Studio Extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span></span>
* <span data-ttu-id="c2f57-106">[Analisador de API do .NET](../../standard/analyzers/api-analyzer.md) – um analisador Roslyn que descobre possíveis riscos de compatibilidade para APIs C# em diferentes plataformas e detecta chamadas a APIs preteridas.</span><span class="sxs-lookup"><span data-stu-id="c2f57-106">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>

<span data-ttu-id="c2f57-107">Além disso, você pode tentar fazer a portabilidade de soluções menores ou projetos individuais para o formato de arquivo de projeto do .NET Core com a ferramenta [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017).</span><span class="sxs-lookup"><span data-stu-id="c2f57-107">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) tool.</span></span>

> [!WARNING] 
> <span data-ttu-id="c2f57-108">CsprojToVs2017 é uma ferramenta de terceiros.</span><span class="sxs-lookup"><span data-stu-id="c2f57-108">CsprojToVs2017 is a third-party tool.</span></span> <span data-ttu-id="c2f57-109">Não há nenhuma garantia de que ela funcionará para todos os seus projetos, e isso pode causar alterações sutis no comportamento que dependem de você.</span><span class="sxs-lookup"><span data-stu-id="c2f57-109">There is no guarantee that it will work for all of your projects, and it may cause subtle changes in behavior that you depend on.</span></span> <span data-ttu-id="c2f57-110">CsprojToVs2017 deve ser usada como um _ponto de partida_ que automatize as funções básicas que podem ser automatizadas.</span><span class="sxs-lookup"><span data-stu-id="c2f57-110">CsprojToVs2017 should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="c2f57-111">Não é uma solução garantida para a migração de formatos de arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="c2f57-111">It is not a guaranteed solution to migrating project file formats.</span></span>