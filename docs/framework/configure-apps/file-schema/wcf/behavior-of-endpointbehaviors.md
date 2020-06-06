---
title: <behavior> de <endpointBehaviors>
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: 489678a5adeae3965acae90a847c4b087478354d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140803"
---
# <a name="behavior-of-endpointbehaviors"></a><span data-ttu-id="409e0-102">\<behavior> de \<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="409e0-102">\<behavior> of \<endpointBehaviors></span></span>
<span data-ttu-id="409e0-103">O `behavior` elemento contém uma coleção de configurações para o comportamento de um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="409e0-103">The `behavior` element contains a collection of settings for the behavior of an endpoint.</span></span> <span data-ttu-id="409e0-104">Cada comportamento é indexado pela sua `name`.</span><span class="sxs-lookup"><span data-stu-id="409e0-104">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="409e0-105">Os pontos de extremidade podem ser vinculados a cada comportamento por meio desse nome.</span><span class="sxs-lookup"><span data-stu-id="409e0-105">Endpoints can link to each behavior through this name.</span></span> <span data-ttu-id="409e0-106">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="409e0-106">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="409e0-107">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="409e0-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="409e0-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="409e0-108">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="String" />
    </endpointBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="409e0-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="409e0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="409e0-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="409e0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="409e0-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="409e0-111">Attributes</span></span>  
  
|<span data-ttu-id="409e0-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="409e0-112">Attribute</span></span>|<span data-ttu-id="409e0-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="409e0-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="409e0-114">name</span><span class="sxs-lookup"><span data-stu-id="409e0-114">name</span></span>|<span data-ttu-id="409e0-115">Uma cadeia de caracteres exclusiva que contém o nome da configuração do comportamento.</span><span class="sxs-lookup"><span data-stu-id="409e0-115">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="409e0-116">Esse valor é uma cadeia de caracteres definida pelo usuário que deve ser exclusiva, pois ele atua como a cadeia de caracteres de identificação para o elemento.</span><span class="sxs-lookup"><span data-stu-id="409e0-116">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="409e0-117">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="409e0-117">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="409e0-118">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="409e0-118">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="409e0-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="409e0-119">Child Elements</span></span>  
  
|<span data-ttu-id="409e0-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="409e0-120">Element</span></span>|<span data-ttu-id="409e0-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="409e0-121">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="409e0-122">Especifica as credenciais usadas para autenticar o cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="409e0-122">Specifies the credentials used to authenticate the client to a service.</span></span>|  
|[\<callbackDebug>](callbackdebug.md)|<span data-ttu-id="409e0-123">Especifica a depuração de serviço para um objeto de retorno de chamada Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="409e0-123">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>|  
|[\<callbackTimeouts>](callbacktimeouts.md)|<span data-ttu-id="409e0-124">Especifica o tempo limite para o retorno de chamada do cliente.</span><span class="sxs-lookup"><span data-stu-id="409e0-124">Specifies the timeout for the client callback.</span></span>|  
|[\<clientVia>](clientvia.md)|<span data-ttu-id="409e0-125">Especifica a rota que uma mensagem deve tomar.</span><span class="sxs-lookup"><span data-stu-id="409e0-125">Specifies the route a message should take.</span></span>|  
|[\<dataContractSerializer>](datacontractserializer.md)|<span data-ttu-id="409e0-126">Contém dados de configuração para o DataContractSerializer.</span><span class="sxs-lookup"><span data-stu-id="409e0-126">Contains configuration data for the DataContractSerializer.</span></span>|  
|[\<dispatcherSynchronization>](dispatchersynchronization.md)|<span data-ttu-id="409e0-127">Especifica um comportamento de ponto de extremidade que permite que um serviço envie respostas de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="409e0-127">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>|  
|[\<enableWebScript>](enablewebscript.md)|<span data-ttu-id="409e0-128">Habilita o comportamento do ponto de extremidade que torna possível consumir o serviço de páginas da Web do ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="409e0-128">Enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span> <span data-ttu-id="409e0-129">O comportamento só deve ser usado em conjunto com a \<webHttpBinding> associação padrão ou com o \<webMessageEncoding> elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="409e0-129">The behavior should only be used in conjunction with either the \<webHttpBinding> standard binding, or the \<webMessageEncoding> binding element.</span></span>|  
|[\<endpointDiscovery>](endpointdiscovery.md)|<span data-ttu-id="409e0-130">Especifica as várias configurações de descoberta para um ponto de extremidade, como sua descoberta, escopos e quaisquer extensões personalizadas para seus metadados.</span><span class="sxs-lookup"><span data-stu-id="409e0-130">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
|[\<soapProcessing>](soapprocessing.md)|<span data-ttu-id="409e0-131">Define o comportamento de ponto de extremidade de cliente usado para realizar marshaling de mensagens entre diferentes tipos de associação e versões de mensagem.</span><span class="sxs-lookup"><span data-stu-id="409e0-131">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>|  
|[\<synchronousReceive>](synchronousreceive-element.md)|<span data-ttu-id="409e0-132">Especifica o comportamento de tempo de execução para receber mensagens em um aplicativo de serviço ou cliente.</span><span class="sxs-lookup"><span data-stu-id="409e0-132">Specifies run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="409e0-133">Ele não tem nenhum atributo ou elemento filho.</span><span class="sxs-lookup"><span data-stu-id="409e0-133">It does not have any attributes or child elements.</span></span>|  
|[\<transactedBatching>](transactedbatching.md)|<span data-ttu-id="409e0-134">Especifica se o envio em lote de transações tem suporte para operações de recebimento.</span><span class="sxs-lookup"><span data-stu-id="409e0-134">Specifies whether transaction batching is supported for receive operations.</span></span>|  
|[\<webHttp>](webhttp.md)|<span data-ttu-id="409e0-135">Especifica o WebHttpBehavior em um ponto de extremidade por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="409e0-135">Specifies the WebHttpBehavior on an endpoint through configuration.</span></span> <span data-ttu-id="409e0-136">Esse comportamento, quando usado em conjunto com a \<webHttpBinding> associação padrão, habilita o modelo de programação da Web para um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="409e0-136">This behavior, when used in conjunction with the \<webHttpBinding> standard binding, enables the Web programming model for a WCF service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="409e0-137">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="409e0-137">Parent Elements</span></span>  
  
|<span data-ttu-id="409e0-138">Elemento</span><span class="sxs-lookup"><span data-stu-id="409e0-138">Element</span></span>|<span data-ttu-id="409e0-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="409e0-139">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|<span data-ttu-id="409e0-140">Uma coleção de elementos de comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="409e0-140">A collection of endpoint behavior elements.</span></span>|
