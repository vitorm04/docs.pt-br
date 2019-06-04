---
title: Elemento <startup>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: e40ca31ddc40cccbeb3b8dda1d148ddec5032d7c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489546"
---
# <a name="startup-element"></a><span data-ttu-id="3e726-102">\<inicialização > elemento</span><span class="sxs-lookup"><span data-stu-id="3e726-102">\<startup> element</span></span>

<span data-ttu-id="3e726-103">Especifica informações de inicialização de tempo de execução de linguagem comum.</span><span class="sxs-lookup"><span data-stu-id="3e726-103">Specifies common language runtime startup information.</span></span>

 <span data-ttu-id="3e726-104">\<configuration> \<startup></span><span class="sxs-lookup"><span data-stu-id="3e726-104">\<configuration> \<startup></span></span>

## <a name="syntax"></a><span data-ttu-id="3e726-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e726-105">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" > 
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3e726-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3e726-106">Attributes and elements</span></span>

 <span data-ttu-id="3e726-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3e726-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3e726-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="3e726-108">Attributes</span></span>

|<span data-ttu-id="3e726-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="3e726-109">Attribute</span></span>|<span data-ttu-id="3e726-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e726-110">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="3e726-111">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="3e726-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3e726-112">Especifica se deseja habilitar o [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] política de ativação de tempo de execução ou usar a política de ativação do .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3e726-112">Specifies whether to enable the [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="3e726-113">atributo useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="3e726-113">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="3e726-114">Valor</span><span class="sxs-lookup"><span data-stu-id="3e726-114">Value</span></span>|<span data-ttu-id="3e726-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e726-115">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="3e726-116">Habilitar [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] política de ativação de tempo de execução para o tempo de execução escolhido, é associar técnicas de ativação de tempo de execução herdado (como o [função CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) para o tempo de execução escolhido do arquivo de configuração em vez de limitação-los na versão 2.0 do CLR.</span><span class="sxs-lookup"><span data-stu-id="3e726-116">Enable [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="3e726-117">Portanto, se a versão do CLR 4 ou posterior é escolhido do arquivo de configuração, assemblies de modo misto criados com versões anteriores do .NET Framework são carregados com a versão do CLR escolhida.</span><span class="sxs-lookup"><span data-stu-id="3e726-117">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="3e726-118">Definir esse valor impede a versão 1.1 do CLR ou a versão 2.0 do CLR seja carregado para o mesmo processo, efetivamente, desabilitando o recurso de lado a lado em processo.</span><span class="sxs-lookup"><span data-stu-id="3e726-118">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="3e726-119">Use a política de ativação padrão para o .NET Framework 4 e posterior permitir a técnicas de ativação para carregar a versão 1.1 ou 2.0 do CLR no processo de execução herdado.</span><span class="sxs-lookup"><span data-stu-id="3e726-119">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="3e726-120">Definir esse valor impede que os assemblies de modo misto do carregamento para o .NET Framework 4 ou posterior, a menos que eles foram criados com o .NET Framework 4 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="3e726-120">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="3e726-121">Esse valor é o padrão.</span><span class="sxs-lookup"><span data-stu-id="3e726-121">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="3e726-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3e726-122">Child elements</span></span>

|<span data-ttu-id="3e726-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="3e726-123">Element</span></span>|<span data-ttu-id="3e726-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e726-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3e726-125">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="3e726-125">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="3e726-126">Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="3e726-126">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="3e726-127">Aplicativos criados com o tempo de execução versão 1.1 ou posterior devem usar o  **\<supportedRuntime >** elemento.</span><span class="sxs-lookup"><span data-stu-id="3e726-127">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="3e726-128">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="3e726-128">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="3e726-129">Especifica a quais versões do Common Language Runtime o aplicativo oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="3e726-129">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3e726-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3e726-130">Parent elements</span></span>

|<span data-ttu-id="3e726-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="3e726-131">Element</span></span>|<span data-ttu-id="3e726-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e726-132">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="3e726-133">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3e726-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3e726-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e726-134">Remarks</span></span>

 <span data-ttu-id="3e726-135">O  **\<supportedRuntime >** elemento deve ser usado por todos os aplicativos criados usando a versão 1.1 ou posterior do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3e726-135">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="3e726-136">Os aplicativos criados para oferecer suporte somente à versão 1.0 do tempo de execução devem usar o  **\<requiredRuntime >** elemento.</span><span class="sxs-lookup"><span data-stu-id="3e726-136">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="3e726-137">O código de inicialização para um aplicativo hospedado no Microsoft Internet Explorer ignorará as  **\<inicialização >** elemento e seus elementos filho.</span><span class="sxs-lookup"><span data-stu-id="3e726-137">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="3e726-138">O atributo useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="3e726-138">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="3e726-139">Esse atributo é útil se seu aplicativo usa caminhos de ativação herdados, como o [função CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), e você deseja esses caminhos para ativar a versão 4 do CLR em vez de uma versão anterior, ou se seu aplicativo criado com o .NET Framework 4, mas tem uma dependência em um assembly de modo misto criado com uma versão anterior do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3e726-139">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="3e726-140">Nesses cenários, defina o atributo como `true`.</span><span class="sxs-lookup"><span data-stu-id="3e726-140">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="3e726-141">Definindo o atributo para `true` impede que o CLR versão 1.1 ou versão 2.0 do CLR seja carregado no mesmo processo, efetivamente, desabilitando o recurso de lado a lado em processo (consulte [execução lado a lado para interoperabilidade COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="3e726-141">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="3e726-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e726-142">Example</span></span>

 <span data-ttu-id="3e726-143">O exemplo a seguir mostra como especificar a versão de tempo de execução em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="3e726-143">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<!-- When used with version 1.0 of the .NET Framework runtime -->
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
<!-- When used with version 1.1 (or later) of the runtime -->
<configuration>
   <startup>
      <supportedRuntime version="v1.1.4322"/>
      <supportedRuntime version="v1.0.3705"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="3e726-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e726-144">See also</span></span>

- [<span data-ttu-id="3e726-145">Esquema de configurações de inicialização</span><span class="sxs-lookup"><span data-stu-id="3e726-145">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3e726-146">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="3e726-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="3e726-147">Como: configurar um aplicativo para dar suporte ao .NET Framework 4 ou a versões posteriores</span><span class="sxs-lookup"><span data-stu-id="3e726-147">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="3e726-148">[Execução lado a lado para interoperabilidade COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3e726-148">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="3e726-149">Execução lado a lado em processo</span><span class="sxs-lookup"><span data-stu-id="3e726-149">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
