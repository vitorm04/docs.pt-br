---
title: Organizando seu projeto para dar suporte ao .NET Framework e ao .NET Core
description: "Ajuda para os proprietários de projeto que desejam compilar sua solução no .NET Framework e .NET Core lado a lado."
keywords: ".NET, .NET Core, .NET Framework, layout de projeto, várias estruturas"
author: conniey
ms.author: mairaw
ms.date: 04/06/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3af62252-1dfa-4336-8d2f-5cfdb57d7724
ms.openlocfilehash: 93bec65e3bbee93855d6f5bce5e2d6cea8bb9f3d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="organizing-your-project-to-support-net-framework-and-net-core"></a><span data-ttu-id="4521c-104">Organizando seu projeto para dar suporte ao .NET Framework e ao .NET Core</span><span class="sxs-lookup"><span data-stu-id="4521c-104">Organizing your project to support .NET Framework and .NET Core</span></span>

<span data-ttu-id="4521c-105">Este artigo ajuda os proprietários de projeto que desejam compilar sua solução no .NET Framework e .NET Core lado a lado.</span><span class="sxs-lookup"><span data-stu-id="4521c-105">This article helps project owners who want to compile their solution against .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="4521c-106">Ele fornece várias opções para organizar projetos para ajudar os desenvolvedores a atingirem esse objetivo.</span><span class="sxs-lookup"><span data-stu-id="4521c-106">It provides several options to organize projects to help developers achieve this goal.</span></span> <span data-ttu-id="4521c-107">A lista a seguir fornece alguns cenários típicos a serem considerados ao decidir como configurar o layout de projeto com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4521c-107">The following list provides some typical scenarios to consider when you're deciding how to setup your project layout with .NET Core.</span></span> <span data-ttu-id="4521c-108">A lista pode não abordar tudo o que você deseja, priorize dependendo das necessidades do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="4521c-108">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

* <span data-ttu-id="4521c-109">[**Combinar projetos existentes e do .NET Core em um mesmo projeto**][option-csproj]</span><span class="sxs-lookup"><span data-stu-id="4521c-109">[**Combine existing projects and .NET Core projects into single projects**][option-csproj]</span></span>

  <span data-ttu-id="4521c-110">*Isso é bom para:*</span><span class="sxs-lookup"><span data-stu-id="4521c-110">*What this is good for:*</span></span>
  * <span data-ttu-id="4521c-111">Simplificar o processo de compilação ao compilar um único projeto em vez de vários, cada um direcionado para uma versão ou plataforma diferente do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4521c-111">Simplifying your build process by compiling a single project rather than compiling multiple projects, each targeting a different .NET Framework version or platform.</span></span>
  * <span data-ttu-id="4521c-112">Simplificar o gerenciamento de arquivos de origem para projetos multiplataforma, pois é necessário gerenciar um único arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="4521c-112">Simplifying source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="4521c-113">Ao adicionar/remover arquivos da origem, as alternativas exigem que você sincronize manualmente esses recursos com outros projetos.</span><span class="sxs-lookup"><span data-stu-id="4521c-113">When adding/removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  * <span data-ttu-id="4521c-114">Fácil geração de um pacote NuGet para consumo.</span><span class="sxs-lookup"><span data-stu-id="4521c-114">Easily generating a NuGet package for consumption.</span></span>
  * <span data-ttu-id="4521c-115">Permite que você escreva código para uma versão específica do .NET Framework nas suas bibliotecas usando diretivas de compilador.</span><span class="sxs-lookup"><span data-stu-id="4521c-115">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="4521c-116">*Cenários sem suporte:*</span><span class="sxs-lookup"><span data-stu-id="4521c-116">*Unsupported scenarios:*</span></span>
  * <span data-ttu-id="4521c-117">Requer que os desenvolvedores usem o Visual Studio 2017 para abrir projetos existentes.</span><span class="sxs-lookup"><span data-stu-id="4521c-117">Requires developers to use Visual Studio 2017 to open existing projects.</span></span> <span data-ttu-id="4521c-118">Para dar suporte a versões mais antigas do Visual Studio, [manter seus arquivos de projeto em pastas diferentes](#support-vs) é uma opção melhor.</span><span class="sxs-lookup"><span data-stu-id="4521c-118">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

* <a name="support-vs"></a><span data-ttu-id="4521c-119">[**Manter projetos existentes e novos projetos do .NET Core separados**][option-csproj-folder]</span><span class="sxs-lookup"><span data-stu-id="4521c-119">[**Keep existing projects and new .NET Core projects separate**][option-csproj-folder]</span></span>

  <span data-ttu-id="4521c-120">*Isso é bom para:*</span><span class="sxs-lookup"><span data-stu-id="4521c-120">*What this is good for:*</span></span>
  * <span data-ttu-id="4521c-121">Continuar a dar suporte ao desenvolvimento em projetos existentes sem a necessidade de atualizar para os desenvolvedores/colaboradores que podem não ter o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="4521c-121">Continuing to support development on existing projects without having to upgrade for developers/contributors who may not have Visual Studio 2017.</span></span>
  * <span data-ttu-id="4521c-122">Diminuir a possibilidade de criar novos bugs em projetos existentes porque nenhuma variação de código é necessária nesses projetos.</span><span class="sxs-lookup"><span data-stu-id="4521c-122">Decreasing the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="4521c-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4521c-123">Example</span></span>

<span data-ttu-id="4521c-124">Considere o repositório abaixo:</span><span class="sxs-lookup"><span data-stu-id="4521c-124">Consider the repository below:</span></span>

<span data-ttu-id="4521c-125">![Projeto existente][example-initial-project]</span><span class="sxs-lookup"><span data-stu-id="4521c-125">![Existing project][example-initial-project]</span></span>

<span data-ttu-id="4521c-126">[**Código-fonte**][example-initial-project-code]</span><span class="sxs-lookup"><span data-stu-id="4521c-126">[**Source Code**][example-initial-project-code]</span></span>

<span data-ttu-id="4521c-127">A seguir são descritas várias maneiras de adicionar suporte ao .NET Core para esse repositório dependendo das restrições e da complexidade dos projetos existentes.</span><span class="sxs-lookup"><span data-stu-id="4521c-127">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="4521c-128">Substituir os projetos existentes por um projeto multiplataforma do .NET Core</span><span class="sxs-lookup"><span data-stu-id="4521c-128">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="4521c-129">Reorganize o repositório para que todos os arquivos *\*.csproj* existentes sejam removidos e seja criado um único arquivo *\*.csproj* direcionado a várias estruturas.</span><span class="sxs-lookup"><span data-stu-id="4521c-129">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="4521c-130">Essa é uma ótima opção, pois um único projeto é capaz de ser compilado para estruturas diferentes.</span><span class="sxs-lookup"><span data-stu-id="4521c-130">This is a great option because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="4521c-131">Ela também tem a capacidade de lidar com diferentes opções de compilação e dependências por estrutura de destino.</span><span class="sxs-lookup"><span data-stu-id="4521c-131">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

<span data-ttu-id="4521c-132">![Criar um csproj direcionado a várias estruturas][example-csproj]</span><span class="sxs-lookup"><span data-stu-id="4521c-132">![Create an csproj that targets multiple frameworks][example-csproj]</span></span>

<span data-ttu-id="4521c-133">[**Código-fonte**][example-csproj-code]</span><span class="sxs-lookup"><span data-stu-id="4521c-133">[**Source Code**][example-csproj-code]</span></span>

<span data-ttu-id="4521c-134">Observe as seguintes alterações:</span><span class="sxs-lookup"><span data-stu-id="4521c-134">Changes to note are:</span></span>
* <span data-ttu-id="4521c-135">Substituição de *packages.config* e *\*.csproj* por um novo [.NET Core *\*.csproj*][example-csproj-netcore].</span><span class="sxs-lookup"><span data-stu-id="4521c-135">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*][example-csproj-netcore].</span></span> <span data-ttu-id="4521c-136">Pacotes NuGet são especificados com `<PackageReference> ItemGroup`.</span><span class="sxs-lookup"><span data-stu-id="4521c-136">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="4521c-137">Manter projetos existentes e criar um projeto do .NET Core</span><span class="sxs-lookup"><span data-stu-id="4521c-137">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="4521c-138">Se houver projetos existentes que usam estruturas mais antigas, poderá ser útil deixá-los inalterados e usar um projeto do .NET Core para ser direcionado para futuras estruturas.</span><span class="sxs-lookup"><span data-stu-id="4521c-138">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

