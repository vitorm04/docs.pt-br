---
title: <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560dd0bb-f9fb-423c-8857-2101a3654b06
ms.openlocfilehash: f04a5ee3940986cabc08895452c12ebcfd631694
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947575"
---
# <a name="participants"></a><span data-ttu-id="64696-101">\<participantes ></span><span class="sxs-lookup"><span data-stu-id="64696-101">\<participants></span></span>
<span data-ttu-id="64696-102">Configure uma lista de participantes que ouça em registros de rastreamento emissores de tempo de execução diretamente e processá-los de forma que eles são configurados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="64696-102">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="64696-103">Isso inclui a escrita em uma saída específica (por exemplo, arquivo, Console, ETW), processamento/agregando os registros ou qualquer outra combinação que pode ser necessária.</span><span class="sxs-lookup"><span data-stu-id="64696-103">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="64696-104">Para obter mais informações sobre os participantes de rastreamento e rastreamento de fluxo de trabalho, consulte [rastreamento de fluxo de trabalho e rastreamento](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) e [participantes](../../../windows-workflow-foundation/tracking-participants.md)de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="64696-104">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="64696-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="64696-105">\<system.serviceModel></span></span>  
<span data-ttu-id="64696-106">\<acompanhamento de ></span><span class="sxs-lookup"><span data-stu-id="64696-106">\<tracking></span></span>  
<span data-ttu-id="64696-107">\<participantes ></span><span class="sxs-lookup"><span data-stu-id="64696-107">\<participants></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64696-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64696-108">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" 
         profileName="String" 
         type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64696-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="64696-109">Attributes and Elements</span></span>  
 <span data-ttu-id="64696-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="64696-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64696-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="64696-111">Attributes</span></span>  
 <span data-ttu-id="64696-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="64696-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="64696-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="64696-113">Child Elements</span></span>  
  
|<span data-ttu-id="64696-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="64696-114">Element</span></span>|<span data-ttu-id="64696-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="64696-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64696-116">\<add></span><span class="sxs-lookup"><span data-stu-id="64696-116">\<add></span></span>](add-of-participants.md)|<span data-ttu-id="64696-117">Contém configurações para um participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="64696-117">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="64696-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="64696-118">Parent Elements</span></span>  
  
|<span data-ttu-id="64696-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="64696-119">Element</span></span>|<span data-ttu-id="64696-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="64696-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64696-121">\<tracking></span><span class="sxs-lookup"><span data-stu-id="64696-121">\<tracking></span></span>](tracking.md)|<span data-ttu-id="64696-122">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="64696-122">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64696-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="64696-123">Remarks</span></span>  
 <span data-ttu-id="64696-124">Os participantes de rastreamento são usados para obter os dados de rastreamento emissores de fluxo de trabalho e armazená-lo em mídias diferentes.</span><span class="sxs-lookup"><span data-stu-id="64696-124">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="64696-125">Da mesma forma, qualquer pós-processamento no controle de que registros também podem ser realizados o participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="64696-125">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="64696-126">Vários participantes de rastreamento podem consumir os eventos de rastreamento simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="64696-126">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="64696-127">Cada participante de rastreamento pode ser associado um perfil de controle diferentes.</span><span class="sxs-lookup"><span data-stu-id="64696-127">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="64696-128">Um participante de rastreamento padrão é fornecido, que grava os registros de rastreamento em uma sessão do ETW.</span><span class="sxs-lookup"><span data-stu-id="64696-128">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="64696-129">O participante é configurado em um serviço de fluxo de trabalho adicionando um comportamento acompanhamento- específico em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="64696-129">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="64696-130">Ativar um participante de rastreamento de ETW permite controlar os registros a serem exibidos no visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="64696-130">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="64696-131">Se isso não atender aos requisitos, você também poderá escrever um participante de rastreamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="64696-131">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64696-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64696-132">Example</span></span>  
 <span data-ttu-id="64696-133">O exemplo de configuração a seguir mostra o participante de rastreamento ETW padrão que está sendo configurado no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="64696-133">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="64696-134">A ID do provedor que o participante de rastreamento ETW usa para gravar os registros de rastreamento no ETW está definida na  **\<seção diagnóstico >** .</span><span class="sxs-lookup"><span data-stu-id="64696-134">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="64696-135">O participante de rastreamento tem um perfil associado a ele para especificar os registros de rastreamento que tiver assinado.</span><span class="sxs-lookup"><span data-stu-id="64696-135">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="64696-136">Isso é definido pelo atributo ProfileName do  **\<elemento add >** .</span><span class="sxs-lookup"><span data-stu-id="64696-136">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="64696-137">Depois que elas são definidas, o participante de rastreamento é adicionado ao comportamento do  **\<serviço etwTracking >** .</span><span class="sxs-lookup"><span data-stu-id="64696-137">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="64696-138">Isso adicionará os participantes de rastreamento selecionado para extensões da instância de fluxo de trabalho, para que eles começam a receber os registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="64696-138">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="64696-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64696-139">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="64696-140">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="64696-140">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="64696-141">Acompanhando participantes</span><span class="sxs-lookup"><span data-stu-id="64696-141">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
