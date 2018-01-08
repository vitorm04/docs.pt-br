---
title: "Gerenciamento de dependências das ferramentas do .NET Core"
description: "Explica como gerenciar suas dependências com as ferramentas do .NET Core."
keywords: CLI, extensibilidade, comandos personalizados, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 74b87cdb-a244-4c13-908c-539118bfeef9
ms.workload: dotnetcore
ms.openlocfilehash: a064ae72a077583cfb544309700555ebd9d398a6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a><span data-ttu-id="39efe-104">Gerenciando dependências com o SDK 1.0 do .NET Core</span><span class="sxs-lookup"><span data-stu-id="39efe-104">Managing dependencies with .NET Core SDK 1.0</span></span>

<span data-ttu-id="39efe-105">Com a mudança dos projetos do .NET Core de project.json para csproj e o MSBuild, também ocorreu um investimento significativo que resultou na unificação do arquivo de projeto e dos ativos que permitem o acompanhamento de dependências.</span><span class="sxs-lookup"><span data-stu-id="39efe-105">With the move of .NET Core projects from project.json to csproj and MSBuild, a significant investment also happened that resulted in unification of the project file and assets that allow tracking of dependencies.</span></span> <span data-ttu-id="39efe-106">Para projetos do .NET Core, isso é semelhante ao project.json.</span><span class="sxs-lookup"><span data-stu-id="39efe-106">For .NET Core projects this is similar to what project.json did.</span></span> <span data-ttu-id="39efe-107">Não há nenhum arquivo JSON ou XML separado que rastreia dependências do NuGet.</span><span class="sxs-lookup"><span data-stu-id="39efe-107">There is no separate JSON or XML file that tracks NuGet dependencies.</span></span> <span data-ttu-id="39efe-108">Com essa alteração, também apresentamos outro tipo de *referência* para a sintaxe csproj, chamada `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="39efe-108">With this change, we've also introduced another type of *reference* into the csproj syntax called the `<PackageReference>`.</span></span> 

<span data-ttu-id="39efe-109">Este documento descreve o novo tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="39efe-109">This document describes the new reference type.</span></span> <span data-ttu-id="39efe-110">Ele também mostra como adicionar uma dependência de pacote usando esse novo tipo de referência para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="39efe-110">It also shows how to add a package dependency using this new reference type to your project.</span></span> 

## <a name="the-new-packagereference-element"></a><span data-ttu-id="39efe-111">O novo elemento \<PackageReference></span><span class="sxs-lookup"><span data-stu-id="39efe-111">The new \<PackageReference> element</span></span>
<span data-ttu-id="39efe-112">O `<PackageReference>` tem a estrutura básica mostrada a seguir:</span><span class="sxs-lookup"><span data-stu-id="39efe-112">The `<PackageReference>` has the following basic structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="39efe-113">Se você estiver familiarizado com o MSBuild, ele será parecido com outros tipos de referência que já existem.</span><span class="sxs-lookup"><span data-stu-id="39efe-113">If you are familiar with MSBuild, it will look familiar to the other reference types that already exist.</span></span> <span data-ttu-id="39efe-114">A chave é a instrução do `Include`, que especifica a ID do pacote que você deseja adicionar ao projeto.</span><span class="sxs-lookup"><span data-stu-id="39efe-114">The key is the `Include` statement which specifies the package id that you wish to add to the project.</span></span> <span data-ttu-id="39efe-115">O elemento filho `<Version>` especifica a versão obtida.</span><span class="sxs-lookup"><span data-stu-id="39efe-115">The `<Version>` child element specifies the version to get.</span></span> <span data-ttu-id="39efe-116">As versões são especificadas por [Regras de versão do NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="39efe-116">The versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="39efe-117">Se você não está familiarizado com a sintaxe `csproj` geral, é possível usar a documentação de [referência de projeto MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) para mais informações.</span><span class="sxs-lookup"><span data-stu-id="39efe-117">If you are not familiar with the overall `csproj` syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>  

<span data-ttu-id="39efe-118">Pode-se adicionar uma dependência disponível somente em um destino específico usando condições como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="39efe-118">Adding a dependency that is available only in a specific target is done using conditions like in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp1.0'" />
```

