---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 8025f5ed42325963aa4b695890caa5031f6bb6a6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204717"
---
# \<mexHttpsBinding>

<span data-ttu-id="dbf82-101">Especifica as configurações para uma associação usada para a troca de mensagens WS-MetadataExchange (WS-MEX) por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="dbf82-101">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="dbf82-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dbf82-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbf82-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dbf82-103">Attributes and Elements</span></span>  

 <span data-ttu-id="dbf82-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dbf82-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbf82-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="dbf82-105">Attributes</span></span>  
  
|<span data-ttu-id="dbf82-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="dbf82-106">Attribute</span></span>|<span data-ttu-id="dbf82-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="dbf82-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="dbf82-108">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="dbf82-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="dbf82-109">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="dbf82-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dbf82-110">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="dbf82-110">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="dbf82-111">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="dbf82-111">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="dbf82-112">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="dbf82-112">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="dbf82-113">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="dbf82-113">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="dbf82-114">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="dbf82-114">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="dbf82-115">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="dbf82-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="dbf82-116">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="dbf82-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dbf82-117">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="dbf82-117">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="dbf82-118">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="dbf82-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="dbf82-119">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="dbf82-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dbf82-120">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="dbf82-120">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="dbf82-121">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="dbf82-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="dbf82-122">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="dbf82-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dbf82-123">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="dbf82-123">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dbf82-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dbf82-124">Child Elements</span></span>  

 <span data-ttu-id="dbf82-125">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="dbf82-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dbf82-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dbf82-126">Parent Elements</span></span>  
  
|<span data-ttu-id="dbf82-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="dbf82-127">Element</span></span>|<span data-ttu-id="dbf82-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="dbf82-128">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="dbf82-129">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="dbf82-129">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbf82-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="dbf82-130">Remarks</span></span>  

 <span data-ttu-id="dbf82-131">Essa associação é essencialmente uma `WSHttpBinding` associação que dá suporte à segurança em nível de transporte usando certificados.</span><span class="sxs-lookup"><span data-stu-id="dbf82-131">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="dbf82-132">Para obter mais informações sobre como configurar e usar esse ponto de extremidade de metadados, consulte [como: configurar uma associação de WS-Metadata Exchange personalizada](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [como recuperar metadados em uma associação não MEX](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)e o [ponto de extremidade de metadados seguro personalizado](../../../wcf/samples/custom-secure-metadata-endpoint.md)de exemplo.</span><span class="sxs-lookup"><span data-stu-id="dbf82-132">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbf82-133">Veja também</span><span class="sxs-lookup"><span data-stu-id="dbf82-133">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="dbf82-134">Como: publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="dbf82-134">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="dbf82-135">Publicando e recuperando metadados através de uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="dbf82-135">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="dbf82-136">Como: configurar uma associação personalizada do WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="dbf82-136">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="dbf82-137">Como: recuperar metadados através de uma associação não MEX</span><span class="sxs-lookup"><span data-stu-id="dbf82-137">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="dbf82-138">Ponto de extremidade de metadados seguros personalizados</span><span class="sxs-lookup"><span data-stu-id="dbf82-138">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="dbf82-139">Metadados</span><span class="sxs-lookup"><span data-stu-id="dbf82-139">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="dbf82-140">Associações</span><span class="sxs-lookup"><span data-stu-id="dbf82-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="dbf82-141">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="dbf82-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="dbf82-142">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="dbf82-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
