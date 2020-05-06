---
title: Propriedades do MSBuild para Microsoft. NET. Sdk
description: Referência para as propriedades do MSBuild que são compreendidas pelo SDK do .NET Core.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 800ff59310d8437d7f770bf20a5bdf37714f8515
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795567"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="f0b17-103">Propriedades do MSBuild para projetos SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="f0b17-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="f0b17-104">Esta página descreve as propriedades do MSBuild para configurar projetos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f0b17-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span> <span data-ttu-id="f0b17-105">Você pode especificar *metadados* para cada propriedade como elementos filho da propriedade.</span><span class="sxs-lookup"><span data-stu-id="f0b17-105">You can specify *metadata* for each property as child elements of the property.</span></span>

> [!NOTE]
> <span data-ttu-id="f0b17-106">Esta página é um trabalho em andamento e não lista todas as propriedades de MSBuild úteis para o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f0b17-106">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="f0b17-107">Para obter uma lista de propriedades comuns do MSBuild, consulte [Propriedades comuns do MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="f0b17-107">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="f0b17-108">Propriedades da estrutura</span><span class="sxs-lookup"><span data-stu-id="f0b17-108">Framework properties</span></span>

- [<span data-ttu-id="f0b17-109">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="f0b17-109">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="f0b17-110">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="f0b17-110">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="f0b17-111">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="f0b17-111">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="f0b17-112">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="f0b17-112">TargetFramework</span></span>

<span data-ttu-id="f0b17-113">A `TargetFramework` propriedade especifica a versão do Framework de destino para o aplicativo, que referencia implicitamente um [metapacote](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="f0b17-113">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="f0b17-114">Para obter uma lista de monikers de estrutura de destino válidos, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="f0b17-114">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="f0b17-115">Para obter mais informações, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="f0b17-115">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="f0b17-116">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="f0b17-116">TargetFrameworks</span></span>

<span data-ttu-id="f0b17-117">Use a `TargetFrameworks` Propriedade quando desejar que seu aplicativo direcione várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="f0b17-117">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="f0b17-118">Para obter uma lista de monikers de estrutura de destino válidos, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="f0b17-118">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="f0b17-119">Essa propriedade será ignorada `TargetFramework` se (singular) for especificado.</span><span class="sxs-lookup"><span data-stu-id="f0b17-119">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="f0b17-120">Para obter mais informações, consulte [estruturas de destino em projetos em estilo SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="f0b17-120">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="f0b17-121">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="f0b17-121">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="f0b17-122">Essa propriedade só se aplica a projetos `netstandard1.x`que usam o.</span><span class="sxs-lookup"><span data-stu-id="f0b17-122">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="f0b17-123">Ele não se aplica a projetos que `netstandard2.x`usam o.</span><span class="sxs-lookup"><span data-stu-id="f0b17-123">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="f0b17-124">Use a `NetStandardImplicitPackageVersion` Propriedade quando desejar especificar uma versão de estrutura inferior à versão do [metapacote](../packages.md#metapackages) .</span><span class="sxs-lookup"><span data-stu-id="f0b17-124">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="f0b17-125">O arquivo de projeto no exemplo a seguir `netstandard1.3` tem como destino, mas usa `NETStandard.Library`a versão 1.6.0 do.</span><span class="sxs-lookup"><span data-stu-id="f0b17-125">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="f0b17-126">Propriedades do pacote</span><span class="sxs-lookup"><span data-stu-id="f0b17-126">Package properties</span></span>

<span data-ttu-id="f0b17-127">Você `PackageId`pode especificar propriedades como, `PackageVersion` `PackageIcon` `Title`,, e `Description` para descrever o pacote que é criado a partir do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="f0b17-127">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="f0b17-128">Para obter informações sobre essas e outras propriedades, consulte [pacote de destino](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="f0b17-128">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties"></a><span data-ttu-id="f0b17-129">Publicar propriedades</span><span class="sxs-lookup"><span data-stu-id="f0b17-129">Publish properties</span></span>

- [<span data-ttu-id="f0b17-130">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="f0b17-130">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="f0b17-131">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="f0b17-131">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="f0b17-132">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="f0b17-132">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="f0b17-133">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="f0b17-133">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="f0b17-134">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="f0b17-134">RuntimeIdentifier</span></span>

<span data-ttu-id="f0b17-135">A `RuntimeIdentifier` propriedade permite que você especifique um único [identificador de tempo de execução (RID)](../rid-catalog.md) para o projeto.</span><span class="sxs-lookup"><span data-stu-id="f0b17-135">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="f0b17-136">O RID permite a publicação de uma implantação autossuficiente.</span><span class="sxs-lookup"><span data-stu-id="f0b17-136">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="f0b17-137">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="f0b17-137">RuntimeIdentifiers</span></span>

<span data-ttu-id="f0b17-138">A `RuntimeIdentifiers` propriedade permite que você especifique uma lista delimitada por ponto-e-vírgula de [RIDs (identificadores de tempo de execução)](../rid-catalog.md) para o projeto.</span><span class="sxs-lookup"><span data-stu-id="f0b17-138">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="f0b17-139">Use essa propriedade se você precisar publicar para vários tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="f0b17-139">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="f0b17-140">`RuntimeIdentifiers`é usado no momento da restauração para garantir que os ativos corretos estejam no grafo.</span><span class="sxs-lookup"><span data-stu-id="f0b17-140">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="f0b17-141">`RuntimeIdentifier`(singular) pode fornecer compilações mais rápidas quando apenas um único tempo de execução é necessário.</span><span class="sxs-lookup"><span data-stu-id="f0b17-141">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="f0b17-142">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="f0b17-142">TrimmerRootAssembly</span></span>

<span data-ttu-id="f0b17-143">O `TrimmerRootAssembly` item permite que você exclua um assembly de [*corte*](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="f0b17-143">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="f0b17-144">O corte é o processo de remover partes não usadas do tempo de execução de um aplicativo empacotado.</span><span class="sxs-lookup"><span data-stu-id="f0b17-144">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="f0b17-145">Em alguns casos, a remoção pode remover incorretamente as referências necessárias.</span><span class="sxs-lookup"><span data-stu-id="f0b17-145">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="f0b17-146">O XML a seguir exclui o `System.Security` assembly de corte.</span><span class="sxs-lookup"><span data-stu-id="f0b17-146">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="f0b17-147">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="f0b17-147">UseAppHost</span></span>

<span data-ttu-id="f0b17-148">A `UseAppHost` Propriedade foi introduzida na versão 2.1.400 do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f0b17-148">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="f0b17-149">Ele controla se um executável nativo é criado para uma implantação ou não.</span><span class="sxs-lookup"><span data-stu-id="f0b17-149">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="f0b17-150">Um executável nativo é necessário para implantações independentes.</span><span class="sxs-lookup"><span data-stu-id="f0b17-150">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="f0b17-151">No .NET Core 3,0 e versões posteriores, um executável dependente da estrutura é criado por padrão.</span><span class="sxs-lookup"><span data-stu-id="f0b17-151">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="f0b17-152">Defina a `UseAppHost` Propriedade como `false` para desabilitar a geração do executável.</span><span class="sxs-lookup"><span data-stu-id="f0b17-152">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="f0b17-153">Para obter mais informações sobre a implantação, consulte [implantação de aplicativos do .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="f0b17-153">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="f0b17-154">Compilar propriedades</span><span class="sxs-lookup"><span data-stu-id="f0b17-154">Compile properties</span></span>

- [<span data-ttu-id="f0b17-155">LangVersion</span><span class="sxs-lookup"><span data-stu-id="f0b17-155">LangVersion</span></span>](#langversion)

### <a name="langversion"></a><span data-ttu-id="f0b17-156">LangVersion</span><span class="sxs-lookup"><span data-stu-id="f0b17-156">LangVersion</span></span>

<span data-ttu-id="f0b17-157">A `LangVersion` propriedade permite especificar uma versão de linguagem de programação específica.</span><span class="sxs-lookup"><span data-stu-id="f0b17-157">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="f0b17-158">Por exemplo, se você quiser acessar os recursos do C# Preview, `LangVersion` defina `preview`como.</span><span class="sxs-lookup"><span data-stu-id="f0b17-158">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="f0b17-159">Para obter mais informações, consulte [controle de versão da linguagem C#](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="f0b17-159">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="f0b17-160">Propriedades de configuração de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="f0b17-160">Run-time configuration properties</span></span>

<span data-ttu-id="f0b17-161">Você pode configurar alguns comportamentos de tempo de execução especificando as propriedades do MSBuild no arquivo de projeto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0b17-161">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="f0b17-162">Para obter informações sobre outras maneiras de configurar o comportamento de tempo de execução, consulte [definições de configuração de tempo de execução do .NET Core](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="f0b17-162">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="f0b17-163">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="f0b17-163">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="f0b17-164">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="f0b17-164">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="f0b17-165">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="f0b17-165">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="f0b17-166">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="f0b17-166">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="f0b17-167">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="f0b17-167">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="f0b17-168">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="f0b17-168">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="f0b17-169">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="f0b17-169">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="f0b17-170">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="f0b17-170">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="f0b17-171">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="f0b17-171">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="f0b17-172">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="f0b17-172">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="f0b17-173">A `ConcurrentGarbageCollection` propriedade define se a [coleta de lixo em segundo plano (simultânea)](../../standard/garbage-collection/background-gc.md) está habilitada.</span><span class="sxs-lookup"><span data-stu-id="f0b17-173">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="f0b17-174">Defina o valor como `false` para desabilitar a coleta de lixo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="f0b17-174">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="f0b17-175">Para obter mais informações, consulte [System. GC. simultaneamente/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span><span class="sxs-lookup"><span data-stu-id="f0b17-175">For more information, see [System.GC.Concurrent/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="f0b17-176">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="f0b17-176">InvariantGlobalization</span></span>

<span data-ttu-id="f0b17-177">A `InvariantGlobalization` propriedade define se o aplicativo é executado no modo *invariável-globalização* , o que significa que ele não tem acesso a dados específicos de cultura.</span><span class="sxs-lookup"><span data-stu-id="f0b17-177">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="f0b17-178">Defina o valor a `true` ser executado no modo invariável-Globally.</span><span class="sxs-lookup"><span data-stu-id="f0b17-178">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="f0b17-179">Para obter mais informações, consulte [modo invariável](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="f0b17-179">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="f0b17-180">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="f0b17-180">RetainVMGarbageCollection</span></span>

<span data-ttu-id="f0b17-181">A `RetainVMGarbageCollection` Propriedade configura o coletor de lixo para colocar os segmentos de memória excluídos em uma lista em espera para uso futuro ou liberá-los.</span><span class="sxs-lookup"><span data-stu-id="f0b17-181">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="f0b17-182">Definir o valor para `true` instruir o coletor de lixo a colocar os segmentos em uma lista de espera.</span><span class="sxs-lookup"><span data-stu-id="f0b17-182">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="f0b17-183">Para obter mais informações, consulte [System. GC. RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span><span class="sxs-lookup"><span data-stu-id="f0b17-183">For more information, see [System.GC.RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="f0b17-184">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="f0b17-184">ServerGarbageCollection</span></span>

<span data-ttu-id="f0b17-185">A `ServerGarbageCollection` propriedade define se o aplicativo usa a coleta de lixo da [estação de trabalho ou a coleta de lixo do servidor](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="f0b17-185">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="f0b17-186">Defina o valor como `true` para usar a coleta de lixo do servidor.</span><span class="sxs-lookup"><span data-stu-id="f0b17-186">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="f0b17-187">Para obter mais informações, consulte [System. GC. Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span><span class="sxs-lookup"><span data-stu-id="f0b17-187">For more information, see [System.GC.Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="f0b17-188">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="f0b17-188">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="f0b17-189">A `ThreadPoolMaxThreads` Propriedade configura o número máximo de threads para o pool de threads de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f0b17-189">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="f0b17-190">Para obter mais informações, consulte [Maximum threads](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="f0b17-190">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="f0b17-191">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="f0b17-191">ThreadPoolMinThreads</span></span>

<span data-ttu-id="f0b17-192">A `ThreadPoolMinThreads` Propriedade configura o número mínimo de threads para o pool de threads de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f0b17-192">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="f0b17-193">Para obter mais informações, consulte [mínimo de threads](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="f0b17-193">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="f0b17-194">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="f0b17-194">TieredCompilation</span></span>

<span data-ttu-id="f0b17-195">A `TieredCompilation` propriedade define se o compilador JIT (just-in-time) usa compilação em [camadas](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="f0b17-195">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="f0b17-196">Defina o valor como `false` para desabilitar a compilação em camadas.</span><span class="sxs-lookup"><span data-stu-id="f0b17-196">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="f0b17-197">Para obter mais informações, consulte [compilação em camadas](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="f0b17-197">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="f0b17-198">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="f0b17-198">TieredCompilationQuickJit</span></span>

<span data-ttu-id="f0b17-199">A `TieredCompilationQuickJit` propriedade define se o compilador JIT usa o JIT rápido.</span><span class="sxs-lookup"><span data-stu-id="f0b17-199">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="f0b17-200">Defina o valor como `false` para desabilitar o JIT rápido.</span><span class="sxs-lookup"><span data-stu-id="f0b17-200">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="f0b17-201">Para obter mais informações, consulte [Quick JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="f0b17-201">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="f0b17-202">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="f0b17-202">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="f0b17-203">A `TieredCompilationQuickJitForLoops` propriedade define se o compilador JIT usa o JIT rápido em métodos que contêm loops.</span><span class="sxs-lookup"><span data-stu-id="f0b17-203">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="f0b17-204">Defina o valor como `true` para habilitar o JIT rápido em métodos que contêm loops.</span><span class="sxs-lookup"><span data-stu-id="f0b17-204">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="f0b17-205">Para obter mais informações, consulte [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="f0b17-205">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties"></a><span data-ttu-id="f0b17-206">Propriedades de referência</span><span class="sxs-lookup"><span data-stu-id="f0b17-206">Reference properties</span></span>

- [<span data-ttu-id="f0b17-207">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="f0b17-207">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="f0b17-208">PackageReference</span><span class="sxs-lookup"><span data-stu-id="f0b17-208">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="f0b17-209">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="f0b17-209">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="f0b17-210">Referência</span><span class="sxs-lookup"><span data-stu-id="f0b17-210">Reference</span></span>](#reference)
- [<span data-ttu-id="f0b17-211">Restaurar propriedades</span><span class="sxs-lookup"><span data-stu-id="f0b17-211">Restore properties</span></span>](#restore-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="f0b17-212">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="f0b17-212">AssetTargetFallback</span></span>

<span data-ttu-id="f0b17-213">A `AssetTargetFallback` propriedade permite que você especifique versões de estrutura compatíveis adicionais para referências de projeto e pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="f0b17-213">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="f0b17-214">Por exemplo, se você especificar uma dependência de pacote `PackageReference` usando, mas esse pacote não contiver ativos que são compatíveis com `TargetFramework`seus projetos `AssetTargetFallback` , a propriedade entrará em cena.</span><span class="sxs-lookup"><span data-stu-id="f0b17-214">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="f0b17-215">A compatibilidade do pacote referenciado é verificada novamente usando cada estrutura de destino especificada em `AssetTargetFallback`.</span><span class="sxs-lookup"><span data-stu-id="f0b17-215">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="f0b17-216">Você pode definir a `AssetTargetFallback` propriedade para uma ou mais [versões da estrutura de destino](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="f0b17-216">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="f0b17-217">PackageReference</span><span class="sxs-lookup"><span data-stu-id="f0b17-217">PackageReference</span></span>

<span data-ttu-id="f0b17-218">O `PackageReference` define uma referência a um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="f0b17-218">The `PackageReference` defines a reference to a NuGet package.</span></span> <span data-ttu-id="f0b17-219">Por exemplo, talvez você queira fazer referência a um único pacote em vez de um [metapacote](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="f0b17-219">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span>

<span data-ttu-id="f0b17-220">O atributo `Include` especifica a ID do pacote.</span><span class="sxs-lookup"><span data-stu-id="f0b17-220">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="f0b17-221">O `Version` atributo especifica a versão ou o intervalo de versão.</span><span class="sxs-lookup"><span data-stu-id="f0b17-221">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="f0b17-222">Para obter informações sobre como especificar uma versão mínima, a versão máxima, o intervalo ou a correspondência exata, consulte [intervalos de versão](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="f0b17-222">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="f0b17-223">Você também pode adicionar os seguintes metadados a uma referência de projeto `IncludeAssets`: `ExcludeAssets`, e `PrivateAssets`.</span><span class="sxs-lookup"><span data-stu-id="f0b17-223">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="f0b17-224">O trecho do arquivo de projeto no exemplo a seguir faz referência ao pacote [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .</span><span class="sxs-lookup"><span data-stu-id="f0b17-224">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="f0b17-225">Para obter mais informações, consulte [referências de pacote em arquivos de projeto](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="f0b17-225">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="f0b17-226">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="f0b17-226">ProjectReference</span></span>

<span data-ttu-id="f0b17-227">O `ProjectReference` item define uma referência a outro projeto.</span><span class="sxs-lookup"><span data-stu-id="f0b17-227">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="f0b17-228">O projeto referenciado é adicionado como uma dependência de pacote NuGet, ou seja, é tratado da mesma forma `PackageReference`que um.</span><span class="sxs-lookup"><span data-stu-id="f0b17-228">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="f0b17-229">O `Include` atributo especifica o caminho para o projeto.</span><span class="sxs-lookup"><span data-stu-id="f0b17-229">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="f0b17-230">Você também pode adicionar os seguintes metadados a uma referência de projeto `IncludeAssets`: `ExcludeAssets`, e `PrivateAssets`.</span><span class="sxs-lookup"><span data-stu-id="f0b17-230">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="f0b17-231">O trecho do arquivo de projeto no exemplo a seguir faz referência `Project2`a um projeto chamado.</span><span class="sxs-lookup"><span data-stu-id="f0b17-231">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="f0b17-232">Referência</span><span class="sxs-lookup"><span data-stu-id="f0b17-232">Reference</span></span>

<span data-ttu-id="f0b17-233">O `Reference` item define uma referência a um arquivo de assembly.</span><span class="sxs-lookup"><span data-stu-id="f0b17-233">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="f0b17-234">O `Include` atributo especifica o nome do arquivo e o `HintPath` elemento filho especifica o caminho para o assembly.</span><span class="sxs-lookup"><span data-stu-id="f0b17-234">The `Include` attribute specifies the name of the file, and the `HintPath` child element specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a><span data-ttu-id="f0b17-235">Restaurar propriedades</span><span class="sxs-lookup"><span data-stu-id="f0b17-235">Restore properties</span></span>

<span data-ttu-id="f0b17-236">A restauração de um pacote referenciado instala todas as suas dependências diretas e todas as dependências dessas dependências.</span><span class="sxs-lookup"><span data-stu-id="f0b17-236">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="f0b17-237">Você pode personalizar a restauração do pacote especificando propriedades como `RestorePackagesPath` e `RestoreIgnoreFailedSources`.</span><span class="sxs-lookup"><span data-stu-id="f0b17-237">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="f0b17-238">Para obter mais informações sobre essas e outras propriedades, consulte [Restore Target](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="f0b17-238">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="f0b17-239">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0b17-239">See also</span></span>

- [<span data-ttu-id="f0b17-240">Referência de esquema do MSBuild</span><span class="sxs-lookup"><span data-stu-id="f0b17-240">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="f0b17-241">Propriedades comuns do MSBuild</span><span class="sxs-lookup"><span data-stu-id="f0b17-241">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="f0b17-242">Propriedades do MSBuild para o pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="f0b17-242">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="f0b17-243">Propriedades do MSBuild para restauração do NuGet</span><span class="sxs-lookup"><span data-stu-id="f0b17-243">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="f0b17-244">Personalizar uma compilação</span><span class="sxs-lookup"><span data-stu-id="f0b17-244">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
