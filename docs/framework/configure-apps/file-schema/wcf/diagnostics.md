---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 2749bc6c66d491a8a160d98b508fb43aa027b806
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398049"
---
# <a name="diagnostics"></a><span data-ttu-id="107a1-101">\<> de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="107a1-101">\<diagnostics></span></span>
<span data-ttu-id="107a1-102">O `diagnostics` elemento define as configurações que podem ser usadas por um administrador para inspeção e controle de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="107a1-102">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
<span data-ttu-id="107a1-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="107a1-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="107a1-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="107a1-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="107a1-105">&nbsp;&nbsp;&nbsp;&nbsp; **\<> de diagnóstico**</span><span class="sxs-lookup"><span data-stu-id="107a1-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="107a1-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="107a1-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="107a1-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="107a1-107">Attributes and Elements</span></span>  
 <span data-ttu-id="107a1-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="107a1-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="107a1-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="107a1-109">Attributes</span></span>  
  
|<span data-ttu-id="107a1-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="107a1-110">Attribute</span></span>|<span data-ttu-id="107a1-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="107a1-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="107a1-112">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="107a1-112">etwProviderId</span></span>|<span data-ttu-id="107a1-113">Uma cadeia de caracteres que especifica o identificador para o provedor de rastreamento de eventos, que grava eventos em sessões do ETW.</span><span class="sxs-lookup"><span data-stu-id="107a1-113">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="107a1-114">performanceCounters</span><span class="sxs-lookup"><span data-stu-id="107a1-114">performanceCounters</span></span>|<span data-ttu-id="107a1-115">Especifica se contadores de desempenho para o assembly estão habilitados.</span><span class="sxs-lookup"><span data-stu-id="107a1-115">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="107a1-116">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="107a1-116">Valid values are</span></span><br /><br /> <span data-ttu-id="107a1-117">Desconto Os contadores de desempenho estão desabilitados.</span><span class="sxs-lookup"><span data-stu-id="107a1-117">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="107a1-118">-Somente: Estão habilitados apenas contadores de desempenho relevantes para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="107a1-118">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="107a1-119">Os Contadores de desempenho podem ser exibidos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="107a1-119">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="107a1-120">Os Uma instância única de contador de desempenho _WCF_Admin é criada.</span><span class="sxs-lookup"><span data-stu-id="107a1-120">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="107a1-121">Esta instância é usada para habilitar a coleta de dados SQM usados pela infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="107a1-121">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="107a1-122">Nenhum dos valores de contador para esta instância estão atualizados e, portanto, permanecerão em zero.</span><span class="sxs-lookup"><span data-stu-id="107a1-122">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="107a1-123">Esse será o valor padrão se nenhuma configuração estiver presente para o WCF.</span><span class="sxs-lookup"><span data-stu-id="107a1-123">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="107a1-124">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="107a1-124">wmiProviderEnabled</span></span>|<span data-ttu-id="107a1-125">Um valor booliano que especifica se o provedor WMI para o assembly está habilitado.</span><span class="sxs-lookup"><span data-stu-id="107a1-125">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="107a1-126">O provedor WMI é necessário para que o usuário tenha acesso em tempo de execução aos recursos de inspeção e controle do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="107a1-126">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="107a1-127">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="107a1-127">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="107a1-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="107a1-128">Child Elements</span></span>  
  
|<span data-ttu-id="107a1-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="107a1-129">Element</span></span>|<span data-ttu-id="107a1-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="107a1-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="107a1-131">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="107a1-131">\<endToEndTracing></span></span>](endtoendtracing.md)|<span data-ttu-id="107a1-132">Um elemento de configuração que permite habilitar e desabilitar diferentes aspectos de rastreamento de ponta a ponta durante a execução de um aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="107a1-132">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="107a1-133">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="107a1-133">\<messageLogging></span></span>](messagelogging.md)|<span data-ttu-id="107a1-134">Descreve as configurações para o log de mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="107a1-134">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="107a1-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="107a1-135">Parent Elements</span></span>  
  
|<span data-ttu-id="107a1-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="107a1-136">Element</span></span>|<span data-ttu-id="107a1-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="107a1-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="107a1-138">serviceModel</span><span class="sxs-lookup"><span data-stu-id="107a1-138">serviceModel</span></span>|<span data-ttu-id="107a1-139">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="107a1-139">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="107a1-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="107a1-140">Remarks</span></span>  
 <span data-ttu-id="107a1-141">A `diagnostics` seção define as configurações de diagnóstico para todos os serviços localizados em um assembly.</span><span class="sxs-lookup"><span data-stu-id="107a1-141">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="107a1-142">Não é possível definir configurações de diagnóstico separadas no nível de serviço, a menos que haja apenas um serviço no assembly.</span><span class="sxs-lookup"><span data-stu-id="107a1-142">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="107a1-143">Os atributos são definidos de acordo com os requisitos da seção.</span><span class="sxs-lookup"><span data-stu-id="107a1-143">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="107a1-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="107a1-144">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="107a1-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="107a1-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
