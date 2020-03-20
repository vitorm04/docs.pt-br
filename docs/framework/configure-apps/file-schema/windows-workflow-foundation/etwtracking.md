---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: d562bd4e3d46a1bdf41fc4065fee926850a49aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152165"
---
# <a name="etwtracking"></a><span data-ttu-id="6b95d-101">\<etwTracking></span><span class="sxs-lookup"><span data-stu-id="6b95d-101">\<etwTracking></span></span>
<span data-ttu-id="6b95d-102">Um comportamento de serviço que permite que um serviço que utiliza o acompanhamento ETW use um <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="6b95d-102">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="6b95d-103">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6b95d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6b95d-104">&nbsp;&nbsp;[**\<Sistema.>de modelo de serviço**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="6b95d-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="6b95d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comportamentos>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="6b95d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="6b95d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviçocomportamentos>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="6b95d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="6b95d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comportamento>**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="6b95d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="6b95d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etwRastreamento>**</span><span class="sxs-lookup"><span data-stu-id="6b95d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etwTracking>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b95d-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b95d-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b95d-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6b95d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6b95d-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6b95d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b95d-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="6b95d-112">Attributes</span></span>  
  
|<span data-ttu-id="6b95d-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="6b95d-113">Attribute</span></span>|<span data-ttu-id="6b95d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="6b95d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6b95d-115">profileName</span><span class="sxs-lookup"><span data-stu-id="6b95d-115">profileName</span></span>|<span data-ttu-id="6b95d-116">Uma cadeia de caracteres que especifica o nome do perfil de rastreamento associado a esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="6b95d-116">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b95d-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6b95d-117">Child Elements</span></span>  
 <span data-ttu-id="6b95d-118">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6b95d-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6b95d-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6b95d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="6b95d-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="6b95d-120">Element</span></span>|<span data-ttu-id="6b95d-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="6b95d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b95d-122">\<> de \<comportamento de>de serviços</span><span class="sxs-lookup"><span data-stu-id="6b95d-122">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="6b95d-123">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="6b95d-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b95d-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="6b95d-124">Remarks</span></span>  
 <span data-ttu-id="6b95d-125">Quando adicionado à configuração de comportamento do serviço, este elemento de configuração configura um participante de rastreamento em um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="6b95d-125">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="6b95d-126">Os participantes de rastreamento são usados para obter os dados de rastreamento emissores de fluxo de trabalho e armazená-lo em mídias diferentes.</span><span class="sxs-lookup"><span data-stu-id="6b95d-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="6b95d-127">Da mesma forma, qualquer pós-processamento no controle de que registros também podem ser realizados o participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6b95d-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b95d-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6b95d-128">Example</span></span>  
 <span data-ttu-id="6b95d-129">O exemplo de configuração a seguir mostra o participante de rastreamento ETW padrão que está sendo configurado no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="6b95d-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="6b95d-130">O ID do Provedor que o Participante de Rastreamento do ETW \*\* \<\*\* usa para escrever os Registros de Rastreamento para ETW é definido na seção de diagnósticos>.</span><span class="sxs-lookup"><span data-stu-id="6b95d-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="6b95d-131">O participante de rastreamento tem um perfil associado a ele para especificar os registros de rastreamento que tiver assinado.</span><span class="sxs-lookup"><span data-stu-id="6b95d-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="6b95d-132">Isso é definido pelo atributo **profileName** do \*\* \<\*\* elemento add>.</span><span class="sxs-lookup"><span data-stu-id="6b95d-132">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="6b95d-133">Uma vez definidos, o Participante de rastreamento é adicionado ao \*\* \<etwTracking>\*\* comportamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="6b95d-133">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="6b95d-134">Isso adicionará os participantes de rastreamento selecionado para extensões da instância de fluxo de trabalho, para que eles começam a receber os registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6b95d-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6b95d-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="6b95d-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="6b95d-136">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="6b95d-136">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6b95d-137">Acompanhando participantes</span><span class="sxs-lookup"><span data-stu-id="6b95d-137">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
