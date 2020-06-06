---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 2749bc6c66d491a8a160d98b508fb43aa027b806
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398049"
---
# \<diagnostics>
<span data-ttu-id="fd4bc-101">O `diagnostics` elemento define as configurações que podem ser usadas por um administrador para inspeção e controle de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="fd4bc-101">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="fd4bc-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fd4bc-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd4bc-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fd4bc-103">Attributes and Elements</span></span>  
 <span data-ttu-id="fd4bc-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fd4bc-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd4bc-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="fd4bc-105">Attributes</span></span>  
  
|<span data-ttu-id="fd4bc-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="fd4bc-106">Attribute</span></span>|<span data-ttu-id="fd4bc-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fd4bc-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd4bc-108">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="fd4bc-108">etwProviderId</span></span>|<span data-ttu-id="fd4bc-109">Uma cadeia de caracteres que especifica o identificador para o provedor de rastreamento de eventos, que grava eventos em sessões do ETW.</span><span class="sxs-lookup"><span data-stu-id="fd4bc-109">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="fd4bc-110">performanceCounters</span><span class="sxs-lookup"><span data-stu-id="fd4bc-110">performanceCounters</span></span>|<span data-ttu-id="fd4bc-111">Especifica se contadores de desempenho para o assembly estão habilitados.</span><span class="sxs-lookup"><span data-stu-id="fd4bc-111">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="fd4bc-112">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="fd4bc-112">Valid values are</span></span><br /><br /> <span data-ttu-id="fd4bc-113">-Desativado: os contadores de desempenho estão desabilitados.</span><span class="sxs-lookup"><span data-stu-id="fd4bc-113">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="fd4bc-114">-Service only: somente contadores de desempenho relevantes para esse serviço estão habilitados.</span><span class="sxs-lookup"><span data-stu-id="fd4bc-114">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="fd4bc-115">-Todos: contadores de desempenho podem ser exibidos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="fd4bc-115">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="fd4bc-116">-Padrão: uma única instância de contador de desempenho _WCF_Admin é criada.</span><span class="sxs-lookup"><span data-stu-id="fd4bc-116">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="fd4bc-117">Esta instância é usada para habilitar a coleta de dados SQM usados pela infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="fd4bc-117">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="fd4bc-118">Nenhum dos valores de contador para esta instância estão atualizados e, portanto, permanecerão em zero.</span><span class="sxs-lookup"><span data-stu-id="fd4bc-118">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="fd4bc-119">Esse será o valor padrão se nenhuma configuração estiver presente para o WCF.</span><span class="sxs-lookup"><span data-stu-id="fd4bc-119">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="fd4bc-120">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="fd4bc-120">wmiProviderEnabled</span></span>|<span data-ttu-id="fd4bc-121">Um valor booliano que especifica se o provedor WMI para o assembly está habilitado.</span><span class="sxs-lookup"><span data-stu-id="fd4bc-121">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="fd4bc-122">O provedor WMI é necessário para que o usuário tenha acesso em tempo de execução aos recursos de inspeção e controle do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="fd4bc-122">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="fd4bc-123">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="fd4bc-123">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd4bc-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fd4bc-124">Child Elements</span></span>  
  
|<span data-ttu-id="fd4bc-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="fd4bc-125">Element</span></span>|<span data-ttu-id="fd4bc-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="fd4bc-126">Description</span></span>|  
|-------------|-----------------|  
|[\<endToEndTracing>](endtoendtracing.md)|<span data-ttu-id="fd4bc-127">Um elemento de configuração que permite habilitar e desabilitar diferentes aspectos de rastreamento de ponta a ponta durante a execução de um aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="fd4bc-127">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[\<messageLogging>](messagelogging.md)|<span data-ttu-id="fd4bc-128">Descreve as configurações para o log de mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="fd4bc-128">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fd4bc-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fd4bc-129">Parent Elements</span></span>  
  
|<span data-ttu-id="fd4bc-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="fd4bc-130">Element</span></span>|<span data-ttu-id="fd4bc-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="fd4bc-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fd4bc-132">serviceModel</span><span class="sxs-lookup"><span data-stu-id="fd4bc-132">serviceModel</span></span>|<span data-ttu-id="fd4bc-133">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="fd4bc-133">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd4bc-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="fd4bc-134">Remarks</span></span>  
 <span data-ttu-id="fd4bc-135">A `diagnostics` seção define as configurações de diagnóstico para todos os serviços localizados em um assembly.</span><span class="sxs-lookup"><span data-stu-id="fd4bc-135">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="fd4bc-136">Não é possível definir configurações de diagnóstico separadas no nível de serviço, a menos que haja apenas um serviço no assembly.</span><span class="sxs-lookup"><span data-stu-id="fd4bc-136">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="fd4bc-137">Os atributos são definidos de acordo com os requisitos da seção.</span><span class="sxs-lookup"><span data-stu-id="fd4bc-137">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd4bc-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fd4bc-138">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fd4bc-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="fd4bc-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
