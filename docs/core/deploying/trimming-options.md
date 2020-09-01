---
title: Opções de corte
description: Saiba como controlar a remoção de aplicativos independentes.
author: sbomer
ms.author: svbomer
ms.date: 08/25/2020
ms.openlocfilehash: d6081a24cc18e424b55d40e152f519c680f11aa0
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271874"
---
# <a name="trimming-options"></a><span data-ttu-id="bc776-103">Opções de corte</span><span class="sxs-lookup"><span data-stu-id="bc776-103">Trimming options</span></span>

<span data-ttu-id="bc776-104">As seguintes propriedades e itens do MSBuild influenciam o comportamento de [implantações autocontidas cortadas](trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="bc776-104">The following MSBuild properties and items influence the behavior of [trimmed self-contained deployments](trim-self-contained.md).</span></span> <span data-ttu-id="bc776-105">Algumas das opções mencionam `ILLink` , que é o nome da ferramenta subjacente que implementa a corte.</span><span class="sxs-lookup"><span data-stu-id="bc776-105">Some of the options mention `ILLink`, which is the name of the underlying tool that implements trimming.</span></span> <span data-ttu-id="bc776-106">Mais informações sobre a `ILLink` ferramenta de linha de comando podem ser encontradas em [illink Options](https://github.com/mono/linker/blob/master/docs/illink-options.md).</span><span class="sxs-lookup"><span data-stu-id="bc776-106">More information about the `ILLink` command-line tool can be found at [illink options](https://github.com/mono/linker/blob/master/docs/illink-options.md).</span></span>

## <a name="enable-trimming"></a><span data-ttu-id="bc776-107">Habilitar corte</span><span class="sxs-lookup"><span data-stu-id="bc776-107">Enable trimming</span></span>

- `<PublishTrimmed>true</PublishTrimmed>`

   <span data-ttu-id="bc776-108">Habilitar corte durante a publicação, com as configurações padrão definidas pelo SDK.</span><span class="sxs-lookup"><span data-stu-id="bc776-108">Enable trimming during publish, with the default settings defined by the SDK.</span></span>

<span data-ttu-id="bc776-109">Ao usar `Microsoft.NET.Sdk` o, isso executará o corte no nível do assembly dos assemblies do Framework do netcoreapp Runtime Pack.</span><span class="sxs-lookup"><span data-stu-id="bc776-109">When using `Microsoft.NET.Sdk`, this will perform assembly-level trimming of the framework assemblies from the netcoreapp runtime pack.</span></span> <span data-ttu-id="bc776-110">As bibliotecas código do aplicativo e não estrutura não são cortadas.</span><span class="sxs-lookup"><span data-stu-id="bc776-110">Application code and non-framework libraries are not trimmed.</span></span> <span data-ttu-id="bc776-111">Outros SDKs podem definir padrões diferentes.</span><span class="sxs-lookup"><span data-stu-id="bc776-111">Other SDKs may define different defaults.</span></span>

## <a name="trimming-granularity"></a><span data-ttu-id="bc776-112">Granularidade de corte</span><span class="sxs-lookup"><span data-stu-id="bc776-112">Trimming granularity</span></span>

<span data-ttu-id="bc776-113">As configurações de granularidade a seguir controlam o quão agressivamente não usado IL é Descartado.</span><span class="sxs-lookup"><span data-stu-id="bc776-113">The following granularity settings control how aggressively unused IL is discarded.</span></span> <span data-ttu-id="bc776-114">Isso pode ser definido como uma propriedade ou como metadados em um [assembly individual](#trimmed-assemblies).</span><span class="sxs-lookup"><span data-stu-id="bc776-114">This can be set as a property, or as metadata on an [individual assembly](#trimmed-assemblies).</span></span>

- `<TrimMode>copyused</TrimMode>`

   <span data-ttu-id="bc776-115">Habilitar o corte em nível de assembly, que manterá um assembly inteiro se qualquer parte dele for usada (de maneira estática e compreendida).</span><span class="sxs-lookup"><span data-stu-id="bc776-115">Enable assembly-level trimming, which will keep an entire assembly if any part of it is used (in a statically-understood way).</span></span>

- `<TrimMode>link</TrimMode>`

    <span data-ttu-id="bc776-116">Habilitar corte em nível de membro, que remove Membros não utilizados dos tipos.</span><span class="sxs-lookup"><span data-stu-id="bc776-116">Enable member-level trimming, which removes unused members from types.</span></span>

<span data-ttu-id="bc776-117">Assemblies com `<IsTrimmable>true</IsTrimmable>` metadados, mas nenhum explícito usarão `TrimMode` o global `TrimMode` .</span><span class="sxs-lookup"><span data-stu-id="bc776-117">Assemblies with `<IsTrimmable>true</IsTrimmable>` metadata but no explicit `TrimMode` will use the global `TrimMode`.</span></span> <span data-ttu-id="bc776-118">O padrão `TrimMode` para `Microsoft.NET.Sdk` é `copyused` .</span><span class="sxs-lookup"><span data-stu-id="bc776-118">The default `TrimMode` for `Microsoft.NET.Sdk` is `copyused`.</span></span>

## <a name="trimmed-assemblies"></a><span data-ttu-id="bc776-119">Assemblies cortados</span><span class="sxs-lookup"><span data-stu-id="bc776-119">Trimmed assemblies</span></span>

<span data-ttu-id="bc776-120">Ao publicar um aplicativo cortado, o SDK computa um `ItemGroup` chamado `ManagedAssemblyToLink` que representa o conjunto de arquivos a serem processados para corte.</span><span class="sxs-lookup"><span data-stu-id="bc776-120">When publishing a trimmed app, the SDK computes an `ItemGroup` called `ManagedAssemblyToLink` that represents the set of files to be processed for trimming.</span></span> <span data-ttu-id="bc776-121">`ManagedAssemblyToLink` pode ter metadados que controlam o comportamento de corte por assembly.</span><span class="sxs-lookup"><span data-stu-id="bc776-121">`ManagedAssemblyToLink` may have metadata that controls the trimming behavior per assembly.</span></span> <span data-ttu-id="bc776-122">Para definir esses metadados, crie um destino que seja executado antes do destino interno `PrepareForILLink` .</span><span class="sxs-lookup"><span data-stu-id="bc776-122">To set this metadata, create a target that runs before the built-in `PrepareForILLink` target.</span></span> <span data-ttu-id="bc776-123">Este exemplo mostra como habilitar o corte de `MyAssembly` :</span><span class="sxs-lookup"><span data-stu-id="bc776-123">This example shows how to enable trimming of `MyAssembly`:</span></span>

```xml
<Target Name="ConfigureTrimming"
        BeforeTargets="PrepareForILLink">
  <ItemGroup>
    <ManagedAssemblyToLink Condition="'%(Filename)' == 'MyAssembly'">
      <IsTrimmable>true</IsTrimmable>
    </ManagedAssemblyToLink>
  </ItemGroup>
</Target>
```

<span data-ttu-id="bc776-124">Não adicione ou remova itens de/para `ManagedAssemblyToLink` , pois o SDK computa esse conjunto durante a publicação e espera que ele não seja alterado.</span><span class="sxs-lookup"><span data-stu-id="bc776-124">Do not add or remove items to/from `ManagedAssemblyToLink`, because the SDK computes this set during publish and expects it not to change.</span></span> <span data-ttu-id="bc776-125">Os metadados com suporte são:</span><span class="sxs-lookup"><span data-stu-id="bc776-125">The supported metadata is:</span></span>

- `<IsTrimmable>true</IsTrimmable>`

  <span data-ttu-id="bc776-126">Controle se o assembly fornecido é cortado.</span><span class="sxs-lookup"><span data-stu-id="bc776-126">Control whether the given assembly is trimmed.</span></span>

- <span data-ttu-id="bc776-127">`<TrimMode>copyused</TrimMode>` ou `<TrimMode>link</TrimMode>`</span><span class="sxs-lookup"><span data-stu-id="bc776-127">`<TrimMode>copyused</TrimMode>` or `<TrimMode>link</TrimMode>`</span></span>

  <span data-ttu-id="bc776-128">Controle a [granularidade de corte](#trimming-granularity) deste assembly.</span><span class="sxs-lookup"><span data-stu-id="bc776-128">Control the [trimming granularity](#trimming-granularity) of this assembly.</span></span> <span data-ttu-id="bc776-129">Isso tem precedência sobre o global `TrimMode` .</span><span class="sxs-lookup"><span data-stu-id="bc776-129">This takes precedence over the global `TrimMode`.</span></span> <span data-ttu-id="bc776-130">`TrimMode`A configuração em um assembly implica `<IsTrimmable>true</IsTrimmable>` .</span><span class="sxs-lookup"><span data-stu-id="bc776-130">Setting `TrimMode` on an assembly implies `<IsTrimmable>true</IsTrimmable>`.</span></span>

## <a name="root-assemblies"></a><span data-ttu-id="bc776-131">Assemblies raiz</span><span class="sxs-lookup"><span data-stu-id="bc776-131">Root assemblies</span></span>

<span data-ttu-id="bc776-132">Todos os assemblies que não têm `<IsTrimmable>true</IsTrimmable>` são consideradas raízes para a análise, o que significa que elas e todas as suas dependências estaticamente compreendidas serão mantidas.</span><span class="sxs-lookup"><span data-stu-id="bc776-132">All assemblies which do not have `<IsTrimmable>true</IsTrimmable>` are considered roots for the analysis, which means that they and all of their statically understood dependencies will be kept.</span></span> <span data-ttu-id="bc776-133">Assemblies adicionais podem ser "com raiz" por nome (sem a `.dll` extensão):</span><span class="sxs-lookup"><span data-stu-id="bc776-133">Additional assemblies may be "rooted" by name (without the `.dll` extension):</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="MyAssembly" />
</ItemGroup>
```

## <a name="root-descriptors"></a><span data-ttu-id="bc776-134">Descritores de raiz</span><span class="sxs-lookup"><span data-stu-id="bc776-134">Root descriptors</span></span>

<span data-ttu-id="bc776-135">Outra maneira de especificar raízes para análise é usando um arquivo XML que usa o formato do [descritor](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format)do vinculador.</span><span class="sxs-lookup"><span data-stu-id="bc776-135">Another way to specify roots for analysis is using an XML file that uses the linker [descriptor format](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format).</span></span> <span data-ttu-id="bc776-136">Isso permite que você acesse membros específicos da raiz em vez de um assembly inteiro.</span><span class="sxs-lookup"><span data-stu-id="bc776-136">This lets you root specific members instead of a whole assembly.</span></span>

```xml
<ItemGroup>
  <TrimmerRootDescriptor Include="MyRoots.xml" />
</ItemGroup>
```

<span data-ttu-id="bc776-137">Por exemplo, `MyRoots.xml` pode raiz um método específico que é acessado dinamicamente pelo aplicativo:</span><span class="sxs-lookup"><span data-stu-id="bc776-137">For example, `MyRoots.xml` might root a specific method that is dynamically accessed by the application:</span></span>

```xml
<linker>
  <assembly fullname="MyAssembly">
    <type fullname="MyAssembly.MyClass">
      <method name="DynamicallyAccessedMethod" />
    </type>
  </assembly>
</linker>
```

## <a name="analysis-warnings"></a><span data-ttu-id="bc776-138">Avisos de análise</span><span class="sxs-lookup"><span data-stu-id="bc776-138">Analysis warnings</span></span>

<span data-ttu-id="bc776-139">A remoção removerá o IL que não está acessível estaticamente.</span><span class="sxs-lookup"><span data-stu-id="bc776-139">Trimming will remove IL that is not statically reachable.</span></span> <span data-ttu-id="bc776-140">Os aplicativos que usam reflexão ou outros padrões que criam dependências dinâmicas podem ser quebrados por corte.</span><span class="sxs-lookup"><span data-stu-id="bc776-140">Apps that use reflection or other patterns that create dynamic dependencies may be broken by trimming.</span></span> <span data-ttu-id="bc776-141">Para avisar sobre tais padrões:</span><span class="sxs-lookup"><span data-stu-id="bc776-141">To warn about such patterns:</span></span>

- `<SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>`

    <span data-ttu-id="bc776-142">Habilitar avisos de análise de corte.</span><span class="sxs-lookup"><span data-stu-id="bc776-142">Enable trim analysis warnings.</span></span>

<span data-ttu-id="bc776-143">Isso incluirá avisos sobre todo o aplicativo, incluindo seu próprio código, código de biblioteca e código de estrutura.</span><span class="sxs-lookup"><span data-stu-id="bc776-143">This will include warnings about the entire app, including your own code, library code, and framework code.</span></span>

## <a name="warning-versions"></a><span data-ttu-id="bc776-144">Versões de aviso</span><span class="sxs-lookup"><span data-stu-id="bc776-144">Warning versions</span></span>

<span data-ttu-id="bc776-145">A análise de corte respeita a [`AnalysisLevel`](../project-sdk/msbuild-props.md#analysislevel) propriedade que controla a versão dos avisos de análise no SDK.</span><span class="sxs-lookup"><span data-stu-id="bc776-145">Trim analysis respects the [`AnalysisLevel`](../project-sdk/msbuild-props.md#analysislevel) property that controls the version of analysis warnings across the SDK.</span></span> <span data-ttu-id="bc776-146">Há outra propriedade que controla a versão dos avisos de análise de corte de forma independente (semelhante a `WarningLevel` para o compilador):</span><span class="sxs-lookup"><span data-stu-id="bc776-146">There is another property that controls the version of trim analysis warnings independently (similar to `WarningLevel` for the compiler):</span></span>

- `<ILLinkWarningLevel>5</ILLinkWarningLevel>`

    <span data-ttu-id="bc776-147">Emitir apenas avisos do nível determinado ou inferior.</span><span class="sxs-lookup"><span data-stu-id="bc776-147">Emit only warnings of the given level or lower.</span></span> <span data-ttu-id="bc776-148">Isso pode ser `9999` incluir todas as versões de aviso.</span><span class="sxs-lookup"><span data-stu-id="bc776-148">This can be `9999` to include all warning versions.</span></span>

## <a name="suppressing-warnings"></a><span data-ttu-id="bc776-149">Suprimindo avisos</span><span class="sxs-lookup"><span data-stu-id="bc776-149">Suppressing warnings</span></span>

<span data-ttu-id="bc776-150">[Códigos de aviso](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes) individuais podem ser suprimidos usando as propriedades usuais do MSBuild respeitadas pelo ferramentas, incluindo `NoWarn` , `WarningsAsErrors` , `WarningsNotAsErrors` e `TreatWarningsAsErrors` .</span><span class="sxs-lookup"><span data-stu-id="bc776-150">Individual [warning codes](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes) can be suppressed using the usual MSBuild properties respected by the toolchain, including `NoWarn`, `WarningsAsErrors`, `WarningsNotAsErrors`, and `TreatWarningsAsErrors`.</span></span> <span data-ttu-id="bc776-151">Há uma opção adicional que controla o comportamento de aviso como erro do ILLink de forma independente:</span><span class="sxs-lookup"><span data-stu-id="bc776-151">There is an additional option that controls the ILLink warn-as-error behavior independently:</span></span>

- `<ILLinkTreatWarningsAsErrors>false</ILLinkTreatWarningsAsErrors>`

    <span data-ttu-id="bc776-152">Não trate avisos ILLink como erros.</span><span class="sxs-lookup"><span data-stu-id="bc776-152">Don't treat ILLink warnings as errors.</span></span> <span data-ttu-id="bc776-153">Isso pode ser útil para evitar a desativação de avisos de análise de corte em erros ao tratar avisos do compilador como erros globalmente.</span><span class="sxs-lookup"><span data-stu-id="bc776-153">This may be useful to avoid turning trim analysis warnings into errors when treating compiler warnings as errors globally.</span></span>

## <a name="removing-symbols"></a><span data-ttu-id="bc776-154">Removendo símbolos</span><span class="sxs-lookup"><span data-stu-id="bc776-154">Removing symbols</span></span>

<span data-ttu-id="bc776-155">Os símbolos normalmente serão cortados para corresponder aos assemblies cortados.</span><span class="sxs-lookup"><span data-stu-id="bc776-155">Symbols will normally be trimmed to match the trimmed assemblies.</span></span> <span data-ttu-id="bc776-156">Você também pode remover todos os símbolos:</span><span class="sxs-lookup"><span data-stu-id="bc776-156">You can also remove all symbols:</span></span>

- `<TrimmerRemoveSymbols>true</TrimmerRemoveSymbols>`

    <span data-ttu-id="bc776-157">Remova os símbolos do aplicativo cortado, incluindo PDBs inseridos e arquivos PDB separados.</span><span class="sxs-lookup"><span data-stu-id="bc776-157">Remove symbols from the trimmed application, including embedded PDBs and separate PDB files.</span></span> <span data-ttu-id="bc776-158">Isso se aplica ao código do aplicativo e a qualquer dependência que venha com símbolos.</span><span class="sxs-lookup"><span data-stu-id="bc776-158">This applies to both the application code and any dependencies that come with symbols.</span></span>

<span data-ttu-id="bc776-159">O SDK também torna possível desabilitar o suporte do depurador usando a propriedade `DebuggerSupport` .</span><span class="sxs-lookup"><span data-stu-id="bc776-159">The SDK also makes it possible to disable debugger support using the property `DebuggerSupport`.</span></span> <span data-ttu-id="bc776-160">Quando o suporte ao depurador estiver desabilitado, a remoção removerá símbolos automaticamente ( `TrimmerRemoveSymbols` padrão será true).</span><span class="sxs-lookup"><span data-stu-id="bc776-160">When debugger support is disabled, trimming will remove symbols automatically (`TrimmerRemoveSymbols` will default to true).</span></span>
