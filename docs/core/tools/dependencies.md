---
title: Gerenciamento de dependências das ferramentas do .NET Core
description: Explica como gerenciar suas dependências com as ferramentas do .NET Core.
ms.date: 03/06/2017
ms.openlocfilehash: 916daca0240c10dc63ca96048590a426bc51d450
ms.sourcegitcommit: feb42222f1430ca7b8115ae45e7a38fc4a1ba623
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/02/2020
ms.locfileid: "76965614"
---
# <a name="manage-dependencies-with-net-core-sdk-10"></a><span data-ttu-id="6410a-103">Gerenciar dependências com o SDK do .NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="6410a-103">Manage dependencies with .NET Core SDK 1.0</span></span>

<span data-ttu-id="6410a-104">Com a mudança dos projetos do .NET Core de project.json para csproj e o MSBuild, também ocorreu um investimento significativo que resultou na unificação do arquivo de projeto e dos ativos que permitem o acompanhamento de dependências.</span><span class="sxs-lookup"><span data-stu-id="6410a-104">With the move of .NET Core projects from project.json to csproj and MSBuild, a significant investment also happened that resulted in unification of the project file and assets that allow tracking of dependencies.</span></span> <span data-ttu-id="6410a-105">Para projetos do .NET Core, isso é semelhante ao que o Project. JSON fazia.</span><span class="sxs-lookup"><span data-stu-id="6410a-105">For .NET Core projects, this is similar to what project.json did.</span></span> <span data-ttu-id="6410a-106">Não há nenhum arquivo JSON ou XML separado que rastreia dependências do NuGet.</span><span class="sxs-lookup"><span data-stu-id="6410a-106">There is no separate JSON or XML file that tracks NuGet dependencies.</span></span> <span data-ttu-id="6410a-107">Com essa alteração, também apresentamos outro tipo de *referência* para a sintaxe csproj, chamada `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="6410a-107">With this change, we've also introduced another type of *reference* into the csproj syntax called the `<PackageReference>`.</span></span>

<span data-ttu-id="6410a-108">Este documento descreve o novo tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="6410a-108">This document describes the new reference type.</span></span> <span data-ttu-id="6410a-109">Ele também mostra como adicionar uma dependência de pacote usando esse novo tipo de referência para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="6410a-109">It also shows how to add a package dependency using this new reference type to your project.</span></span>

## <a name="the-new-packagereference-element"></a><span data-ttu-id="6410a-110">O novo elemento \<PackageReference></span><span class="sxs-lookup"><span data-stu-id="6410a-110">The new \<PackageReference> element</span></span>

<span data-ttu-id="6410a-111">O `<PackageReference>` tem a estrutura básica mostrada a seguir:</span><span class="sxs-lookup"><span data-stu-id="6410a-111">The `<PackageReference>` has the following basic structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="6410a-112">Se você estiver familiarizado com o MSBuild, ele será parecido com outros tipos de referência que já existem.</span><span class="sxs-lookup"><span data-stu-id="6410a-112">If you are familiar with MSBuild, it will look familiar to the other reference types that already exist.</span></span> <span data-ttu-id="6410a-113">A chave é a instrução `Include`, que especifica a ID do pacote que você deseja adicionar ao projeto.</span><span class="sxs-lookup"><span data-stu-id="6410a-113">The key is the `Include` statement, which specifies the package ID that you wish to add to the project.</span></span> <span data-ttu-id="6410a-114">O elemento filho `<Version>` especifica a versão obtida.</span><span class="sxs-lookup"><span data-stu-id="6410a-114">The `<Version>` child element specifies the version to get.</span></span> <span data-ttu-id="6410a-115">As versões são especificadas por [Regras de versão do NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="6410a-115">The versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="6410a-116">Se você não estiver familiarizado com a sintaxe Project-File, consulte a documentação de [referência do projeto MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="6410a-116">If you're not familiar with the project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="6410a-117">Use condições para adicionar uma dependência que está disponível somente em um destino específico, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6410a-117">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="6410a-118">A dependência só será válida se a compilação estiver acontecendo para o destino fornecido.</span><span class="sxs-lookup"><span data-stu-id="6410a-118">The dependency will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="6410a-119">O `$(TargetFramework)` na condição é uma propriedade do MSBuild que está sendo definida no projeto.</span><span class="sxs-lookup"><span data-stu-id="6410a-119">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="6410a-120">Para aplicativos .NET Core mais comuns, não será necessário fazer isso.</span><span class="sxs-lookup"><span data-stu-id="6410a-120">For most common .NET Core applications, you will not need to do this.</span></span>

## <a name="add-a-dependency-to-the-project"></a><span data-ttu-id="6410a-121">Adicionar uma dependência ao projeto</span><span class="sxs-lookup"><span data-stu-id="6410a-121">Add a dependency to the project</span></span>

<span data-ttu-id="6410a-122">Adicionar uma dependência ao projeto é simples.</span><span class="sxs-lookup"><span data-stu-id="6410a-122">Adding a dependency to your project is straightforward.</span></span> <span data-ttu-id="6410a-123">Veja um exemplo de como adicionar a versão `9.0.1` do Json.NET ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="6410a-123">Here is an example of how to add Json.NET version `9.0.1` to your project.</span></span> <span data-ttu-id="6410a-124">Obviamente, isso se aplica a qualquer outra dependência NuGet.</span><span class="sxs-lookup"><span data-stu-id="6410a-124">Of course, it is applicable to any other NuGet dependency.</span></span>

<span data-ttu-id="6410a-125">O arquivo de projeto tem dois ou mais nós de `<ItemGroup>`.</span><span class="sxs-lookup"><span data-stu-id="6410a-125">Your project file has two or more `<ItemGroup>` nodes.</span></span> <span data-ttu-id="6410a-126">Um dos nós já tem `<PackageReference>` elementos.</span><span class="sxs-lookup"><span data-stu-id="6410a-126">One of the nodes already has `<PackageReference>` elements in it.</span></span> <span data-ttu-id="6410a-127">Você pode adicionar sua nova dependência a este nó ou criar uma nova; o resultado será o mesmo.</span><span class="sxs-lookup"><span data-stu-id="6410a-127">You can add your new dependency to this node or create a new one; the result will be the same.</span></span>

<span data-ttu-id="6410a-128">O exemplo a seguir usa o modelo padrão Descartado pelo `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="6410a-128">The following example uses the default template that's dropped by `dotnet new console`.</span></span> <span data-ttu-id="6410a-129">Este é um aplicativo de console simples.</span><span class="sxs-lookup"><span data-stu-id="6410a-129">This is a simple console application.</span></span> <span data-ttu-id="6410a-130">Ao abrir o projeto, você encontrará o `<ItemGroup>` já existente `<PackageReference>` nele.</span><span class="sxs-lookup"><span data-stu-id="6410a-130">When you open up the project, you'll find the `<ItemGroup>` with already existing `<PackageReference>` in it.</span></span> <span data-ttu-id="6410a-131">Adicione o seguinte a ele:</span><span class="sxs-lookup"><span data-stu-id="6410a-131">Add the following to it:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

<span data-ttu-id="6410a-132">Depois disso, salve o projeto e execute o comando `dotnet restore` para instalar a dependência.</span><span class="sxs-lookup"><span data-stu-id="6410a-132">After this, save the project and run the `dotnet restore` command to install the dependency.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="6410a-133">O projeto completo tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="6410a-133">The full project looks like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
</Project>
```

## <a name="remove-a-dependency-from-the-project"></a><span data-ttu-id="6410a-134">Remover uma dependência do projeto</span><span class="sxs-lookup"><span data-stu-id="6410a-134">Remove a dependency from the project</span></span>

<span data-ttu-id="6410a-135">Para remover uma dependência do arquivo de projeto, simplesmente remova `<PackageReference>` do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="6410a-135">Removing a dependency from the project file involves simply removing the `<PackageReference>` from the project file.</span></span>
