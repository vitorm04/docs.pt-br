---
title: Portabilidade do .NET Framework para .NET Core
description: "Entenda o processo de compatibilidade e descubra ferramentas que podem ser úteis ao realizar a portabilidade de um projeto do .NET Framework para o .NET Core."
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 00d00d38-99af-44f4-a75f-defcd9729dc5
ms.openlocfilehash: 4fc68a3dbdec634d8e92a066a46939ba19c65db7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="porting-to-net-core-from-net-framework"></a><span data-ttu-id="0dd5e-104">Portabilidade do .NET Framework para .NET Core</span><span class="sxs-lookup"><span data-stu-id="0dd5e-104">Porting to .NET Core from .NET Framework</span></span>

<span data-ttu-id="0dd5e-105">Se você tiver código em execução no .NET Framework, poderá ser útil executar seu código no .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="0dd5e-105">If you've got code running on the .NET Framework, you may be interested in running your code on .NET Core 1.0.</span></span>  <span data-ttu-id="0dd5e-106">Esse artigo aborda uma visão geral do processo de portabilidade e uma lista das ferramentas que podem ser úteis na portabilidade para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0dd5e-106">This article covers an overview of the porting process and a list of the tools you may find helpful when porting to .NET Core.</span></span>

## <a name="overview-of-the-porting-process"></a><span data-ttu-id="0dd5e-107">Visão geral do processo de portabilidade</span><span class="sxs-lookup"><span data-stu-id="0dd5e-107">Overview of the Porting Process</span></span>

<span data-ttu-id="0dd5e-108">O processo recomendado de portabilidade segue a série de etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="0dd5e-108">The recommended process for porting follows the following series of steps.</span></span>  <span data-ttu-id="0dd5e-109">Cada uma dessas partes do processo é abordada em mais detalhes nos próximos artigos.</span><span class="sxs-lookup"><span data-stu-id="0dd5e-109">Each of these parts of the process are covered in more detail in further articles.</span></span>

1. <span data-ttu-id="0dd5e-110">Identifique e considere as dependências de terceiros.</span><span class="sxs-lookup"><span data-stu-id="0dd5e-110">Identify and account for your third-party dependencies.</span></span>

   <span data-ttu-id="0dd5e-111">Isso inclui compreender quais são suas dependências de terceiros, como você depende delas, como ver se elas também são executadas no .NET Core e as etapas a ser seguidas caso não sejam.</span><span class="sxs-lookup"><span data-stu-id="0dd5e-111">This will involve understanding what your third-party dependencies are, how you depend on them, how to see if they also run on .NET Core, and steps you can take if they don't.</span></span>
   
2. <span data-ttu-id="0dd5e-112">Redirecione todos os projetos que você deseja portar para o .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="0dd5e-112">Retarget all projects you wish to port to target .NET Framework 4.6.2.</span></span>

   <span data-ttu-id="0dd5e-113">Isso garante que você possa usar alternativas de API para destinos específicos de .NET Framework nos casos em que o .NET Core não dá suporte a uma determinada API.</span><span class="sxs-lookup"><span data-stu-id="0dd5e-113">This ensures that you can use API alternatives for .NET Framework-specific targets in the cases where .NET Core can't support a particular API.</span></span>
   
