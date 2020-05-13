---
title: Como o MSBuild gera nomes de arquivo de manifesto
description: Descreve os fatores que influenciam o nome de um nome de arquivo de manifesto de recurso gerado pelo MSBuild no momento da compilação.
ms.date: 05/08/2020
ms.topic: conceptual
ms.openlocfilehash: 383bf6a077b0631e70ddaa4721b20e992127a73c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83232322"
---
# <a name="how-resource-manifest-files-are-named"></a><span data-ttu-id="1ec77-103">Como os arquivos de manifesto de recurso são nomeados</span><span class="sxs-lookup"><span data-stu-id="1ec77-103">How resource manifest files are named</span></span>

<span data-ttu-id="1ec77-104">Quando o MSBuild compila um projeto do .NET Core, os arquivos de recursos XML, que têm a extensão de arquivo *. resx* , são convertidos em arquivos *. Resources* binários.</span><span class="sxs-lookup"><span data-stu-id="1ec77-104">When MSBuild compiles a .NET Core project, XML resource files, which have the *.resx* file extension, are converted into binary *.resources* files.</span></span> <span data-ttu-id="1ec77-105">Os arquivos binários são inseridos na saída do compilador e podem ser lidos pelo <xref:System.Resources.ResourceManager> .</span><span class="sxs-lookup"><span data-stu-id="1ec77-105">The binary files are embedded into the output of the compiler and can be read by the <xref:System.Resources.ResourceManager>.</span></span> <span data-ttu-id="1ec77-106">Este artigo descreve como o MSBuild escolhe um nome para cada arquivo *. Resources* .</span><span class="sxs-lookup"><span data-stu-id="1ec77-106">This article describes how MSBuild chooses a name for each *.resources* file.</span></span>

