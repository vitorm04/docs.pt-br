---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: e7614f158826e3522ac8e17d60c1ea65fefc8612
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174441"
---
# <a name="etwtracking"></a><span data-ttu-id="0d768-101">\<etwTracking></span><span class="sxs-lookup"><span data-stu-id="0d768-101">\<etwTracking></span></span>
<span data-ttu-id="0d768-102">Um comportamento de serviço que permite que um serviço que utiliza o acompanhamento ETW use um <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="0d768-102">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="0d768-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0d768-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="0d768-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="0d768-104">\<behaviors></span></span>  
<span data-ttu-id="0d768-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="0d768-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="0d768-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="0d768-106">\<behavior></span></span>  
<span data-ttu-id="0d768-107">\<etwTracking></span><span class="sxs-lookup"><span data-stu-id="0d768-107">\<etwTracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d768-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d768-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d768-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0d768-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0d768-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0d768-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d768-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="0d768-111">Attributes</span></span>  
  
|<span data-ttu-id="0d768-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="0d768-112">Attribute</span></span>|<span data-ttu-id="0d768-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d768-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0d768-114">profileName</span><span class="sxs-lookup"><span data-stu-id="0d768-114">profileName</span></span>|<span data-ttu-id="0d768-115">Uma cadeia de caracteres que especifica o nome do perfil de rastreamento associado a esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="0d768-115">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d768-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0d768-116">Child Elements</span></span>  
 <span data-ttu-id="0d768-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0d768-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d768-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0d768-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0d768-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="0d768-119">Element</span></span>|<span data-ttu-id="0d768-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d768-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d768-121">\<comportamento > de \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="0d768-121">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="0d768-122">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="0d768-122">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d768-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d768-123">Remarks</span></span>  
 <span data-ttu-id="0d768-124">Quando adicionado à configuração de comportamento do serviço, este elemento de configuração configura um participante de rastreamento em um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0d768-124">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="0d768-125">Os participantes de rastreamento são usados para obter os dados de rastreamento emissores de fluxo de trabalho e armazená-lo em mídias diferentes.</span><span class="sxs-lookup"><span data-stu-id="0d768-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="0d768-126">Da mesma forma, qualquer pós-processamento no controle de que registros também podem ser realizados o participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="0d768-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d768-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d768-127">Example</span></span>  
 <span data-ttu-id="0d768-128">O exemplo de configuração a seguir mostra o participante de rastreamento ETW padrão que está sendo configurado no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="0d768-128">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="0d768-129">A Id do provedor que o participante de rastreamento de ETW usa para gravar os registros de rastreamento ETW é definida na  **\<diagnóstico >** seção.</span><span class="sxs-lookup"><span data-stu-id="0d768-129">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="0d768-130">O participante de rastreamento tem um perfil associado a ele para especificar os registros de rastreamento que tiver assinado.</span><span class="sxs-lookup"><span data-stu-id="0d768-130">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="0d768-131">Isso é definido pelo **profileName** atributo da  **\<Adicionar >** elemento.</span><span class="sxs-lookup"><span data-stu-id="0d768-131">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="0d768-132">Depois que eles são definidos, o participante de rastreamento é adicionado para o  **\<etwTracking >** comportamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="0d768-132">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="0d768-133">Isso adicionará os participantes de rastreamento selecionado para extensões da instância de fluxo de trabalho, para que eles começam a receber os registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="0d768-133">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0d768-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d768-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="0d768-135">Rastreamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="0d768-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0d768-136">Participantes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="0d768-136">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
