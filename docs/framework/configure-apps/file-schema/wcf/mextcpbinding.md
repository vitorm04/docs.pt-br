---
title: '&lt;mexTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: a69f0af60d3f6723285ceb239a86775c9a1b510f
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147168"
---
# <a name="ltmextcpbindinggt"></a><span data-ttu-id="72d53-102">&lt;mexTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="72d53-102">&lt;mexTcpBinding&gt;</span></span>
<span data-ttu-id="72d53-103">Especifica as configurações para uma associação usada para a troca de mensagens WS-MetadataExchange (WS-MEX) sobre TCP.</span><span class="sxs-lookup"><span data-stu-id="72d53-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
 <span data-ttu-id="72d53-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="72d53-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="72d53-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="72d53-105">\<bindings></span></span>  
<span data-ttu-id="72d53-106">\<mexTcpBinding></span><span class="sxs-lookup"><span data-stu-id="72d53-106">\<mexTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72d53-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72d53-107">Syntax</span></span>  
  
```xml  
<mexTcpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72d53-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="72d53-108">Attributes and Elements</span></span>  
 <span data-ttu-id="72d53-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="72d53-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72d53-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="72d53-110">Attributes</span></span>  
  
|<span data-ttu-id="72d53-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="72d53-111">Attribute</span></span>|<span data-ttu-id="72d53-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="72d53-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="72d53-113">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação close.</span><span class="sxs-lookup"><span data-stu-id="72d53-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="72d53-114">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="72d53-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="72d53-115">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="72d53-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="72d53-116">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="72d53-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="72d53-117">Esse valor deve ser exclusivo porque ele é usado como identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="72d53-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="72d53-118">Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="72d53-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="72d53-119">Além disso, esse nome é exclusivo entre as associações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="72d53-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="72d53-120">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="72d53-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="72d53-121">Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="72d53-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="72d53-122">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação open.</span><span class="sxs-lookup"><span data-stu-id="72d53-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="72d53-123">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="72d53-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="72d53-124">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="72d53-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="72d53-125">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento ser concluída.</span><span class="sxs-lookup"><span data-stu-id="72d53-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="72d53-126">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="72d53-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="72d53-127">O padrão é 10:00:00.</span><span class="sxs-lookup"><span data-stu-id="72d53-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="72d53-128">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio ser concluída.</span><span class="sxs-lookup"><span data-stu-id="72d53-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="72d53-129">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="72d53-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="72d53-130">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="72d53-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72d53-131">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="72d53-131">Child Elements</span></span>  
 <span data-ttu-id="72d53-132">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="72d53-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="72d53-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="72d53-133">Parent Elements</span></span>  
  
|<span data-ttu-id="72d53-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="72d53-134">Element</span></span>|<span data-ttu-id="72d53-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="72d53-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72d53-136">\<associações ></span><span class="sxs-lookup"><span data-stu-id="72d53-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="72d53-137">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="72d53-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="72d53-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72d53-138">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MexTcpBindingElement>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>  
 [<span data-ttu-id="72d53-139">Como: Publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="72d53-139">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="72d53-140">Publicando e recuperando metadados através de uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="72d53-140">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="72d53-141">Metadados</span><span class="sxs-lookup"><span data-stu-id="72d53-141">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="72d53-142">Associações</span><span class="sxs-lookup"><span data-stu-id="72d53-142">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="72d53-143">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="72d53-143">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="72d53-144">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="72d53-144">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="72d53-145">\<associação ></span><span class="sxs-lookup"><span data-stu-id="72d53-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
