---
title: Porta do .NET Framework para o .NET Core
description: Entenda o processo de compatibilidade e descubra ferramentas que podem ser úteis ao realizar a portabilidade de um projeto do .NET Framework para o .NET Core.
author: cartermp
ms.date: 10/22/2019
ms.custom: seodec18
ms.openlocfilehash: 0684be25cee6ae3f778e7134b4c3a29ac87caf25
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798799"
---
# <a name="overview-of-the-porting-process-from-net-framework-to-net-core"></a><span data-ttu-id="f06b9-103">Visão geral do processo de portabilidade do .NET Framework para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="f06b9-103">Overview of the porting process from .NET Framework to .NET Core</span></span>

<span data-ttu-id="f06b9-104">Você pode ter um código que atualmente é executado no .NET Framework que você está interessado em portar para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f06b9-104">You might have code that currently runs on the .NET Framework that you're interested in porting to .NET Core.</span></span> <span data-ttu-id="f06b9-105">Este artigo fornece:</span><span class="sxs-lookup"><span data-stu-id="f06b9-105">This article provides:</span></span>

* <span data-ttu-id="f06b9-106">Uma visão geral do processo de portabilidade.</span><span class="sxs-lookup"><span data-stu-id="f06b9-106">An overview of the porting process.</span></span>
* <span data-ttu-id="f06b9-107">Uma lista das ferramentas que você pode achar útil quando está portando seu código para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f06b9-107">A list of the tools you may find helpful when you're porting your code to .NET Core.</span></span>

## <a name="overview-of-the-porting-process"></a><span data-ttu-id="f06b9-108">Visão geral do processo de portabilidade</span><span class="sxs-lookup"><span data-stu-id="f06b9-108">Overview of the porting process</span></span>

<span data-ttu-id="f06b9-109">Recomendamos que você use o seguinte processo ao portar seu projeto para o .NET Core:</span><span class="sxs-lookup"><span data-stu-id="f06b9-109">We recommend you to use the following process when porting your project to .NET Core:</span></span>

1. <span data-ttu-id="f06b9-110">Redirecione todos os projetos que você deseja portar para o .NET Framework 4.7.2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="f06b9-110">Retarget all projects you wish to port to target the .NET Framework 4.7.2 or higher.</span></span>

   <span data-ttu-id="f06b9-111">Essa etapa garante que você possa usar alternativas de API para destinos específicos do .NET Framework quando o .NET Core não oferecer suporte a determinada API.</span><span class="sxs-lookup"><span data-stu-id="f06b9-111">This step ensures that you can use API alternatives for .NET Framework-specific targets when .NET Core doesn't support a particular API.</span></span>

2. <span data-ttu-id="f06b9-112">Use o [.net Portability Analyzer](../../standard/analyzers/portability-analyzer.md) para analisar seus assemblies e ver se eles são portáteis para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f06b9-112">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to analyze your assemblies and see if they're portable to .NET Core.</span></span>

   <span data-ttu-id="f06b9-113">A ferramenta Analisador de portabilidade de API analisa os assemblies compilados e gera um relatório.</span><span class="sxs-lookup"><span data-stu-id="f06b9-113">The API Portability Analyzer tool analyzes your compiled assemblies and generates a report.</span></span> <span data-ttu-id="f06b9-114">Este relatório mostra um resumo de portabilidade de alto nível e uma análise de cada API que você está usando e que não está disponível no núcleo da rede.</span><span class="sxs-lookup"><span data-stu-id="f06b9-114">This report shows a high-level portability summary and a breakdown of each API you're using that isn't available on NET Core.</span></span>

3. <span data-ttu-id="f06b9-115">Instale o [.NET API Analyzer](../../standard/analyzers/api-analyzer.md) em seus projetos para identificar as APIs que geram <xref:System.PlatformNotSupportedException> em algumas plataformas e outros problemas de compatibilidade em potencial.</span><span class="sxs-lookup"><span data-stu-id="f06b9-115">Install the [.NET API analyzer](../../standard/analyzers/api-analyzer.md) into your projects to identify APIs throwing <xref:System.PlatformNotSupportedException> on some platforms and some other potential compatibility issues.</span></span>

   <span data-ttu-id="f06b9-116">Essa ferramenta é semelhante ao analisador de portabilidade, mas em vez de analisar se as coisas podem ser criadas no .NET Core, ela analisará se você estiver usando uma API de uma forma que irá lançar o <xref:System.PlatformNotSupportedException> em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f06b9-116">This tool is similar to the portability analyzer, but instead of analyzing if things can build on .NET Core, it will analyze if you're using an API in a way that will throw the <xref:System.PlatformNotSupportedException> at runtime.</span></span> <span data-ttu-id="f06b9-117">Embora isso não seja comum se você estiver mudando de .NET Framework 4.7.2 ou superior, é bom verificar.</span><span class="sxs-lookup"><span data-stu-id="f06b9-117">Although this isn't common if you're moving from .NET Framework 4.7.2 or higher, it's good to check.</span></span>

