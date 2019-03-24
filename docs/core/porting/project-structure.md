---
title: Organizar projetos do .NET Framework e .NET Core
description: Ajuda para os proprietários de projeto que desejam compilar sua solução no .NET Framework e .NET Core lado a lado.
author: conniey
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: ab484ccc2c5b51b2ee1dca57df51669d288f3e6b
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58186059"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a><span data-ttu-id="66b0a-103">Organize seu projeto para oferecer suporte ao .NET Framework e ao .NET Core</span><span class="sxs-lookup"><span data-stu-id="66b0a-103">Organize your project to support both .NET Framework and .NET Core</span></span>

<span data-ttu-id="66b0a-104">Saiba como criar uma solução compilada para .NET Framework e .NET Core simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="66b0a-104">Learn how to create a solution that compiles for both .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="66b0a-105">Veja várias opções para organizar projetos que o ajudam a atingir esse objetivo.</span><span class="sxs-lookup"><span data-stu-id="66b0a-105">See several options to organize projects to help you achieve this goal.</span></span> <span data-ttu-id="66b0a-106">Estes são alguns cenários típicos que você deve considerar ao decidir como configurar o layout de projeto com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="66b0a-106">Here are some typical scenarios to consider when you're deciding how to setup your project layout with .NET Core.</span></span> <span data-ttu-id="66b0a-107">A lista pode não abordar tudo o que você deseja, priorize dependendo das necessidades do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="66b0a-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

