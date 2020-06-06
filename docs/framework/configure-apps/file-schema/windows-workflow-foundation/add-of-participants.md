---
title: <add> de <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c730850-6f8e-4102-acb8-8effb4e09463
ms.openlocfilehash: 61832edbf7d206d6a5f7a85619eb17ebc010c193
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152353"
---
# <a name="add-of-participants"></a><span data-ttu-id="59fd6-102">\<add> de \<participants></span><span class="sxs-lookup"><span data-stu-id="59fd6-102">\<add> of \<participants></span></span>
<span data-ttu-id="59fd6-103">Configure um participante de rastreamento que escuta para registros de rastreamento emissores de runtime diretamente e processá-los de forma que ele foi configurado.</span><span class="sxs-lookup"><span data-stu-id="59fd6-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="59fd6-104">Isso inclui a escrita em uma saída específica (por exemplo, arquivo, Console, ETW), processamento/agregando os registros ou qualquer outra combinação que pode ser necessária.</span><span class="sxs-lookup"><span data-stu-id="59fd6-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="59fd6-105">Para obter mais informações sobre os participantes de rastreamento e rastreamento de fluxo de trabalho, consulte [rastreamento de fluxo de trabalho e rastreamento](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) e [participantes](../../../windows-workflow-foundation/tracking-participants.md)de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="59fd6-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<participants>**](participants.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="59fd6-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59fd6-106">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" profileName="String" type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59fd6-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="59fd6-107">Attributes and Elements</span></span>  
 <span data-ttu-id="59fd6-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="59fd6-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59fd6-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="59fd6-109">Attributes</span></span>  
  
|<span data-ttu-id="59fd6-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="59fd6-110">Element</span></span>|<span data-ttu-id="59fd6-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="59fd6-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="59fd6-112">name</span><span class="sxs-lookup"><span data-stu-id="59fd6-112">name</span></span>|<span data-ttu-id="59fd6-113">Uma cadeia de caracteres que especifica o nome de um participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="59fd6-113">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="59fd6-114">profileName</span><span class="sxs-lookup"><span data-stu-id="59fd6-114">profileName</span></span>|<span data-ttu-id="59fd6-115">Uma cadeia de caracteres que especifica o nome do perfil de rastreamento que define os registros de rastreamento o participante de rastreamento tiver assinado.</span><span class="sxs-lookup"><span data-stu-id="59fd6-115">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="59fd6-116">type</span><span class="sxs-lookup"><span data-stu-id="59fd6-116">type</span></span>|<span data-ttu-id="59fd6-117">Uma cadeia de caracteres que especifica o tipo de um participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="59fd6-117">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59fd6-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="59fd6-118">Child Elements</span></span>  
 <span data-ttu-id="59fd6-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="59fd6-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59fd6-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="59fd6-120">Parent Elements</span></span>  
  
|<span data-ttu-id="59fd6-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="59fd6-121">Element</span></span>|<span data-ttu-id="59fd6-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="59fd6-122">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](participants.md)|<span data-ttu-id="59fd6-123">Uma lista de participantes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="59fd6-123">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59fd6-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="59fd6-124">Remarks</span></span>  
 <span data-ttu-id="59fd6-125">Os participantes de rastreamento são usados para obter os dados de rastreamento emissores de fluxo de trabalho e armazená-lo em mídias diferentes.</span><span class="sxs-lookup"><span data-stu-id="59fd6-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="59fd6-126">Da mesma forma, qualquer pós-processamento no controle de que registros também podem ser realizados o participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="59fd6-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="59fd6-127">Vários participantes de rastreamento podem consumir os eventos de rastreamento simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="59fd6-127">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="59fd6-128">Cada participante de rastreamento pode ser associado um perfil de controle diferentes.</span><span class="sxs-lookup"><span data-stu-id="59fd6-128">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="59fd6-129">Um participante de rastreamento padrão é fornecido, que grava os registros de rastreamento em uma sessão do ETW.</span><span class="sxs-lookup"><span data-stu-id="59fd6-129">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="59fd6-130">O participante é configurado em um serviço de fluxo de trabalho adicionando um comportamento acompanhamento- específico em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="59fd6-130">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="59fd6-131">Ativar um participante de rastreamento de ETW permite controlar os registros a serem exibidos no visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="59fd6-131">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="59fd6-132">Se isso não atender aos requisitos, você também poderá escrever um participante de rastreamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="59fd6-132">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59fd6-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59fd6-133">Example</span></span>  
 <span data-ttu-id="59fd6-134">O exemplo de configuração a seguir mostra o participante de rastreamento ETW padrão que está sendo configurado no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="59fd6-134">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="59fd6-135">A ID do provedor que o participante de rastreamento ETW usa para gravar os registros de rastreamento no ETW é definida na **\<diagnostics>** seção.</span><span class="sxs-lookup"><span data-stu-id="59fd6-135">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="59fd6-136">O participante de rastreamento tem um perfil associado a ele para especificar os registros de rastreamento que tiver assinado.</span><span class="sxs-lookup"><span data-stu-id="59fd6-136">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="59fd6-137">Isso é definido pelo atributo **ProfileName** do **\<add>** elemento.</span><span class="sxs-lookup"><span data-stu-id="59fd6-137">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="59fd6-138">Depois que elas são definidas, o participante de rastreamento é adicionado ao **\<etwTracking>** comportamento do serviço.</span><span class="sxs-lookup"><span data-stu-id="59fd6-138">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="59fd6-139">Isso adicionará os participantes de rastreamento selecionado para extensões da instância de fluxo de trabalho, para que eles começam a receber os registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="59fd6-139">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59fd6-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="59fd6-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="59fd6-141">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="59fd6-141">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="59fd6-142">Acompanhando participantes</span><span class="sxs-lookup"><span data-stu-id="59fd6-142">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
