---
title: '&lt;inicialização&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 82ee7b163efcefae0f2a169b74d29ea4c9f5398a
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222734"
---
# <a name="ltstartupgt-element"></a><span data-ttu-id="84823-102">&lt;inicialização&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="84823-102">&lt;startup&gt; element</span></span>

<span data-ttu-id="84823-103">Especifica informações de inicialização de tempo de execução de linguagem comum.</span><span class="sxs-lookup"><span data-stu-id="84823-103">Specifies common language runtime startup information.</span></span>

 <span data-ttu-id="84823-104">\<Configuração > \<inicialização ></span><span class="sxs-lookup"><span data-stu-id="84823-104">\<configuration> \<startup></span></span>

## <a name="syntax"></a><span data-ttu-id="84823-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84823-105">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" > 
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="84823-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="84823-106">Attributes and elements</span></span>

 <span data-ttu-id="84823-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="84823-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="84823-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="84823-108">Attributes</span></span>

|<span data-ttu-id="84823-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="84823-109">Attribute</span></span>|<span data-ttu-id="84823-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="84823-110">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="84823-111">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="84823-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="84823-112">Especifica se deseja habilitar o [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] política de ativação de tempo de execução ou para usar o [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] política de ativação.</span><span class="sxs-lookup"><span data-stu-id="84823-112">Specifies whether to enable the [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy or to use the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="84823-113">atributo useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="84823-113">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="84823-114">Valor</span><span class="sxs-lookup"><span data-stu-id="84823-114">Value</span></span>|<span data-ttu-id="84823-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="84823-115">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="84823-116">Habilitar [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] política de ativação de tempo de execução para o tempo de execução escolhido, é associar técnicas de ativação de tempo de execução herdado (como o [função CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) para o tempo de execução escolhido do arquivo de configuração em vez de limitação-los na versão 2.0 do CLR.</span><span class="sxs-lookup"><span data-stu-id="84823-116">Enable [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="84823-117">Portanto, se a versão do CLR 4 ou posterior é escolhido do arquivo de configuração, assemblies de modo misto criados com versões anteriores do .NET Framework são carregados com a versão do CLR escolhida.</span><span class="sxs-lookup"><span data-stu-id="84823-117">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="84823-118">Definir esse valor impede a versão 1.1 do CLR ou a versão 2.0 do CLR seja carregado para o mesmo processo, efetivamente, desabilitando o recurso de lado a lado em processo.</span><span class="sxs-lookup"><span data-stu-id="84823-118">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="84823-119">Use a política de ativação padrão para o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] e posterior, que é permitir a técnicas de ativação para carregar a versão 1.1 ou 2.0 do CLR no processo de execução herdado.</span><span class="sxs-lookup"><span data-stu-id="84823-119">Use the default activation policy for the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="84823-120">Definir esse valor impede que os assemblies de modo misto do carregamento para o .NET Framework 4 ou posterior, a menos que eles foram criados com o .NET Framework 4 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="84823-120">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="84823-121">Esse valor é o padrão.</span><span class="sxs-lookup"><span data-stu-id="84823-121">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="84823-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="84823-122">Child elements</span></span>

|<span data-ttu-id="84823-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="84823-123">Element</span></span>|<span data-ttu-id="84823-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="84823-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="84823-125">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="84823-125">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="84823-126">Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="84823-126">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="84823-127">Aplicativos criados com o tempo de execução versão 1.1 ou posterior devem usar o  **\<supportedRuntime >** elemento.</span><span class="sxs-lookup"><span data-stu-id="84823-127">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="84823-128">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="84823-128">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="84823-129">Especifica a quais versões do Common Language Runtime o aplicativo oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="84823-129">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="84823-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="84823-130">Parent elements</span></span>

|<span data-ttu-id="84823-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="84823-131">Element</span></span>|<span data-ttu-id="84823-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="84823-132">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="84823-133">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="84823-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="84823-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="84823-134">Remarks</span></span>

 <span data-ttu-id="84823-135">O  **\<supportedRuntime >** elemento deve ser usado por todos os aplicativos criados usando a versão 1.1 ou posterior do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="84823-135">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="84823-136">Os aplicativos criados para oferecer suporte somente à versão 1.0 do tempo de execução devem usar o  **\<requiredRuntime >** elemento.</span><span class="sxs-lookup"><span data-stu-id="84823-136">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="84823-137">O código de inicialização para um aplicativo hospedado no Microsoft Internet Explorer ignorará as  **\<inicialização >** elemento e seus elementos filho.</span><span class="sxs-lookup"><span data-stu-id="84823-137">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="84823-138">O atributo useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="84823-138">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="84823-139">Esse atributo é útil se seu aplicativo usa caminhos de ativação herdados, como o [função CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), e você deseja esses caminhos para ativar a versão 4 do CLR em vez de uma versão anterior, ou se seu aplicativo criado com o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] , mas tem uma dependência em um assembly de modo misto criado com uma versão anterior do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="84823-139">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="84823-140">Nesses cenários, defina o atributo como `true`.</span><span class="sxs-lookup"><span data-stu-id="84823-140">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="84823-141">Definindo o atributo para `true` impede que o CLR versão 1.1 ou versão 2.0 do CLR seja carregado no mesmo processo, efetivamente, desabilitando o recurso de lado a lado em processo (consulte [execução lado a lado para interoperabilidade COM](https://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)).</span><span class="sxs-lookup"><span data-stu-id="84823-141">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)).</span></span>

## <a name="example"></a><span data-ttu-id="84823-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="84823-142">Example</span></span>

 <span data-ttu-id="84823-143">O exemplo a seguir mostra como especificar a versão de tempo de execução em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="84823-143">The following example shows how to specify the runtime version in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="84823-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84823-144">See also</span></span>

- [<span data-ttu-id="84823-145">Esquema de configurações de inicialização</span><span class="sxs-lookup"><span data-stu-id="84823-145">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="84823-146">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="84823-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="84823-147">Como: Configurar um aplicativo para dar suporte a .NET Framework 4 ou versões posteriores</span><span class="sxs-lookup"><span data-stu-id="84823-147">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [<span data-ttu-id="84823-148">Execução lado a lado para interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="84823-148">Side-by-Side Execution for COM Interop</span></span>](https://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)
- [<span data-ttu-id="84823-149">Execução lado a lado em processo</span><span class="sxs-lookup"><span data-stu-id="84823-149">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)