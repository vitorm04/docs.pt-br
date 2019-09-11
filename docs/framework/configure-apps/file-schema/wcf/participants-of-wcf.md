---
title: <participants>do WCF
ms.date: 03/30/2017
ms.assetid: d99dbddc-0057-4e18-8e42-f91411d39970
ms.openlocfilehash: 35ed7a49967143838a6f74c51e77c553817bd09a
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855085"
---
# <a name="participants-of-wcf"></a><span data-ttu-id="c61eb-102">\<participantes > do WCF</span><span class="sxs-lookup"><span data-stu-id="c61eb-102">\<participants> of WCF</span></span>
<span data-ttu-id="c61eb-103">Configure uma lista de participantes que ouça em registros de rastreamento emissores de tempo de execução diretamente e processá-los de forma que eles são configurados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c61eb-103">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="c61eb-104">Isso inclui a escrita em uma saída específica (por exemplo, arquivo, Console, ETW), processamento/agregando os registros ou qualquer outra combinação que pode ser necessária.</span><span class="sxs-lookup"><span data-stu-id="c61eb-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
<span data-ttu-id="c61eb-105">Para obter mais informações sobre os participantes de rastreamento e rastreamento de fluxo de trabalho, consulte [rastreamento de fluxo de trabalho e rastreamento](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) e [participantes](../../../windows-workflow-foundation/tracking-participants.md)de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c61eb-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="c61eb-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c61eb-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c61eb-107">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c61eb-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c61eb-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="c61eb-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>  
<span data-ttu-id="c61eb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<participantes >**</span><span class="sxs-lookup"><span data-stu-id="c61eb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<participants>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c61eb-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c61eb-110">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c61eb-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c61eb-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c61eb-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c61eb-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c61eb-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="c61eb-113">Attributes</span></span>  
 <span data-ttu-id="c61eb-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c61eb-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c61eb-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c61eb-115">Child Elements</span></span>  
  
|<span data-ttu-id="c61eb-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="c61eb-116">Element</span></span>|<span data-ttu-id="c61eb-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="c61eb-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c61eb-118">\<add></span><span class="sxs-lookup"><span data-stu-id="c61eb-118">\<add></span></span>](../windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="c61eb-119">Contém configurações para um participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c61eb-119">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c61eb-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c61eb-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c61eb-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="c61eb-121">Element</span></span>|<span data-ttu-id="c61eb-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="c61eb-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c61eb-123">\<tracking></span><span class="sxs-lookup"><span data-stu-id="c61eb-123">\<tracking></span></span>](../windows-workflow-foundation/tracking.md)|<span data-ttu-id="c61eb-124">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c61eb-124">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c61eb-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="c61eb-125">Remarks</span></span>  
 <span data-ttu-id="c61eb-126">Os participantes de rastreamento são usados para obter os dados de rastreamento emissores de fluxo de trabalho e armazená-lo em mídias diferentes.</span><span class="sxs-lookup"><span data-stu-id="c61eb-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="c61eb-127">Da mesma forma, qualquer pós-processamento no controle de que registros também podem ser realizados o participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c61eb-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="c61eb-128">Vários participantes de rastreamento podem consumir os eventos de rastreamento simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="c61eb-128">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="c61eb-129">Cada participante de rastreamento pode ser associado um perfil de controle diferentes.</span><span class="sxs-lookup"><span data-stu-id="c61eb-129">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="c61eb-130">Um participante de rastreamento padrão é fornecido, que grava os registros de rastreamento em uma sessão do ETW.</span><span class="sxs-lookup"><span data-stu-id="c61eb-130">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="c61eb-131">O participante é configurado em um serviço de fluxo de trabalho adicionando um comportamento acompanhamento- específico em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c61eb-131">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="c61eb-132">Ativar um participante de rastreamento de ETW permite controlar os registros a serem exibidos no visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="c61eb-132">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="c61eb-133">Se isso não atender aos requisitos, você também poderá escrever um participante de rastreamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="c61eb-133">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c61eb-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c61eb-134">Example</span></span>  
 <span data-ttu-id="c61eb-135">O exemplo de configuração a seguir mostra o participante de rastreamento ETW padrão que está sendo configurado no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="c61eb-135">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="c61eb-136">A Id de provedor que usa o participante de rastreamento ETW para gravar os registros de rastreamento ETW é definida na `<diagnostics>` seção.</span><span class="sxs-lookup"><span data-stu-id="c61eb-136">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="c61eb-137">O participante de rastreamento tem um perfil associado a ele para especificar os registros de rastreamento que tiver assinado.</span><span class="sxs-lookup"><span data-stu-id="c61eb-137">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="c61eb-138">Isso é definido pelo `profileName` atributo o `<add>` elemento.</span><span class="sxs-lookup"><span data-stu-id="c61eb-138">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="c61eb-139">Depois que eles são definidos, o participante de rastreamento é adicionado para o `<etwTracking>` comportamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="c61eb-139">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="c61eb-140">Isso adicionará os participantes de rastreamento selecionado para extensões da instância de fluxo de trabalho, para que eles começam a receber os registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c61eb-140">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml  
<configuration>
  <system.web>
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0" />
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
  
## <a name="see-also"></a><span data-ttu-id="c61eb-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c61eb-141">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- [<span data-ttu-id="c61eb-142">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c61eb-142">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c61eb-143">Acompanhando participantes</span><span class="sxs-lookup"><span data-stu-id="c61eb-143">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
