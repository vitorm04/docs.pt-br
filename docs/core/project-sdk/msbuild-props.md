---
title: Propriedades do MSBuild para Microsoft. NET. Sdk
description: Referência para as propriedades do MSBuild que são compreendidas pelo SDK do .NET Core.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 00d9152d864ac0727a511f4c3c15abba82aab904
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503814"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="007db-103">Propriedades do MSBuild para projetos SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="007db-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="007db-104">Esta página descreve as propriedades do MSBuild para configurar projetos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="007db-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="007db-105">Esta página é um trabalho em andamento e não lista todas as propriedades de MSBuild úteis para o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="007db-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="007db-106">Para obter uma lista de propriedades comuns do MSBuild, consulte [Propriedades comuns do MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="007db-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="007db-107">Propriedades da estrutura</span><span class="sxs-lookup"><span data-stu-id="007db-107">Framework properties</span></span>

- [<span data-ttu-id="007db-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="007db-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="007db-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="007db-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="007db-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="007db-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="007db-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="007db-111">TargetFramework</span></span>

<span data-ttu-id="007db-112">A propriedade `TargetFramework` especifica a versão do Framework de destino para o aplicativo, que referencia implicitamente um [metapacote](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="007db-112">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="007db-113">Para obter uma lista de monikers de estrutura de destino válidos, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="007db-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="007db-114">Para obter mais informações, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="007db-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="007db-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="007db-115">TargetFrameworks</span></span>

<span data-ttu-id="007db-116">Use a propriedade `TargetFrameworks` quando desejar que seu aplicativo direcione várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="007db-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="007db-117">Para obter uma lista de monikers de estrutura de destino válidos, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="007db-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="007db-118">Essa propriedade será ignorada se `TargetFramework` (singular) for especificado.</span><span class="sxs-lookup"><span data-stu-id="007db-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="007db-119">Para obter mais informações, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="007db-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="007db-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="007db-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="007db-121">Essa propriedade só se aplica a projetos que usam `netstandard1.x`.</span><span class="sxs-lookup"><span data-stu-id="007db-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="007db-122">Ele não se aplica a projetos que usam `netstandard2.x`.</span><span class="sxs-lookup"><span data-stu-id="007db-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="007db-123">Use a propriedade `NetStandardImplicitPackageVersion` quando desejar especificar uma versão de estrutura inferior à versão do [metapacote](../packages.md#metapackages) .</span><span class="sxs-lookup"><span data-stu-id="007db-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="007db-124">O arquivo de projeto no exemplo a seguir tem como destino `netstandard1.3`, mas usa a versão 1.6.0 do `NETStandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="007db-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a><span data-ttu-id="007db-125">Publicar propriedades</span><span class="sxs-lookup"><span data-stu-id="007db-125">Publish properties</span></span>

- [<span data-ttu-id="007db-126">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="007db-126">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="007db-127">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="007db-127">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="007db-128">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="007db-128">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="007db-129">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="007db-129">RuntimeIdentifier</span></span>

<span data-ttu-id="007db-130">A propriedade `RuntimeIdentifier` permite que você especifique um único [identificador de tempo de execução (RID)](../rid-catalog.md) para o projeto.</span><span class="sxs-lookup"><span data-stu-id="007db-130">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="007db-131">O RID permite a publicação de uma implantação autossuficiente.</span><span class="sxs-lookup"><span data-stu-id="007db-131">The RID enables publishing a self-contained deployment.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="007db-132">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="007db-132">RuntimeIdentifiers</span></span>

<span data-ttu-id="007db-133">A propriedade `RuntimeIdentifiers` permite especificar uma lista delimitada por ponto-e-vírgula de [RIDs (identificadores de tempo de execução)](../rid-catalog.md) para o projeto.</span><span class="sxs-lookup"><span data-stu-id="007db-133">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="007db-134">Use essa propriedade se você precisar publicar para vários tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="007db-134">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="007db-135">`RuntimeIdentifiers` é usado no momento da restauração para garantir que os ativos corretos estejam no grafo.</span><span class="sxs-lookup"><span data-stu-id="007db-135">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="007db-136">`RuntimeIdentifier` (singular) pode fornecer compilações mais rápidas quando apenas um único tempo de execução é necessário.</span><span class="sxs-lookup"><span data-stu-id="007db-136">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a><span data-ttu-id="007db-137">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="007db-137">UseAppHost</span></span>

<span data-ttu-id="007db-138">A propriedade `UseAppHost` foi introduzida na versão 2.1.400 do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="007db-138">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="007db-139">Ele controla se um executável nativo é criado para uma implantação ou não.</span><span class="sxs-lookup"><span data-stu-id="007db-139">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="007db-140">Um executável nativo é necessário para implantações independentes.</span><span class="sxs-lookup"><span data-stu-id="007db-140">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="007db-141">No .NET Core 3,0 e versões posteriores, um executável dependente da estrutura é criado por padrão.</span><span class="sxs-lookup"><span data-stu-id="007db-141">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="007db-142">Defina a propriedade `UseAppHost` como `false` para desabilitar a geração do executável.</span><span class="sxs-lookup"><span data-stu-id="007db-142">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="007db-143">Para obter mais informações sobre a implantação, consulte [implantação de aplicativos do .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="007db-143">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="007db-144">Compilar propriedades</span><span class="sxs-lookup"><span data-stu-id="007db-144">Compile properties</span></span>

### <a name="langversion"></a><span data-ttu-id="007db-145">LangVersion</span><span class="sxs-lookup"><span data-stu-id="007db-145">LangVersion</span></span>

<span data-ttu-id="007db-146">A propriedade `LangVersion` permite especificar uma versão de linguagem de programação específica.</span><span class="sxs-lookup"><span data-stu-id="007db-146">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="007db-147">Por exemplo, se você quiser acesso a C# recursos de visualização, defina `LangVersion` como `preview`.</span><span class="sxs-lookup"><span data-stu-id="007db-147">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="007db-148">Para obter mais informações, consulte [ C# controle de versão de idioma](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="007db-148">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="nuget-packages"></a><span data-ttu-id="007db-149">Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="007db-149">NuGet packages</span></span>

- [<span data-ttu-id="007db-150">PackageReference</span><span class="sxs-lookup"><span data-stu-id="007db-150">PackageReference</span></span>](#packagereference)

### <a name="packagereference"></a><span data-ttu-id="007db-151">PackageReference</span><span class="sxs-lookup"><span data-stu-id="007db-151">PackageReference</span></span>

<span data-ttu-id="007db-152">O `PackageReference` item permite que você especifique uma dependência do NuGet.</span><span class="sxs-lookup"><span data-stu-id="007db-152">The `PackageReference` item lets you specify a NuGet dependency.</span></span> <span data-ttu-id="007db-153">Por exemplo, talvez você queira fazer referência a um único pacote em vez de um [metapacote](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="007db-153">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="007db-154">O atributo `Include` especifica a ID do pacote.</span><span class="sxs-lookup"><span data-stu-id="007db-154">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="007db-155">O trecho do arquivo de projeto no exemplo a seguir faz referência ao pacote [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .</span><span class="sxs-lookup"><span data-stu-id="007db-155">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="007db-156">Para obter mais informações, consulte [referências de pacote em arquivos de projeto](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="007db-156">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="pack-and-restore-targets"></a><span data-ttu-id="007db-157">Empacotar e restaurar destinos</span><span class="sxs-lookup"><span data-stu-id="007db-157">Pack and restore targets</span></span>

<span data-ttu-id="007db-158">O MSBuild 15,1 introduziu `pack` e `restore` destinos para criar e restaurar pacotes NuGet como parte de uma compilação.</span><span class="sxs-lookup"><span data-stu-id="007db-158">MSBuild 15.1 introduced `pack` and `restore` targets for creating and restoring NuGet packages as part of a build.</span></span> <span data-ttu-id="007db-159">Para obter informações sobre as propriedades do MSBuild para esses destinos, incluindo `PackageTargetFallback`, consulte [o NuGet Pack e restaurar como destinos do MSBuild](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="007db-159">For information about the MSBuild properties for these targets, including `PackageTargetFallback`, see [NuGet pack and restore as MSBuild targets](/nuget/reference/msbuild-targets).</span></span>

## <a name="see-also"></a><span data-ttu-id="007db-160">Confira também</span><span class="sxs-lookup"><span data-stu-id="007db-160">See also</span></span>

- [<span data-ttu-id="007db-161">Referência de esquema do MSBuild</span><span class="sxs-lookup"><span data-stu-id="007db-161">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="007db-162">Propriedades comuns do MSBuild</span><span class="sxs-lookup"><span data-stu-id="007db-162">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="007db-163">Propriedades do MSBuild para o pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="007db-163">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="007db-164">Propriedades do MSBuild para restauração do NuGet</span><span class="sxs-lookup"><span data-stu-id="007db-164">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="007db-165">Personalizar uma compilação</span><span class="sxs-lookup"><span data-stu-id="007db-165">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
