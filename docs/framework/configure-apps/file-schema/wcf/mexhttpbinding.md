---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: c6ff5b2cfee1d55b9399b97f3b3397e6bbf8eca2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400235"
---
# <a name="mexhttpbinding"></a><span data-ttu-id="05242-101">\<mexHttpBinding></span><span class="sxs-lookup"><span data-stu-id="05242-101">\<mexHttpBinding></span></span>
<span data-ttu-id="05242-102">Especifica as configurações para uma associação usada para a troca de mensagens WS-MetadataExchange (WS-MEX) sobre HTTP.</span><span class="sxs-lookup"><span data-stu-id="05242-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
<span data-ttu-id="05242-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="05242-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="05242-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="05242-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="05242-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="05242-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="05242-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> mexHttpBinding**</span><span class="sxs-lookup"><span data-stu-id="05242-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05242-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="05242-107">Syntax</span></span>  
  
```xml  
<mexHttpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05242-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="05242-108">Attributes and Elements</span></span>  
 <span data-ttu-id="05242-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="05242-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05242-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="05242-110">Attributes</span></span>  
  
|<span data-ttu-id="05242-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="05242-111">Attribute</span></span>|<span data-ttu-id="05242-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="05242-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="05242-113">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="05242-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="05242-114">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="05242-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="05242-115">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="05242-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="05242-116">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="05242-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="05242-117">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="05242-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="05242-118">Cada associação tem um `name` atributo `namespace` e que, juntos, o identifica exclusivamente nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="05242-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="05242-119">Além disso, esse nome é exclusivo entre associações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="05242-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="05242-120">A partir do, não é necessário que as associações e os comportamentos tenham um nome. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05242-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="05242-121">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="05242-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="05242-122">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="05242-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="05242-123">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="05242-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="05242-124">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="05242-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="05242-125">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="05242-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="05242-126">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="05242-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="05242-127">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="05242-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="05242-128">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="05242-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="05242-129">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="05242-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="05242-130">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="05242-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05242-131">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="05242-131">Child Elements</span></span>  
 <span data-ttu-id="05242-132">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="05242-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05242-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="05242-133">Parent Elements</span></span>  
  
|<span data-ttu-id="05242-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="05242-134">Element</span></span>|<span data-ttu-id="05242-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="05242-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05242-136">\<bindings></span><span class="sxs-lookup"><span data-stu-id="05242-136">\<bindings></span></span>](bindings.md)|<span data-ttu-id="05242-137">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="05242-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05242-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="05242-138">Remarks</span></span>  
 <span data-ttu-id="05242-139">Essa associação é essencialmente uma `WSHttpBinding` associação com segurança desabilitada.</span><span class="sxs-lookup"><span data-stu-id="05242-139">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="05242-140">Ele dá suporte à maioria das solicitações de metadados.</span><span class="sxs-lookup"><span data-stu-id="05242-140">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05242-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05242-141">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="05242-142">Como: Publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="05242-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="05242-143">Publicando e recuperando metadados através de uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="05242-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="05242-144">Metadados</span><span class="sxs-lookup"><span data-stu-id="05242-144">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="05242-145">Associações</span><span class="sxs-lookup"><span data-stu-id="05242-145">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="05242-146">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="05242-146">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="05242-147">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="05242-147">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="05242-148">\<binding></span><span class="sxs-lookup"><span data-stu-id="05242-148">\<binding></span></span>](../../../misc/binding.md)
