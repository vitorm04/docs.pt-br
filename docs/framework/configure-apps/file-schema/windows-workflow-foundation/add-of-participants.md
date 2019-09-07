---
title: <add> de <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c730850-6f8e-4102-acb8-8effb4e09463
ms.openlocfilehash: 479430abd06561cc294b3da3d0922b737364b50f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398928"
---
# <a name="add-of-participants"></a><span data-ttu-id="60f5f-102">\<Adicionar > de \<participantes ></span><span class="sxs-lookup"><span data-stu-id="60f5f-102">\<add> of \<participants></span></span>
<span data-ttu-id="60f5f-103">Configure um participante de rastreamento que escuta para registros de rastreamento emissores de tempo de execução diretamente e processá-los de forma que ele foi configurado.</span><span class="sxs-lookup"><span data-stu-id="60f5f-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="60f5f-104">Isso inclui a escrita em uma saída específica (por exemplo, arquivo, Console, ETW), processamento/agregando os registros ou qualquer outra combinação que pode ser necessária.</span><span class="sxs-lookup"><span data-stu-id="60f5f-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="60f5f-105">Para obter mais informações sobre os participantes de rastreamento e rastreamento de fluxo de trabalho, consulte [rastreamento de fluxo de trabalho e rastreamento](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) e [participantes](../../../windows-workflow-foundation/tracking-participants.md)de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="60f5f-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="60f5f-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="60f5f-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="60f5f-107">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="60f5f-107">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="60f5f-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<acompanhamento de >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="60f5f-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="60f5f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<participantes >** ](participants.md)</span><span class="sxs-lookup"><span data-stu-id="60f5f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<participants>**](participants.md)</span></span>\
<span data-ttu-id="60f5f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="60f5f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60f5f-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60f5f-111">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" profileName="String" type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60f5f-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="60f5f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="60f5f-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="60f5f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60f5f-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="60f5f-114">Attributes</span></span>  
  
|<span data-ttu-id="60f5f-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="60f5f-115">Element</span></span>|<span data-ttu-id="60f5f-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="60f5f-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="60f5f-117">name</span><span class="sxs-lookup"><span data-stu-id="60f5f-117">name</span></span>|<span data-ttu-id="60f5f-118">Uma cadeia de caracteres que especifica o nome de um participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="60f5f-118">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="60f5f-119">profileName</span><span class="sxs-lookup"><span data-stu-id="60f5f-119">profileName</span></span>|<span data-ttu-id="60f5f-120">Uma cadeia de caracteres que especifica o nome do perfil de rastreamento que define os registros de rastreamento o participante de rastreamento tiver assinado.</span><span class="sxs-lookup"><span data-stu-id="60f5f-120">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="60f5f-121">tipo</span><span class="sxs-lookup"><span data-stu-id="60f5f-121">type</span></span>|<span data-ttu-id="60f5f-122">Uma cadeia de caracteres que especifica o tipo de um participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="60f5f-122">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60f5f-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="60f5f-123">Child Elements</span></span>  
 <span data-ttu-id="60f5f-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="60f5f-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="60f5f-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="60f5f-125">Parent Elements</span></span>  
  
|<span data-ttu-id="60f5f-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="60f5f-126">Element</span></span>|<span data-ttu-id="60f5f-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="60f5f-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60f5f-128">\<participants></span><span class="sxs-lookup"><span data-stu-id="60f5f-128">\<participants></span></span>](participants.md)|<span data-ttu-id="60f5f-129">Uma lista de participantes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="60f5f-129">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60f5f-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="60f5f-130">Remarks</span></span>  
 <span data-ttu-id="60f5f-131">Os participantes de rastreamento são usados para obter os dados de rastreamento emissores de fluxo de trabalho e armazená-lo em mídias diferentes.</span><span class="sxs-lookup"><span data-stu-id="60f5f-131">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="60f5f-132">Da mesma forma, qualquer pós-processamento no controle de que registros também podem ser realizados o participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="60f5f-132">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="60f5f-133">Vários participantes de rastreamento podem consumir os eventos de rastreamento simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="60f5f-133">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="60f5f-134">Cada participante de rastreamento pode ser associado um perfil de controle diferentes.</span><span class="sxs-lookup"><span data-stu-id="60f5f-134">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="60f5f-135">Um participante de rastreamento padrão é fornecido, que grava os registros de rastreamento em uma sessão do ETW.</span><span class="sxs-lookup"><span data-stu-id="60f5f-135">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="60f5f-136">O participante é configurado em um serviço de fluxo de trabalho adicionando um comportamento acompanhamento- específico em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="60f5f-136">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="60f5f-137">Ativar um participante de rastreamento de ETW permite controlar os registros a serem exibidos no visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="60f5f-137">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="60f5f-138">Se isso não atender aos requisitos, você também poderá escrever um participante de rastreamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="60f5f-138">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60f5f-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="60f5f-139">Example</span></span>  
 <span data-ttu-id="60f5f-140">O exemplo de configuração a seguir mostra o participante de rastreamento ETW padrão que está sendo configurado no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="60f5f-140">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="60f5f-141">A ID do provedor que o participante de rastreamento ETW usa para gravar os registros de rastreamento no ETW está definida na  **\<seção diagnóstico >** .</span><span class="sxs-lookup"><span data-stu-id="60f5f-141">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="60f5f-142">O participante de rastreamento tem um perfil associado a ele para especificar os registros de rastreamento que tiver assinado.</span><span class="sxs-lookup"><span data-stu-id="60f5f-142">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="60f5f-143">Isso é definido pelo atributo **ProfileName** do  **\<elemento add >** .</span><span class="sxs-lookup"><span data-stu-id="60f5f-143">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="60f5f-144">Depois que elas são definidas, o participante de rastreamento é adicionado ao comportamento do  **\<serviço etwTracking >** .</span><span class="sxs-lookup"><span data-stu-id="60f5f-144">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="60f5f-145">Isso adicionará os participantes de rastreamento selecionado para extensões da instância de fluxo de trabalho, para que eles começam a receber os registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="60f5f-145">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="60f5f-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60f5f-146">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="60f5f-147">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="60f5f-147">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="60f5f-148">Acompanhando participantes</span><span class="sxs-lookup"><span data-stu-id="60f5f-148">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