<span data-ttu-id="39efe-119">Isso significa que a dependência só será válida se o build estiver ocorrendo para esse destino específico.</span><span class="sxs-lookup"><span data-stu-id="39efe-119">The above means that the dependency will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="39efe-120">O `$(TargetFramework)` na condição é uma propriedade do MSBuild que está sendo definida no projeto.</span><span class="sxs-lookup"><span data-stu-id="39efe-120">The `$(TargetFramework)` in the condition is a MSBuild property that is being set in the project.</span></span> <span data-ttu-id="39efe-121">Para aplicativos .NET Core mais comuns, não será necessário fazer isso.</span><span class="sxs-lookup"><span data-stu-id="39efe-121">For most common .NET Core applications, you will not need to do this.</span></span> 

## <a name="adding-a-dependency-to-your-project"></a><span data-ttu-id="39efe-122">Adicionar uma dependência ao projeto</span><span class="sxs-lookup"><span data-stu-id="39efe-122">Adding a dependency to your project</span></span>
<span data-ttu-id="39efe-123">Adicionar uma dependência ao projeto é simples.</span><span class="sxs-lookup"><span data-stu-id="39efe-123">Adding a dependency to your project is straightforward.</span></span> <span data-ttu-id="39efe-124">Veja um exemplo de como adicionar a versão `9.0.1` do Json.NET ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="39efe-124">Here is an example of how to add Json.NET version `9.0.1` to your project.</span></span> <span data-ttu-id="39efe-125">Obviamente, isso se aplica a qualquer outra dependência NuGet.</span><span class="sxs-lookup"><span data-stu-id="39efe-125">Of course, it is applicable to any other NuGet dependency.</span></span> 

<span data-ttu-id="39efe-126">Ao abrir o arquivo de projeto, você verá dois ou mais nós `<ItemGroup>`.</span><span class="sxs-lookup"><span data-stu-id="39efe-126">When you open your project file, you will see two or more `<ItemGroup>` nodes.</span></span> <span data-ttu-id="39efe-127">Você perceberá que um dos nós já tem elementos `<PackageReference>` contidos nele.</span><span class="sxs-lookup"><span data-stu-id="39efe-127">You will notice that one of the nodes already has `<PackageReference>` elements in it.</span></span> <span data-ttu-id="39efe-128">É possível adicionar a nova dependência a esse nó ou criar uma nova; isso cabe a você, pois o resultado será o mesmo.</span><span class="sxs-lookup"><span data-stu-id="39efe-128">You can add your new dependency to this node, or create a new one; it is completely up to you as the result will be the same.</span></span> 

<span data-ttu-id="39efe-129">Neste exemplo, usaremos o modelo padrão removido pelo `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="39efe-129">In this example we will use the default template that is dropped by `dotnet new console`.</span></span> <span data-ttu-id="39efe-130">Este é um aplicativo de console simples.</span><span class="sxs-lookup"><span data-stu-id="39efe-130">This is a simple console application.</span></span> <span data-ttu-id="39efe-131">Ao abrir o projeto, localizamos o `<ItemGroup>` com `<PackageReference>` já existentes nele.</span><span class="sxs-lookup"><span data-stu-id="39efe-131">When we open up the project, we first find the `<ItemGroup>` with already existing `<PackageReference>` in it.</span></span> <span data-ttu-id="39efe-132">Em seguida, adicionamos o seguinte:</span><span class="sxs-lookup"><span data-stu-id="39efe-132">We then add the following to it:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```
<span data-ttu-id="39efe-133">Depois disso, salve o projeto e execute o comando de `dotnet restore` para instalar a dependência.</span><span class="sxs-lookup"><span data-stu-id="39efe-133">After this, we save the project and run the `dotnet restore` command to install the dependency.</span></span> 

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="39efe-134">O projeto completo tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="39efe-134">The full project looks like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
</Project>
```

## <a name="removing-a-dependency-from-the-project"></a><span data-ttu-id="39efe-135">Remover uma dependência do projeto</span><span class="sxs-lookup"><span data-stu-id="39efe-135">Removing a dependency from the project</span></span>
<span data-ttu-id="39efe-136">Para remover uma dependência do arquivo de projeto, simplesmente remova `<PackageReference>` do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="39efe-136">Removing a dependency from the project file involves simply removing the `<PackageReference>` from the project file.</span></span>
