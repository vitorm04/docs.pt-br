---
title: <workflow> do WCF
ms.date: 03/30/2017
ms.assetid: c0443eba-d3b4-4fae-886e-9878daf77691
ms.openlocfilehash: 9920a9b75a033515584f4108503faa45687b7203
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362195"
---
# <a name="workflow-of-wcf"></a><span data-ttu-id="ae726-102">\<fluxo de trabalho > do WCF</span><span class="sxs-lookup"><span data-stu-id="ae726-102">\<workflow> of WCF</span></span>
<span data-ttu-id="ae726-103">Configure um participante de rastreamento que escuta para registros de rastreamento emissores de tempo de execução diretamente e processá-los de forma que ele foi configurado.</span><span class="sxs-lookup"><span data-stu-id="ae726-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="ae726-104">Isso inclui a escrita em uma saída específica (por exemplo, arquivo, Console, ETW), processamento/agregando os registros ou qualquer outra combinação que pode ser necessária.</span><span class="sxs-lookup"><span data-stu-id="ae726-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="ae726-105">Para obter mais informações no controle de fluxo de trabalho e os participantes de rastreamento, consulte [fluxo de trabalho, controle e rastreamento](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) e [participantes de rastreamento](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="ae726-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span></span>  
  
 <span data-ttu-id="ae726-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ae726-106">\<system.serviceModel></span></span>  
<span data-ttu-id="ae726-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="ae726-107">\<tracking></span></span>  
<span data-ttu-id="ae726-108">\<os participantes ></span><span class="sxs-lookup"><span data-stu-id="ae726-108">\<participants></span></span>  
<span data-ttu-id="ae726-109">\<add></span><span class="sxs-lookup"><span data-stu-id="ae726-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae726-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae726-110">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae726-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ae726-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ae726-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ae726-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae726-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="ae726-113">Attributes</span></span>  
  
|<span data-ttu-id="ae726-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="ae726-114">Element</span></span>|<span data-ttu-id="ae726-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae726-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ae726-116">name</span><span class="sxs-lookup"><span data-stu-id="ae726-116">name</span></span>|<span data-ttu-id="ae726-117">Uma cadeia de caracteres que especifica o nome de um participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="ae726-117">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="ae726-118">profileName</span><span class="sxs-lookup"><span data-stu-id="ae726-118">profileName</span></span>|<span data-ttu-id="ae726-119">Uma cadeia de caracteres que especifica o nome do perfil de rastreamento que define os registros de rastreamento o participante de rastreamento tiver assinado.</span><span class="sxs-lookup"><span data-stu-id="ae726-119">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="ae726-120">tipo</span><span class="sxs-lookup"><span data-stu-id="ae726-120">type</span></span>|<span data-ttu-id="ae726-121">Uma cadeia de caracteres que especifica o tipo de um participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="ae726-121">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae726-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ae726-122">Child Elements</span></span>  
 <span data-ttu-id="ae726-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ae726-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ae726-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ae726-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ae726-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="ae726-125">Element</span></span>|<span data-ttu-id="ae726-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae726-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae726-127">\<participants></span><span class="sxs-lookup"><span data-stu-id="ae726-127">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="ae726-128">Uma lista de participantes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="ae726-128">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae726-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="ae726-129">Remarks</span></span>  
 <span data-ttu-id="ae726-130">Os participantes de rastreamento são usados para obter os dados de rastreamento emissores de fluxo de trabalho e armazená-lo em mídias diferentes.</span><span class="sxs-lookup"><span data-stu-id="ae726-130">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="ae726-131">Da mesma forma, qualquer pós-processamento no controle de que registros também podem ser realizados o participante de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="ae726-131">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="ae726-132">Vários participantes de rastreamento podem consumir os eventos de rastreamento simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="ae726-132">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="ae726-133">Cada participante de rastreamento pode ser associado um perfil de controle diferentes.</span><span class="sxs-lookup"><span data-stu-id="ae726-133">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="ae726-134">Um participante de rastreamento padrão é fornecido, que grava os registros de rastreamento em uma sessão do ETW.</span><span class="sxs-lookup"><span data-stu-id="ae726-134">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="ae726-135">O participante é configurado em um serviço de fluxo de trabalho adicionando um comportamento acompanhamento- específico em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="ae726-135">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="ae726-136">Ativar um participante de rastreamento de ETW permite controlar os registros a serem exibidos no visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="ae726-136">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="ae726-137">Se isso não atender aos requisitos, você também poderá escrever um participante de rastreamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="ae726-137">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae726-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae726-138">Example</span></span>  
 <span data-ttu-id="ae726-139">O exemplo de configuração a seguir mostra o participante de rastreamento ETW padrão que está sendo configurado no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="ae726-139">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="ae726-140">A Id de provedor que usa o participante de rastreamento ETW para gravar os registros de rastreamento ETW é definida na `<diagnostics>` seção.</span><span class="sxs-lookup"><span data-stu-id="ae726-140">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="ae726-141">O participante de rastreamento tem um perfil associado a ele para especificar os registros de rastreamento que tiver assinado.</span><span class="sxs-lookup"><span data-stu-id="ae726-141">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="ae726-142">Isso é definido pelo `profileName` atributo o `<add>` elemento.</span><span class="sxs-lookup"><span data-stu-id="ae726-142">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="ae726-143">Depois que eles são definidos, o participante de rastreamento é adicionado para o `<etwTracking>` comportamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="ae726-143">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="ae726-144">Isso adicionará os participantes de rastreamento selecionado para extensões da instância de fluxo de trabalho, para que eles começam a receber os registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="ae726-144">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
             profileName="HealthMonitoring_Tracking_Profile" />
      </participants>
    </tracking>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="ae726-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae726-145">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="ae726-146">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="ae726-146">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ae726-147">Acompanhando participantes</span><span class="sxs-lookup"><span data-stu-id="ae726-147">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
