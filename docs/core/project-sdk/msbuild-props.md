---
title: Propriedades do MSBuild para Microsoft. NET. Sdk
description: Referência para as propriedades e os itens do MSBuild que são compreendidos pelo SDK do .NET Core.
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: c1093a0acd5b75ae6478767d690966a30fe84a31
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656256"
---
# <a name="msbuild-reference-for-net-core-sdk-projects"></a><span data-ttu-id="5d08a-103">Referência do MSBuild para projetos de SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5d08a-103">MSBuild reference for .NET Core SDK projects</span></span>

<span data-ttu-id="5d08a-104">Esta página é uma referência para as propriedades e os itens do MSBuild que você pode usar para configurar projetos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5d08a-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="5d08a-105">Esta página é um trabalho em andamento e não lista todas as propriedades de MSBuild úteis para o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5d08a-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="5d08a-106">Para obter uma lista de propriedades comuns do MSBuild, consulte [Propriedades comuns do MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="5d08a-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="5d08a-107">Propriedades da estrutura</span><span class="sxs-lookup"><span data-stu-id="5d08a-107">Framework properties</span></span>

- [<span data-ttu-id="5d08a-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="5d08a-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="5d08a-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="5d08a-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="5d08a-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="5d08a-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="5d08a-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="5d08a-111">TargetFramework</span></span>

<span data-ttu-id="5d08a-112">A `TargetFramework` propriedade especifica a versão do Framework de destino para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5d08a-112">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="5d08a-113">Para obter uma lista de monikers de estrutura de destino válidos, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="5d08a-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="5d08a-114">Para obter mais informações, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="5d08a-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="5d08a-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="5d08a-115">TargetFrameworks</span></span>

<span data-ttu-id="5d08a-116">Use a `TargetFrameworks` propriedade quando desejar que seu aplicativo direcione várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="5d08a-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="5d08a-117">Para obter uma lista de monikers de estrutura de destino válidos, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="5d08a-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

> [!NOTE]
> <span data-ttu-id="5d08a-118">Essa propriedade será ignorada se `TargetFramework` (singular) for especificado.</span><span class="sxs-lookup"><span data-stu-id="5d08a-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="5d08a-119">Para obter mais informações, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="5d08a-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="5d08a-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="5d08a-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="5d08a-121">Essa propriedade só se aplica a projetos que usam o `netstandard1.x` .</span><span class="sxs-lookup"><span data-stu-id="5d08a-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="5d08a-122">Ele não se aplica a projetos que usam o `netstandard2.x` .</span><span class="sxs-lookup"><span data-stu-id="5d08a-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="5d08a-123">Use a `NetStandardImplicitPackageVersion` propriedade quando desejar especificar uma versão de estrutura inferior à versão do metapacote.</span><span class="sxs-lookup"><span data-stu-id="5d08a-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="5d08a-124">O arquivo de projeto no exemplo a seguir tem `netstandard1.3` como destino, mas usa a versão 1.6.0 do `NETStandard.Library` .</span><span class="sxs-lookup"><span data-stu-id="5d08a-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="5d08a-125">Propriedades do pacote</span><span class="sxs-lookup"><span data-stu-id="5d08a-125">Package properties</span></span>

<span data-ttu-id="5d08a-126">Você pode especificar propriedades como `PackageId` ,, `PackageVersion` , `PackageIcon` `Title` e `Description` para descrever o pacote que é criado a partir do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="5d08a-126">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="5d08a-127">Para obter informações sobre essas e outras propriedades, consulte [pacote de destino](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="5d08a-127">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-and-items"></a><span data-ttu-id="5d08a-128">Publicar Propriedades e itens</span><span class="sxs-lookup"><span data-stu-id="5d08a-128">Publish properties and items</span></span>

- [<span data-ttu-id="5d08a-129">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="5d08a-129">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="5d08a-130">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="5d08a-130">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="5d08a-131">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="5d08a-131">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="5d08a-132">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="5d08a-132">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="5d08a-133">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="5d08a-133">RuntimeIdentifier</span></span>

<span data-ttu-id="5d08a-134">A `RuntimeIdentifier` propriedade permite que você especifique um único [identificador de tempo de execução (RID)](../rid-catalog.md) para o projeto.</span><span class="sxs-lookup"><span data-stu-id="5d08a-134">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="5d08a-135">O RID permite a publicação de uma implantação autossuficiente.</span><span class="sxs-lookup"><span data-stu-id="5d08a-135">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="5d08a-136">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="5d08a-136">RuntimeIdentifiers</span></span>

<span data-ttu-id="5d08a-137">A `RuntimeIdentifiers` propriedade permite que você especifique uma lista delimitada por ponto-e-vírgula de [RIDs (identificadores de tempo de execução)](../rid-catalog.md) para o projeto.</span><span class="sxs-lookup"><span data-stu-id="5d08a-137">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="5d08a-138">Use essa propriedade se você precisar publicar para vários tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="5d08a-138">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="5d08a-139">`RuntimeIdentifiers` é usado no momento da restauração para garantir que os ativos corretos estejam no grafo.</span><span class="sxs-lookup"><span data-stu-id="5d08a-139">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="5d08a-140">`RuntimeIdentifier` (singular) pode fornecer compilações mais rápidas quando apenas um único tempo de execução é necessário.</span><span class="sxs-lookup"><span data-stu-id="5d08a-140">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="5d08a-141">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="5d08a-141">TrimmerRootAssembly</span></span>

<span data-ttu-id="5d08a-142">O `TrimmerRootAssembly` Item permite que você exclua um assembly de [*corte*](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="5d08a-142">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="5d08a-143">O corte é o processo de remover partes não usadas do tempo de execução de um aplicativo empacotado.</span><span class="sxs-lookup"><span data-stu-id="5d08a-143">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="5d08a-144">Em alguns casos, a remoção pode remover incorretamente as referências necessárias.</span><span class="sxs-lookup"><span data-stu-id="5d08a-144">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="5d08a-145">O XML a seguir exclui o `System.Security` assembly de corte.</span><span class="sxs-lookup"><span data-stu-id="5d08a-145">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="5d08a-146">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="5d08a-146">UseAppHost</span></span>

<span data-ttu-id="5d08a-147">A `UseAppHost` propriedade foi introduzida na versão 2.1.400 do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5d08a-147">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="5d08a-148">Ele controla se um executável nativo é criado para uma implantação ou não.</span><span class="sxs-lookup"><span data-stu-id="5d08a-148">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="5d08a-149">Um executável nativo é necessário para implantações independentes.</span><span class="sxs-lookup"><span data-stu-id="5d08a-149">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="5d08a-150">No .NET Core 3,0 e versões posteriores, um executável dependente da estrutura é criado por padrão.</span><span class="sxs-lookup"><span data-stu-id="5d08a-150">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="5d08a-151">Defina a `UseAppHost` propriedade como `false` para desabilitar a geração do executável.</span><span class="sxs-lookup"><span data-stu-id="5d08a-151">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="5d08a-152">Para obter mais informações sobre a implantação, consulte [implantação de aplicativos do .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="5d08a-152">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="5d08a-153">Compilar propriedades</span><span class="sxs-lookup"><span data-stu-id="5d08a-153">Compile properties</span></span>

- [<span data-ttu-id="5d08a-154">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="5d08a-154">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="5d08a-155">LangVersion</span><span class="sxs-lookup"><span data-stu-id="5d08a-155">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="5d08a-156">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="5d08a-156">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="5d08a-157">A `EmbeddedResourceUseDependentUponConvention` propriedade define se os nomes de arquivo de manifesto de recurso são gerados a partir de informações de tipo em arquivos de origem que são colocados com arquivos de recursos.</span><span class="sxs-lookup"><span data-stu-id="5d08a-157">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="5d08a-158">Por exemplo, se *Form1. resx* estiver na mesma pasta que *Form1.cs*e `EmbeddedResourceUseDependentUponConvention` for definido como `true` , o arquivo *. Resources* gerado usará seu nome do primeiro tipo definido em *Form1.cs*.</span><span class="sxs-lookup"><span data-stu-id="5d08a-158">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="5d08a-159">Por exemplo, se `MyNamespace.Form1` for o primeiro tipo definido em *Form1.cs*, o nome de arquivo gerado *será MyNamespace. Form1. Resources*.</span><span class="sxs-lookup"><span data-stu-id="5d08a-159">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="5d08a-160">Se `LogicalName` `ManifestResourceName` os metadados,, ou `DependentUpon` forem especificados para um `EmbeddedResource` Item, o nome do arquivo de manifesto gerado para esse arquivo de recurso será baseado nesses metadados em vez disso.</span><span class="sxs-lookup"><span data-stu-id="5d08a-160">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="5d08a-161">Por padrão, em um novo projeto .NET Core, essa propriedade é definida como `true` .</span><span class="sxs-lookup"><span data-stu-id="5d08a-161">By default, in a new .NET Core project, this property is set to `true`.</span></span> <span data-ttu-id="5d08a-162">Se for definido como `false` , e não `LogicalName` , ou os `ManifestResourceName` `DependentUpon` metadados forem especificados para o `EmbeddedResource` item no arquivo de projeto, o nome do arquivo de manifesto de recurso será baseado no namespace raiz do projeto e no caminho de arquivo relativo para o arquivo *. resx* .</span><span class="sxs-lookup"><span data-stu-id="5d08a-162">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="5d08a-163">Para obter mais informações, consulte [como os arquivos de manifesto de recurso são nomeados](../resources/manifest-file-names.md).</span><span class="sxs-lookup"><span data-stu-id="5d08a-163">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="5d08a-164">LangVersion</span><span class="sxs-lookup"><span data-stu-id="5d08a-164">LangVersion</span></span>

<span data-ttu-id="5d08a-165">A `LangVersion` propriedade permite especificar uma versão de linguagem de programação específica.</span><span class="sxs-lookup"><span data-stu-id="5d08a-165">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="5d08a-166">Por exemplo, se você quiser acessar os recursos do C# Preview, defina `LangVersion` como `preview` .</span><span class="sxs-lookup"><span data-stu-id="5d08a-166">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="5d08a-167">Para obter mais informações, consulte [controle de versão da linguagem C#](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="5d08a-167">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="code-analysis-properties"></a><span data-ttu-id="5d08a-168">Propriedades de análise de código</span><span class="sxs-lookup"><span data-stu-id="5d08a-168">Code analysis properties</span></span>

### <a name="analysislevel"></a><span data-ttu-id="5d08a-169">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="5d08a-169">AnalysisLevel</span></span>

<span data-ttu-id="5d08a-170">A `AnalysisLevel` propriedade permite especificar um nível de análise de código.</span><span class="sxs-lookup"><span data-stu-id="5d08a-170">The `AnalysisLevel` property lets you specify a code analysis level.</span></span> <span data-ttu-id="5d08a-171">Por exemplo, se você quiser acessar analisadores de código de visualização, defina `AnalysisLevel` como `preview` .</span><span class="sxs-lookup"><span data-stu-id="5d08a-171">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span> <span data-ttu-id="5d08a-172">O valor padrão é `latest`.</span><span class="sxs-lookup"><span data-stu-id="5d08a-172">The default value is `latest`.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="5d08a-173">A tabela a seguir mostra as opções disponíveis.</span><span class="sxs-lookup"><span data-stu-id="5d08a-173">The following table shows the available options.</span></span>

| <span data-ttu-id="5d08a-174">Valor</span><span class="sxs-lookup"><span data-stu-id="5d08a-174">Value</span></span> | <span data-ttu-id="5d08a-175">Significado</span><span class="sxs-lookup"><span data-stu-id="5d08a-175">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="5d08a-176">Os analisadores de código mais recentes que foram lançados são usados.</span><span class="sxs-lookup"><span data-stu-id="5d08a-176">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="5d08a-177">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="5d08a-177">This is the default.</span></span> |
| `preview` | <span data-ttu-id="5d08a-178">Os analisadores de código mais recentes são usados, mesmo se estiverem em versão prévia.</span><span class="sxs-lookup"><span data-stu-id="5d08a-178">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="5d08a-179">O conjunto de regras que foi habilitado para a versão 5,0 do .NET é usado, mesmo se as regras mais recentes estiverem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="5d08a-179">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="5d08a-180">O conjunto de regras que foi habilitado para a versão 5,0 do .NET é usado, mesmo se as regras mais recentes estiverem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="5d08a-180">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

### <a name="analysismode"></a><span data-ttu-id="5d08a-181">Analysismode</span><span class="sxs-lookup"><span data-stu-id="5d08a-181">AnalysisMode</span></span>

<span data-ttu-id="5d08a-182">A partir do .NET 5,0 RC2, o SDK do .NET é fornecido com todas as [regras de qualidade de código "CA"](/visualstudio/code-quality/code-analysis-for-managed-code-warnings).</span><span class="sxs-lookup"><span data-stu-id="5d08a-182">Starting with .NET 5.0 RC2, the .NET SDK ships with all of the ["CA" code quality rules](/visualstudio/code-quality/code-analysis-for-managed-code-warnings).</span></span> <span data-ttu-id="5d08a-183">Por padrão, somente [algumas regras são habilitadas](../../fundamentals/productivity/code-analysis.md#enabled-rules) como avisos de compilação.</span><span class="sxs-lookup"><span data-stu-id="5d08a-183">By default, only [some rules are enabled](../../fundamentals/productivity/code-analysis.md#enabled-rules) as build warnings.</span></span> <span data-ttu-id="5d08a-184">A `AnalysisMode` propriedade permite que você personalize o conjunto de regras habilitadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="5d08a-184">The `AnalysisMode` property lets you customize the set of rules that are enabled by default.</span></span> <span data-ttu-id="5d08a-185">Você pode alternar para um modo de análise mais agressivo (recusar) ou um modo de análise mais conservador (opcional).</span><span class="sxs-lookup"><span data-stu-id="5d08a-185">You can either switch to a more aggressive (opt-out) analysis mode or a more conservative (opt-in) analysis mode.</span></span> <span data-ttu-id="5d08a-186">Por exemplo, se você quiser habilitar todas as regras por padrão como avisos de compilação, defina o valor como `AllEnabledByDefault` .</span><span class="sxs-lookup"><span data-stu-id="5d08a-186">For example, if you want to enable all rules by default as build warnings, set the value to `AllEnabledByDefault`.</span></span>

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

<span data-ttu-id="5d08a-187">A tabela a seguir mostra as opções disponíveis.</span><span class="sxs-lookup"><span data-stu-id="5d08a-187">The following table shows the available options.</span></span>

| <span data-ttu-id="5d08a-188">Valor</span><span class="sxs-lookup"><span data-stu-id="5d08a-188">Value</span></span> | <span data-ttu-id="5d08a-189">Significado</span><span class="sxs-lookup"><span data-stu-id="5d08a-189">Meaning</span></span> |
|-|-|
| `Default` | <span data-ttu-id="5d08a-190">Modo padrão, em que determinadas regras são habilitadas como avisos de compilação, determinadas regras são habilitadas como sugestões de IDE do Visual Studio e o restante é desabilitado.</span><span class="sxs-lookup"><span data-stu-id="5d08a-190">Default mode, where certain rules are enabled as build warnings, certain rules are enabled as Visual Studio IDE suggestions, and the remainder are disabled.</span></span> |
| `AllEnabledByDefault` | <span data-ttu-id="5d08a-191">Modo agressivo ou de aceitação, em que todas as regras são habilitadas por padrão como avisos de compilação.</span><span class="sxs-lookup"><span data-stu-id="5d08a-191">Aggressive or opt-out mode, where all rules are enabled by default as build warnings.</span></span> <span data-ttu-id="5d08a-192">Você pode [recusar](../../fundamentals/productivity/configure-code-analysis-rules.md) seletivamente as regras individuais para desabilitá-las.</span><span class="sxs-lookup"><span data-stu-id="5d08a-192">You can selectively [opt out](../../fundamentals/productivity/configure-code-analysis-rules.md) of individual rules to disable them.</span></span> |
| `AllDisabledByDefault` | <span data-ttu-id="5d08a-193">Modo conservador ou opt, onde todas as regras estão desabilitadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="5d08a-193">Conservative or opt-in mode, where all rules are disabled by default.</span></span> <span data-ttu-id="5d08a-194">Você pode [optar](../../fundamentals/productivity/configure-code-analysis-rules.md) seletivamente por regras individuais para habilitá-las.</span><span class="sxs-lookup"><span data-stu-id="5d08a-194">You can selectively [opt into](../../fundamentals/productivity/configure-code-analysis-rules.md) individual rules to enable them.</span></span> |

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="5d08a-195">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="5d08a-195">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="5d08a-196">A `CodeAnalysisTreatWarningsAsErrors` propriedade permite que você configure se os avisos de análise de qualidade de código (CAxxxx) devem ser tratados como avisos e interromper a compilação.</span><span class="sxs-lookup"><span data-stu-id="5d08a-196">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code quality analysis warnings (CAxxxx) should be treated as warnings and break the build.</span></span> <span data-ttu-id="5d08a-197">Se você usar o `-warnaserror` sinalizador ao compilar seus projetos, os avisos de [análise de qualidade de código do .net](../../fundamentals/productivity/code-analysis.md#code-quality-analysis) também serão tratados como erros.</span><span class="sxs-lookup"><span data-stu-id="5d08a-197">If you use the `-warnaserror` flag when you build your projects, [.NET code quality analysis](../../fundamentals/productivity/code-analysis.md#code-quality-analysis) warnings are also treated as errors.</span></span> <span data-ttu-id="5d08a-198">Se você não quiser que os avisos de análise de qualidade de código sejam tratados como erros, você poderá definir a `CodeAnalysisTreatWarningsAsErrors` Propriedade do MSBuild como `false` em seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="5d08a-198">If you do not want code quality analysis warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="5d08a-199">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="5d08a-199">EnableNETAnalyzers</span></span>

<span data-ttu-id="5d08a-200">A [análise de qualidade de código .net](../../fundamentals/productivity/code-analysis.md#code-quality-analysis) está habilitada, por padrão, para projetos direcionados ao .NET 5,0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="5d08a-200">[.NET code quality analysis](../../fundamentals/productivity/code-analysis.md#code-quality-analysis) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="5d08a-201">Você pode habilitar a análise de código .NET para projetos destinados a versões anteriores do .NET, definindo a `EnableNETAnalyzers` propriedade como `true` .</span><span class="sxs-lookup"><span data-stu-id="5d08a-201">You can enable .NET code analysis for projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to `true`.</span></span> <span data-ttu-id="5d08a-202">Para desabilitar a análise de código em qualquer projeto, defina essa propriedade como `false` .</span><span class="sxs-lookup"><span data-stu-id="5d08a-202">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="5d08a-203">Outra maneira de habilitar a análise de código .NET em projetos que visam versões .NET anteriores ao .NET 5,0 é definir a propriedade [AnalysisLevel](#analysislevel) como `latest` .</span><span class="sxs-lookup"><span data-stu-id="5d08a-203">Another way to enable .NET code analysis on projects that target .NET versions prior to .NET 5.0 is to set the [AnalysisLevel](#analysislevel) property to `latest`.</span></span>

### <a name="enforcecodestyleinbuild"></a><span data-ttu-id="5d08a-204">EnforceCodeStyleInBuild</span><span class="sxs-lookup"><span data-stu-id="5d08a-204">EnforceCodeStyleInBuild</span></span>

<span data-ttu-id="5d08a-205">A [análise de estilo de código .net](../../fundamentals/productivity/code-analysis.md#code-style-analysis) está desabilitada, por padrão, na compilação para todos os projetos .net.</span><span class="sxs-lookup"><span data-stu-id="5d08a-205">[.NET code style analysis](../../fundamentals/productivity/code-analysis.md#code-style-analysis) is disabled, by default, on build for all .NET projects.</span></span> <span data-ttu-id="5d08a-206">Você pode habilitar a análise de estilo de código para projetos .NET definindo a `EnforceCodeStyleInBuild` propriedade como `true` .</span><span class="sxs-lookup"><span data-stu-id="5d08a-206">You can enable code style analysis for .NET projects by setting the `EnforceCodeStyleInBuild` property to `true`.</span></span>

```xml
<PropertyGroup>
  <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
</PropertyGroup>
```

<span data-ttu-id="5d08a-207">Todas as regras de estilo de código [configuradas](../../fundamentals/productivity/code-analysis.md#code-style-analysis) para serem avisos ou erros serão executadas em violações de compilação e relatório.</span><span class="sxs-lookup"><span data-stu-id="5d08a-207">All code style rules that are [configured](../../fundamentals/productivity/code-analysis.md#code-style-analysis) to be warnings or errors will execute on build and report violations.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="5d08a-208">Propriedades de configuração de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5d08a-208">Run-time configuration properties</span></span>

<span data-ttu-id="5d08a-209">Você pode configurar alguns comportamentos de tempo de execução especificando as propriedades do MSBuild no arquivo de projeto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5d08a-209">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="5d08a-210">Para obter informações sobre outras maneiras de configurar o comportamento de tempo de execução, consulte [definições de configuração de tempo de execução do .NET Core](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="5d08a-210">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="5d08a-211">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="5d08a-211">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="5d08a-212">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="5d08a-212">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="5d08a-213">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="5d08a-213">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="5d08a-214">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="5d08a-214">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="5d08a-215">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="5d08a-215">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="5d08a-216">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="5d08a-216">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="5d08a-217">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="5d08a-217">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="5d08a-218">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="5d08a-218">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="5d08a-219">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="5d08a-219">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="5d08a-220">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="5d08a-220">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="5d08a-221">A `ConcurrentGarbageCollection` propriedade define se a [coleta de lixo em segundo plano (simultânea)](../../standard/garbage-collection/background-gc.md) está habilitada.</span><span class="sxs-lookup"><span data-stu-id="5d08a-221">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="5d08a-222">Defina o valor como `false` para desabilitar a coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="5d08a-222">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="5d08a-223">Para obter mais informações, consulte [background GC](../run-time-config/garbage-collector.md#background-gc).</span><span class="sxs-lookup"><span data-stu-id="5d08a-223">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="5d08a-224">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="5d08a-224">InvariantGlobalization</span></span>

<span data-ttu-id="5d08a-225">A `InvariantGlobalization` propriedade define se o aplicativo é executado no modo *invariável-globalização* , o que significa que ele não tem acesso a dados específicos de cultura.</span><span class="sxs-lookup"><span data-stu-id="5d08a-225">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="5d08a-226">Defina o valor a `true` ser executado no modo invariável-Globally.</span><span class="sxs-lookup"><span data-stu-id="5d08a-226">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="5d08a-227">Para obter mais informações, consulte [modo invariável](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="5d08a-227">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="5d08a-228">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="5d08a-228">RetainVMGarbageCollection</span></span>

<span data-ttu-id="5d08a-229">A `RetainVMGarbageCollection` Propriedade configura o coletor de lixo para colocar os segmentos de memória excluídos em uma lista em espera para uso futuro ou liberá-los.</span><span class="sxs-lookup"><span data-stu-id="5d08a-229">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="5d08a-230">Definir o valor para `true` instruir o coletor de lixo a colocar os segmentos em uma lista de espera.</span><span class="sxs-lookup"><span data-stu-id="5d08a-230">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="5d08a-231">Para obter mais informações, consulte [reter VM](../run-time-config/garbage-collector.md#retain-vm).</span><span class="sxs-lookup"><span data-stu-id="5d08a-231">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="5d08a-232">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="5d08a-232">ServerGarbageCollection</span></span>

<span data-ttu-id="5d08a-233">A `ServerGarbageCollection` propriedade define se o aplicativo usa a coleta de lixo da [estação de trabalho ou a coleta de lixo do servidor](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="5d08a-233">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="5d08a-234">Defina o valor como para `true` usar a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="5d08a-234">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="5d08a-235">Para obter mais informações, consulte [estação de trabalho versus servidor](../run-time-config/garbage-collector.md#workstation-vs-server).</span><span class="sxs-lookup"><span data-stu-id="5d08a-235">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="5d08a-236">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="5d08a-236">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="5d08a-237">A `ThreadPoolMaxThreads` Propriedade configura o número máximo de threads para o pool de threads de trabalho.</span><span class="sxs-lookup"><span data-stu-id="5d08a-237">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="5d08a-238">Para obter mais informações, consulte [Maximum threads](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="5d08a-238">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="5d08a-239">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="5d08a-239">ThreadPoolMinThreads</span></span>

<span data-ttu-id="5d08a-240">A `ThreadPoolMinThreads` Propriedade configura o número mínimo de threads para o pool de threads de trabalho.</span><span class="sxs-lookup"><span data-stu-id="5d08a-240">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="5d08a-241">Para obter mais informações, consulte [mínimo de threads](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="5d08a-241">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="5d08a-242">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="5d08a-242">TieredCompilation</span></span>

<span data-ttu-id="5d08a-243">A `TieredCompilation` propriedade define se o compilador JIT (just-in-time) usa compilação em [camadas](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="5d08a-243">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="5d08a-244">Defina o valor como `false` para desabilitar a compilação em camadas.</span><span class="sxs-lookup"><span data-stu-id="5d08a-244">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="5d08a-245">Para obter mais informações, consulte [compilação em camadas](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="5d08a-245">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="5d08a-246">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="5d08a-246">TieredCompilationQuickJit</span></span>

<span data-ttu-id="5d08a-247">A `TieredCompilationQuickJit` propriedade define se o compilador JIT usa o JIT rápido.</span><span class="sxs-lookup"><span data-stu-id="5d08a-247">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="5d08a-248">Defina o valor como `false` para desabilitar o JIT rápido.</span><span class="sxs-lookup"><span data-stu-id="5d08a-248">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="5d08a-249">Para obter mais informações, consulte [Quick JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="5d08a-249">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="5d08a-250">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="5d08a-250">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="5d08a-251">A `TieredCompilationQuickJitForLoops` propriedade define se o compilador JIT usa o JIT rápido em métodos que contêm loops.</span><span class="sxs-lookup"><span data-stu-id="5d08a-251">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="5d08a-252">Defina o valor como `true` para habilitar o JIT rápido em métodos que contêm loops.</span><span class="sxs-lookup"><span data-stu-id="5d08a-252">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="5d08a-253">Para obter mais informações, consulte [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="5d08a-253">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a><span data-ttu-id="5d08a-254">Propriedades e itens de referência</span><span class="sxs-lookup"><span data-stu-id="5d08a-254">Reference properties and items</span></span>

- [<span data-ttu-id="5d08a-255">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="5d08a-255">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="5d08a-256">PackageReference</span><span class="sxs-lookup"><span data-stu-id="5d08a-256">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="5d08a-257">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="5d08a-257">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="5d08a-258">Referência</span><span class="sxs-lookup"><span data-stu-id="5d08a-258">Reference</span></span>](#reference)
- [<span data-ttu-id="5d08a-259">Restaurar propriedades</span><span class="sxs-lookup"><span data-stu-id="5d08a-259">Restore properties</span></span>](#restore-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="5d08a-260">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="5d08a-260">AssetTargetFallback</span></span>

<span data-ttu-id="5d08a-261">A `AssetTargetFallback` propriedade permite que você especifique versões de estrutura compatíveis adicionais para referências de projeto e pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="5d08a-261">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="5d08a-262">Por exemplo, se você especificar uma dependência de pacote usando `PackageReference` , mas esse pacote não contiver ativos que são compatíveis com seus projetos `TargetFramework` , a `AssetTargetFallback` Propriedade entrará em cena.</span><span class="sxs-lookup"><span data-stu-id="5d08a-262">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="5d08a-263">A compatibilidade do pacote referenciado é verificada novamente usando cada estrutura de destino especificada em `AssetTargetFallback` .</span><span class="sxs-lookup"><span data-stu-id="5d08a-263">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="5d08a-264">Você pode definir a `AssetTargetFallback` propriedade para uma ou mais [versões da estrutura de destino](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="5d08a-264">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="5d08a-265">PackageReference</span><span class="sxs-lookup"><span data-stu-id="5d08a-265">PackageReference</span></span>

<span data-ttu-id="5d08a-266">O `PackageReference` Item define uma referência a um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="5d08a-266">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="5d08a-267">O atributo `Include` especifica a ID do pacote.</span><span class="sxs-lookup"><span data-stu-id="5d08a-267">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="5d08a-268">O `Version` atributo especifica a versão ou o intervalo de versão.</span><span class="sxs-lookup"><span data-stu-id="5d08a-268">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="5d08a-269">Para obter informações sobre como especificar uma versão mínima, a versão máxima, o intervalo ou a correspondência exata, consulte [intervalos de versão](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="5d08a-269">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="5d08a-270">Você também pode adicionar os seguintes metadados a uma referência de projeto: `IncludeAssets` , `ExcludeAssets` e `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="5d08a-270">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="5d08a-271">O trecho do arquivo de projeto no exemplo a seguir faz referência ao pacote [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .</span><span class="sxs-lookup"><span data-stu-id="5d08a-271">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="5d08a-272">Para obter mais informações, consulte [referências de pacote em arquivos de projeto](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="5d08a-272">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="5d08a-273">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="5d08a-273">ProjectReference</span></span>

<span data-ttu-id="5d08a-274">O `ProjectReference` Item define uma referência a outro projeto.</span><span class="sxs-lookup"><span data-stu-id="5d08a-274">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="5d08a-275">O projeto referenciado é adicionado como uma dependência de pacote NuGet, ou seja, é tratado da mesma forma que um `PackageReference` .</span><span class="sxs-lookup"><span data-stu-id="5d08a-275">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="5d08a-276">O `Include` atributo especifica o caminho para o projeto.</span><span class="sxs-lookup"><span data-stu-id="5d08a-276">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="5d08a-277">Você também pode adicionar os seguintes metadados a uma referência de projeto: `IncludeAssets` , `ExcludeAssets` e `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="5d08a-277">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="5d08a-278">O trecho do arquivo de projeto no exemplo a seguir faz referência a um projeto chamado `Project2` .</span><span class="sxs-lookup"><span data-stu-id="5d08a-278">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="5d08a-279">Referência</span><span class="sxs-lookup"><span data-stu-id="5d08a-279">Reference</span></span>

<span data-ttu-id="5d08a-280">O `Reference` Item define uma referência a um arquivo de assembly.</span><span class="sxs-lookup"><span data-stu-id="5d08a-280">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="5d08a-281">O `Include` atributo especifica o nome do arquivo e os `HintPath` metadados especificam o caminho para o assembly.</span><span class="sxs-lookup"><span data-stu-id="5d08a-281">The `Include` attribute specifies the name of the file, and the `HintPath` metadata specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a><span data-ttu-id="5d08a-282">Restaurar propriedades</span><span class="sxs-lookup"><span data-stu-id="5d08a-282">Restore properties</span></span>

<span data-ttu-id="5d08a-283">A restauração de um pacote referenciado instala todas as suas dependências diretas e todas as dependências dessas dependências.</span><span class="sxs-lookup"><span data-stu-id="5d08a-283">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="5d08a-284">Você pode personalizar a restauração do pacote especificando propriedades como `RestorePackagesPath` e `RestoreIgnoreFailedSources` .</span><span class="sxs-lookup"><span data-stu-id="5d08a-284">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="5d08a-285">Para obter mais informações sobre essas e outras propriedades, consulte [Restore Target](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="5d08a-285">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="5d08a-286">Confira também</span><span class="sxs-lookup"><span data-stu-id="5d08a-286">See also</span></span>

- [<span data-ttu-id="5d08a-287">Referência de esquema do MSBuild</span><span class="sxs-lookup"><span data-stu-id="5d08a-287">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="5d08a-288">Propriedades comuns do MSBuild</span><span class="sxs-lookup"><span data-stu-id="5d08a-288">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="5d08a-289">Propriedades do MSBuild para o pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="5d08a-289">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="5d08a-290">Propriedades do MSBuild para restauração do NuGet</span><span class="sxs-lookup"><span data-stu-id="5d08a-290">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="5d08a-291">Personalizar uma compilação</span><span class="sxs-lookup"><span data-stu-id="5d08a-291">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
