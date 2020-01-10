---
title: Organizar projetos do .NET Framework e .NET Core
description: Ajuda para os proprietários de projeto que desejam compilar sua solução no .NET Framework e .NET Core lado a lado.
author: conniey
ms.date: 12/07/2018
ms.openlocfilehash: d71cc3102846c08f4e35831921b8cc4ca82f9e1b
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777329"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a><span data-ttu-id="59edd-103">Organize seu projeto para oferecer suporte ao .NET Framework e ao .NET Core</span><span class="sxs-lookup"><span data-stu-id="59edd-103">Organize your project to support both .NET Framework and .NET Core</span></span>

<span data-ttu-id="59edd-104">Você pode criar uma solução que compila para o .NET Framework e o .NET Core lado a lado.</span><span class="sxs-lookup"><span data-stu-id="59edd-104">You can create a solution that compiles for both .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="59edd-105">Este artigo aborda várias opções de organização de projeto para ajudá-lo a atingir essa meta.</span><span class="sxs-lookup"><span data-stu-id="59edd-105">This article covers several project-organization options to help you achieve this goal.</span></span> <span data-ttu-id="59edd-106">Aqui estão alguns cenários típicos a considerar quando você está decidindo como configurar o layout do projeto com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="59edd-106">Here are some typical scenarios to consider when you're deciding how to set up your project layout with .NET Core.</span></span> <span data-ttu-id="59edd-107">A lista pode não abordar tudo o que você deseja, priorize dependendo das necessidades do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="59edd-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