3. <span data-ttu-id="0dd5e-114">Use a [ferramenta Analisador de Portabilidade de API](https://github.com/Microsoft/dotnet-apiport/) para analisar seus assemblies e desenvolver um plano de portabilidade com base em seus resultados.</span><span class="sxs-lookup"><span data-stu-id="0dd5e-114">Use the [API Portability Analyzer tool](https://github.com/Microsoft/dotnet-apiport/) to analyze your assemblies and develop a plan to port based on its results.</span></span>

   <span data-ttu-id="0dd5e-115">A ferramenta Analisador de Portabilidade de API analisará seus assemblies compilados e gerará um relatório que mostra um resumo de portabilidade de alto nível e um detalhamento de cada API usada que não está disponível no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0dd5e-115">The API Portability Analyzer tool will analyze your compiled assemblies and generate a report which shows a high-level portability summary and a breakdown of each API you're using that isn't available on .NET Core.</span></span>  <span data-ttu-id="0dd5e-116">Você pode usar esse relatório junto com uma análise da sua base de código para desenvolver um plano para como você realizará a portabilidade do código.</span><span class="sxs-lookup"><span data-stu-id="0dd5e-116">You can use this report alongside an analysis of your codebase to develop a plan for how you'll port your code over.</span></span>
   
4. <span data-ttu-id="0dd5e-117">Porte seu código de testes.</span><span class="sxs-lookup"><span data-stu-id="0dd5e-117">Port your tests code.</span></span>

   <span data-ttu-id="0dd5e-118">Como a portabilidade para o .NET Core é uma grande mudança para sua base de código, é altamente recomendável portar seus testes para poder realizar testes à medida que o código é portado.</span><span class="sxs-lookup"><span data-stu-id="0dd5e-118">Because porting to .NET Core is such a big change to your codebase, it's highly recommended to get your tests ported so that you can run tests as you port code over.</span></span>  <span data-ttu-id="0dd5e-119">MSTest, xUnit e NUnit dão suporte ao .NET Core 1.0 no momento.</span><span class="sxs-lookup"><span data-stu-id="0dd5e-119">MSTest, xUnit, and NUnit all support .NET Core 1.0 today.</span></span>
   
6. <span data-ttu-id="0dd5e-120">Execute seu plano de portabilidade.</span><span class="sxs-lookup"><span data-stu-id="0dd5e-120">Execute your plan for porting!</span></span>

## <a name="tools-to-help"></a><span data-ttu-id="0dd5e-121">Ferramentas para ajudar</span><span class="sxs-lookup"><span data-stu-id="0dd5e-121">Tools to help</span></span>

<span data-ttu-id="0dd5e-122">Esta é uma breve lista das ferramentas que serão úteis:</span><span class="sxs-lookup"><span data-stu-id="0dd5e-122">Here's a short list of the tools you'll find helpful:</span></span>

* <span data-ttu-id="0dd5e-123">NuGet – [Cliente Nuget](https://dist.nuget.org/index.html) ou [Explorador de Pacotes NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), o gerenciador de pacotes da Microsoft para implementações do .NET.</span><span class="sxs-lookup"><span data-stu-id="0dd5e-123">NuGet - [Nuget Client](https://dist.nuget.org/index.html) or [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), Microsoft's package manager for .NET implementations.</span></span>
* <span data-ttu-id="0dd5e-124">Analisador de Portabilidade de API – [ferramenta de linha de comando](https://github.com/Microsoft/dotnet-apiport/releases) ou [Extensão do Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), uma cadeia de ferramentas que pode gerar um relatório sobre a portabilidade do seu código entre o .NET Framework e .NET Core, com detalhamento dos problemas assembly por assembly.</span><span class="sxs-lookup"><span data-stu-id="0dd5e-124">Api Portability Analyzer - [command line tool](https://github.com/Microsoft/dotnet-apiport/releases) or [Visual Studio Extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), a toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core, with an assembly-by-assembly breakdown of issues.</span></span>  <span data-ttu-id="0dd5e-125">Consulte [Ferramentas para ajudar no processo](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="0dd5e-125">See [Tooling to help you on the process](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) for more information.</span></span>
* <span data-ttu-id="0dd5e-126">Pesquisa Inversa de Pacotes – Um [serviço Web útil](https://packagesearch.azurewebsites.net) que permite pesquisar por um tipo e localizar os pacotes que contêm esse tipo.</span><span class="sxs-lookup"><span data-stu-id="0dd5e-126">Reverse Package Search - A [useful web service](https://packagesearch.azurewebsites.net) that allows you to search for a type and find packages containing that type.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0dd5e-127">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="0dd5e-127">Next steps</span></span>

[<span data-ttu-id="0dd5e-128">Analisando dependências de terceiros.</span><span class="sxs-lookup"><span data-stu-id="0dd5e-128">Analyzing your third-party dependencies.</span></span>](third-party-deps.md)
   
