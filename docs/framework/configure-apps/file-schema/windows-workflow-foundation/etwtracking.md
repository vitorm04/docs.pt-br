---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: d562bd4e3d46a1bdf41fc4065fee926850a49aa1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152165"
---
# \<etwTracking>
<span data-ttu-id="cd5a4-101">Um comportamento de serviço que permite que um serviço que utiliza o acompanhamento ETW use um <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="cd5a4-101">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etwTracking>**  
  
## <a name="syntax"></a><span data-ttu-id="cd5a4-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd5a4-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd5a4-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cd5a4-103">Attributes and Elements</span></span>  
 <span data-ttu-id="cd5a4-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cd5a4-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd5a4-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="cd5a4-105">Attributes</span></span>  
  
|<span data-ttu-id="cd5a4-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="cd5a4-106">Attribute</span></span>|<span data-ttu-id="cd5a4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="cd5a4-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cd5a4-108">profileName</span><span class="sxs-lookup"><span data-stu-id="cd5a4-108">profileName</span></span>|<span data-ttu-id="cd5a4-109">Uma cadeia de caracteres que especifica o nome do perfil de rastreamento associado a esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="cd5a4-109">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd5a4-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cd5a4-110">Child Elements</span></span>  
 <span data-ttu-id="cd5a4-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="cd5a4-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cd5a4-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cd5a4-112">Parent Elements</span></span>  
  
|<span data-ttu-id="cd5a4-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="cd5a4-113">Element</span></span>|<span data-ttu-id="cd5a4-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="cd5a4-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd5a4-115">\<behavior>desse\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="cd5a4-115">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="cd5a4-116">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="cd5a4-116">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd5a4-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="cd5a4-117">Remarks</span></span>  
 <span data-ttu-id="cd5a4-118">Quando adicionado à configuração de comportamento do serviço, este elemento de configuração configura um participante de rastreamento em um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="cd5a4-118">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="cd5a4-119">Os participantes de rastreamento são usados para obter os dados de rastreamento emissores de fluxo de trabalho e armazená-lo em mídias diferentes.</span><span class="sxs-lookup"><span data-stu-id="cd5a4-119">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="cd5a4-120">Da mesma forma, qualquer pós-processamento no controle de que registros também podem ser realizados o participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="cd5a4-120">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd5a4-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cd5a4-121">Example</span></span>  
 <span data-ttu-id="cd5a4-122">O exemplo de configuração a seguir mostra o participante de rastreamento ETW padrão que está sendo configurado no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="cd5a4-122">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="cd5a4-123">A ID do provedor que o participante de rastreamento ETW usa para gravar os registros de rastreamento no ETW é definida na **\<diagnostics>** seção.</span><span class="sxs-lookup"><span data-stu-id="cd5a4-123">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="cd5a4-124">O participante de rastreamento tem um perfil associado a ele para especificar os registros de rastreamento que tiver assinado.</span><span class="sxs-lookup"><span data-stu-id="cd5a4-124">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="cd5a4-125">Isso é definido pelo atributo **ProfileName** do **\<add>** elemento.</span><span class="sxs-lookup"><span data-stu-id="cd5a4-125">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="cd5a4-126">Depois que elas são definidas, o participante de rastreamento é adicionado ao **\<etwTracking>** comportamento do serviço.</span><span class="sxs-lookup"><span data-stu-id="cd5a4-126">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="cd5a4-127">Isso adicionará os participantes de rastreamento selecionado para extensões da instância de fluxo de trabalho, para que eles começam a receber os registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="cd5a4-127">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cd5a4-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="cd5a4-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="cd5a4-129">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="cd5a4-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="cd5a4-130">Acompanhando participantes</span><span class="sxs-lookup"><span data-stu-id="cd5a4-130">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
