---
title: Propriedades do MSBuild para Microsoft. NET. Sdk
description: Referência para as propriedades do MSBuild que são compreendidas pelo SDK do .NET Core.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 105b7d67ea24515ea88481cb4a4fe42d2a03cfd0
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506774"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="0ed18-103">Propriedades do MSBuild para projetos SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="0ed18-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="0ed18-104">Esta página descreve as propriedades do MSBuild para configurar projetos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0ed18-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="0ed18-105">Esta página é um trabalho em andamento e não lista todas as propriedades de MSBuild úteis para o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0ed18-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="0ed18-106">Para obter uma lista de propriedades comuns do MSBuild, consulte [Propriedades comuns do MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="0ed18-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="0ed18-107">Propriedades da estrutura</span><span class="sxs-lookup"><span data-stu-id="0ed18-107">Framework properties</span></span>

- [<span data-ttu-id="0ed18-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="0ed18-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="0ed18-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="0ed18-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="0ed18-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="0ed18-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="0ed18-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="0ed18-111">TargetFramework</span></span>

<span data-ttu-id="0ed18-112">A `TargetFramework` propriedade especifica a versão do Framework de destino para o aplicativo, que referencia implicitamente um [metapacote](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="0ed18-112">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="0ed18-113">Para obter uma lista de monikers de estrutura de destino válidos, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="0ed18-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="0ed18-114">Para obter mais informações, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="0ed18-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="0ed18-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="0ed18-115">TargetFrameworks</span></span>

<span data-ttu-id="0ed18-116">Use a `TargetFrameworks` Propriedade quando desejar que seu aplicativo direcione várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="0ed18-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="0ed18-117">Para obter uma lista de monikers de estrutura de destino válidos, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="0ed18-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="0ed18-118">Essa propriedade será ignorada `TargetFramework` se (singular) for especificado.</span><span class="sxs-lookup"><span data-stu-id="0ed18-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="0ed18-119">Para obter mais informações, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="0ed18-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="0ed18-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="0ed18-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="0ed18-121">Essa propriedade só se aplica a projetos `netstandard1.x`que usam o.</span><span class="sxs-lookup"><span data-stu-id="0ed18-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="0ed18-122">Ele não se aplica a projetos que `netstandard2.x`usam o.</span><span class="sxs-lookup"><span data-stu-id="0ed18-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="0ed18-123">Use a `NetStandardImplicitPackageVersion` Propriedade quando desejar especificar uma versão de estrutura inferior à versão do [metapacote](../packages.md#metapackages) .</span><span class="sxs-lookup"><span data-stu-id="0ed18-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="0ed18-124">O arquivo de projeto no exemplo a seguir `netstandard1.3` tem como destino, mas usa `NETStandard.Library`a versão 1.6.0 do.</span><span class="sxs-lookup"><span data-stu-id="0ed18-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a><span data-ttu-id="0ed18-125">Publicar propriedades</span><span class="sxs-lookup"><span data-stu-id="0ed18-125">Publish properties</span></span>

- [<span data-ttu-id="0ed18-126">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="0ed18-126">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="0ed18-127">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="0ed18-127">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="0ed18-128">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="0ed18-128">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="0ed18-129">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="0ed18-129">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="0ed18-130">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="0ed18-130">RuntimeIdentifier</span></span>

<span data-ttu-id="0ed18-131">A `RuntimeIdentifier` propriedade permite que você especifique um único [identificador de tempo de execução (RID)](../rid-catalog.md) para o projeto.</span><span class="sxs-lookup"><span data-stu-id="0ed18-131">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="0ed18-132">O RID permite a publicação de uma implantação autossuficiente.</span><span class="sxs-lookup"><span data-stu-id="0ed18-132">The RID enables publishing a self-contained deployment.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="0ed18-133">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="0ed18-133">RuntimeIdentifiers</span></span>

<span data-ttu-id="0ed18-134">A `RuntimeIdentifiers` propriedade permite que você especifique uma lista delimitada por ponto-e-vírgula de [RIDs (identificadores de tempo de execução)](../rid-catalog.md) para o projeto.</span><span class="sxs-lookup"><span data-stu-id="0ed18-134">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="0ed18-135">Use essa propriedade se você precisar publicar para vários tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="0ed18-135">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="0ed18-136">`RuntimeIdentifiers`é usado no momento da restauração para garantir que os ativos corretos estejam no grafo.</span><span class="sxs-lookup"><span data-stu-id="0ed18-136">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="0ed18-137">`RuntimeIdentifier`(singular) pode fornecer compilações mais rápidas quando apenas um único tempo de execução é necessário.</span><span class="sxs-lookup"><span data-stu-id="0ed18-137">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="0ed18-138">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="0ed18-138">TrimmerRootAssembly</span></span>

<span data-ttu-id="0ed18-139">O `TrimmerRootAssembly` item permite que você exclua um assembly de [*corte*](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="0ed18-139">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="0ed18-140">O corte é o processo de remover partes não usadas do tempo de execução de um aplicativo empacotado.</span><span class="sxs-lookup"><span data-stu-id="0ed18-140">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="0ed18-141">Em alguns casos, a remoção pode remover incorretamente as referências necessárias.</span><span class="sxs-lookup"><span data-stu-id="0ed18-141">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="0ed18-142">O XML a seguir exclui o `System.Security` assembly de corte.</span><span class="sxs-lookup"><span data-stu-id="0ed18-142">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
  </ItemGroup>
</Project>
```

### <a name="useapphost"></a><span data-ttu-id="0ed18-143">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="0ed18-143">UseAppHost</span></span>

<span data-ttu-id="0ed18-144">A `UseAppHost` Propriedade foi introduzida na versão 2.1.400 do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0ed18-144">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="0ed18-145">Ele controla se um executável nativo é criado para uma implantação ou não.</span><span class="sxs-lookup"><span data-stu-id="0ed18-145">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="0ed18-146">Um executável nativo é necessário para implantações independentes.</span><span class="sxs-lookup"><span data-stu-id="0ed18-146">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="0ed18-147">No .NET Core 3,0 e versões posteriores, um executável dependente da estrutura é criado por padrão.</span><span class="sxs-lookup"><span data-stu-id="0ed18-147">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="0ed18-148">Defina a `UseAppHost` Propriedade como `false` para desabilitar a geração do executável.</span><span class="sxs-lookup"><span data-stu-id="0ed18-148">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="0ed18-149">Para obter mais informações sobre a implantação, consulte [implantação de aplicativos do .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="0ed18-149">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="0ed18-150">Compilar propriedades</span><span class="sxs-lookup"><span data-stu-id="0ed18-150">Compile properties</span></span>

- [<span data-ttu-id="0ed18-151">LangVersion</span><span class="sxs-lookup"><span data-stu-id="0ed18-151">LangVersion</span></span>](#langversion)

### <a name="langversion"></a><span data-ttu-id="0ed18-152">LangVersion</span><span class="sxs-lookup"><span data-stu-id="0ed18-152">LangVersion</span></span>

<span data-ttu-id="0ed18-153">A `LangVersion` propriedade permite especificar uma versão de linguagem de programação específica.</span><span class="sxs-lookup"><span data-stu-id="0ed18-153">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="0ed18-154">Por exemplo, se você quiser acessar os recursos do C# Preview, `LangVersion` defina `preview`como.</span><span class="sxs-lookup"><span data-stu-id="0ed18-154">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="0ed18-155">Para obter mais informações, consulte [controle de versão da linguagem C#](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="0ed18-155">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="0ed18-156">Propriedades de configuração de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="0ed18-156">Run-time configuration properties</span></span>

<span data-ttu-id="0ed18-157">Você pode configurar alguns comportamentos de tempo de execução especificando as propriedades do MSBuild no arquivo de projeto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0ed18-157">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="0ed18-158">Para obter informações sobre outras maneiras de configurar o comportamento de tempo de execução, consulte [definições de configuração de tempo de execução do .NET Core](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="0ed18-158">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="0ed18-159">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="0ed18-159">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="0ed18-160">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="0ed18-160">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="0ed18-161">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="0ed18-161">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="0ed18-162">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="0ed18-162">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="0ed18-163">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="0ed18-163">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="0ed18-164">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="0ed18-164">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="0ed18-165">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="0ed18-165">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="0ed18-166">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="0ed18-166">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="0ed18-167">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="0ed18-167">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="0ed18-168">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="0ed18-168">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="0ed18-169">A `ConcurrentGarbageCollection` propriedade define se a [coleta de lixo em segundo plano (simultânea)](../../standard/garbage-collection/background-gc.md) está habilitada.</span><span class="sxs-lookup"><span data-stu-id="0ed18-169">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="0ed18-170">Defina o valor como `false` para desabilitar a coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="0ed18-170">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="0ed18-171">Para obter mais informações, consulte [System. GC. simultaneamente/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span><span class="sxs-lookup"><span data-stu-id="0ed18-171">For more information, see [System.GC.Concurrent/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="invariantglobalization"></a><span data-ttu-id="0ed18-172">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="0ed18-172">InvariantGlobalization</span></span>

<span data-ttu-id="0ed18-173">A `InvariantGlobalization` propriedade define se o aplicativo é executado no modo *invariável-globalização* , o que significa que ele não tem acesso a dados específicos de cultura.</span><span class="sxs-lookup"><span data-stu-id="0ed18-173">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="0ed18-174">Defina o valor a `true` ser executado no modo invariável-Globally.</span><span class="sxs-lookup"><span data-stu-id="0ed18-174">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="0ed18-175">Para obter mais informações, consulte [modo invariável](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="0ed18-175">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>
</Project>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="0ed18-176">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="0ed18-176">RetainVMGarbageCollection</span></span>

<span data-ttu-id="0ed18-177">A `RetainVMGarbageCollection` Propriedade configura o coletor de lixo para colocar os segmentos de memória excluídos em uma lista em espera para uso futuro ou liberá-los.</span><span class="sxs-lookup"><span data-stu-id="0ed18-177">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="0ed18-178">Definir o valor para `true` instruir o coletor de lixo a colocar os segmentos em uma lista de espera.</span><span class="sxs-lookup"><span data-stu-id="0ed18-178">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="0ed18-179">Para obter mais informações, consulte [System. GC. RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span><span class="sxs-lookup"><span data-stu-id="0ed18-179">For more information, see [System.GC.RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="0ed18-180">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="0ed18-180">ServerGarbageCollection</span></span>

<span data-ttu-id="0ed18-181">A `ServerGarbageCollection` propriedade define se o aplicativo usa a coleta de lixo da [estação de trabalho ou a coleta de lixo do servidor](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="0ed18-181">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="0ed18-182">Defina o valor como `true` para usar a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="0ed18-182">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="0ed18-183">Para obter mais informações, consulte [System. GC. Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span><span class="sxs-lookup"><span data-stu-id="0ed18-183">For more information, see [System.GC.Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="0ed18-184">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="0ed18-184">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="0ed18-185">A `ThreadPoolMaxThreads` Propriedade configura o número máximo de threads para o pool de threads de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0ed18-185">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="0ed18-186">Para obter mais informações, consulte [Maximum threads](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="0ed18-186">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>
</Project>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="0ed18-187">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="0ed18-187">ThreadPoolMinThreads</span></span>

<span data-ttu-id="0ed18-188">A `ThreadPoolMinThreads` Propriedade configura o número mínimo de threads para o pool de threads de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0ed18-188">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="0ed18-189">Para obter mais informações, consulte [mínimo de threads](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="0ed18-189">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilation"></a><span data-ttu-id="0ed18-190">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="0ed18-190">TieredCompilation</span></span>

<span data-ttu-id="0ed18-191">A `TieredCompilation` propriedade define se o compilador JIT (just-in-time) usa compilação em [camadas](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="0ed18-191">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="0ed18-192">Defina o valor como `false` para desabilitar a compilação em camadas.</span><span class="sxs-lookup"><span data-stu-id="0ed18-192">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="0ed18-193">Para obter mais informações, consulte [compilação em camadas](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="0ed18-193">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="0ed18-194">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="0ed18-194">TieredCompilationQuickJit</span></span>

<span data-ttu-id="0ed18-195">A `TieredCompilationQuickJit` propriedade define se o compilador JIT usa o JIT rápido.</span><span class="sxs-lookup"><span data-stu-id="0ed18-195">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="0ed18-196">Defina o valor como `false` para desabilitar o JIT rápido.</span><span class="sxs-lookup"><span data-stu-id="0ed18-196">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="0ed18-197">Para obter mais informações, consulte [Quick JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="0ed18-197">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="0ed18-198">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="0ed18-198">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="0ed18-199">A `TieredCompilationQuickJitForLoops` propriedade define se o compilador JIT usa o JIT rápido em métodos que contêm loops.</span><span class="sxs-lookup"><span data-stu-id="0ed18-199">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="0ed18-200">Defina o valor como `true` para habilitar o JIT rápido em métodos que contêm loops.</span><span class="sxs-lookup"><span data-stu-id="0ed18-200">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="0ed18-201">Para obter mais informações, consulte [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="0ed18-201">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>
</Project>
```

## <a name="nuget-packages"></a><span data-ttu-id="0ed18-202">Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="0ed18-202">NuGet packages</span></span>

- [<span data-ttu-id="0ed18-203">PackageReference</span><span class="sxs-lookup"><span data-stu-id="0ed18-203">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="0ed18-204">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="0ed18-204">AssetTargetFallback</span></span>](#assettargetfallback)

### <a name="packagereference"></a><span data-ttu-id="0ed18-205">PackageReference</span><span class="sxs-lookup"><span data-stu-id="0ed18-205">PackageReference</span></span>

<span data-ttu-id="0ed18-206">O `PackageReference` item permite que você especifique uma dependência do NuGet.</span><span class="sxs-lookup"><span data-stu-id="0ed18-206">The `PackageReference` item lets you specify a NuGet dependency.</span></span> <span data-ttu-id="0ed18-207">Por exemplo, talvez você queira fazer referência a um único pacote em vez de um [metapacote](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="0ed18-207">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="0ed18-208">O atributo `Include` especifica a ID do pacote.</span><span class="sxs-lookup"><span data-stu-id="0ed18-208">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="0ed18-209">O trecho do arquivo de projeto no exemplo a seguir faz referência ao pacote [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .</span><span class="sxs-lookup"><span data-stu-id="0ed18-209">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="0ed18-210">Para obter mais informações, consulte [referências de pacote em arquivos de projeto](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="0ed18-210">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="assettargetfallback"></a><span data-ttu-id="0ed18-211">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="0ed18-211">AssetTargetFallback</span></span>

<span data-ttu-id="0ed18-212">A `AssetTargetFallback` propriedade permite que você especifique versões de estrutura compatíveis adicionais para projetos que seu projeto faz referência e pacotes NuGet que seu projeto consome.</span><span class="sxs-lookup"><span data-stu-id="0ed18-212">The `AssetTargetFallback` property lets you specify additional compatible framework versions for projects that your project references and NuGet packages that your project consumes.</span></span> <span data-ttu-id="0ed18-213">Por exemplo, se você especificar uma dependência de pacote `PackageReference` usando, mas esse pacote não contiver ativos que são compatíveis com `TargetFramework`seus projetos `AssetTargetFallback` , a propriedade entrará em cena.</span><span class="sxs-lookup"><span data-stu-id="0ed18-213">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="0ed18-214">A compatibilidade do pacote referenciado é verificada novamente usando cada estrutura de destino especificada em `AssetTargetFallback`.</span><span class="sxs-lookup"><span data-stu-id="0ed18-214">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="0ed18-215">Você pode definir a `AssetTargetFallback` propriedade para uma ou mais [versões da estrutura de destino](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="0ed18-215">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a><span data-ttu-id="0ed18-216">Empacotar e restaurar destinos</span><span class="sxs-lookup"><span data-stu-id="0ed18-216">Pack and restore targets</span></span>

<span data-ttu-id="0ed18-217">O MSBuild 15,1 `pack` introduziu e `restore` tem como destino a criação e a restauração de pacotes NuGet como parte de uma compilação.</span><span class="sxs-lookup"><span data-stu-id="0ed18-217">MSBuild 15.1 introduced `pack` and `restore` targets for creating and restoring NuGet packages as part of a build.</span></span> <span data-ttu-id="0ed18-218">Para obter informações sobre as propriedades do MSBuild para esses destinos `PackageTargetFallback`, incluindo, consulte [NuGet Pack e restaurar como destinos do MSBuild](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="0ed18-218">For information about the MSBuild properties for these targets, including `PackageTargetFallback`, see [NuGet pack and restore as MSBuild targets](/nuget/reference/msbuild-targets).</span></span>

## <a name="see-also"></a><span data-ttu-id="0ed18-219">Confira também</span><span class="sxs-lookup"><span data-stu-id="0ed18-219">See also</span></span>

- [<span data-ttu-id="0ed18-220">Referência de esquema do MSBuild</span><span class="sxs-lookup"><span data-stu-id="0ed18-220">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="0ed18-221">Propriedades comuns do MSBuild</span><span class="sxs-lookup"><span data-stu-id="0ed18-221">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="0ed18-222">Propriedades do MSBuild para o pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="0ed18-222">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="0ed18-223">Propriedades do MSBuild para restauração do NuGet</span><span class="sxs-lookup"><span data-stu-id="0ed18-223">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="0ed18-224">Personalizar uma compilação</span><span class="sxs-lookup"><span data-stu-id="0ed18-224">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
