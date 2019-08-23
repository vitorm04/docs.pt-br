---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: 653693fef92072cb1e6e23234359b765f0f18fc9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940226"
---
# <a name="etwtracking"></a><span data-ttu-id="58e42-101">\<etwTracking></span><span class="sxs-lookup"><span data-stu-id="58e42-101">\<etwTracking></span></span>
<span data-ttu-id="58e42-102">Um comportamento de serviço que permite que um serviço que utiliza o acompanhamento ETW use um <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="58e42-102">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="58e42-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="58e42-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="58e42-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="58e42-104">\<behaviors></span></span>  
<span data-ttu-id="58e42-105">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="58e42-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="58e42-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="58e42-106">\<behavior></span></span>  
<span data-ttu-id="58e42-107">\<etwTracking></span><span class="sxs-lookup"><span data-stu-id="58e42-107">\<etwTracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58e42-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58e42-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58e42-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="58e42-109">Attributes and Elements</span></span>  
 <span data-ttu-id="58e42-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="58e42-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58e42-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="58e42-111">Attributes</span></span>  
  
|<span data-ttu-id="58e42-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="58e42-112">Attribute</span></span>|<span data-ttu-id="58e42-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="58e42-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="58e42-114">profileName</span><span class="sxs-lookup"><span data-stu-id="58e42-114">profileName</span></span>|<span data-ttu-id="58e42-115">Uma cadeia de caracteres que especifica o nome do perfil de rastreamento associado a esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="58e42-115">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58e42-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="58e42-116">Child Elements</span></span>  
 <span data-ttu-id="58e42-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="58e42-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58e42-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="58e42-118">Parent Elements</span></span>  
  
|<span data-ttu-id="58e42-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="58e42-119">Element</span></span>|<span data-ttu-id="58e42-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="58e42-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58e42-121">\<comportamento > de \<percomportamentos ></span><span class="sxs-lookup"><span data-stu-id="58e42-121">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="58e42-122">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="58e42-122">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58e42-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="58e42-123">Remarks</span></span>  
 <span data-ttu-id="58e42-124">Quando adicionado à configuração de comportamento do serviço, este elemento de configuração configura um participante de rastreamento em um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="58e42-124">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="58e42-125">Os participantes de rastreamento são usados para obter os dados de rastreamento emissores de fluxo de trabalho e armazená-lo em mídias diferentes.</span><span class="sxs-lookup"><span data-stu-id="58e42-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="58e42-126">Da mesma forma, qualquer pós-processamento no controle de que registros também podem ser realizados o participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="58e42-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58e42-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="58e42-127">Example</span></span>  
 <span data-ttu-id="58e42-128">O exemplo de configuração a seguir mostra o participante de rastreamento ETW padrão que está sendo configurado no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="58e42-128">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="58e42-129">A ID do provedor que o participante de rastreamento ETW usa para gravar os registros de rastreamento no ETW está definida na  **\<seção diagnóstico >** .</span><span class="sxs-lookup"><span data-stu-id="58e42-129">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="58e42-130">O participante de rastreamento tem um perfil associado a ele para especificar os registros de rastreamento que tiver assinado.</span><span class="sxs-lookup"><span data-stu-id="58e42-130">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="58e42-131">Isso é definido pelo atributo ProfileName do  **\<elemento add >** .</span><span class="sxs-lookup"><span data-stu-id="58e42-131">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="58e42-132">Depois que elas são definidas, o participante de rastreamento é adicionado ao comportamento do  **\<serviço etwTracking >** .</span><span class="sxs-lookup"><span data-stu-id="58e42-132">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="58e42-133">Isso adicionará os participantes de rastreamento selecionado para extensões da instância de fluxo de trabalho, para que eles começam a receber os registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="58e42-133">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="58e42-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58e42-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="58e42-135">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="58e42-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="58e42-136">Acompanhando participantes</span><span class="sxs-lookup"><span data-stu-id="58e42-136">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
