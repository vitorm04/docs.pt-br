---
title: Portabilidade do .NET Framework para .NET Core
description: Entenda o processo de compatibilidade e descubra ferramentas que podem ser úteis ao realizar a portabilidade de um projeto do .NET Framework para o .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 10/23/2018
ms.openlocfilehash: 0c0ec3d8ab09e34e8dae24623903ca571f2cca6c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50192766"
---
# <a name="porting-to-net-core-from-net-framework"></a><span data-ttu-id="f9be2-103">Portabilidade do .NET Framework para .NET Core</span><span class="sxs-lookup"><span data-stu-id="f9be2-103">Porting to .NET Core from .NET Framework</span></span>

<span data-ttu-id="f9be2-104">Se você tiver código em execução no .NET Framework, poderá ser útil executá-lo no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f9be2-104">If you've got code running on the .NET Framework, you may be interested in running your code on .NET Core.</span></span>  <span data-ttu-id="f9be2-105">Esse artigo aborda uma visão geral do processo de portabilidade e uma lista das ferramentas que podem ser úteis na portabilidade para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f9be2-105">This article covers an overview of the porting process and a list of the tools you may find helpful when porting to .NET Core.</span></span>

## <a name="overview-of-the-porting-process"></a><span data-ttu-id="f9be2-106">Visão geral do processo de portabilidade</span><span class="sxs-lookup"><span data-stu-id="f9be2-106">Overview of the Porting Process</span></span>

<span data-ttu-id="f9be2-107">O processo recomendado de portabilidade segue a série de etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="f9be2-107">The recommended process for porting follows the following series of steps.</span></span>  <span data-ttu-id="f9be2-108">Cada uma dessas partes do processo é abordada em mais detalhes nos próximos artigos.</span><span class="sxs-lookup"><span data-stu-id="f9be2-108">Each of these parts of the process are covered in more detail in further articles.</span></span>

1. <span data-ttu-id="f9be2-109">Identifique e considere as dependências de terceiros.</span><span class="sxs-lookup"><span data-stu-id="f9be2-109">Identify and account for your third-party dependencies.</span></span>

   <span data-ttu-id="f9be2-110">Isso inclui compreender quais são suas dependências de terceiros, como você depende delas, como ver se elas também são executadas no .NET Core e as etapas a ser seguidas caso não sejam.</span><span class="sxs-lookup"><span data-stu-id="f9be2-110">This will involve understanding what your third-party dependencies are, how you depend on them, how to see if they also run on .NET Core, and steps you can take if they don't.</span></span>
   
2. <span data-ttu-id="f9be2-111">Redirecione todos os projetos que você deseja portar para direcionar para a versão mais recente do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f9be2-111">Retarget all projects you wish to port to target the latest version of .NET Framework.</span></span>

   <span data-ttu-id="f9be2-112">Isso garante que você possa usar alternativas de API para destinos específicos de .NET Framework nos casos em que o .NET Core não dá suporte a uma determinada API.</span><span class="sxs-lookup"><span data-stu-id="f9be2-112">This ensures that you can use API alternatives for .NET Framework-specific targets in the cases where .NET Core can't support a particular API.</span></span>
   
3. <span data-ttu-id="f9be2-113">Use o [Analisador de Portabilidade do .NET](../../standard/analyzers/portability-analyzer.md) para analisar seus assemblies e desenvolver um plano de portabilidade com base nos resultados dele.</span><span class="sxs-lookup"><span data-stu-id="f9be2-113">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to analyze your assemblies and develop a plan to port based on its results.</span></span>

   <span data-ttu-id="f9be2-114">A ferramenta Analisador de Portabilidade de API analisará seus assemblies compilados e gerará um relatório que mostra um resumo de portabilidade de alto nível e um detalhamento de cada API usada que não está disponível no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f9be2-114">The API Portability Analyzer tool will analyze your compiled assemblies and generate a report which shows a high-level portability summary and a breakdown of each API you're using that isn't available on .NET Core.</span></span>  <span data-ttu-id="f9be2-115">Você pode usar esse relatório junto com uma análise da sua base de código para desenvolver um plano para como você realizará a portabilidade do código.</span><span class="sxs-lookup"><span data-stu-id="f9be2-115">You can use this report alongside an analysis of your codebase to develop a plan for how you'll port your code over.</span></span>
   
