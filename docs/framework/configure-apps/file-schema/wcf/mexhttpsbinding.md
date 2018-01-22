---
title: '&lt;mexHttpsBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a6725741e6e0e67f3d26dc3bc1e83a57f6fcd430
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="ltmexhttpsbindinggt"></a><span data-ttu-id="3a10a-102">&lt;mexHttpsBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="3a10a-102">&lt;mexHttpsBinding&gt;</span></span>
<span data-ttu-id="3a10a-103">Especifica as configurações de uma associação usada para a troca de mensagens WS-MetadataExchange (WS-MEX) sobre HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3a10a-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
 <span data-ttu-id="3a10a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3a10a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3a10a-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="3a10a-105">\<bindings></span></span>  
<span data-ttu-id="3a10a-106">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="3a10a-106">\<mexHttpsBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a10a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a10a-107">Syntax</span></span>  
  
```xml  
<mexHttpsBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan">  
   </binding>  
</mexHttpsBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a10a-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3a10a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3a10a-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3a10a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a10a-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="3a10a-110">Attributes</span></span>  
  
|<span data-ttu-id="3a10a-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="3a10a-111">Attribute</span></span>|<span data-ttu-id="3a10a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a10a-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="3a10a-113">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de fechamento concluir.</span><span class="sxs-lookup"><span data-stu-id="3a10a-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="3a10a-114">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="3a10a-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3a10a-115">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="3a10a-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="3a10a-116">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="3a10a-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="3a10a-117">Esse valor deve ser exclusivo, porque ele é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="3a10a-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="3a10a-118">Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="3a10a-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="3a10a-119">Além disso, esse nome é exclusivo entre as associações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="3a10a-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="3a10a-120">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="3a10a-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="3a10a-121">Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="3a10a-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="3a10a-122">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de abertura concluir.</span><span class="sxs-lookup"><span data-stu-id="3a10a-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="3a10a-123">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="3a10a-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3a10a-124">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="3a10a-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="3a10a-125">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento concluir.</span><span class="sxs-lookup"><span data-stu-id="3a10a-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="3a10a-126">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="3a10a-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3a10a-127">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="3a10a-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="3a10a-128">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio concluir.</span><span class="sxs-lookup"><span data-stu-id="3a10a-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="3a10a-129">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="3a10a-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3a10a-130">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="3a10a-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a10a-131">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3a10a-131">Child Elements</span></span>  
 <span data-ttu-id="3a10a-132">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3a10a-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a10a-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3a10a-133">Parent Elements</span></span>  
  
|<span data-ttu-id="3a10a-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="3a10a-134">Element</span></span>|<span data-ttu-id="3a10a-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a10a-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a10a-136">\<bindings></span><span class="sxs-lookup"><span data-stu-id="3a10a-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="3a10a-137">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="3a10a-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a10a-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a10a-138">Remarks</span></span>  
 <span data-ttu-id="3a10a-139">Essa associação é essencialmente um `WSHttpBinding` de associação que dá suporte à segurança em nível de transporte usando certificados.</span><span class="sxs-lookup"><span data-stu-id="3a10a-139">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="3a10a-140">Para obter mais informações sobre como configurar e usar esse um ponto de extremidade de metadados, consulte [como: configurar uma associação de personalizado WS-Metadata Exchange](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [como: recuperar metadados sobre uma associação não MEX](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)e o exemplo [personalizado proteger metadados de ponto de extremidade](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="3a10a-140">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a10a-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a10a-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>  
 <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>  
 [<span data-ttu-id="3a10a-142">Como publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="3a10a-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="3a10a-143">Publicando e recuperando metadados através de uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="3a10a-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="3a10a-144">Como configurar uma associação personalizada do WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="3a10a-144">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)  
 [<span data-ttu-id="3a10a-145">Como recuperar metadados por meio de uma associação não MEX</span><span class="sxs-lookup"><span data-stu-id="3a10a-145">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)  
 [<span data-ttu-id="3a10a-146">Ponto de extremidade de metadados seguros personalizado</span><span class="sxs-lookup"><span data-stu-id="3a10a-146">Custom Secure Metadata Endpoint</span></span>](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)  
 [<span data-ttu-id="3a10a-147">Metadados</span><span class="sxs-lookup"><span data-stu-id="3a10a-147">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="3a10a-148">Associações</span><span class="sxs-lookup"><span data-stu-id="3a10a-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="3a10a-149">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="3a10a-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="3a10a-150">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="3a10a-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="3a10a-151">\<binding></span><span class="sxs-lookup"><span data-stu-id="3a10a-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
