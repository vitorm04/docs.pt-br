---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: 0d0904c02e31def1b5264bec9f61eac0c9a8e964
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931226"
---
# <a name="mexnamedpipebinding"></a><span data-ttu-id="9766e-101">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="9766e-101">\<mexNamedPipeBinding></span></span>
<span data-ttu-id="9766e-102">Especifica as configurações para uma associação usada para a troca de mensagens WS-MetadataExchange (WS-MEX) sobre o pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="9766e-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
 <span data-ttu-id="9766e-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9766e-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="9766e-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="9766e-104">\<bindings></span></span>  
<span data-ttu-id="9766e-105">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="9766e-105">\<mexNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9766e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9766e-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9766e-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9766e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="9766e-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9766e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9766e-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="9766e-109">Attributes</span></span>  
  
|<span data-ttu-id="9766e-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="9766e-110">Attribute</span></span>|<span data-ttu-id="9766e-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="9766e-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="9766e-112">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="9766e-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="9766e-113">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9766e-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9766e-114">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9766e-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="9766e-115">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="9766e-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="9766e-116">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="9766e-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="9766e-117">Cada associação tem um `name` atributo `namespace` e que, juntos, o identifica exclusivamente nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="9766e-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="9766e-118">Além disso, esse nome é exclusivo entre associações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="9766e-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="9766e-119">A partir do, não é necessário que as associações e os comportamentos tenham um nome. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9766e-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="9766e-120">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="9766e-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="9766e-121">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="9766e-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="9766e-122">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9766e-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9766e-123">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9766e-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="9766e-124">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="9766e-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="9766e-125">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9766e-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9766e-126">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="9766e-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="9766e-127">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="9766e-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="9766e-128">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="9766e-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9766e-129">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="9766e-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9766e-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9766e-130">Child Elements</span></span>  
 <span data-ttu-id="9766e-131">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9766e-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9766e-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9766e-132">Parent Elements</span></span>  
  
|<span data-ttu-id="9766e-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="9766e-133">Element</span></span>|<span data-ttu-id="9766e-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="9766e-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9766e-135">\<bindings></span><span class="sxs-lookup"><span data-stu-id="9766e-135">\<bindings></span></span>](bindings.md)|<span data-ttu-id="9766e-136">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="9766e-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9766e-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9766e-137">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="9766e-138">Como: Publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="9766e-138">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="9766e-139">Publicando e recuperando metadados através de uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="9766e-139">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="9766e-140">Metadados</span><span class="sxs-lookup"><span data-stu-id="9766e-140">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="9766e-141">Associações</span><span class="sxs-lookup"><span data-stu-id="9766e-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9766e-142">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="9766e-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9766e-143">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="9766e-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9766e-144">\<binding></span><span class="sxs-lookup"><span data-stu-id="9766e-144">\<binding></span></span>](../../../misc/binding.md)