4. <span data-ttu-id="f06b9-118">Converta todas as suas dependências de `packages.config` para o formato [PackageReference](/nuget/consume-packages/package-references-in-project-files) com a [ferramenta de conversão no Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).</span><span class="sxs-lookup"><span data-stu-id="f06b9-118">Convert all of your `packages.config` dependencies to the [PackageReference](/nuget/consume-packages/package-references-in-project-files) format with the [conversion tool in Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).</span></span>

   <span data-ttu-id="f06b9-119">Esta etapa envolve a conversão de suas dependências do formato herdado `packages.config`.</span><span class="sxs-lookup"><span data-stu-id="f06b9-119">This step involves converting your dependencies from the legacy `packages.config` format.</span></span> <span data-ttu-id="f06b9-120">`packages.config` não funciona no .NET Core, portanto, essa conversão será necessária se você tiver dependências de pacote.</span><span class="sxs-lookup"><span data-stu-id="f06b9-120">`packages.config` doesn't work on .NET Core, so this conversion is required if you have package dependencies.</span></span>

5. <span data-ttu-id="f06b9-121">Crie novos projetos para o .NET Core e copie sobre os arquivos de origem ou tente converter o arquivo de projeto existente com uma ferramenta.</span><span class="sxs-lookup"><span data-stu-id="f06b9-121">Create new projects for .NET Core and copy over source files, or attempt to convert your existing project file with a tool.</span></span>

   <span data-ttu-id="f06b9-122">O .NET Core usa um formato de arquivo de [projeto](../tools/csproj.md) simplificado (e diferente) do que o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f06b9-122">.NET Core uses a simplified (and different) [project file format](../tools/csproj.md) than .NET Framework.</span></span> <span data-ttu-id="f06b9-123">Você precisará converter os arquivos de projeto nesse formato para continuar.</span><span class="sxs-lookup"><span data-stu-id="f06b9-123">You'll need to convert your project files into this format to continue.</span></span>

6. <span data-ttu-id="f06b9-124">Portar seu código de teste.</span><span class="sxs-lookup"><span data-stu-id="f06b9-124">Port your test code.</span></span>

   <span data-ttu-id="f06b9-125">Como a portabilidade para o .NET Core é uma mudança significativa para sua base de código, é altamente recomendável portar seus testes para poder realizar testes à medida que o código é portado.</span><span class="sxs-lookup"><span data-stu-id="f06b9-125">Because porting to .NET Core is such a significant change to your codebase, it's highly recommended to get your tests ported, so that you can run tests as you port your code over.</span></span> <span data-ttu-id="f06b9-126">MSTest, xUnit e NUnit funcionam no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f06b9-126">MSTest, xUnit, and NUnit all work on .NET Core.</span></span>

<span data-ttu-id="f06b9-127">Além disso, você pode tentar portar soluções menores ou projetos individuais para o formato de arquivo de projeto do .NET Core com a ferramenta [dotnet try-Convert](https://github.com/dotnet/try-convert) em uma única operação.</span><span class="sxs-lookup"><span data-stu-id="f06b9-127">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [dotnet try-convert](https://github.com/dotnet/try-convert) tool in one operation.</span></span> <span data-ttu-id="f06b9-128">Não há garantia de que o `dotnet try-convert` funcione para todos os seus projetos e pode causar alterações sutis no comportamento que você depende.</span><span class="sxs-lookup"><span data-stu-id="f06b9-128">`dotnet try-convert` is not guaranteedto work for all your projects, and it may cause subtle changes in behavior that you may find that you depended on.</span></span> <span data-ttu-id="f06b9-129">Ele deve ser usado como um _ponto de partida_ que automatiza as coisas básicas que podem ser automatizadas.</span><span class="sxs-lookup"><span data-stu-id="f06b9-129">It should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="f06b9-130">Não é uma solução garantida para migrar um projeto.</span><span class="sxs-lookup"><span data-stu-id="f06b9-130">It isn't a guaranteed solution to migrating a project.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="f06b9-131">Avançar</span><span class="sxs-lookup"><span data-stu-id="f06b9-131">Next</span></span>](net-framework-tech-unavailable.md)
