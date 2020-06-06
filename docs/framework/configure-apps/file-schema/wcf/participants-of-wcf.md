---
title: <participants>do WCF
ms.date: 03/30/2017
ms.assetid: d99dbddc-0057-4e18-8e42-f91411d39970
ms.openlocfilehash: 35ed7a49967143838a6f74c51e77c553817bd09a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855085"
---
# <a name="participants-of-wcf"></a><span data-ttu-id="8d061-102">\<participants>do WCF</span><span class="sxs-lookup"><span data-stu-id="8d061-102">\<participants> of WCF</span></span>
<span data-ttu-id="8d061-103">Configure uma lista de participantes que ouça em registros de rastreamento emissores de runtime diretamente e processá-los de forma que eles são configurados de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8d061-103">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="8d061-104">Isso inclui a escrita em uma saída específica (por exemplo, arquivo, Console, ETW), processamento/agregando os registros ou qualquer outra combinação que pode ser necessária.</span><span class="sxs-lookup"><span data-stu-id="8d061-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
<span data-ttu-id="8d061-105">Para obter mais informações sobre os participantes de rastreamento e rastreamento de fluxo de trabalho, consulte [rastreamento de fluxo de trabalho e rastreamento](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) e [participantes](../../../windows-workflow-foundation/tracking-participants.md)de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8d061-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<participants>**  
  
## <a name="syntax"></a><span data-ttu-id="8d061-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d061-106">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d061-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8d061-107">Attributes and Elements</span></span>  
 <span data-ttu-id="8d061-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8d061-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d061-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="8d061-109">Attributes</span></span>  
 <span data-ttu-id="8d061-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="8d061-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8d061-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8d061-111">Child Elements</span></span>  
  
|<span data-ttu-id="8d061-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="8d061-112">Element</span></span>|<span data-ttu-id="8d061-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d061-113">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](../windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="8d061-114">Contém configurações para um participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8d061-114">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d061-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8d061-115">Parent Elements</span></span>  
  
|<span data-ttu-id="8d061-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="8d061-116">Element</span></span>|<span data-ttu-id="8d061-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d061-117">Description</span></span>|  
|-------------|-----------------|  
|[\<tracking>](../windows-workflow-foundation/tracking.md)|<span data-ttu-id="8d061-118">Representa uma seção de configuração para definir configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8d061-118">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d061-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="8d061-119">Remarks</span></span>  
 <span data-ttu-id="8d061-120">Os participantes de rastreamento são usados para obter os dados de rastreamento emissores de fluxo de trabalho e armazená-lo em mídias diferentes.</span><span class="sxs-lookup"><span data-stu-id="8d061-120">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="8d061-121">Da mesma forma, qualquer pós-processamento no controle de que registros também podem ser realizados o participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8d061-121">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="8d061-122">Vários participantes de rastreamento podem consumir os eventos de rastreamento simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="8d061-122">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="8d061-123">Cada participante de rastreamento pode ser associado um perfil de controle diferentes.</span><span class="sxs-lookup"><span data-stu-id="8d061-123">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="8d061-124">Um participante de rastreamento padrão é fornecido, que grava os registros de rastreamento em uma sessão do ETW.</span><span class="sxs-lookup"><span data-stu-id="8d061-124">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="8d061-125">O participante é configurado em um serviço de fluxo de trabalho adicionando um comportamento acompanhamento- específico em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="8d061-125">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="8d061-126">Ativar um participante de rastreamento de ETW permite controlar os registros a serem exibidos no visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="8d061-126">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="8d061-127">Se isso não atender aos requisitos, você também poderá escrever um participante de rastreamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="8d061-127">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d061-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8d061-128">Example</span></span>  
 <span data-ttu-id="8d061-129">O exemplo de configuração a seguir mostra o participante de rastreamento ETW padrão que está sendo configurado no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="8d061-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="8d061-130">A Id de provedor que usa o participante de rastreamento ETW para gravar os registros de rastreamento ETW é definida na `<diagnostics>` seção.</span><span class="sxs-lookup"><span data-stu-id="8d061-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="8d061-131">O participante de rastreamento tem um perfil associado a ele para especificar os registros de rastreamento que tiver assinado.</span><span class="sxs-lookup"><span data-stu-id="8d061-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="8d061-132">Isso é definido pelo `profileName` atributo o `<add>` elemento.</span><span class="sxs-lookup"><span data-stu-id="8d061-132">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="8d061-133">Depois que eles são definidos, o participante de rastreamento é adicionado para o `<etwTracking>` comportamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="8d061-133">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="8d061-134">Isso adicionará os participantes de rastreamento selecionado para extensões da instância de fluxo de trabalho, para que eles começam a receber os registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8d061-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8d061-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="8d061-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- [<span data-ttu-id="8d061-136">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8d061-136">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8d061-137">Acompanhando participantes</span><span class="sxs-lookup"><span data-stu-id="8d061-137">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