* [<span data-ttu-id="66b0a-108">**Combinar projetos existentes e projetos do .NET Core em um mesmo projeto**</span><span class="sxs-lookup"><span data-stu-id="66b0a-108">**Combine existing projects and .NET Core projects into single projects**</span></span>](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  <span data-ttu-id="66b0a-109">*Isso é bom para:*</span><span class="sxs-lookup"><span data-stu-id="66b0a-109">*What this is good for:*</span></span>
  * <span data-ttu-id="66b0a-110">Simplificar o processo de compilação ao compilar um único projeto em vez de vários, cada um direcionado para uma versão ou plataforma diferente do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="66b0a-110">Simplifying your build process by compiling a single project rather than compiling multiple projects, each targeting a different .NET Framework version or platform.</span></span>
  * <span data-ttu-id="66b0a-111">Simplificar o gerenciamento de arquivos de origem para projetos multiplataforma, pois é necessário gerenciar um único arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="66b0a-111">Simplifying source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="66b0a-112">Ao adicionar/remover arquivos da origem, as alternativas exigem que você sincronize manualmente esses recursos com outros projetos.</span><span class="sxs-lookup"><span data-stu-id="66b0a-112">When adding/removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  * <span data-ttu-id="66b0a-113">Fácil geração de um pacote NuGet para consumo.</span><span class="sxs-lookup"><span data-stu-id="66b0a-113">Easily generating a NuGet package for consumption.</span></span>
  * <span data-ttu-id="66b0a-114">Permite que você escreva código para uma versão específica do .NET Framework nas suas bibliotecas usando diretivas de compilador.</span><span class="sxs-lookup"><span data-stu-id="66b0a-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="66b0a-115">*Cenários sem suporte:*</span><span class="sxs-lookup"><span data-stu-id="66b0a-115">*Unsupported scenarios:*</span></span>
  * <span data-ttu-id="66b0a-116">Requer que os desenvolvedores usem o Visual Studio 2017 para abrir projetos existentes.</span><span class="sxs-lookup"><span data-stu-id="66b0a-116">Requires developers to use Visual Studio 2017 to open existing projects.</span></span> <span data-ttu-id="66b0a-117">Para dar suporte a versões mais antigas do Visual Studio, [manter seus arquivos de projeto em pastas diferentes](#support-vs) é uma opção melhor.</span><span class="sxs-lookup"><span data-stu-id="66b0a-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

* <a name="support-vs"></a><span data-ttu-id="66b0a-118">[**Manter os projetos existentes e os novos projetos do .NET Core separados**](#keep-existing-projects-and-create-a-net-core-project)</span><span class="sxs-lookup"><span data-stu-id="66b0a-118">[**Keep existing projects and new .NET Core projects separate**](#keep-existing-projects-and-create-a-net-core-project)</span></span>

  <span data-ttu-id="66b0a-119">*Isso é bom para:*</span><span class="sxs-lookup"><span data-stu-id="66b0a-119">*What this is good for:*</span></span>
  * <span data-ttu-id="66b0a-120">Continuar a dar suporte ao desenvolvimento em projetos existentes sem a necessidade de atualizar para os desenvolvedores/colaboradores que podem não ter o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="66b0a-120">Continuing to support development on existing projects without having to upgrade for developers/contributors who may not have Visual Studio 2017.</span></span>
  * <span data-ttu-id="66b0a-121">Diminuir a possibilidade de criar novos bugs em projetos existentes porque nenhuma variação de código é necessária nesses projetos.</span><span class="sxs-lookup"><span data-stu-id="66b0a-121">Decreasing the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="66b0a-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="66b0a-122">Example</span></span>

<span data-ttu-id="66b0a-123">Considere o repositório abaixo:</span><span class="sxs-lookup"><span data-stu-id="66b0a-123">Consider the repository below:</span></span>

![Projeto existente](./media/project-structure/existing-project-structure.png)

[<span data-ttu-id="66b0a-125">**Código-fonte**</span><span class="sxs-lookup"><span data-stu-id="66b0a-125">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

<span data-ttu-id="66b0a-126">A seguir são descritas várias maneiras de adicionar suporte ao .NET Core para esse repositório dependendo das restrições e da complexidade dos projetos existentes.</span><span class="sxs-lookup"><span data-stu-id="66b0a-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="66b0a-127">Substituir os projetos existentes por um projeto multiplataforma do .NET Core</span><span class="sxs-lookup"><span data-stu-id="66b0a-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="66b0a-128">Reorganize o repositório para que todos os arquivos *\*.csproj* existentes sejam removidos e seja criado um único arquivo *\*.csproj* direcionado a várias estruturas.</span><span class="sxs-lookup"><span data-stu-id="66b0a-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="66b0a-129">Essa é uma ótima opção, pois um único projeto é capaz de ser compilado para estruturas diferentes.</span><span class="sxs-lookup"><span data-stu-id="66b0a-129">This is a great option because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="66b0a-130">Ela também tem a capacidade de lidar com diferentes opções de compilação e dependências por estrutura de destino.</span><span class="sxs-lookup"><span data-stu-id="66b0a-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

![Criar um csproj direcionado a várias estruturas](./media/project-structure/multi-targeted-project.png)

[<span data-ttu-id="66b0a-132">**Código-fonte**</span><span class="sxs-lookup"><span data-stu-id="66b0a-132">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

<span data-ttu-id="66b0a-133">Observe as seguintes alterações:</span><span class="sxs-lookup"><span data-stu-id="66b0a-133">Changes to note are:</span></span>

* <span data-ttu-id="66b0a-134">Substituição de *packages.config* e *\*.csproj* por um novo [*\*.csproj* do .NET Core](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span><span class="sxs-lookup"><span data-stu-id="66b0a-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span></span> <span data-ttu-id="66b0a-135">Pacotes NuGet são especificados com `<PackageReference> ItemGroup`.</span><span class="sxs-lookup"><span data-stu-id="66b0a-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="66b0a-136">Manter projetos existentes e criar um projeto do .NET Core</span><span class="sxs-lookup"><span data-stu-id="66b0a-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="66b0a-137">Se houver projetos existentes que usam estruturas mais antigas, poderá ser útil deixá-los inalterados e usar um projeto do .NET Core para ser direcionado para futuras estruturas.</span><span class="sxs-lookup"><span data-stu-id="66b0a-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

![Projeto do .NET Core com um projeto existente em uma pasta diferente](./media/project-structure/separate-projects-same-source.png)

[<span data-ttu-id="66b0a-139">**Código-fonte**</span><span class="sxs-lookup"><span data-stu-id="66b0a-139">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

<span data-ttu-id="66b0a-140">Observe as seguintes alterações:</span><span class="sxs-lookup"><span data-stu-id="66b0a-140">Changes to note are:</span></span>

* <span data-ttu-id="66b0a-141">O .NET Core e projetos existentes são mantidos em pastas separadas.</span><span class="sxs-lookup"><span data-stu-id="66b0a-141">The .NET Core and existing projects are kept in separate folders.</span></span>
  * <span data-ttu-id="66b0a-142">Manter projetos em pastas separadas evita a necessidade de ter o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="66b0a-142">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017.</span></span> <span data-ttu-id="66b0a-143">Você pode criar uma solução separada que abre somente os projetos antigos.</span><span class="sxs-lookup"><span data-stu-id="66b0a-143">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="66b0a-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66b0a-144">See also</span></span>

<span data-ttu-id="66b0a-145">Confira a [Documentação de portabilidade do .NET Core](index.md) para obter mais diretrizes de migração para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="66b0a-145">Please see the [.NET Core porting documentation](index.md) for more guidance on migrating to .NET Core.</span></span>
