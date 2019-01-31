---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: f9f6186cc88f2cc0fed8404f9e4d5776d41e2818
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55284851"
---
# <a name="mexnamedpipebinding"></a><span data-ttu-id="7edaf-101">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="7edaf-101">\<mexNamedPipeBinding></span></span>
<span data-ttu-id="7edaf-102">Especifica as configurações para uma associação usada para a troca de mensagens WS-MetadataExchange (WS-MEX) sobre pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="7edaf-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
 <span data-ttu-id="7edaf-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7edaf-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="7edaf-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="7edaf-104">\<bindings></span></span>  
<span data-ttu-id="7edaf-105">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="7edaf-105">\<mexNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7edaf-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7edaf-106">Syntax</span></span>  
  
```xml  
<mexNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7edaf-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7edaf-107">Attributes and Elements</span></span>  
 <span data-ttu-id="7edaf-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7edaf-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7edaf-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="7edaf-109">Attributes</span></span>  
  
|<span data-ttu-id="7edaf-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="7edaf-110">Attribute</span></span>|<span data-ttu-id="7edaf-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="7edaf-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="7edaf-112">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação close.</span><span class="sxs-lookup"><span data-stu-id="7edaf-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="7edaf-113">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7edaf-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7edaf-114">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="7edaf-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="7edaf-115">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="7edaf-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="7edaf-116">Esse valor deve ser exclusivo porque ele é usado como identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="7edaf-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="7edaf-117">Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="7edaf-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="7edaf-118">Além disso, esse nome é exclusivo entre as associações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="7edaf-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="7edaf-119">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="7edaf-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7edaf-120">Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7edaf-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="7edaf-121">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação open.</span><span class="sxs-lookup"><span data-stu-id="7edaf-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="7edaf-122">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7edaf-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7edaf-123">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="7edaf-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="7edaf-124">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento ser concluída.</span><span class="sxs-lookup"><span data-stu-id="7edaf-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="7edaf-125">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7edaf-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7edaf-126">O padrão é 10:00:00.</span><span class="sxs-lookup"><span data-stu-id="7edaf-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="7edaf-127">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio ser concluída.</span><span class="sxs-lookup"><span data-stu-id="7edaf-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="7edaf-128">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7edaf-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7edaf-129">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="7edaf-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7edaf-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7edaf-130">Child Elements</span></span>  
 <span data-ttu-id="7edaf-131">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7edaf-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7edaf-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7edaf-132">Parent Elements</span></span>  
  
|<span data-ttu-id="7edaf-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="7edaf-133">Element</span></span>|<span data-ttu-id="7edaf-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="7edaf-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7edaf-135">\<bindings></span><span class="sxs-lookup"><span data-stu-id="7edaf-135">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="7edaf-136">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="7edaf-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7edaf-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7edaf-137">See also</span></span>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="7edaf-138">Como: Publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="7edaf-138">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="7edaf-139">Publicando e recuperando metadados através de uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="7edaf-139">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="7edaf-140">Metadados</span><span class="sxs-lookup"><span data-stu-id="7edaf-140">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="7edaf-141">Associações</span><span class="sxs-lookup"><span data-stu-id="7edaf-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="7edaf-142">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="7edaf-142">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7edaf-143">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="7edaf-143">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7edaf-144">\<binding></span><span class="sxs-lookup"><span data-stu-id="7edaf-144">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
