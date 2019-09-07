---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: 094fbf95042c00287fb8dfcca28753cfe501a8d8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398764"
---
# <a name="etwtracking"></a><span data-ttu-id="df1b5-101">\<etwTracking></span><span class="sxs-lookup"><span data-stu-id="df1b5-101">\<etwTracking></span></span>
<span data-ttu-id="df1b5-102">Um comportamento de serviço que permite que um serviço que utiliza o acompanhamento ETW use um <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="df1b5-102">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="df1b5-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="df1b5-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="df1b5-104">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="df1b5-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="df1b5-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="df1b5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="df1b5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="df1b5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="df1b5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="df1b5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="df1b5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> etwTracking**</span><span class="sxs-lookup"><span data-stu-id="df1b5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etwTracking>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df1b5-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df1b5-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df1b5-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="df1b5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="df1b5-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="df1b5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df1b5-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="df1b5-112">Attributes</span></span>  
  
|<span data-ttu-id="df1b5-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="df1b5-113">Attribute</span></span>|<span data-ttu-id="df1b5-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="df1b5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="df1b5-115">profileName</span><span class="sxs-lookup"><span data-stu-id="df1b5-115">profileName</span></span>|<span data-ttu-id="df1b5-116">Uma cadeia de caracteres que especifica o nome do perfil de rastreamento associado a esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="df1b5-116">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df1b5-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="df1b5-117">Child Elements</span></span>  
 <span data-ttu-id="df1b5-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="df1b5-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df1b5-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="df1b5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="df1b5-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="df1b5-120">Element</span></span>|<span data-ttu-id="df1b5-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="df1b5-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df1b5-122">\<comportamento > de \<percomportamentos ></span><span class="sxs-lookup"><span data-stu-id="df1b5-122">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="df1b5-123">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="df1b5-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df1b5-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="df1b5-124">Remarks</span></span>  
 <span data-ttu-id="df1b5-125">Quando adicionado à configuração de comportamento do serviço, este elemento de configuração configura um participante de rastreamento em um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="df1b5-125">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="df1b5-126">Os participantes de rastreamento são usados para obter os dados de rastreamento emissores de fluxo de trabalho e armazená-lo em mídias diferentes.</span><span class="sxs-lookup"><span data-stu-id="df1b5-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="df1b5-127">Da mesma forma, qualquer pós-processamento no controle de que registros também podem ser realizados o participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="df1b5-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df1b5-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df1b5-128">Example</span></span>  
 <span data-ttu-id="df1b5-129">O exemplo de configuração a seguir mostra o participante de rastreamento ETW padrão que está sendo configurado no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="df1b5-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="df1b5-130">A ID do provedor que o participante de rastreamento ETW usa para gravar os registros de rastreamento no ETW está definida na  **\<seção diagnóstico >** .</span><span class="sxs-lookup"><span data-stu-id="df1b5-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="df1b5-131">O participante de rastreamento tem um perfil associado a ele para especificar os registros de rastreamento que tiver assinado.</span><span class="sxs-lookup"><span data-stu-id="df1b5-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="df1b5-132">Isso é definido pelo atributo **ProfileName** do  **\<elemento add >** .</span><span class="sxs-lookup"><span data-stu-id="df1b5-132">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="df1b5-133">Depois que elas são definidas, o participante de rastreamento é adicionado ao comportamento do  **\<serviço etwTracking >** .</span><span class="sxs-lookup"><span data-stu-id="df1b5-133">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="df1b5-134">Isso adicionará os participantes de rastreamento selecionado para extensões da instância de fluxo de trabalho, para que eles começam a receber os registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="df1b5-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="df1b5-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df1b5-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="df1b5-136">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="df1b5-136">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="df1b5-137">Acompanhando participantes</span><span class="sxs-lookup"><span data-stu-id="df1b5-137">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
