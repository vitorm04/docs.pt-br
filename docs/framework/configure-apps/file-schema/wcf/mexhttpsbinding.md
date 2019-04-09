---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 4e96c28ac9b372092d06538d24d165dde6c5fe48
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203126"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="bef73-101">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="bef73-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="bef73-102">Especifica as configurações para uma associação usada para a troca de mensagens WS-MetadataExchange (WS-MEX) sobre HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bef73-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
 <span data-ttu-id="bef73-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bef73-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="bef73-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="bef73-104">\<bindings></span></span>  
<span data-ttu-id="bef73-105">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="bef73-105">\<mexHttpsBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bef73-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bef73-106">Syntax</span></span>  
  
```xml  
<mexHttpsBinding>
  <binding closeTimeout="TimeSpan"
            name="string"
            openTimeout="TimeSpan"
            receiveTimeout="TimeSpan"
            sendTimeout="TimeSpan">
  </binding>
</mexHttpsBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bef73-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bef73-107">Attributes and Elements</span></span>  
 <span data-ttu-id="bef73-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bef73-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bef73-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="bef73-109">Attributes</span></span>  
  
|<span data-ttu-id="bef73-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="bef73-110">Attribute</span></span>|<span data-ttu-id="bef73-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="bef73-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="bef73-112">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação close.</span><span class="sxs-lookup"><span data-stu-id="bef73-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="bef73-113">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bef73-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bef73-114">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="bef73-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="bef73-115">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="bef73-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="bef73-116">Esse valor deve ser exclusivo porque ele é usado como identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="bef73-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="bef73-117">Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="bef73-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="bef73-118">Além disso, esse nome é exclusivo entre as associações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="bef73-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="bef73-119">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="bef73-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="bef73-120">Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="bef73-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="bef73-121">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação open.</span><span class="sxs-lookup"><span data-stu-id="bef73-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="bef73-122">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bef73-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bef73-123">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="bef73-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="bef73-124">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento ser concluída.</span><span class="sxs-lookup"><span data-stu-id="bef73-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="bef73-125">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bef73-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bef73-126">O padrão é 10:00:00.</span><span class="sxs-lookup"><span data-stu-id="bef73-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="bef73-127">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio ser concluída.</span><span class="sxs-lookup"><span data-stu-id="bef73-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="bef73-128">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bef73-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bef73-129">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="bef73-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bef73-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bef73-130">Child Elements</span></span>  
 <span data-ttu-id="bef73-131">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="bef73-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bef73-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bef73-132">Parent Elements</span></span>  
  
|<span data-ttu-id="bef73-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="bef73-133">Element</span></span>|<span data-ttu-id="bef73-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="bef73-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bef73-135">\<bindings></span><span class="sxs-lookup"><span data-stu-id="bef73-135">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="bef73-136">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="bef73-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bef73-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="bef73-137">Remarks</span></span>  
 <span data-ttu-id="bef73-138">Essa associação é essencialmente um `WSHttpBinding` associação que dá suporte à segurança em nível de transporte usando certificados.</span><span class="sxs-lookup"><span data-stu-id="bef73-138">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="bef73-139">Para obter mais informações sobre como configurar e usar tal um ponto de extremidade de metadados, consulte [como: Configurar um personalizado WS-Metadata Exchange associação](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [como: Recuperar metadados através de uma associação não MEX](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)e o exemplo [ponto de extremidade do personalizado proteger metadados](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="bef73-139">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bef73-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bef73-140">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="bef73-141">Como: publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="bef73-141">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="bef73-142">Publicando e recuperando metadados através de uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="bef73-142">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="bef73-143">Como: configurar uma associação personalizada do WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="bef73-143">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="bef73-144">Como: recuperar metadados através de uma associação não MEX</span><span class="sxs-lookup"><span data-stu-id="bef73-144">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="bef73-145">Ponto de extremidade de metadados seguros personalizados</span><span class="sxs-lookup"><span data-stu-id="bef73-145">Custom Secure Metadata Endpoint</span></span>](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="bef73-146">Metadados</span><span class="sxs-lookup"><span data-stu-id="bef73-146">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="bef73-147">Associações</span><span class="sxs-lookup"><span data-stu-id="bef73-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="bef73-148">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="bef73-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="bef73-149">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="bef73-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="bef73-150">\<binding></span><span class="sxs-lookup"><span data-stu-id="bef73-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