> [!TIP]
> <span data-ttu-id="1ec77-107">Se você adicionar explicitamente um item de recurso ao seu arquivo de projeto e ele também estiver [incluído com o padrão include globs for .NET Core](../project-sdk/overview.md#default-compilation-includes), você receberá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="1ec77-107">If you explicitly add a resource item to your project file, and it's also [included with the default include globs for .NET Core](../project-sdk/overview.md#default-compilation-includes), you will get a build error.</span></span> <span data-ttu-id="1ec77-108">Para incluir manualmente os arquivos de recurso como `EmbeddedResource` itens, defina a `EnableDefaultEmbeddedResourceItems` propriedade como false.</span><span class="sxs-lookup"><span data-stu-id="1ec77-108">To manually include resource files as `EmbeddedResource` items, set the `EnableDefaultEmbeddedResourceItems` property to false.</span></span>

## <a name="default-name"></a><span data-ttu-id="1ec77-109">Nome padrão</span><span class="sxs-lookup"><span data-stu-id="1ec77-109">Default name</span></span>

<span data-ttu-id="1ec77-110">No .NET Core 3,0 e posterior, o nome padrão de um manifesto de recurso é usado quando as duas condições a seguir são atendidas:</span><span class="sxs-lookup"><span data-stu-id="1ec77-110">In .NET Core 3.0 and later, the default name for a resource manifest is used when both of the following conditions are met:</span></span>

- <span data-ttu-id="1ec77-111">O arquivo de recurso não é incluído explicitamente no arquivo de projeto como um `EmbeddedResource` item `LogicalName` com `ManifestResourceName` metadados, `DependentUpon` ou.</span><span class="sxs-lookup"><span data-stu-id="1ec77-111">The resource file is not explicitly included in the project file as an `EmbeddedResource` item with `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata.</span></span>
- <span data-ttu-id="1ec77-112">A `EmbeddedResourceUseDependentUponConvention` propriedade não está definida como `false` no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="1ec77-112">The `EmbeddedResourceUseDependentUponConvention` property is not set to `false` in the project file.</span></span> <span data-ttu-id="1ec77-113">Por padrão, essa propriedade é definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="1ec77-113">By default, this property is set to `true`.</span></span> <span data-ttu-id="1ec77-114">Para obter mais informações, consulte [EmbeddedResourceUseDependentUponConvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention).</span><span class="sxs-lookup"><span data-stu-id="1ec77-114">For more information, see [EmbeddedResourceUseDependentUponConvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention).</span></span>

<span data-ttu-id="1ec77-115">Se o arquivo de recurso for colocado com um arquivo de origem (*. cs* ou *. vb*) do mesmo nome de arquivo raiz, o nome completo do primeiro tipo definido no arquivo de origem será usado para o nome do arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="1ec77-115">If the resource file is colocated with a source file (*.cs* or *.vb*) of the same root file name, the full name of the first type that's defined in the source file is used for the manifest file name.</span></span> <span data-ttu-id="1ec77-116">Por exemplo, se `MyNamespace.Form1` for o primeiro tipo definido em *Form1.cs*e *Form1.cs* estiver colocalizado com *Form1. resx*, o nome de manifesto gerado para esse arquivo de recurso será *MyNamespace. Form1. Resources*.</span><span class="sxs-lookup"><span data-stu-id="1ec77-116">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, and *Form1.cs* is colocated with *Form1.resx*, the generated manifest name for that resource file is *MyNamespace.Form1.resources*.</span></span>

## <a name="logicalname-metadata"></a><span data-ttu-id="1ec77-117">Metadados LogicalName</span><span class="sxs-lookup"><span data-stu-id="1ec77-117">LogicalName metadata</span></span>

<span data-ttu-id="1ec77-118">Se um arquivo de recurso estiver explicitamente incluído no arquivo de projeto como um `EmbeddedResource` item com `LogicalName` metadados, o `LogicalName` valor será usado como o nome do manifesto.</span><span class="sxs-lookup"><span data-stu-id="1ec77-118">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `LogicalName` metadata, the `LogicalName` value is used as the manifest name.</span></span> <span data-ttu-id="1ec77-119">`LogicalName`tem precedência sobre qualquer outro metadado ou configuração.</span><span class="sxs-lookup"><span data-stu-id="1ec77-119">`LogicalName` takes precedence over any other metadata or setting.</span></span>

<span data-ttu-id="1ec77-120">Por exemplo, o nome do manifesto para o arquivo de recurso que é definido no trecho de arquivo de projeto a seguir é *um somename. Resources*.</span><span class="sxs-lookup"><span data-stu-id="1ec77-120">For example, the manifest name for the resource file that's defined in the following project file snippet is *SomeName.resources*.</span></span>

```xml
<EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
```

<span data-ttu-id="1ec77-121">-ou-</span><span class="sxs-lookup"><span data-stu-id="1ec77-121">-or-</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
```

## <a name="manifestresourcename-metadata"></a><span data-ttu-id="1ec77-122">Metadados do ManifestResourceName</span><span class="sxs-lookup"><span data-stu-id="1ec77-122">ManifestResourceName metadata</span></span>

<span data-ttu-id="1ec77-123">Se um arquivo de recurso estiver explicitamente incluído no arquivo de projeto como um `EmbeddedResource` item com `ManifestResourceName` metadados (e `LogicalName` estiver ausente), o `ManifestResourceName` valor, combinado com a extensão de arquivo *. Resources*, será usado como o nome do arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="1ec77-123">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `ManifestResourceName` metadata (and `LogicalName` is absent), the `ManifestResourceName` value, combined with the file extension *.resources*, is used as the manifest file name.</span></span>

<span data-ttu-id="1ec77-124">Por exemplo, o nome do manifesto para o arquivo de recurso que é definido no trecho de arquivo de projeto a seguir é *um somename. Resources*.</span><span class="sxs-lookup"><span data-stu-id="1ec77-124">For example, the manifest name for the resource file that's defined in the following project file snippet is *SomeName.resources*.</span></span>

```xml
<EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
```

<span data-ttu-id="1ec77-125">O nome do manifesto para o arquivo de recurso que é definido no trecho de arquivo de projeto a seguir é *somename.fr-fr. Resources*.</span><span class="sxs-lookup"><span data-stu-id="1ec77-125">The manifest name for the resource file that's defined in the following project file snippet is *SomeName.fr-FR.resources*.</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
```

## <a name="dependentupon-metadata"></a><span data-ttu-id="1ec77-126">Metadados do DependentUpon</span><span class="sxs-lookup"><span data-stu-id="1ec77-126">DependentUpon metadata</span></span>

<span data-ttu-id="1ec77-127">Se um arquivo de recurso estiver explicitamente incluído no arquivo de projeto como um `EmbeddedResource` item com `DependentUpon` metadados (e `LogicalName` e `ManifestResourceName` estiver ausente), as informações do arquivo de origem definido por `DependentUpon` são usadas para o nome do arquivo de manifesto de recurso.</span><span class="sxs-lookup"><span data-stu-id="1ec77-127">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `DependentUpon` metadata (and `LogicalName` and `ManifestResourceName` are absent), information from the source file defined by `DependentUpon` is used for the resource manifest file name.</span></span> <span data-ttu-id="1ec77-128">Especificamente, o nome do primeiro tipo que é definido no arquivo de origem é usado no nome do manifesto da seguinte maneira: *namespace. ClassName \[ . Culture]. Resources*.</span><span class="sxs-lookup"><span data-stu-id="1ec77-128">Specifically, the name of the first type that's defined in the source file is used in the manifest name as follows: *Namespace.Classname\[.Culture].resources*.</span></span>

<span data-ttu-id="1ec77-129">Por exemplo, o nome do manifesto para o arquivo de recurso que é definido no trecho de arquivo de projeto a seguir é *namespace. ClassName. Resources* (em que `Namespace.Classname` é a primeira classe que é definida em *myTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="1ec77-129">For example, the manifest name for the resource file that's defined in the following project file snippet is *Namespace.Classname.resources* (where `Namespace.Classname` is the first class that's defined in *MyTypes.cs*).</span></span>

```xml
<EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
```

<span data-ttu-id="1ec77-130">O nome do manifesto para o arquivo de recurso que é definido no trecho de arquivo de projeto a seguir é *namespace.ClassName.fr-fr. Resources* (em que `Namespace.Classname` é a primeira classe que é definida em *myTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="1ec77-130">The manifest name for the resource file that's defined in the following project file snippet is *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the first class that's defined in *MyTypes.cs*).</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
```

## <a name="embeddedresourceusedependentuponconvention-property"></a><span data-ttu-id="1ec77-131">Propriedade EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="1ec77-131">EmbeddedResourceUseDependentUponConvention property</span></span>

<span data-ttu-id="1ec77-132">Se `EmbeddedResourceUseDependentUponConvention` é definido como `false` no arquivo de projeto, cada nome de arquivo de manifesto de recurso é baseado no namespace raiz do projeto e no caminho relativo da raiz do projeto para o arquivo *. resx* .</span><span class="sxs-lookup"><span data-stu-id="1ec77-132">If `EmbeddedResourceUseDependentUponConvention` is set to `false` in the project file, each resource manifest file name is based off the root namespace for the project and the relative path from the project root to the *.resx* file.</span></span> <span data-ttu-id="1ec77-133">Mais especificamente, o nome do arquivo de manifesto do recurso gerado é *RootNamespace. RelativePathWithDotsForSlashes. \[ Culture.] recursos*do.</span><span class="sxs-lookup"><span data-stu-id="1ec77-133">More specifically, the generated resource manifest file name is *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources*.</span></span> <span data-ttu-id="1ec77-134">Essa também é a lógica usada para gerar nomes de manifesto em versões do .NET Core anteriores à 3,0.</span><span class="sxs-lookup"><span data-stu-id="1ec77-134">This is also the logic used to generate manifest names in .NET Core versions prior to 3.0.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="1ec77-135">Se `RootNamespace` não estiver definido, o padrão será o nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="1ec77-135">If `RootNamespace` is not defined, it defaults to the project name.</span></span>
> - <span data-ttu-id="1ec77-136">Se `LogicalName` os `ManifestResourceName` metadados, ou `DependentUpon` forem especificados para um `EmbeddedResource` item no arquivo de projeto, essa regra de nomenclatura não se aplicará a esse arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="1ec77-136">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item in the project file, this naming rule does not apply to that resource file.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ec77-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="1ec77-137">See also</span></span>

- [<span data-ttu-id="1ec77-138">Como o nome do recurso de manifesto funciona</span><span class="sxs-lookup"><span data-stu-id="1ec77-138">How Manifest Resource Naming Works</span></span>](https://gist.github.com/BenVillalobos/041673b9a73bec60fdc3bf0f86fae62a)
- [<span data-ttu-id="1ec77-139">Propriedades do MSBuild para projetos SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="1ec77-139">MSBuild properties for .NET Core SDK projects</span></span>](../project-sdk/msbuild-props.md)
- [<span data-ttu-id="1ec77-140">Alterações significativas do MSBuild</span><span class="sxs-lookup"><span data-stu-id="1ec77-140">MSBuild breaking changes</span></span>](../compatibility/msbuild.md)
