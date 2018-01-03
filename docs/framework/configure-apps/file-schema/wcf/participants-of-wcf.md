---
title: '&lt;participantes&gt; do WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d99dbddc-0057-4e18-8e42-f91411d39970
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 881ee8486d7939e743613fb8a0261a4fcfe7499f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltparticipantsgt-of-wcf"></a><span data-ttu-id="df530-102">&lt;participantes&gt; do WCF</span><span class="sxs-lookup"><span data-stu-id="df530-102">&lt;participants&gt; of WCF</span></span>
<span data-ttu-id="df530-103">Configure uma lista de participantes que ouça em registros de rastreamento emissores de tempo de execução diretamente e processá-los de forma que eles são configurados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="df530-103">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="df530-104">Isso inclui a escrita em uma saída específica (por exemplo, arquivo, Console, ETW), processamento/agregando os registros ou qualquer outra combinação que pode ser necessária.</span><span class="sxs-lookup"><span data-stu-id="df530-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="df530-105">Para obter mais informações no controle de fluxo de trabalho e participantes de rastreamento, consulte [fluxo de trabalho de rastreamento e rastreamento](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) e [participantes de rastreamento](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="df530-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span></span>  
  
 <span data-ttu-id="df530-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="df530-106">\<system.serviceModel></span></span>  
<span data-ttu-id="df530-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="df530-107">\<tracking></span></span>  
<span data-ttu-id="df530-108">\<os participantes ></span><span class="sxs-lookup"><span data-stu-id="df530-108">\<participants></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df530-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df530-109">Syntax</span></span>  
  
```xml
   <tracking>    <participants>       <add name="String"            profileName="String"           type="String" />    </participants> </tracking>   
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df530-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="df530-110">Attributes and Elements</span></span>  
 <span data-ttu-id="df530-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="df530-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df530-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="df530-112">Attributes</span></span>  
 <span data-ttu-id="df530-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="df530-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="df530-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="df530-114">Child Elements</span></span>  
  
|<span data-ttu-id="df530-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="df530-115">Element</span></span>|<span data-ttu-id="df530-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="df530-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df530-117">\<add></span><span class="sxs-lookup"><span data-stu-id="df530-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="df530-118">Contém configurações para um participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="df530-118">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="df530-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="df530-119">Parent Elements</span></span>  
  
|<span data-ttu-id="df530-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="df530-120">Element</span></span>|<span data-ttu-id="df530-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="df530-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df530-122">\<controle ></span><span class="sxs-lookup"><span data-stu-id="df530-122">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="df530-123">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="df530-123">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df530-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="df530-124">Remarks</span></span>  
 <span data-ttu-id="df530-125">Os participantes de rastreamento são usados para obter os dados de rastreamento emissores de fluxo de trabalho e armazená-lo em mídias diferentes.</span><span class="sxs-lookup"><span data-stu-id="df530-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="df530-126">Da mesma forma, qualquer pós-processamento no controle de que registros também podem ser realizados o participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="df530-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="df530-127">Vários participantes de rastreamento podem consumir os eventos de rastreamento simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="df530-127">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="df530-128">Cada participante de rastreamento pode ser associado um perfil de controle diferentes.</span><span class="sxs-lookup"><span data-stu-id="df530-128">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="df530-129">Um participante de rastreamento padrão é fornecido, que grava os registros de rastreamento em uma sessão do ETW.</span><span class="sxs-lookup"><span data-stu-id="df530-129">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="df530-130">O participante é configurado em um serviço de fluxo de trabalho adicionando um comportamento acompanhamento- específico em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="df530-130">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="df530-131">Ativar um participante de rastreamento de ETW permite controlar os registros a serem exibidos no visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="df530-131">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="df530-132">Se isso não atender aos requisitos, você também poderá escrever um participante de rastreamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="df530-132">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df530-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df530-133">Example</span></span>  
 <span data-ttu-id="df530-134">O exemplo de configuração a seguir mostra o participante de rastreamento ETW padrão que está sendo configurado no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="df530-134">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="df530-135">A Id de provedor que usa o participante de rastreamento ETW para gravar os registros de rastreamento ETW é definida na `<diagnostics>` seção.</span><span class="sxs-lookup"><span data-stu-id="df530-135">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="df530-136">O participante de rastreamento tem um perfil associado a ele para especificar os registros de rastreamento que tiver assinado.</span><span class="sxs-lookup"><span data-stu-id="df530-136">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="df530-137">Isso é definido pelo `profileName` atributo o `<add>` elemento.</span><span class="sxs-lookup"><span data-stu-id="df530-137">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="df530-138">Depois que eles são definidos, o participante de rastreamento é adicionado para o `<etwTracking>` comportamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="df530-138">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="df530-139">Isso adicionará os participantes de rastreamento selecionado para extensões da instância de fluxo de trabalho, para que eles começam a receber os registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="df530-139">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml  
<configuration>   
  <system.web>   
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>   
  </system.web>   
  <system.serviceModel>   
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />                
    <tracking>   
      <participants>   
        <add name="EtwTrackingParticipant"   
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"   
             profileName="HealthMonitoring_Tracking_Profile"/>   
      </participants>   
    </tracking>   
    <behaviors>   
      <serviceBehaviors>   
        <behavior>   
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>   
      </serviceBehaviors>   
    </behaviors>   
  </system.serviceModel>   
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="df530-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df530-140">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 [<span data-ttu-id="df530-141">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="df530-141">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="df530-142">Acompanhando participantes</span><span class="sxs-lookup"><span data-stu-id="df530-142">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
