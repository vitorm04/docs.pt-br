---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 8a8145bbfcb3eefb06d159d834232d94166fa6dd
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736712"
---
# <a name="mexhttpbinding"></a><span data-ttu-id="80cfb-101">\<mexHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="80cfb-101">\<mexHttpBinding></span></span>
<span data-ttu-id="80cfb-102">Especifica as configurações para uma associação usada para a troca de mensagens WS-MetadataExchange (WS-MEX) sobre HTTP.</span><span class="sxs-lookup"><span data-stu-id="80cfb-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
<span data-ttu-id="80cfb-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="80cfb-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="80cfb-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="80cfb-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="80cfb-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="80cfb-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="80cfb-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="80cfb-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80cfb-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80cfb-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80cfb-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="80cfb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="80cfb-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="80cfb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80cfb-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="80cfb-110">Attributes</span></span>  
  
|<span data-ttu-id="80cfb-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="80cfb-111">Attribute</span></span>|<span data-ttu-id="80cfb-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="80cfb-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="80cfb-113">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="80cfb-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="80cfb-114">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="80cfb-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="80cfb-115">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="80cfb-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="80cfb-116">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="80cfb-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="80cfb-117">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="80cfb-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="80cfb-118">Cada associação tem um atributo `name` e `namespace` que, juntos, o identificam exclusivamente nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="80cfb-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="80cfb-119">Além disso, esse nome é exclusivo entre associações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="80cfb-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="80cfb-120">A partir do [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="80cfb-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="80cfb-121">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="80cfb-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="80cfb-122">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="80cfb-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="80cfb-123">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="80cfb-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="80cfb-124">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="80cfb-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="80cfb-125">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="80cfb-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="80cfb-126">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="80cfb-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="80cfb-127">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="80cfb-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="80cfb-128">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="80cfb-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="80cfb-129">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="80cfb-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="80cfb-130">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="80cfb-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80cfb-131">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="80cfb-131">Child Elements</span></span>  
 <span data-ttu-id="80cfb-132">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="80cfb-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="80cfb-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="80cfb-133">Parent Elements</span></span>  
  
|<span data-ttu-id="80cfb-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="80cfb-134">Element</span></span>|<span data-ttu-id="80cfb-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="80cfb-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80cfb-136">\<bindings ></span><span class="sxs-lookup"><span data-stu-id="80cfb-136">\<bindings></span></span>](bindings.md)|<span data-ttu-id="80cfb-137">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="80cfb-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80cfb-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="80cfb-138">Remarks</span></span>  
 <span data-ttu-id="80cfb-139">Essa associação é essencialmente uma associação de `WSHttpBinding` com segurança desabilitada.</span><span class="sxs-lookup"><span data-stu-id="80cfb-139">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="80cfb-140">Ele dá suporte à maioria das solicitações de metadados.</span><span class="sxs-lookup"><span data-stu-id="80cfb-140">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80cfb-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80cfb-141">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="80cfb-142">Como publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="80cfb-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="80cfb-143">Publicando e recuperando metadados através de uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="80cfb-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="80cfb-144">Metadados</span><span class="sxs-lookup"><span data-stu-id="80cfb-144">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="80cfb-145">Associações</span><span class="sxs-lookup"><span data-stu-id="80cfb-145">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="80cfb-146">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="80cfb-146">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="80cfb-147">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="80cfb-147">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="80cfb-148">\<binding ></span><span class="sxs-lookup"><span data-stu-id="80cfb-148">\<binding></span></span>](bindings.md)
