---
title: <behavior> de <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: 115f94fc3f17dc5b4dd1ee3a090f2c9d121f810b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139725"
---
# <a name="behavior-of-servicebehaviors"></a><span data-ttu-id="be8bd-102">\<behavior> de \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="be8bd-102">\<behavior> of \<serviceBehaviors></span></span>
<span data-ttu-id="be8bd-103">O `behavior` elemento contém uma coleção de configurações para o comportamento de um serviço.</span><span class="sxs-lookup"><span data-stu-id="be8bd-103">The `behavior` element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="be8bd-104">Cada comportamento é indexado pela sua `name`.</span><span class="sxs-lookup"><span data-stu-id="be8bd-104">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="be8bd-105">Os serviços podem vincular a cada comportamento por meio desse nome usando o `behaviorConfiguration` atributo do [\<endpoint>](endpoint-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="be8bd-105">Services can link to each behavior through this name using the `behaviorConfiguration` attribute of the [\<endpoint>](endpoint-element.md) element.</span></span> <span data-ttu-id="be8bd-106">Isso permite que os pontos de extremidade compartilhem configurações comuns de comportamento sem redefinir as configurações.</span><span class="sxs-lookup"><span data-stu-id="be8bd-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span> <span data-ttu-id="be8bd-107">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="be8bd-107">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="be8bd-108">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="be8bd-108">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be8bd-109">Elementos de comportamento específicos para atividades de fluxo de trabalho do Windows, como o [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) elemento, são documentados na página [ \<behavior> de \<serviceBehaviors> ](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) .</span><span class="sxs-lookup"><span data-stu-id="be8bd-109">Behavior elements specific to Windows Workflow activities, such as the [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) element, are documented in the [\<behavior> of \<serviceBehaviors>](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) page.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="be8bd-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="be8bd-110">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <serviceBehaviors>
       <behavior name="String" />
    </serviceBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be8bd-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="be8bd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="be8bd-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="be8bd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be8bd-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="be8bd-113">Attributes</span></span>  
  
|<span data-ttu-id="be8bd-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="be8bd-114">Attribute</span></span>|<span data-ttu-id="be8bd-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="be8bd-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="be8bd-116">name</span><span class="sxs-lookup"><span data-stu-id="be8bd-116">name</span></span>|<span data-ttu-id="be8bd-117">Uma cadeia de caracteres exclusiva que contém o nome da configuração do comportamento.</span><span class="sxs-lookup"><span data-stu-id="be8bd-117">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="be8bd-118">Esse valor é uma cadeia de caracteres definida pelo usuário que deve ser exclusiva, pois ele atua como a cadeia de caracteres de identificação para o elemento.</span><span class="sxs-lookup"><span data-stu-id="be8bd-118">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="be8bd-119">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="be8bd-119">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="be8bd-120">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="be8bd-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be8bd-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="be8bd-121">Child Elements</span></span>  
  
|<span data-ttu-id="be8bd-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="be8bd-122">Element</span></span>|<span data-ttu-id="be8bd-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="be8bd-123">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-element.md)|<span data-ttu-id="be8bd-124">Contém dados de configuração para o DataContractSerializer.</span><span class="sxs-lookup"><span data-stu-id="be8bd-124">Contains configuration data for the DataContractSerializer.</span></span>|  
|[\<persistenceProvider>](persistenceprovider.md)|<span data-ttu-id="be8bd-125">Especifica o tipo da implementação do provedor de persistência a ser usado, bem como o tempo limite a ser usado para operações de persistência.</span><span class="sxs-lookup"><span data-stu-id="be8bd-125">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>|  
|[\<routing>](routing-of-servicebehavior.md)|<span data-ttu-id="be8bd-126">Fornece acesso de tempo de execução ao serviço de roteamento para permitir a modificação dinâmica da configuração de roteamento.</span><span class="sxs-lookup"><span data-stu-id="be8bd-126">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>|  
|[\<serviceAuthenticationManager>](serviceauthenticationmanager.md)|<span data-ttu-id="be8bd-127">Fornece um elemento de configuração de fluxo de trabalho que estabelece no nível de serviço a validade de uma transmissão, mensagem ou originador.</span><span class="sxs-lookup"><span data-stu-id="be8bd-127">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>|  
|[\<serviceAuthorization>](serviceauthorization-element.md)|<span data-ttu-id="be8bd-128">Especifica as configurações que autorizam o acesso às operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="be8bd-128">Specifies settings that authorize access to service operations.</span></span>|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="be8bd-129">Especifica a credencial a ser usada na autenticação do serviço e nas configurações relacionadas à validação da credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="be8bd-129">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>|  
|[\<serviceDebug>](servicedebug.md)|<span data-ttu-id="be8bd-130">Especifica recursos de depuração e de informações de ajuda para um serviço Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="be8bd-130">Specifies debugging and help information features for a Windows Communication Foundation (WCF) service.</span></span>|  
|[\<serviceDiscovery>](servicediscovery.md)|<span data-ttu-id="be8bd-131">Especifica a descoberta de pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="be8bd-131">Specifies the discoverability of service endpoints.</span></span>|  
|[\<serviceMetadata>](servicemetadata.md)|<span data-ttu-id="be8bd-132">Especifica a publicação de metadados de serviço e informações associadas.</span><span class="sxs-lookup"><span data-stu-id="be8bd-132">Specifies the publication of service metadata and associated information.</span></span>|  
|[\<serviceSecurityAudit>](servicesecurityaudit.md)|<span data-ttu-id="be8bd-133">Especifica as configurações que habilitam a auditoria de eventos de segurança durante operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="be8bd-133">Specifies settings that enable auditing of security events during service operations.</span></span>|  
|[\<serviceThrottling>](servicethrottling.md)|<span data-ttu-id="be8bd-134">Especifica o mecanismo de limitação de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="be8bd-134">Specifies the throttling mechanism of a WCF service.</span></span>|  
|[\<serviceTimeouts>](servicetimeouts.md)|<span data-ttu-id="be8bd-135">Especifica o tempo limite para um serviço.</span><span class="sxs-lookup"><span data-stu-id="be8bd-135">Specifies the timeout for a service.</span></span>|  
|[\<workflowRuntime>](workflowruntime.md)|<span data-ttu-id="be8bd-136">Especifica as configurações para uma instância de WorkflowRuntime para hospedar serviços WCF baseados em fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="be8bd-136">Specifies settings for an instance of WorkflowRuntime for hosting workflow-based WCF services.</span></span>|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="be8bd-137">Habilita a recuperação de informações de endereço de metadados dos cabeçalhos de mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="be8bd-137">Enables the retrieval of metadata address information from the request message headers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="be8bd-138">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="be8bd-138">Parent Elements</span></span>  
  
|<span data-ttu-id="be8bd-139">Elemento</span><span class="sxs-lookup"><span data-stu-id="be8bd-139">Element</span></span>|<span data-ttu-id="be8bd-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="be8bd-140">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors.md)|<span data-ttu-id="be8bd-141">Uma coleção de elementos de comportamento de serviço.</span><span class="sxs-lookup"><span data-stu-id="be8bd-141">A collection of service behavior elements.</span></span>|
