---
title: '&lt;participantes&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560dd0bb-f9fb-423c-8857-2101a3654b06
ms.openlocfilehash: d5ce06a535283a7789419fb9d87433a45e37fa81
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757028"
---
# <a name="ltparticipantsgt"></a><span data-ttu-id="eb2cf-102">&lt;participantes&gt;</span><span class="sxs-lookup"><span data-stu-id="eb2cf-102">&lt;participants&gt;</span></span>
<span data-ttu-id="eb2cf-103">Configure uma lista de participantes que ouça em registros de rastreamento emissores de tempo de execução diretamente e processá-los de forma que eles são configurados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="eb2cf-103">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="eb2cf-104">Isso inclui a escrita em uma saída específica (por exemplo, arquivo, Console, ETW), processamento/agregando os registros ou qualquer outra combinação que pode ser necessária.</span><span class="sxs-lookup"><span data-stu-id="eb2cf-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="eb2cf-105">Para obter mais informações no controle de fluxo de trabalho e participantes de rastreamento, consulte [fluxo de trabalho de rastreamento e rastreamento](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) e [participantes de rastreamento](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="eb2cf-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="eb2cf-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="eb2cf-106">\<system.serviceModel></span></span>  
<span data-ttu-id="eb2cf-107">\<controle ></span><span class="sxs-lookup"><span data-stu-id="eb2cf-107">\<tracking></span></span>  
<span data-ttu-id="eb2cf-108">\<os participantes ></span><span class="sxs-lookup"><span data-stu-id="eb2cf-108">\<participants></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb2cf-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb2cf-109">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" 
         profileName="String" 
         type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb2cf-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="eb2cf-110">Attributes and Elements</span></span>  
 <span data-ttu-id="eb2cf-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="eb2cf-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb2cf-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="eb2cf-112">Attributes</span></span>  
 <span data-ttu-id="eb2cf-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="eb2cf-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eb2cf-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="eb2cf-114">Child Elements</span></span>  
  
|<span data-ttu-id="eb2cf-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="eb2cf-115">Element</span></span>|<span data-ttu-id="eb2cf-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb2cf-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb2cf-117">\<add></span><span class="sxs-lookup"><span data-stu-id="eb2cf-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="eb2cf-118">Contém configurações para um participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="eb2cf-118">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eb2cf-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="eb2cf-119">Parent Elements</span></span>  
  
|<span data-ttu-id="eb2cf-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="eb2cf-120">Element</span></span>|<span data-ttu-id="eb2cf-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb2cf-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb2cf-122">\<controle ></span><span class="sxs-lookup"><span data-stu-id="eb2cf-122">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="eb2cf-123">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="eb2cf-123">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb2cf-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb2cf-124">Remarks</span></span>  
 <span data-ttu-id="eb2cf-125">Os participantes de rastreamento são usados para obter os dados de rastreamento emissores de fluxo de trabalho e armazená-lo em mídias diferentes.</span><span class="sxs-lookup"><span data-stu-id="eb2cf-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="eb2cf-126">Da mesma forma, qualquer pós-processamento no controle de que registros também podem ser realizados o participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="eb2cf-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="eb2cf-127">Vários participantes de rastreamento podem consumir os eventos de rastreamento simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="eb2cf-127">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="eb2cf-128">Cada participante de rastreamento pode ser associado um perfil de controle diferentes.</span><span class="sxs-lookup"><span data-stu-id="eb2cf-128">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="eb2cf-129">Um participante de rastreamento padrão é fornecido, que grava os registros de rastreamento em uma sessão do ETW.</span><span class="sxs-lookup"><span data-stu-id="eb2cf-129">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="eb2cf-130">O participante é configurado em um serviço de fluxo de trabalho adicionando um comportamento acompanhamento- específico em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="eb2cf-130">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="eb2cf-131">Ativar um participante de rastreamento de ETW permite controlar os registros a serem exibidos no visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="eb2cf-131">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="eb2cf-132">Se isso não atender aos requisitos, você também poderá escrever um participante de rastreamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="eb2cf-132">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb2cf-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eb2cf-133">Example</span></span>  
 <span data-ttu-id="eb2cf-134">O exemplo de configuração a seguir mostra o participante de rastreamento ETW padrão que está sendo configurado no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="eb2cf-134">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="eb2cf-135">A Id de provedor que usa o participante de rastreamento do ETW para gravar os registros de rastreamento ETW é definida no  **\<diagnóstico >** seção.</span><span class="sxs-lookup"><span data-stu-id="eb2cf-135">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="eb2cf-136">O participante de rastreamento tem um perfil associado a ele para especificar os registros de rastreamento que tiver assinado.</span><span class="sxs-lookup"><span data-stu-id="eb2cf-136">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="eb2cf-137">Isso é definido pelo **profileName** atributo o  **\<Adicionar >** elemento.</span><span class="sxs-lookup"><span data-stu-id="eb2cf-137">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="eb2cf-138">Depois que eles são definidos, o participante de rastreamento é adicionado para o  **\<etwTracking >** comportamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="eb2cf-138">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="eb2cf-139">Isso adicionará os participantes de rastreamento selecionado para extensões da instância de fluxo de trabalho, para que eles começam a receber os registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="eb2cf-139">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eb2cf-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb2cf-140">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>  
 [<span data-ttu-id="eb2cf-141">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="eb2cf-141">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="eb2cf-142">Acompanhando participantes</span><span class="sxs-lookup"><span data-stu-id="eb2cf-142">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