- [<span data-ttu-id="59edd-108">**Combinar projetos existentes e projetos do .NET Core em um mesmo projeto**</span><span class="sxs-lookup"><span data-stu-id="59edd-108">**Combine existing projects and .NET Core projects into single projects**</span></span>](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  <span data-ttu-id="59edd-109">*Isso é bom para:*</span><span class="sxs-lookup"><span data-stu-id="59edd-109">*What this is good for:*</span></span>
  - <span data-ttu-id="59edd-110">Simplifica o processo de compilação Compilando um único projeto em vez de vários projetos que têm como destino uma versão ou plataforma diferente .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="59edd-110">Simplifies your build process by compiling a single project rather than multiple projects that each target a different .NET Framework version or platform.</span></span>
  - <span data-ttu-id="59edd-111">Simplifica o gerenciamento de arquivos de origem para projetos multiplataforma porque você deve gerenciar um único arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="59edd-111">Simplifies source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="59edd-112">Ao adicionar ou remover arquivos de origem, as alternativas exigem que você os sincronize manualmente com seus outros projetos.</span><span class="sxs-lookup"><span data-stu-id="59edd-112">When adding or removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  - <span data-ttu-id="59edd-113">Gere facilmente um pacote NuGet para consumo.</span><span class="sxs-lookup"><span data-stu-id="59edd-113">Easily generate a NuGet package for consumption.</span></span>
  - <span data-ttu-id="59edd-114">Permite que você escreva código para uma versão específica do .NET Framework nas suas bibliotecas usando diretivas de compilador.</span><span class="sxs-lookup"><span data-stu-id="59edd-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="59edd-115">*Cenários sem suporte:*</span><span class="sxs-lookup"><span data-stu-id="59edd-115">*Unsupported scenarios:*</span></span>
  - <span data-ttu-id="59edd-116">Exige que os desenvolvedores usem o Visual Studio 2017 ou uma versão posterior para abrir projetos existentes.</span><span class="sxs-lookup"><span data-stu-id="59edd-116">Requires developers to use Visual Studio 2017 or a later version to open existing projects.</span></span> <span data-ttu-id="59edd-117">Para dar suporte a versões mais antigas do Visual Studio, [manter seus arquivos de projeto em pastas diferentes](#support-vs) é uma opção melhor.</span><span class="sxs-lookup"><span data-stu-id="59edd-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

- <a name="support-vs"></a><span data-ttu-id="59edd-118">[**Manter os projetos existentes e os novos projetos do .NET Core separados**](#keep-existing-projects-and-create-a-net-core-project)</span><span class="sxs-lookup"><span data-stu-id="59edd-118">[**Keep existing projects and new .NET Core projects separate**](#keep-existing-projects-and-create-a-net-core-project)</span></span>

  <span data-ttu-id="59edd-119">*Isso é bom para:*</span><span class="sxs-lookup"><span data-stu-id="59edd-119">*What this is good for:*</span></span>
  - <span data-ttu-id="59edd-120">Dá suporte ao desenvolvimento em projetos existentes para desenvolvedores e colaboradores que podem não ter o Visual Studio 2017 ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="59edd-120">Supports development on existing projects for developers and contributors who may not have Visual Studio 2017 or a later version.</span></span>
  - <span data-ttu-id="59edd-121">Diminui a possibilidade de criar novos bugs em projetos existentes porque nenhuma variação de código é necessária nesses projetos.</span><span class="sxs-lookup"><span data-stu-id="59edd-121">Decreases the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="59edd-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59edd-122">Example</span></span>

<span data-ttu-id="59edd-123">Considere o repositório abaixo:</span><span class="sxs-lookup"><span data-stu-id="59edd-123">Consider the repository below:</span></span>

![Projeto existente](./media/project-structure/existing-project-structure.png)

[<span data-ttu-id="59edd-125">**Código-fonte**</span><span class="sxs-lookup"><span data-stu-id="59edd-125">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

<span data-ttu-id="59edd-126">A seguir são descritas várias maneiras de adicionar suporte ao .NET Core para esse repositório dependendo das restrições e da complexidade dos projetos existentes.</span><span class="sxs-lookup"><span data-stu-id="59edd-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="59edd-127">Substituir os projetos existentes por um projeto multiplataforma do .NET Core</span><span class="sxs-lookup"><span data-stu-id="59edd-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="59edd-128">Reorganize o repositório para que todos os arquivos *\*.csproj* existentes sejam removidos e seja criado um único arquivo *\*.csproj* direcionado a várias estruturas.</span><span class="sxs-lookup"><span data-stu-id="59edd-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="59edd-129">Essa é uma ótima opção, pois um único projeto é capaz de Compilar para estruturas diferentes.</span><span class="sxs-lookup"><span data-stu-id="59edd-129">This is a great option, because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="59edd-130">Ela também tem a capacidade de lidar com diferentes opções de compilação e dependências por estrutura de destino.</span><span class="sxs-lookup"><span data-stu-id="59edd-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

![Criar um csproj que tem como alvo várias estruturas](./media/project-structure/multi-targeted-project.png)

[<span data-ttu-id="59edd-132">**Código-fonte**</span><span class="sxs-lookup"><span data-stu-id="59edd-132">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

<span data-ttu-id="59edd-133">Observe as seguintes alterações:</span><span class="sxs-lookup"><span data-stu-id="59edd-133">Changes to note are:</span></span>

- <span data-ttu-id="59edd-134">Substituição de *packages.config* e *\*.csproj* por um novo [ *\*.csproj* do .NET Core](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span><span class="sxs-lookup"><span data-stu-id="59edd-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span></span> <span data-ttu-id="59edd-135">Pacotes NuGet são especificados com `<PackageReference> ItemGroup`.</span><span class="sxs-lookup"><span data-stu-id="59edd-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="59edd-136">Manter projetos existentes e criar um projeto do .NET Core</span><span class="sxs-lookup"><span data-stu-id="59edd-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="59edd-137">Se houver projetos existentes que usam estruturas mais antigas, poderá ser útil deixá-los inalterados e usar um projeto do .NET Core para ser direcionado para futuras estruturas.</span><span class="sxs-lookup"><span data-stu-id="59edd-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

![Projeto do .NET Core com um projeto existente em uma pasta diferente](./media/project-structure/separate-projects-same-source.png)

[<span data-ttu-id="59edd-139">**Código-fonte**</span><span class="sxs-lookup"><span data-stu-id="59edd-139">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

<span data-ttu-id="59edd-140">O .NET Core e projetos existentes são mantidos em pastas separadas.</span><span class="sxs-lookup"><span data-stu-id="59edd-140">The .NET Core and existing projects are kept in separate folders.</span></span> <span data-ttu-id="59edd-141">Manter projetos em pastas separadas evita forçá-lo a ter o Visual Studio 2017 ou versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="59edd-141">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017 or later versions.</span></span> <span data-ttu-id="59edd-142">Você pode criar uma solução separada que abre somente os projetos antigos.</span><span class="sxs-lookup"><span data-stu-id="59edd-142">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="59edd-143">Veja também</span><span class="sxs-lookup"><span data-stu-id="59edd-143">See also</span></span>

- [<span data-ttu-id="59edd-144">Documentação de portabilidade do .NET Core</span><span class="sxs-lookup"><span data-stu-id="59edd-144">.NET Core porting documentation</span></span>](index.md)
