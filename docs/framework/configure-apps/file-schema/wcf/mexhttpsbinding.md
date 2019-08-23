---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 30d1aa27ce29b6aa4091c3e7be05746ad462102a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931267"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="06ce7-101">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="06ce7-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="06ce7-102">Especifica as configurações para uma associação usada para a troca de mensagens WS-MetadataExchange (WS-MEX) por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="06ce7-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
 <span data-ttu-id="06ce7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="06ce7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="06ce7-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="06ce7-104">\<bindings></span></span>  
<span data-ttu-id="06ce7-105">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="06ce7-105">\<mexHttpsBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06ce7-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06ce7-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06ce7-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="06ce7-107">Attributes and Elements</span></span>  
 <span data-ttu-id="06ce7-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="06ce7-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06ce7-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="06ce7-109">Attributes</span></span>  
  
|<span data-ttu-id="06ce7-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="06ce7-110">Attribute</span></span>|<span data-ttu-id="06ce7-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="06ce7-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="06ce7-112">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="06ce7-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="06ce7-113">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="06ce7-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="06ce7-114">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="06ce7-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="06ce7-115">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="06ce7-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="06ce7-116">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="06ce7-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="06ce7-117">Cada associação tem um `name` atributo `namespace` e que, juntos, o identifica exclusivamente nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="06ce7-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="06ce7-118">Além disso, esse nome é exclusivo entre associações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="06ce7-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="06ce7-119">A partir do, não é necessário que as associações e os comportamentos tenham um nome. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06ce7-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="06ce7-120">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="06ce7-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="06ce7-121">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="06ce7-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="06ce7-122">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="06ce7-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="06ce7-123">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="06ce7-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="06ce7-124">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="06ce7-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="06ce7-125">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="06ce7-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="06ce7-126">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="06ce7-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="06ce7-127">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="06ce7-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="06ce7-128">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="06ce7-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="06ce7-129">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="06ce7-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06ce7-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="06ce7-130">Child Elements</span></span>  
 <span data-ttu-id="06ce7-131">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="06ce7-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="06ce7-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="06ce7-132">Parent Elements</span></span>  
  
|<span data-ttu-id="06ce7-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="06ce7-133">Element</span></span>|<span data-ttu-id="06ce7-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="06ce7-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06ce7-135">\<bindings></span><span class="sxs-lookup"><span data-stu-id="06ce7-135">\<bindings></span></span>](bindings.md)|<span data-ttu-id="06ce7-136">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="06ce7-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06ce7-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="06ce7-137">Remarks</span></span>  
 <span data-ttu-id="06ce7-138">Essa associação é essencialmente uma `WSHttpBinding` associação que dá suporte à segurança em nível de transporte usando certificados.</span><span class="sxs-lookup"><span data-stu-id="06ce7-138">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="06ce7-139">Para obter mais informações sobre como configurar e usar esse ponto de extremidade [de metadados, consulte Como: Configurar uma associação](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)de troca personalizada de WS- [Metadata, como: Recuperar metadados em uma associação](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)não MEX e o ponto de extremidade de [metadados seguro personalizado](../../../wcf/samples/custom-secure-metadata-endpoint.md)de exemplo.</span><span class="sxs-lookup"><span data-stu-id="06ce7-139">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06ce7-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06ce7-140">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="06ce7-141">Como: Publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="06ce7-141">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="06ce7-142">Publicando e recuperando metadados através de uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="06ce7-142">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="06ce7-143">Como: Configurar uma associação de WS-Metadata Exchange personalizada</span><span class="sxs-lookup"><span data-stu-id="06ce7-143">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="06ce7-144">Como: Recuperar metadados em uma associação não MEX</span><span class="sxs-lookup"><span data-stu-id="06ce7-144">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="06ce7-145">Ponto de extremidade de metadados seguros personalizado</span><span class="sxs-lookup"><span data-stu-id="06ce7-145">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="06ce7-146">Metadados</span><span class="sxs-lookup"><span data-stu-id="06ce7-146">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="06ce7-147">Associações</span><span class="sxs-lookup"><span data-stu-id="06ce7-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="06ce7-148">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="06ce7-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="06ce7-149">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="06ce7-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="06ce7-150">\<binding></span><span class="sxs-lookup"><span data-stu-id="06ce7-150">\<binding></span></span>](../../../misc/binding.md)
