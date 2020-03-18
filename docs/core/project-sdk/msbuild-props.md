---
title: Propriedades MSBuild para Microsoft.NET.Sdk
description: Referência para as propriedades MSBuild que são compreendidas pelo .NET Core SDK.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: d4a204a1e0216313418d278ec3bd333f72db8751
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399178"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="6e351-103">Propriedades MSBuild para projetos .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="6e351-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="6e351-104">Esta página descreve as propriedades mSBuild para configurar projetos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6e351-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="6e351-105">Esta página é um trabalho em andamento e não lista todas as propriedades úteis do MSBuild para o .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="6e351-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="6e351-106">Para obter uma lista de propriedades comuns do MSBuild, consulte [Propriedades Comuns do MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="6e351-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="6e351-107">Propriedades do framework</span><span class="sxs-lookup"><span data-stu-id="6e351-107">Framework properties</span></span>

- [<span data-ttu-id="6e351-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="6e351-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="6e351-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="6e351-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="6e351-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="6e351-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="6e351-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="6e351-111">TargetFramework</span></span>

<span data-ttu-id="6e351-112">A `TargetFramework` propriedade especifica a versão de quadro de destino para o aplicativo, que faz referência implícita a um [metapacote](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="6e351-112">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="6e351-113">Para obter uma lista de apelidos de quadro de destino válidos, consulte [Frameworks target em projetos estilo SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="6e351-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="6e351-114">Para obter mais informações, consulte [Frameworks target em projetos no estilo SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="6e351-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="6e351-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="6e351-115">TargetFrameworks</span></span>

<span data-ttu-id="6e351-116">Use `TargetFrameworks` a propriedade quando quiser que seu aplicativo tenha como alvo várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="6e351-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="6e351-117">Para obter uma lista de apelidos de quadro de destino válidos, consulte [Frameworks target em projetos estilo SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="6e351-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="6e351-118">Esta propriedade é `TargetFramework` ignorada se (singular) for especificado.</span><span class="sxs-lookup"><span data-stu-id="6e351-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="6e351-119">Para obter mais informações, consulte [Frameworks target em projetos no estilo SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="6e351-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="6e351-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="6e351-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="6e351-121">Esta propriedade só se `netstandard1.x`aplica a projetos usando .</span><span class="sxs-lookup"><span data-stu-id="6e351-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="6e351-122">Não se aplica a projetos `netstandard2.x`que usam.</span><span class="sxs-lookup"><span data-stu-id="6e351-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="6e351-123">Use `NetStandardImplicitPackageVersion` a propriedade quando quiser especificar uma versão de framework menor que a versão [metapacote.](../packages.md#metapackages)</span><span class="sxs-lookup"><span data-stu-id="6e351-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="6e351-124">O arquivo do projeto no `netstandard1.3` exemplo a seguir é alvo, mas usa a versão 1.6.0 de `NETStandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="6e351-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a><span data-ttu-id="6e351-125">Publicar propriedades</span><span class="sxs-lookup"><span data-stu-id="6e351-125">Publish properties</span></span>

- [<span data-ttu-id="6e351-126">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="6e351-126">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="6e351-127">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="6e351-127">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="6e351-128">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="6e351-128">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="6e351-129">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="6e351-129">RuntimeIdentifier</span></span>

<span data-ttu-id="6e351-130">A `RuntimeIdentifier` propriedade permite especificar um único [identificador de tempo de execução (RID)](../rid-catalog.md) para o projeto.</span><span class="sxs-lookup"><span data-stu-id="6e351-130">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="6e351-131">O RID permite a publicação de uma implantação autossuficiente.</span><span class="sxs-lookup"><span data-stu-id="6e351-131">The RID enables publishing a self-contained deployment.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="6e351-132">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="6e351-132">RuntimeIdentifiers</span></span>

<span data-ttu-id="6e351-133">A `RuntimeIdentifiers` propriedade permite especificar uma lista delimitada de [rids (runtime) deponto e](../rid-catalog.md) ponto e vírgula para o projeto.</span><span class="sxs-lookup"><span data-stu-id="6e351-133">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="6e351-134">Use esta propriedade se você precisar publicar para vários tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="6e351-134">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="6e351-135">`RuntimeIdentifiers`é usado no momento de restauração para garantir que os ativos certos estejam no gráfico.</span><span class="sxs-lookup"><span data-stu-id="6e351-135">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="6e351-136">`RuntimeIdentifier`(singular) pode fornecer compilações mais rápidas quando apenas um único tempo de execução é necessário.</span><span class="sxs-lookup"><span data-stu-id="6e351-136">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a><span data-ttu-id="6e351-137">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="6e351-137">UseAppHost</span></span>

<span data-ttu-id="6e351-138">A `UseAppHost` propriedade foi introduzida na versão 2.1.400 do .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="6e351-138">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="6e351-139">Ele controla se um executável nativo é criado ou não para uma implantação.</span><span class="sxs-lookup"><span data-stu-id="6e351-139">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="6e351-140">Um executável nativo é necessário para implantações independentes.</span><span class="sxs-lookup"><span data-stu-id="6e351-140">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="6e351-141">Nas versões .NET Core 3.0 e posteriores, um executável dependente de estrutura é criado por padrão.</span><span class="sxs-lookup"><span data-stu-id="6e351-141">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="6e351-142">Defina `UseAppHost` a `false` propriedade para desativar a geração do executável.</span><span class="sxs-lookup"><span data-stu-id="6e351-142">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="6e351-143">Para obter mais informações sobre a implantação, consulte [a implantação do aplicativo .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="6e351-143">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="6e351-144">Compilar propriedades</span><span class="sxs-lookup"><span data-stu-id="6e351-144">Compile properties</span></span>

### <a name="langversion"></a><span data-ttu-id="6e351-145">LangVersion</span><span class="sxs-lookup"><span data-stu-id="6e351-145">LangVersion</span></span>

<span data-ttu-id="6e351-146">A `LangVersion` propriedade permite especificar uma versão específica do idioma de programação.</span><span class="sxs-lookup"><span data-stu-id="6e351-146">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="6e351-147">Por exemplo, se você quiser acessar os `LangVersion` `preview`recursos de visualização C#, definido como .</span><span class="sxs-lookup"><span data-stu-id="6e351-147">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="6e351-148">Para obter mais informações, consulte [a versão do idioma C#](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="6e351-148">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="nuget-packages"></a><span data-ttu-id="6e351-149">Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="6e351-149">NuGet packages</span></span>

- [<span data-ttu-id="6e351-150">PackageReference</span><span class="sxs-lookup"><span data-stu-id="6e351-150">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="6e351-151">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="6e351-151">AssetTargetFallback</span></span>](#assettargetfallback)

### <a name="packagereference"></a><span data-ttu-id="6e351-152">PackageReference</span><span class="sxs-lookup"><span data-stu-id="6e351-152">PackageReference</span></span>

<span data-ttu-id="6e351-153">O `PackageReference` item permite especificar uma dependência nuGet.</span><span class="sxs-lookup"><span data-stu-id="6e351-153">The `PackageReference` item lets you specify a NuGet dependency.</span></span> <span data-ttu-id="6e351-154">Por exemplo, você pode querer referenciar um único pacote em vez de um [metapacote](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="6e351-154">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="6e351-155">O atributo `Include` especifica a ID do pacote.</span><span class="sxs-lookup"><span data-stu-id="6e351-155">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="6e351-156">O trecho do arquivo do projeto no exemplo a seguir faz referência ao pacote [System.Runtime.](https://www.nuget.org/packages/System.Runtime/)</span><span class="sxs-lookup"><span data-stu-id="6e351-156">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="6e351-157">Para obter mais informações, consulte [referências de pacote em arquivos de projeto](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="6e351-157">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="assettargetfallback"></a><span data-ttu-id="6e351-158">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="6e351-158">AssetTargetFallback</span></span>

<span data-ttu-id="6e351-159">A `AssetTargetFallback` propriedade permite que você especifique versões de estrutura compatíveis adicionais para projetos que seu projeto faz referência sustais e pacotes NuGet que seu projeto consome.</span><span class="sxs-lookup"><span data-stu-id="6e351-159">The `AssetTargetFallback` property lets you specify additional compatible framework versions for projects that your project references and NuGet packages that your project consumes.</span></span> <span data-ttu-id="6e351-160">Por exemplo, se você especificar `PackageReference` uma dependência de pacote usando, mas esse `TargetFramework`pacote `AssetTargetFallback` não contiver ativos compatíveis com os de seus projetos, a propriedade entra em jogo.</span><span class="sxs-lookup"><span data-stu-id="6e351-160">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="6e351-161">A compatibilidade do pacote referenciado é recontrolada usando cada estrutura `AssetTargetFallback`de destino especificada em .</span><span class="sxs-lookup"><span data-stu-id="6e351-161">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="6e351-162">Você pode `AssetTargetFallback` definir a propriedade como uma ou mais [versões de quadro-alvo](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="6e351-162">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a><span data-ttu-id="6e351-163">Embalar e restaurar alvos</span><span class="sxs-lookup"><span data-stu-id="6e351-163">Pack and restore targets</span></span>

<span data-ttu-id="6e351-164">O MSBuild 15.1 introduziu `pack` e `restore` tem como objetivos criar e restaurar pacotes NuGet como parte de uma compilação.</span><span class="sxs-lookup"><span data-stu-id="6e351-164">MSBuild 15.1 introduced `pack` and `restore` targets for creating and restoring NuGet packages as part of a build.</span></span> <span data-ttu-id="6e351-165">Para obter informações sobre as propriedades MSBuild para esses alvos, incluindo `PackageTargetFallback`, consulte [NuGet pack e restore como alvos MSBuild](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="6e351-165">For information about the MSBuild properties for these targets, including `PackageTargetFallback`, see [NuGet pack and restore as MSBuild targets](/nuget/reference/msbuild-targets).</span></span>

## <a name="see-also"></a><span data-ttu-id="6e351-166">Confira também</span><span class="sxs-lookup"><span data-stu-id="6e351-166">See also</span></span>

- [<span data-ttu-id="6e351-167">Referência de esquema MSBuild</span><span class="sxs-lookup"><span data-stu-id="6e351-167">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="6e351-168">Propriedades Comuns do MSBuild</span><span class="sxs-lookup"><span data-stu-id="6e351-168">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="6e351-169">Propriedades MSBuild para pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="6e351-169">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="6e351-170">Propriedades mSBuild para restauração NuGet</span><span class="sxs-lookup"><span data-stu-id="6e351-170">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="6e351-171">Personalize uma compilação</span><span class="sxs-lookup"><span data-stu-id="6e351-171">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