<span data-ttu-id="4521c-139">![Projeto .NET Core com um projeto existente em uma pasta diferente][example-csproj-different-folder]</span><span class="sxs-lookup"><span data-stu-id="4521c-139">![.NET Core project with existing project in different folder][example-csproj-different-folder]</span></span>

<span data-ttu-id="4521c-140">[**Código-fonte**][example-csproj-different-code]</span><span class="sxs-lookup"><span data-stu-id="4521c-140">[**Source Code**][example-csproj-different-code]</span></span>

<span data-ttu-id="4521c-141">Observe as seguintes alterações:</span><span class="sxs-lookup"><span data-stu-id="4521c-141">Changes to note are:</span></span>
* <span data-ttu-id="4521c-142">O .NET Core e projetos existentes são mantidos em pastas separadas.</span><span class="sxs-lookup"><span data-stu-id="4521c-142">The .NET Core and existing projects are kept in separate folders.</span></span>
    * <span data-ttu-id="4521c-143">Manter projetos em pastas separadas evita a necessidade de ter o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="4521c-143">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017.</span></span> <span data-ttu-id="4521c-144">Você pode criar uma solução separada que abre somente os projetos antigos.</span><span class="sxs-lookup"><span data-stu-id="4521c-144">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="4521c-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4521c-145">See Also</span></span>

<span data-ttu-id="4521c-146">Consulte a [Documentação de portabilidade do .NET Core][porting-doc] para obter mais diretrizes sobre a migração para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4521c-146">Please see the [.NET Core porting documentation][porting-doc] for more guidance on migrating to .NET Core.</span></span>

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "Projeto existente"
[example-initial-project-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library/

[example-csproj]: media/project-structure/project.csproj.png "Criar um csproj direcionado a várias estruturas"
[example-csproj-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj/
[example-csproj-netcore]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj/src/Car/Car.csproj

[example-csproj-different-folder]: media/project-structure/project.csproj.different.png "Projeto .NET Core com PCL existente em uma pasta diferente"
[example-csproj-different-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj-keep-existing/

[option-csproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project
[option-csproj-folder]: #keep-existing-projects-and-create-a-net-core-project
