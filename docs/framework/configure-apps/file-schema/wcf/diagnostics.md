---
title: "&lt;diagnóstico&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5c7997b3ffc1a1c3a16372398f43e8f0d06aadee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdiagnosticsgt"></a><span data-ttu-id="da869-102">&lt;diagnóstico&gt;</span><span class="sxs-lookup"><span data-stu-id="da869-102">&lt;diagnostics&gt;</span></span>
<span data-ttu-id="da869-103">O `diagnostics` elemento define configurações que podem ser usadas por um administrador para inspeção de tempo de execução e o controle.</span><span class="sxs-lookup"><span data-stu-id="da869-103">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
 <span data-ttu-id="da869-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="da869-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="da869-105">\<diagnóstico ></span><span class="sxs-lookup"><span data-stu-id="da869-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da869-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da869-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
   <diagnostics etwProviderId="String"       performanceCounters="Off/ServiceOnly/All/Default"              wmiProviderEnabled="Boolean" >       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
       <messageLogging logEntireMessage="Boolean"  
          logMalformedMessages="Boolean"  
          logMessagesAtServiceLevel="Boolean"  
          logMessagesAtTransportLevel="Boolean"  
          maxMessagesToLog="Integer"  
          maxSizeOfMessageToLog="Integer" >  
          <filters>  
             <clear />  
          </filters>  
       </messageLogging>  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da869-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="da869-107">Attributes and Elements</span></span>  
 <span data-ttu-id="da869-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="da869-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da869-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="da869-109">Attributes</span></span>  
  
|<span data-ttu-id="da869-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="da869-110">Attribute</span></span>|<span data-ttu-id="da869-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="da869-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="da869-112">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="da869-112">etwProviderId</span></span>|<span data-ttu-id="da869-113">Uma cadeia de caracteres que especifica o identificador para o provedor de rastreamento de eventos, que grava eventos em sessões ETW.</span><span class="sxs-lookup"><span data-stu-id="da869-113">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="da869-114">performanceCounters</span><span class="sxs-lookup"><span data-stu-id="da869-114">performanceCounters</span></span>|<span data-ttu-id="da869-115">Especifica se os contadores de desempenho para o assembly estão habilitados.</span><span class="sxs-lookup"><span data-stu-id="da869-115">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="da869-116">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="da869-116">Valid values are</span></span><br /><br /> <span data-ttu-id="da869-117">-Off: Os contadores de desempenho estão desabilitados.</span><span class="sxs-lookup"><span data-stu-id="da869-117">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="da869-118">-ServiceOnly: Somente contadores de desempenho relevantes para esse serviço está habilitado.</span><span class="sxs-lookup"><span data-stu-id="da869-118">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="da869-119">-Todos os: Desempenho contadores podem ser visualizados em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="da869-119">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="da869-120">-Padrão: Um _WCF_Admin de instância do contador de desempenho é criada.</span><span class="sxs-lookup"><span data-stu-id="da869-120">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="da869-121">Esta instância é usada para habilitar a coleta de dados SQM usado pela infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="da869-121">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="da869-122">Nenhum dos valores de contador para esta instância são atualizadas e, portanto, permanecerão em zero.</span><span class="sxs-lookup"><span data-stu-id="da869-122">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="da869-123">Este é o valor padrão se nenhuma configuração estiver presente para o WCF.</span><span class="sxs-lookup"><span data-stu-id="da869-123">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="da869-124">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="da869-124">wmiProviderEnabled</span></span>|<span data-ttu-id="da869-125">Um valor booleano que especifica se o provedor WMI para o assembly está habilitado.</span><span class="sxs-lookup"><span data-stu-id="da869-125">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="da869-126">O provedor WMI é necessário para o usuário acessar o tempo de execução para os recursos de inspeção e controle do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="da869-126">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="da869-127">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="da869-127">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="da869-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="da869-128">Child Elements</span></span>  
  
|<span data-ttu-id="da869-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="da869-129">Element</span></span>|<span data-ttu-id="da869-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="da869-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da869-131">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="da869-131">\<endToEndTracing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|<span data-ttu-id="da869-132">Um elemento de configuração que permite habilitar e desabilitar diferentes aspectos de rastreamento ponta a ponta durante a execução de um aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="da869-132">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="da869-133">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="da869-133">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|<span data-ttu-id="da869-134">Descreve as configurações de log de mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="da869-134">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="da869-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="da869-135">Parent Elements</span></span>  
  
|<span data-ttu-id="da869-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="da869-136">Element</span></span>|<span data-ttu-id="da869-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="da869-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="da869-138">ServiceModel</span><span class="sxs-lookup"><span data-stu-id="da869-138">serviceModel</span></span>|<span data-ttu-id="da869-139">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="da869-139">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da869-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="da869-140">Remarks</span></span>  
 <span data-ttu-id="da869-141">O `diagnostics` seção define as configurações de diagnóstico para todos os serviços localizados em um assembly.</span><span class="sxs-lookup"><span data-stu-id="da869-141">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="da869-142">Não é possível definir as configurações de diagnóstico separada no nível de serviço, a menos que haja apenas um serviço no assembly.</span><span class="sxs-lookup"><span data-stu-id="da869-142">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="da869-143">Atributos são definidos de acordo com os requisitos da seção.</span><span class="sxs-lookup"><span data-stu-id="da869-143">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da869-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="da869-144">Example</span></span>  
  
```xml  
<diagnostics wmiProviderEnabled="false"  
       performanceCounters="all">  
       <messageLogging logEntireMessage="true"  
          logMalformedMessages="true"  
          logMessagesAtServiceLevel="true"  
          logMessagesAtTransportLevel="true"  
          maxMessagesToLog="42"  
          maxSizeOfMessageToLog="42">  
         <filters>  
         <clear />  
    </filters>  
       </messageLogging>  
</diagnostics>  
```  
  
## <a name="see-also"></a><span data-ttu-id="da869-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da869-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>
