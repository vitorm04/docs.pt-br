---
title: <mexTcpBinding>
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: 491597da508487c3988b284c84411123d434fe72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932529"
---
# <a name="mextcpbinding"></a><span data-ttu-id="b3574-101">\<mexTcpBinding></span><span class="sxs-lookup"><span data-stu-id="b3574-101">\<mexTcpBinding></span></span>
<span data-ttu-id="b3574-102">Especifica as configurações para uma associação usada para a troca de mensagens WS-MetadataExchange (WS-MEX) sobre TCP.</span><span class="sxs-lookup"><span data-stu-id="b3574-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
 <span data-ttu-id="b3574-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b3574-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="b3574-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="b3574-104">\<bindings></span></span>  
<span data-ttu-id="b3574-105">\<mexTcpBinding></span><span class="sxs-lookup"><span data-stu-id="b3574-105">\<mexTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3574-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3574-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3574-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b3574-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b3574-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b3574-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3574-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="b3574-109">Attributes</span></span>  
  
|<span data-ttu-id="b3574-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="b3574-110">Attribute</span></span>|<span data-ttu-id="b3574-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="b3574-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="b3574-112">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="b3574-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="b3574-113">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b3574-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b3574-114">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b3574-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="b3574-115">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="b3574-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="b3574-116">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="b3574-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="b3574-117">Cada associação tem um `name` atributo `namespace` e que, juntos, o identifica exclusivamente nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="b3574-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="b3574-118">Além disso, esse nome é exclusivo entre associações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="b3574-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="b3574-119">A partir do, não é necessário que as associações e os comportamentos tenham um nome. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3574-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="b3574-120">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="b3574-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="b3574-121">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="b3574-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="b3574-122">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b3574-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b3574-123">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b3574-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="b3574-124">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="b3574-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="b3574-125">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b3574-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b3574-126">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="b3574-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="b3574-127">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="b3574-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="b3574-128">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b3574-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b3574-129">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b3574-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b3574-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b3574-130">Child Elements</span></span>  
 <span data-ttu-id="b3574-131">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b3574-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b3574-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b3574-132">Parent Elements</span></span>  
  
|<span data-ttu-id="b3574-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="b3574-133">Element</span></span>|<span data-ttu-id="b3574-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="b3574-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3574-135">\<bindings></span><span class="sxs-lookup"><span data-stu-id="b3574-135">\<bindings></span></span>](bindings.md)|<span data-ttu-id="b3574-136">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="b3574-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b3574-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3574-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.MexTcpBindingElement>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>
- [<span data-ttu-id="b3574-138">Como: Publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="b3574-138">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="b3574-139">Publicando e recuperando metadados através de uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="b3574-139">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="b3574-140">Metadados</span><span class="sxs-lookup"><span data-stu-id="b3574-140">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="b3574-141">Associações</span><span class="sxs-lookup"><span data-stu-id="b3574-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b3574-142">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="b3574-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b3574-143">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="b3574-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b3574-144">\<binding></span><span class="sxs-lookup"><span data-stu-id="b3574-144">\<binding></span></span>](../../../misc/binding.md)
