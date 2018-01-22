---
title: "&lt;inicialização&gt; elemento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
caps.latest.revision: "19"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4299775cd23162839ab9846adc7d2c64cc18a404
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="ltstartupgt-element"></a><span data-ttu-id="f40a9-102">&lt;inicialização&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="f40a9-102">&lt;startup&gt; Element</span></span>
<span data-ttu-id="f40a9-103">Especifica informações de inicialização de tempo de execução de linguagem comum.</span><span class="sxs-lookup"><span data-stu-id="f40a9-103">Specifies common language runtime startup information.</span></span>  
  
 <span data-ttu-id="f40a9-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f40a9-104">\<configuration></span></span>  
<span data-ttu-id="f40a9-105">\<startup></span><span class="sxs-lookup"><span data-stu-id="f40a9-105">\<startup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f40a9-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f40a9-106">Syntax</span></span>  
  
```xml  
<startup useLegacyV2RuntimeActivationPolicy="true|false" >   
</startup>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f40a9-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f40a9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f40a9-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f40a9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f40a9-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f40a9-109">Attributes</span></span>  
  
|<span data-ttu-id="f40a9-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="f40a9-110">Attribute</span></span>|<span data-ttu-id="f40a9-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f40a9-111">Description</span></span>|  
|---------------|-----------------|  
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="f40a9-112">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="f40a9-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f40a9-113">Especifica se deseja habilitar o [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] política de ativação de tempo de execução ou usar o [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] política de ativação.</span><span class="sxs-lookup"><span data-stu-id="f40a9-113">Specifies whether to enable the [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy or to use the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] activation policy.</span></span>|  
  
## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="f40a9-114">useLegacyV2RuntimeActivationPolicy Attribute</span><span class="sxs-lookup"><span data-stu-id="f40a9-114">useLegacyV2RuntimeActivationPolicy Attribute</span></span>  
  
|<span data-ttu-id="f40a9-115">Valor</span><span class="sxs-lookup"><span data-stu-id="f40a9-115">Value</span></span>|<span data-ttu-id="f40a9-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="f40a9-116">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="f40a9-117">Habilitar [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] política de ativação de tempo de execução para o tempo de execução escolhido, que é associar as técnicas de ativação herdadas do tempo de execução (como o [função CorBindToRuntimeEx](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) para o tempo de execução escolhido do arquivo de configuração em vez de limitá-los no CLR versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="f40a9-117">Enable [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="f40a9-118">Portanto, se você escolher a versão do CLR 4 ou posterior do arquivo de configuração, os assemblies de modo misto criados com versões anteriores do .NET Framework são carregados com a versão do CLR escolhida.</span><span class="sxs-lookup"><span data-stu-id="f40a9-118">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="f40a9-119">Definir esse valor impede CLR versão 1.1 ou CLR versão 2.0 carregados no mesmo processo, efetivamente, desabilitando o recurso de lado a lado em processo.</span><span class="sxs-lookup"><span data-stu-id="f40a9-119">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|  
|`false`|<span data-ttu-id="f40a9-120">Use a política de ativação padrão para o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] e posterior, que é permitir que o tempo de execução herdado técnicas de ativação para carregar o CLR versão 1.1 ou 2.0 no processo de.</span><span class="sxs-lookup"><span data-stu-id="f40a9-120">Use the default activation policy for the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="f40a9-121">Definir esse valor impede que os assemblies de modo misto do carregamento para o .NET Framework 4 ou posterior, a menos que eles foram criados com o .NET Framework 4 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="f40a9-121">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="f40a9-122">Esse valor é o padrão.</span><span class="sxs-lookup"><span data-stu-id="f40a9-122">This value is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f40a9-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f40a9-123">Child Elements</span></span>  
  
|<span data-ttu-id="f40a9-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="f40a9-124">Element</span></span>|<span data-ttu-id="f40a9-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="f40a9-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f40a9-126">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="f40a9-126">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="f40a9-127">Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="f40a9-127">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="f40a9-128">Os aplicativos criados com o tempo de execução versão 1.1 ou posterior devem usar o  **\<supportedRuntime >** elemento.</span><span class="sxs-lookup"><span data-stu-id="f40a9-128">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="f40a9-129">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="f40a9-129">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="f40a9-130">Especifica a quais versões do Common Language Runtime o aplicativo oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="f40a9-130">Specifies which versions of the common language runtime the application supports.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f40a9-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f40a9-131">Parent Elements</span></span>  
  
|<span data-ttu-id="f40a9-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="f40a9-132">Element</span></span>|<span data-ttu-id="f40a9-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="f40a9-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f40a9-134">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f40a9-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f40a9-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="f40a9-135">Remarks</span></span>  
 <span data-ttu-id="f40a9-136">O  **\<supportedRuntime >** elemento deve ser usado por todos os aplicativos criados com a versão 1.1 ou posterior do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f40a9-136">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="f40a9-137">Os aplicativos criados para oferecer suporte a apenas versão 1.0 do tempo de execução devem usar o  **\<requiredRuntime >** elemento.</span><span class="sxs-lookup"><span data-stu-id="f40a9-137">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>  
  
 <span data-ttu-id="f40a9-138">O código de inicialização para um aplicativo hospedado no Microsoft Internet Explorer ignora o  **\<inicialização >** elemento e seus elementos filho.</span><span class="sxs-lookup"><span data-stu-id="f40a9-138">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>  
  
## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="f40a9-139">O atributo useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="f40a9-139">The useLegacyV2RuntimeActivationPolicy Attribute</span></span>  
 <span data-ttu-id="f40a9-140">Esse atributo é útil se seu aplicativo usa caminhos de ativação herdadas, como o [função CorBindToRuntimeEx](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), e você deseja que esses caminhos para ativar a versão 4 do CLR em vez de uma versão anterior, ou se seu aplicativo criado com o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] , mas tem uma dependência em um assembly de modo misto criado com uma versão anterior do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f40a9-140">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="f40a9-141">Nesses cenários, defina o atributo como `true`.</span><span class="sxs-lookup"><span data-stu-id="f40a9-141">In those scenarios, set the attribute to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f40a9-142">Definindo o atributo para `true` impede que o CLR versão 1.1 ou CLR versão 2.0 seja carregado no mesmo processo, efetivamente, desabilitando o recurso de lado a lado em processo (consulte [execução lado a lado para interoperabilidade COM](http://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)).</span><span class="sxs-lookup"><span data-stu-id="f40a9-142">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](http://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f40a9-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f40a9-143">Example</span></span>  
 <span data-ttu-id="f40a9-144">O exemplo a seguir mostra como especificar a versão de tempo de execução em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="f40a9-144">The following example shows how to specify the runtime version in a configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f40a9-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f40a9-145">See Also</span></span>  
 [<span data-ttu-id="f40a9-146">Esquema de configurações de inicialização</span><span class="sxs-lookup"><span data-stu-id="f40a9-146">Startup Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [<span data-ttu-id="f40a9-147">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="f40a9-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 <span data-ttu-id="f40a9-148">[\<PaveOver> Specifying Which Runtime Version to Use](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2) (PaveOver> Especificando a versão do tempo de execução a ser usada)</span><span class="sxs-lookup"><span data-stu-id="f40a9-148">[\<PaveOver> Specifying Which Runtime Version to Use](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)</span></span>  
 [<span data-ttu-id="f40a9-149">Execução lado a lado para interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="f40a9-149">Side-by-Side Execution for COM Interop</span></span>](http://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)  
 [<span data-ttu-id="f40a9-150">Execução lado a lado em processo</span><span class="sxs-lookup"><span data-stu-id="f40a9-150">In-Process Side-by-Side Execution</span></span>](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)
