---
title: '&lt;mexHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 5822064af711c1a2c16bddfd142f415541b9604d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748806"
---
# <a name="ltmexhttpbindinggt"></a><span data-ttu-id="aa39b-102">&lt;mexHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="aa39b-102">&lt;mexHttpBinding&gt;</span></span>
<span data-ttu-id="aa39b-103">Especifica as configurações de uma associação usada para a troca de mensagens WS-MetadataExchange (WS-MEX) sobre HTTP.</span><span class="sxs-lookup"><span data-stu-id="aa39b-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
 <span data-ttu-id="aa39b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="aa39b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="aa39b-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="aa39b-105">\<bindings></span></span>  
<span data-ttu-id="aa39b-106">\<mexHttpBinding></span><span class="sxs-lookup"><span data-stu-id="aa39b-106">\<mexHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa39b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa39b-107">Syntax</span></span>  
  
```xml  
<mexHttpBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan">  
   </binding>  
</mexHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa39b-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="aa39b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="aa39b-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="aa39b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa39b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="aa39b-110">Attributes</span></span>  
  
|<span data-ttu-id="aa39b-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="aa39b-111">Attribute</span></span>|<span data-ttu-id="aa39b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa39b-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="aa39b-113">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de fechamento concluir.</span><span class="sxs-lookup"><span data-stu-id="aa39b-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="aa39b-114">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="aa39b-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="aa39b-115">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="aa39b-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="aa39b-116">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="aa39b-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="aa39b-117">Esse valor deve ser exclusivo, porque ele é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="aa39b-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="aa39b-118">Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="aa39b-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="aa39b-119">Além disso, esse nome é exclusivo entre as associações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="aa39b-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="aa39b-120">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="aa39b-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="aa39b-121">Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="aa39b-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="aa39b-122">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de abertura concluir.</span><span class="sxs-lookup"><span data-stu-id="aa39b-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="aa39b-123">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="aa39b-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="aa39b-124">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="aa39b-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="aa39b-125">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento concluir.</span><span class="sxs-lookup"><span data-stu-id="aa39b-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="aa39b-126">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="aa39b-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="aa39b-127">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="aa39b-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="aa39b-128">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio concluir.</span><span class="sxs-lookup"><span data-stu-id="aa39b-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="aa39b-129">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="aa39b-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="aa39b-130">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="aa39b-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa39b-131">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="aa39b-131">Child Elements</span></span>  
 <span data-ttu-id="aa39b-132">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="aa39b-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aa39b-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="aa39b-133">Parent Elements</span></span>  
  
|<span data-ttu-id="aa39b-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="aa39b-134">Element</span></span>|<span data-ttu-id="aa39b-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa39b-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa39b-136">\<associações ></span><span class="sxs-lookup"><span data-stu-id="aa39b-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="aa39b-137">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="aa39b-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa39b-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa39b-138">Remarks</span></span>  
 <span data-ttu-id="aa39b-139">Essa associação é essencialmente um `WSHttpBinding` associação com segurança desativada.</span><span class="sxs-lookup"><span data-stu-id="aa39b-139">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="aa39b-140">Ele dá suporte à maioria das solicitações de metadados.</span><span class="sxs-lookup"><span data-stu-id="aa39b-140">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa39b-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa39b-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>  
 <xref:System.ServiceModel.Configuration.MexHttpBindingElement>  
 [<span data-ttu-id="aa39b-142">Como publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="aa39b-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="aa39b-143">Publicando e recuperando metadados através de uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="aa39b-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="aa39b-144">Metadados</span><span class="sxs-lookup"><span data-stu-id="aa39b-144">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="aa39b-145">Associações</span><span class="sxs-lookup"><span data-stu-id="aa39b-145">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="aa39b-146">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="aa39b-146">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="aa39b-147">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="aa39b-147">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="aa39b-148">\<associação ></span><span class="sxs-lookup"><span data-stu-id="aa39b-148">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
