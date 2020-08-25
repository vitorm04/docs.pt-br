---
title: Propriedades do MSBuild para Microsoft. NET. Sdk
description: Referência para as propriedades e os itens do MSBuild que são compreendidos pelo SDK do .NET Core.
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: 39cbd18121d2b8659b2f5270f39624798f4ebbdc
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810515"
---
# <a name="msbuild-reference-for-net-core-sdk-projects"></a><span data-ttu-id="aad1d-103">Referência do MSBuild para projetos de SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="aad1d-103">MSBuild reference for .NET Core SDK projects</span></span>

<span data-ttu-id="aad1d-104">Esta página é uma referência para as propriedades e os itens do MSBuild que você pode usar para configurar projetos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aad1d-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="aad1d-105">Esta página é um trabalho em andamento e não lista todas as propriedades de MSBuild úteis para o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aad1d-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="aad1d-106">Para obter uma lista de propriedades comuns do MSBuild, consulte [Propriedades comuns do MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="aad1d-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="aad1d-107">Propriedades da estrutura</span><span class="sxs-lookup"><span data-stu-id="aad1d-107">Framework properties</span></span>

- [<span data-ttu-id="aad1d-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="aad1d-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="aad1d-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="aad1d-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="aad1d-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="aad1d-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="aad1d-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="aad1d-111">TargetFramework</span></span>

<span data-ttu-id="aad1d-112">A `TargetFramework` propriedade especifica a versão do Framework de destino para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aad1d-112">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="aad1d-113">Para obter uma lista de monikers de estrutura de destino válidos, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="aad1d-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="aad1d-114">Para obter mais informações, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="aad1d-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="aad1d-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="aad1d-115">TargetFrameworks</span></span>

<span data-ttu-id="aad1d-116">Use a `TargetFrameworks` propriedade quando desejar que seu aplicativo direcione várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="aad1d-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="aad1d-117">Para obter uma lista de monikers de estrutura de destino válidos, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="aad1d-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="aad1d-118">Essa propriedade será ignorada se `TargetFramework` (singular) for especificado.</span><span class="sxs-lookup"><span data-stu-id="aad1d-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="aad1d-119">Para obter mais informações, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="aad1d-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="aad1d-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="aad1d-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="aad1d-121">Essa propriedade só se aplica a projetos que usam o `netstandard1.x` .</span><span class="sxs-lookup"><span data-stu-id="aad1d-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="aad1d-122">Ele não se aplica a projetos que usam o `netstandard2.x` .</span><span class="sxs-lookup"><span data-stu-id="aad1d-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="aad1d-123">Use a `NetStandardImplicitPackageVersion` propriedade quando desejar especificar uma versão de estrutura inferior à versão do metapacote.</span><span class="sxs-lookup"><span data-stu-id="aad1d-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="aad1d-124">O arquivo de projeto no exemplo a seguir tem `netstandard1.3` como destino, mas usa a versão 1.6.0 do `NETStandard.Library` .</span><span class="sxs-lookup"><span data-stu-id="aad1d-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="aad1d-125">Propriedades do pacote</span><span class="sxs-lookup"><span data-stu-id="aad1d-125">Package properties</span></span>

<span data-ttu-id="aad1d-126">Você pode especificar propriedades como `PackageId` ,, `PackageVersion` , `PackageIcon` `Title` e `Description` para descrever o pacote que é criado a partir do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="aad1d-126">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="aad1d-127">Para obter informações sobre essas e outras propriedades, consulte [pacote de destino](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="aad1d-127">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-and-items"></a><span data-ttu-id="aad1d-128">Publicar Propriedades e itens</span><span class="sxs-lookup"><span data-stu-id="aad1d-128">Publish properties and items</span></span>

- [<span data-ttu-id="aad1d-129">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="aad1d-129">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="aad1d-130">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="aad1d-130">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="aad1d-131">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="aad1d-131">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="aad1d-132">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="aad1d-132">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="aad1d-133">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="aad1d-133">RuntimeIdentifier</span></span>

<span data-ttu-id="aad1d-134">A `RuntimeIdentifier` propriedade permite que você especifique um único [identificador de tempo de execução (RID)](../rid-catalog.md) para o projeto.</span><span class="sxs-lookup"><span data-stu-id="aad1d-134">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="aad1d-135">O RID permite a publicação de uma implantação autossuficiente.</span><span class="sxs-lookup"><span data-stu-id="aad1d-135">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="aad1d-136">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="aad1d-136">RuntimeIdentifiers</span></span>

<span data-ttu-id="aad1d-137">A `RuntimeIdentifiers` propriedade permite que você especifique uma lista delimitada por ponto-e-vírgula de [RIDs (identificadores de tempo de execução)](../rid-catalog.md) para o projeto.</span><span class="sxs-lookup"><span data-stu-id="aad1d-137">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="aad1d-138">Use essa propriedade se você precisar publicar para vários tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="aad1d-138">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="aad1d-139">`RuntimeIdentifiers` é usado no momento da restauração para garantir que os ativos corretos estejam no grafo.</span><span class="sxs-lookup"><span data-stu-id="aad1d-139">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="aad1d-140">`RuntimeIdentifier` (singular) pode fornecer compilações mais rápidas quando apenas um único tempo de execução é necessário.</span><span class="sxs-lookup"><span data-stu-id="aad1d-140">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="aad1d-141">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="aad1d-141">TrimmerRootAssembly</span></span>

<span data-ttu-id="aad1d-142">O `TrimmerRootAssembly` Item permite que você exclua um assembly de [*corte*](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="aad1d-142">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="aad1d-143">O corte é o processo de remover partes não usadas do tempo de execução de um aplicativo empacotado.</span><span class="sxs-lookup"><span data-stu-id="aad1d-143">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="aad1d-144">Em alguns casos, a remoção pode remover incorretamente as referências necessárias.</span><span class="sxs-lookup"><span data-stu-id="aad1d-144">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="aad1d-145">O XML a seguir exclui o `System.Security` assembly de corte.</span><span class="sxs-lookup"><span data-stu-id="aad1d-145">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="aad1d-146">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="aad1d-146">UseAppHost</span></span>

<span data-ttu-id="aad1d-147">A `UseAppHost` propriedade foi introduzida na versão 2.1.400 do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aad1d-147">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="aad1d-148">Ele controla se um executável nativo é criado para uma implantação ou não.</span><span class="sxs-lookup"><span data-stu-id="aad1d-148">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="aad1d-149">Um executável nativo é necessário para implantações independentes.</span><span class="sxs-lookup"><span data-stu-id="aad1d-149">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="aad1d-150">No .NET Core 3,0 e versões posteriores, um executável dependente da estrutura é criado por padrão.</span><span class="sxs-lookup"><span data-stu-id="aad1d-150">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="aad1d-151">Defina a `UseAppHost` propriedade como `false` para desabilitar a geração do executável.</span><span class="sxs-lookup"><span data-stu-id="aad1d-151">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="aad1d-152">Para obter mais informações sobre a implantação, consulte [implantação de aplicativos do .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="aad1d-152">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="aad1d-153">Compilar propriedades</span><span class="sxs-lookup"><span data-stu-id="aad1d-153">Compile properties</span></span>

- [<span data-ttu-id="aad1d-154">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="aad1d-154">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="aad1d-155">LangVersion</span><span class="sxs-lookup"><span data-stu-id="aad1d-155">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="aad1d-156">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="aad1d-156">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="aad1d-157">A `EmbeddedResourceUseDependentUponConvention` propriedade define se os nomes de arquivo de manifesto de recurso são gerados a partir de informações de tipo em arquivos de origem que são colocados com arquivos de recursos.</span><span class="sxs-lookup"><span data-stu-id="aad1d-157">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="aad1d-158">Por exemplo, se *Form1. resx* estiver na mesma pasta que *Form1.cs*e `EmbeddedResourceUseDependentUponConvention` for definido como `true` , o arquivo *. Resources* gerado usará seu nome do primeiro tipo definido em *Form1.cs*.</span><span class="sxs-lookup"><span data-stu-id="aad1d-158">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="aad1d-159">Por exemplo, se `MyNamespace.Form1` for o primeiro tipo definido em *Form1.cs*, o nome de arquivo gerado *será MyNamespace. Form1. Resources*.</span><span class="sxs-lookup"><span data-stu-id="aad1d-159">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="aad1d-160">Se `LogicalName` `ManifestResourceName` os metadados,, ou `DependentUpon` forem especificados para um `EmbeddedResource` Item, o nome do arquivo de manifesto gerado para esse arquivo de recurso será baseado nesses metadados em vez disso.</span><span class="sxs-lookup"><span data-stu-id="aad1d-160">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="aad1d-161">Por padrão, em um novo projeto .NET Core, essa propriedade é definida como `true` .</span><span class="sxs-lookup"><span data-stu-id="aad1d-161">By default, in a new .NET Core project, this property is set to `true`.</span></span> <span data-ttu-id="aad1d-162">Se for definido como `false` , e não `LogicalName` , ou os `ManifestResourceName` `DependentUpon` metadados forem especificados para o `EmbeddedResource` item no arquivo de projeto, o nome do arquivo de manifesto de recurso será baseado no namespace raiz do projeto e no caminho de arquivo relativo para o arquivo *. resx* .</span><span class="sxs-lookup"><span data-stu-id="aad1d-162">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="aad1d-163">Para obter mais informações, consulte [como os arquivos de manifesto de recurso são nomeados](../resources/manifest-file-names.md).</span><span class="sxs-lookup"><span data-stu-id="aad1d-163">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="aad1d-164">LangVersion</span><span class="sxs-lookup"><span data-stu-id="aad1d-164">LangVersion</span></span>

<span data-ttu-id="aad1d-165">A `LangVersion` propriedade permite especificar uma versão de linguagem de programação específica.</span><span class="sxs-lookup"><span data-stu-id="aad1d-165">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="aad1d-166">Por exemplo, se você quiser acessar os recursos do C# Preview, defina `LangVersion` como `preview` .</span><span class="sxs-lookup"><span data-stu-id="aad1d-166">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="aad1d-167">Para obter mais informações, consulte [controle de versão da linguagem C#](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="aad1d-167">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="code-analysis-properties"></a><span data-ttu-id="aad1d-168">Propriedades de análise de código</span><span class="sxs-lookup"><span data-stu-id="aad1d-168">Code analysis properties</span></span>

### <a name="analysislevel"></a><span data-ttu-id="aad1d-169">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="aad1d-169">AnalysisLevel</span></span>

<span data-ttu-id="aad1d-170">A `AnalysisLevel` propriedade permite especificar um nível de análise de código.</span><span class="sxs-lookup"><span data-stu-id="aad1d-170">The `AnalysisLevel` property lets you specify a code analysis level.</span></span> <span data-ttu-id="aad1d-171">Por exemplo, se você quiser acessar analisadores de código de visualização, defina `AnalysisLevel` como `preview` .</span><span class="sxs-lookup"><span data-stu-id="aad1d-171">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span> <span data-ttu-id="aad1d-172">O valor padrão é `latest`.</span><span class="sxs-lookup"><span data-stu-id="aad1d-172">The default value is `latest`.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="aad1d-173">A tabela a seguir mostra as opções disponíveis.</span><span class="sxs-lookup"><span data-stu-id="aad1d-173">The following table shows the available options.</span></span>

| <span data-ttu-id="aad1d-174">Valor</span><span class="sxs-lookup"><span data-stu-id="aad1d-174">Value</span></span> | <span data-ttu-id="aad1d-175">Significado</span><span class="sxs-lookup"><span data-stu-id="aad1d-175">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="aad1d-176">Os analisadores de código mais recentes que foram lançados são usados.</span><span class="sxs-lookup"><span data-stu-id="aad1d-176">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="aad1d-177">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="aad1d-177">This is the default.</span></span> |
| `preview` | <span data-ttu-id="aad1d-178">Os analisadores de código mais recentes são usados, mesmo se estiverem em versão prévia.</span><span class="sxs-lookup"><span data-stu-id="aad1d-178">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="aad1d-179">O conjunto de regras que foi habilitado para a versão 5,0 do .NET é usado, mesmo se as regras mais recentes estiverem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="aad1d-179">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="aad1d-180">O conjunto de regras que foi habilitado para a versão 5,0 do .NET é usado, mesmo se as regras mais recentes estiverem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="aad1d-180">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="aad1d-181">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="aad1d-181">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="aad1d-182">A `CodeAnalysisTreatWarningsAsErrors` propriedade permite configurar se os avisos de análise de código devem ser tratados como avisos e interromper a compilação.</span><span class="sxs-lookup"><span data-stu-id="aad1d-182">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code analysis warnings should be treated as warnings and break the build.</span></span> <span data-ttu-id="aad1d-183">Se você usar o `-warnaserror` sinalizador ao compilar seus projetos, os avisos de [análise de código do .net](../../fundamentals/productivity/code-analysis.md) também serão tratados como erros.</span><span class="sxs-lookup"><span data-stu-id="aad1d-183">If you use the `-warnaserror` flag when you build your projects, [.NET code analysis](../../fundamentals/productivity/code-analysis.md) warnings are also treated as errors.</span></span> <span data-ttu-id="aad1d-184">Se você quiser que os avisos do compilador sejam tratados como erros, poderá definir a `CodeAnalysisTreatWarningsAsErrors` Propriedade MSBuild como `false` em seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="aad1d-184">If you only want compiler warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="aad1d-185">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="aad1d-185">EnableNETAnalyzers</span></span>

<span data-ttu-id="aad1d-186">A [análise de código .net](../../fundamentals/productivity/code-analysis.md) está habilitada, por padrão, para projetos direcionados ao .NET 5,0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="aad1d-186">[.NET Code analysis](../../fundamentals/productivity/code-analysis.md) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="aad1d-187">Você pode habilitar a análise de código .NET para projetos destinados a versões anteriores do .NET, definindo a `EnableNETAnalyzers` propriedade como true.</span><span class="sxs-lookup"><span data-stu-id="aad1d-187">You can enable .NET code analysis for projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to true.</span></span> <span data-ttu-id="aad1d-188">Para desabilitar a análise de código em qualquer projeto, defina essa propriedade como `false` .</span><span class="sxs-lookup"><span data-stu-id="aad1d-188">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="aad1d-189">Outra maneira de habilitar a análise de código .NET em projetos que visam versões .NET anteriores ao .NET 5,0 é definir a propriedade [AnalysisLevel](#analysislevel) como `latest` .</span><span class="sxs-lookup"><span data-stu-id="aad1d-189">Another way to enable .NET code analysis on projects that target .NET versions prior to .NET 5.0 is to set the [AnalysisLevel](#analysislevel) property to `latest`.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="aad1d-190">Propriedades de configuração de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="aad1d-190">Run-time configuration properties</span></span>

<span data-ttu-id="aad1d-191">Você pode configurar alguns comportamentos de tempo de execução especificando as propriedades do MSBuild no arquivo de projeto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aad1d-191">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="aad1d-192">Para obter informações sobre outras maneiras de configurar o comportamento de tempo de execução, consulte [definições de configuração de tempo de execução do .NET Core](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="aad1d-192">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="aad1d-193">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="aad1d-193">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="aad1d-194">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="aad1d-194">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="aad1d-195">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="aad1d-195">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="aad1d-196">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="aad1d-196">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="aad1d-197">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="aad1d-197">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="aad1d-198">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="aad1d-198">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="aad1d-199">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="aad1d-199">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="aad1d-200">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="aad1d-200">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="aad1d-201">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="aad1d-201">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="aad1d-202">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="aad1d-202">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="aad1d-203">A `ConcurrentGarbageCollection` propriedade define se a [coleta de lixo em segundo plano (simultânea)](../../standard/garbage-collection/background-gc.md) está habilitada.</span><span class="sxs-lookup"><span data-stu-id="aad1d-203">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="aad1d-204">Defina o valor como `false` para desabilitar a coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="aad1d-204">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="aad1d-205">Para obter mais informações, consulte [background GC](../run-time-config/garbage-collector.md#background-gc).</span><span class="sxs-lookup"><span data-stu-id="aad1d-205">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="aad1d-206">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="aad1d-206">InvariantGlobalization</span></span>

<span data-ttu-id="aad1d-207">A `InvariantGlobalization` propriedade define se o aplicativo é executado no modo *invariável-globalização* , o que significa que ele não tem acesso a dados específicos de cultura.</span><span class="sxs-lookup"><span data-stu-id="aad1d-207">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="aad1d-208">Defina o valor a `true` ser executado no modo invariável-Globally.</span><span class="sxs-lookup"><span data-stu-id="aad1d-208">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="aad1d-209">Para obter mais informações, consulte [modo invariável](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="aad1d-209">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="aad1d-210">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="aad1d-210">RetainVMGarbageCollection</span></span>

<span data-ttu-id="aad1d-211">A `RetainVMGarbageCollection` Propriedade configura o coletor de lixo para colocar os segmentos de memória excluídos em uma lista em espera para uso futuro ou liberá-los.</span><span class="sxs-lookup"><span data-stu-id="aad1d-211">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="aad1d-212">Definir o valor para `true` instruir o coletor de lixo a colocar os segmentos em uma lista de espera.</span><span class="sxs-lookup"><span data-stu-id="aad1d-212">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="aad1d-213">Para obter mais informações, consulte [reter VM](../run-time-config/garbage-collector.md#retain-vm).</span><span class="sxs-lookup"><span data-stu-id="aad1d-213">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="aad1d-214">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="aad1d-214">ServerGarbageCollection</span></span>

<span data-ttu-id="aad1d-215">A `ServerGarbageCollection` propriedade define se o aplicativo usa a coleta de lixo da [estação de trabalho ou a coleta de lixo do servidor](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="aad1d-215">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="aad1d-216">Defina o valor como para `true` usar a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="aad1d-216">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="aad1d-217">Para obter mais informações, consulte [estação de trabalho versus servidor](../run-time-config/garbage-collector.md#workstation-vs-server).</span><span class="sxs-lookup"><span data-stu-id="aad1d-217">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="aad1d-218">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="aad1d-218">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="aad1d-219">A `ThreadPoolMaxThreads` Propriedade configura o número máximo de threads para o pool de threads de trabalho.</span><span class="sxs-lookup"><span data-stu-id="aad1d-219">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="aad1d-220">Para obter mais informações, consulte [Maximum threads](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="aad1d-220">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="aad1d-221">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="aad1d-221">ThreadPoolMinThreads</span></span>

<span data-ttu-id="aad1d-222">A `ThreadPoolMinThreads` Propriedade configura o número mínimo de threads para o pool de threads de trabalho.</span><span class="sxs-lookup"><span data-stu-id="aad1d-222">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="aad1d-223">Para obter mais informações, consulte [mínimo de threads](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="aad1d-223">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="aad1d-224">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="aad1d-224">TieredCompilation</span></span>

<span data-ttu-id="aad1d-225">A `TieredCompilation` propriedade define se o compilador JIT (just-in-time) usa compilação em [camadas](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="aad1d-225">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="aad1d-226">Defina o valor como `false` para desabilitar a compilação em camadas.</span><span class="sxs-lookup"><span data-stu-id="aad1d-226">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="aad1d-227">Para obter mais informações, consulte [compilação em camadas](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="aad1d-227">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="aad1d-228">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="aad1d-228">TieredCompilationQuickJit</span></span>

<span data-ttu-id="aad1d-229">A `TieredCompilationQuickJit` propriedade define se o compilador JIT usa o JIT rápido.</span><span class="sxs-lookup"><span data-stu-id="aad1d-229">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="aad1d-230">Defina o valor como `false` para desabilitar o JIT rápido.</span><span class="sxs-lookup"><span data-stu-id="aad1d-230">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="aad1d-231">Para obter mais informações, consulte [Quick JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="aad1d-231">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="aad1d-232">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="aad1d-232">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="aad1d-233">A `TieredCompilationQuickJitForLoops` propriedade define se o compilador JIT usa o JIT rápido em métodos que contêm loops.</span><span class="sxs-lookup"><span data-stu-id="aad1d-233">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="aad1d-234">Defina o valor como `true` para habilitar o JIT rápido em métodos que contêm loops.</span><span class="sxs-lookup"><span data-stu-id="aad1d-234">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="aad1d-235">Para obter mais informações, consulte [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="aad1d-235">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a><span data-ttu-id="aad1d-236">Propriedades e itens de referência</span><span class="sxs-lookup"><span data-stu-id="aad1d-236">Reference properties and items</span></span>

- [<span data-ttu-id="aad1d-237">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="aad1d-237">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="aad1d-238">PackageReference</span><span class="sxs-lookup"><span data-stu-id="aad1d-238">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="aad1d-239">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="aad1d-239">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="aad1d-240">Referência</span><span class="sxs-lookup"><span data-stu-id="aad1d-240">Reference</span></span>](#reference)
- [<span data-ttu-id="aad1d-241">Restaurar propriedades</span><span class="sxs-lookup"><span data-stu-id="aad1d-241">Restore properties</span></span>](#restore-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="aad1d-242">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="aad1d-242">AssetTargetFallback</span></span>

<span data-ttu-id="aad1d-243">A `AssetTargetFallback` propriedade permite que você especifique versões de estrutura compatíveis adicionais para referências de projeto e pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="aad1d-243">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="aad1d-244">Por exemplo, se você especificar uma dependência de pacote usando `PackageReference` , mas esse pacote não contiver ativos que são compatíveis com seus projetos `TargetFramework` , a `AssetTargetFallback` Propriedade entrará em cena.</span><span class="sxs-lookup"><span data-stu-id="aad1d-244">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="aad1d-245">A compatibilidade do pacote referenciado é verificada novamente usando cada estrutura de destino especificada em `AssetTargetFallback` .</span><span class="sxs-lookup"><span data-stu-id="aad1d-245">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="aad1d-246">Você pode definir a `AssetTargetFallback` propriedade para uma ou mais [versões da estrutura de destino](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="aad1d-246">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="aad1d-247">PackageReference</span><span class="sxs-lookup"><span data-stu-id="aad1d-247">PackageReference</span></span>

<span data-ttu-id="aad1d-248">O `PackageReference` Item define uma referência a um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="aad1d-248">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="aad1d-249">O atributo `Include` especifica a ID do pacote.</span><span class="sxs-lookup"><span data-stu-id="aad1d-249">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="aad1d-250">O `Version` atributo especifica a versão ou o intervalo de versão.</span><span class="sxs-lookup"><span data-stu-id="aad1d-250">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="aad1d-251">Para obter informações sobre como especificar uma versão mínima, a versão máxima, o intervalo ou a correspondência exata, consulte [intervalos de versão](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="aad1d-251">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="aad1d-252">Você também pode adicionar os seguintes metadados a uma referência de projeto: `IncludeAssets` , `ExcludeAssets` e `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="aad1d-252">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="aad1d-253">O trecho do arquivo de projeto no exemplo a seguir faz referência ao pacote [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .</span><span class="sxs-lookup"><span data-stu-id="aad1d-253">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="aad1d-254">Para obter mais informações, consulte [referências de pacote em arquivos de projeto](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="aad1d-254">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="aad1d-255">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="aad1d-255">ProjectReference</span></span>

<span data-ttu-id="aad1d-256">O `ProjectReference` Item define uma referência a outro projeto.</span><span class="sxs-lookup"><span data-stu-id="aad1d-256">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="aad1d-257">O projeto referenciado é adicionado como uma dependência de pacote NuGet, ou seja, é tratado da mesma forma que um `PackageReference` .</span><span class="sxs-lookup"><span data-stu-id="aad1d-257">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="aad1d-258">O `Include` atributo especifica o caminho para o projeto.</span><span class="sxs-lookup"><span data-stu-id="aad1d-258">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="aad1d-259">Você também pode adicionar os seguintes metadados a uma referência de projeto: `IncludeAssets` , `ExcludeAssets` e `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="aad1d-259">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="aad1d-260">O trecho do arquivo de projeto no exemplo a seguir faz referência a um projeto chamado `Project2` .</span><span class="sxs-lookup"><span data-stu-id="aad1d-260">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="aad1d-261">Referência</span><span class="sxs-lookup"><span data-stu-id="aad1d-261">Reference</span></span>

<span data-ttu-id="aad1d-262">O `Reference` Item define uma referência a um arquivo de assembly.</span><span class="sxs-lookup"><span data-stu-id="aad1d-262">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="aad1d-263">O `Include` atributo especifica o nome do arquivo e os `HintPath` metadados especificam o caminho para o assembly.</span><span class="sxs-lookup"><span data-stu-id="aad1d-263">The `Include` attribute specifies the name of the file, and the `HintPath` metadata specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a><span data-ttu-id="aad1d-264">Restaurar propriedades</span><span class="sxs-lookup"><span data-stu-id="aad1d-264">Restore properties</span></span>

<span data-ttu-id="aad1d-265">A restauração de um pacote referenciado instala todas as suas dependências diretas e todas as dependências dessas dependências.</span><span class="sxs-lookup"><span data-stu-id="aad1d-265">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="aad1d-266">Você pode personalizar a restauração do pacote especificando propriedades como `RestorePackagesPath` e `RestoreIgnoreFailedSources` .</span><span class="sxs-lookup"><span data-stu-id="aad1d-266">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="aad1d-267">Para obter mais informações sobre essas e outras propriedades, consulte [Restore Target](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="aad1d-267">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="aad1d-268">Confira também</span><span class="sxs-lookup"><span data-stu-id="aad1d-268">See also</span></span>

- [<span data-ttu-id="aad1d-269">Referência de esquema do MSBuild</span><span class="sxs-lookup"><span data-stu-id="aad1d-269">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="aad1d-270">Propriedades comuns do MSBuild</span><span class="sxs-lookup"><span data-stu-id="aad1d-270">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="aad1d-271">Propriedades do MSBuild para o pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="aad1d-271">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="aad1d-272">Propriedades do MSBuild para restauração do NuGet</span><span class="sxs-lookup"><span data-stu-id="aad1d-272">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="aad1d-273">Personalizar uma compilação</span><span class="sxs-lookup"><span data-stu-id="aad1d-273">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
