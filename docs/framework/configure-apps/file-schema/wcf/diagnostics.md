---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 170cae5b328c86073c1d8e7710bb19e98ab5688c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925871"
---
# <a name="diagnostics"></a><span data-ttu-id="41174-101">\<> de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="41174-101">\<diagnostics></span></span>
<span data-ttu-id="41174-102">O `diagnostics` elemento define as configurações que podem ser usadas por um administrador para inspeção e controle de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="41174-102">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
 <span data-ttu-id="41174-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="41174-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="41174-104">\<> de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="41174-104">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41174-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41174-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics etwProviderId="String"
               performanceCounters="Off/ServiceOnly/All/Default"
               wmiProviderEnabled="Boolean">
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
      <filters>
        <clear />
      </filters>
    </messageLogging>
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41174-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="41174-106">Attributes and Elements</span></span>  
 <span data-ttu-id="41174-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="41174-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41174-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="41174-108">Attributes</span></span>  
  
|<span data-ttu-id="41174-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="41174-109">Attribute</span></span>|<span data-ttu-id="41174-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="41174-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="41174-111">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="41174-111">etwProviderId</span></span>|<span data-ttu-id="41174-112">Uma cadeia de caracteres que especifica o identificador para o provedor de rastreamento de eventos, que grava eventos em sessões do ETW.</span><span class="sxs-lookup"><span data-stu-id="41174-112">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="41174-113">performanceCounters</span><span class="sxs-lookup"><span data-stu-id="41174-113">performanceCounters</span></span>|<span data-ttu-id="41174-114">Especifica se contadores de desempenho para o assembly estão habilitados.</span><span class="sxs-lookup"><span data-stu-id="41174-114">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="41174-115">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="41174-115">Valid values are</span></span><br /><br /> <span data-ttu-id="41174-116">Desconto Os contadores de desempenho estão desabilitados.</span><span class="sxs-lookup"><span data-stu-id="41174-116">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="41174-117">-Somente: Estão habilitados apenas contadores de desempenho relevantes para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="41174-117">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="41174-118">Os Contadores de desempenho podem ser exibidos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="41174-118">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="41174-119">Os Uma instância única de contador de desempenho _WCF_Admin é criada.</span><span class="sxs-lookup"><span data-stu-id="41174-119">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="41174-120">Esta instância é usada para habilitar a coleta de dados SQM usados pela infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="41174-120">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="41174-121">Nenhum dos valores de contador para esta instância estão atualizados e, portanto, permanecerão em zero.</span><span class="sxs-lookup"><span data-stu-id="41174-121">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="41174-122">Esse será o valor padrão se nenhuma configuração estiver presente para o WCF.</span><span class="sxs-lookup"><span data-stu-id="41174-122">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="41174-123">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="41174-123">wmiProviderEnabled</span></span>|<span data-ttu-id="41174-124">Um valor booliano que especifica se o provedor WMI para o assembly está habilitado.</span><span class="sxs-lookup"><span data-stu-id="41174-124">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="41174-125">O provedor WMI é necessário para que o usuário tenha acesso em tempo de execução aos recursos de inspeção e controle do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="41174-125">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="41174-126">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="41174-126">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41174-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="41174-127">Child Elements</span></span>  
  
|<span data-ttu-id="41174-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="41174-128">Element</span></span>|<span data-ttu-id="41174-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="41174-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41174-130">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="41174-130">\<endToEndTracing></span></span>](endtoendtracing.md)|<span data-ttu-id="41174-131">Um elemento de configuração que permite habilitar e desabilitar diferentes aspectos de rastreamento de ponta a ponta durante a execução de um aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="41174-131">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="41174-132">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="41174-132">\<messageLogging></span></span>](messagelogging.md)|<span data-ttu-id="41174-133">Descreve as configurações para o log de mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="41174-133">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="41174-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="41174-134">Parent Elements</span></span>  
  
|<span data-ttu-id="41174-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="41174-135">Element</span></span>|<span data-ttu-id="41174-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="41174-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="41174-137">serviceModel</span><span class="sxs-lookup"><span data-stu-id="41174-137">serviceModel</span></span>|<span data-ttu-id="41174-138">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="41174-138">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41174-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="41174-139">Remarks</span></span>  
 <span data-ttu-id="41174-140">A `diagnostics` seção define as configurações de diagnóstico para todos os serviços localizados em um assembly.</span><span class="sxs-lookup"><span data-stu-id="41174-140">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="41174-141">Não é possível definir configurações de diagnóstico separadas no nível de serviço, a menos que haja apenas um serviço no assembly.</span><span class="sxs-lookup"><span data-stu-id="41174-141">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="41174-142">Os atributos são definidos de acordo com os requisitos da seção.</span><span class="sxs-lookup"><span data-stu-id="41174-142">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41174-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41174-143">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="41174-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41174-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
