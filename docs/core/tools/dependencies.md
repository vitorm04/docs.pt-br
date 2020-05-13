---
title: Gerenciar dependências no .NET Core
description: Explica como gerenciar dependências de projeto para um aplicativo .NET Core.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: b77acc7d4f03a45784f753d3daaa9810f110a6ac
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205948"
---
# <a name="manage-dependencies-in-net-core-applications"></a><span data-ttu-id="518c9-103">Gerenciar dependências em aplicativos .NET Core</span><span class="sxs-lookup"><span data-stu-id="518c9-103">Manage dependencies in .NET Core applications</span></span>

<span data-ttu-id="518c9-104">Este artigo explica como adicionar e remover dependências editando o arquivo de projeto ou usando a CLI.</span><span class="sxs-lookup"><span data-stu-id="518c9-104">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="518c9-105">O \< elemento> PackageReference</span><span class="sxs-lookup"><span data-stu-id="518c9-105">The \<PackageReference> element</span></span>

<span data-ttu-id="518c9-106">O `<PackageReference>` elemento de arquivo de projeto tem a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="518c9-106">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="518c9-107">O `Include` atributo especifica a ID do pacote a ser adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="518c9-107">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="518c9-108">O `Version` atributo especifica a versão a ser obtida.</span><span class="sxs-lookup"><span data-stu-id="518c9-108">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="518c9-109">As versões são especificadas de acordo com [as regras de versão do NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="518c9-109">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="518c9-110">Se você não estiver familiarizado com a sintaxe Project-File, consulte a documentação de [referência do projeto MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="518c9-110">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="518c9-111">Use condições para adicionar uma dependência que está disponível somente em um destino específico, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="518c9-111">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="518c9-112">A dependência no exemplo anterior só será válida se a compilação estiver acontecendo para o destino fornecido.</span><span class="sxs-lookup"><span data-stu-id="518c9-112">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="518c9-113">O `$(TargetFramework)` na condição é uma propriedade do MSBuild que está sendo definida no projeto.</span><span class="sxs-lookup"><span data-stu-id="518c9-113">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="518c9-114">Para aplicativos .NET Core mais comuns, você não precisa fazer isso.</span><span class="sxs-lookup"><span data-stu-id="518c9-114">For most common .NET Core applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="518c9-115">Adicionar uma dependência editando o arquivo de projeto</span><span class="sxs-lookup"><span data-stu-id="518c9-115">Add a dependency by editing the project file</span></span>

<span data-ttu-id="518c9-116">Para adicionar uma dependência, adicione um `<PackageReference>` elemento dentro de um `<ItemGroup>` elemento.</span><span class="sxs-lookup"><span data-stu-id="518c9-116">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="518c9-117">Você pode adicionar um existente `<ItemGroup>` ou criar um novo.</span><span class="sxs-lookup"><span data-stu-id="518c9-117">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="518c9-118">O exemplo a seguir usa o projeto de aplicativo de console padrão criado por `dotnet new console` :</span><span class="sxs-lookup"><span data-stu-id="518c9-118">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore" Version="3.1.2" />
  </ItemGroup>

</Project>
```

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="518c9-119">Adicionar uma dependência usando a CLI</span><span class="sxs-lookup"><span data-stu-id="518c9-119">Add a dependency by using the CLI</span></span>

<span data-ttu-id="518c9-120">Para adicionar uma dependência, execute o [dotnet add package](dotnet-add-package.md) comando, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="518c9-120">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="518c9-121">Remover uma dependência editando o arquivo de projeto</span><span class="sxs-lookup"><span data-stu-id="518c9-121">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="518c9-122">Para remover uma dependência, remova seu `<PackageReference>` elemento do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="518c9-122">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="518c9-123">Remover uma dependência usando a CLI</span><span class="sxs-lookup"><span data-stu-id="518c9-123">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="518c9-124">Para remover uma dependência, execute o [dotnet remove package](dotnet-remove-package.md) comando, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="518c9-124">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="518c9-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="518c9-125">See also</span></span>

* [<span data-ttu-id="518c9-126">Referências de pacotes em arquivos de projeto</span><span class="sxs-lookup"><span data-stu-id="518c9-126">Package references in project files</span></span>](../project-sdk/msbuild-props.md#reference-properties-and-items)
* <span data-ttu-id="518c9-127">[dotnet list packagelinha](dotnet-remove-package.md)</span><span class="sxs-lookup"><span data-stu-id="518c9-127">[dotnet list package command](dotnet-remove-package.md)</span></span>
