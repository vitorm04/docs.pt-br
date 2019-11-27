---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 924d68dd828622b74c5e424a695f80874391b453
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430343"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="57279-101">\<mexHttpsBinding ></span><span class="sxs-lookup"><span data-stu-id="57279-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="57279-102">Especifica as configurações para uma associação usada para a troca de mensagens WS-MetadataExchange (WS-MEX) por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="57279-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
<span data-ttu-id="57279-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="57279-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="57279-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="57279-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="57279-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="57279-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="57279-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpsBinding >**</span><span class="sxs-lookup"><span data-stu-id="57279-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57279-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57279-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57279-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="57279-108">Attributes and Elements</span></span>  
 <span data-ttu-id="57279-109">As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.</span><span class="sxs-lookup"><span data-stu-id="57279-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57279-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="57279-110">Attributes</span></span>  
  
|<span data-ttu-id="57279-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="57279-111">Attribute</span></span>|<span data-ttu-id="57279-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="57279-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="57279-113">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="57279-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="57279-114">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="57279-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="57279-115">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="57279-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="57279-116">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="57279-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="57279-117">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="57279-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="57279-118">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="57279-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="57279-119">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="57279-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="57279-120">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="57279-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="57279-121">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="57279-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="57279-122">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="57279-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="57279-123">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="57279-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="57279-124">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="57279-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="57279-125">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="57279-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="57279-126">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="57279-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="57279-127">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="57279-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="57279-128">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="57279-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57279-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="57279-129">Child Elements</span></span>  
 <span data-ttu-id="57279-130">None.</span><span class="sxs-lookup"><span data-stu-id="57279-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="57279-131">Elementos Pai</span><span class="sxs-lookup"><span data-stu-id="57279-131">Parent Elements</span></span>  
  
|<span data-ttu-id="57279-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="57279-132">Element</span></span>|<span data-ttu-id="57279-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="57279-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57279-134">associações de \<></span><span class="sxs-lookup"><span data-stu-id="57279-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="57279-135">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="57279-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57279-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="57279-136">Remarks</span></span>  
 <span data-ttu-id="57279-137">Essa associação é essencialmente uma associação `WSHttpBinding` que dá suporte à segurança em nível de transporte usando certificados.</span><span class="sxs-lookup"><span data-stu-id="57279-137">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="57279-138">Para obter mais informações sobre como configurar e usar esse ponto de extremidade de metadados, consulte [como: configurar uma associação de WS-Metadata Exchange personalizada](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [como recuperar metadados em uma associação não MEX](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)e o [ponto de extremidade de metadados seguro personalizado](../../../wcf/samples/custom-secure-metadata-endpoint.md)de exemplo.</span><span class="sxs-lookup"><span data-stu-id="57279-138">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57279-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57279-139">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="57279-140">Como publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="57279-140">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="57279-141">Publicando e recuperando metadados através de uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="57279-141">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="57279-142">Como configurar uma associação personalizada do WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="57279-142">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="57279-143">Como recuperar metadados por meio de uma associação não MEX</span><span class="sxs-lookup"><span data-stu-id="57279-143">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="57279-144">Ponto de extremidade de metadados seguros personalizado</span><span class="sxs-lookup"><span data-stu-id="57279-144">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="57279-145">Metadados</span><span class="sxs-lookup"><span data-stu-id="57279-145">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="57279-146">Associações</span><span class="sxs-lookup"><span data-stu-id="57279-146">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="57279-147">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="57279-147">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="57279-148">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="57279-148">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="57279-149">> de associação de \<</span><span class="sxs-lookup"><span data-stu-id="57279-149">\<binding></span></span>](bindings.md)