4. <span data-ttu-id="f9be2-116">Porte seu código de testes.</span><span class="sxs-lookup"><span data-stu-id="f9be2-116">Port your tests code.</span></span>

   <span data-ttu-id="f9be2-117">Como a portabilidade para o .NET Core é uma grande mudança para sua base de código, é altamente recomendável portar seus testes para poder realizar testes à medida que o código é portado.</span><span class="sxs-lookup"><span data-stu-id="f9be2-117">Because porting to .NET Core is such a big change to your codebase, it's highly recommended to get your tests ported so that you can run tests as you port code over.</span></span>  <span data-ttu-id="f9be2-118">No momento, MSTest, xUnit e NUnit são compatíveis com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f9be2-118">MSTest, xUnit, and NUnit all support .NET Core today.</span></span>
   
6. <span data-ttu-id="f9be2-119">Execute seu plano de portabilidade.</span><span class="sxs-lookup"><span data-stu-id="f9be2-119">Execute your plan for porting!</span></span>

## <a name="tools-to-help"></a><span data-ttu-id="f9be2-120">Ferramentas para ajudar</span><span class="sxs-lookup"><span data-stu-id="f9be2-120">Tools to help</span></span>

<span data-ttu-id="f9be2-121">Esta é uma breve lista das ferramentas que serão úteis:</span><span class="sxs-lookup"><span data-stu-id="f9be2-121">Here's a short list of the tools you'll find helpful:</span></span>

* <span data-ttu-id="f9be2-122">NuGet – [Cliente Nuget](https://dist.nuget.org/index.html) ou [Explorador de Pacotes NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), o gerenciador de pacotes da Microsoft para implementações do .NET.</span><span class="sxs-lookup"><span data-stu-id="f9be2-122">NuGet - [Nuget Client](https://dist.nuget.org/index.html) or [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), Microsoft's package manager for .NET implementations.</span></span>
* <span data-ttu-id="f9be2-123">Analisador de Portabilidade de API – [ferramenta de linha de comando](https://github.com/Microsoft/dotnet-apiport/releases) ou [Extensão do Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), uma cadeia de ferramentas que pode gerar um relatório sobre a portabilidade do seu código entre o .NET Framework e .NET Core, com detalhamento dos problemas assembly por assembly.</span><span class="sxs-lookup"><span data-stu-id="f9be2-123">Api Portability Analyzer - [command line tool](https://github.com/Microsoft/dotnet-apiport/releases) or [Visual Studio Extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), a toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core, with an assembly-by-assembly breakdown of issues.</span></span>  <span data-ttu-id="f9be2-124">Consulte [Ferramentas para ajudar no processo](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="f9be2-124">See [Tooling to help you on the process](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) for more information.</span></span>
* <span data-ttu-id="f9be2-125">Pesquisa Inversa de Pacotes – Um [serviço Web útil](https://packagesearch.azurewebsites.net) que permite pesquisar por um tipo e localizar os pacotes que contêm esse tipo.</span><span class="sxs-lookup"><span data-stu-id="f9be2-125">Reverse Package Search - A [useful web service](https://packagesearch.azurewebsites.net) that allows you to search for a type and find packages containing that type.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f9be2-126">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="f9be2-126">Next steps</span></span>

[<span data-ttu-id="f9be2-127">Analisando dependências de terceiros.</span><span class="sxs-lookup"><span data-stu-id="f9be2-127">Analyzing your third-party dependencies.</span></span>](third-party-deps.md)
   
