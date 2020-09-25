---
title: <mexTcpBinding>
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: 0d12f886eaee6283ee686209dfc129e397a8e1fe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204691"
---
# \<mexTcpBinding>

<span data-ttu-id="ebea9-101">Especifica as configurações para uma associação usada para a troca de mensagens WS-MetadataExchange (WS-MEX) sobre TCP.</span><span class="sxs-lookup"><span data-stu-id="ebea9-101">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="ebea9-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ebea9-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ebea9-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ebea9-103">Attributes and Elements</span></span>  

 <span data-ttu-id="ebea9-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ebea9-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ebea9-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="ebea9-105">Attributes</span></span>  
  
|<span data-ttu-id="ebea9-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="ebea9-106">Attribute</span></span>|<span data-ttu-id="ebea9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ebea9-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="ebea9-108">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="ebea9-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="ebea9-109">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="ebea9-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ebea9-110">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="ebea9-110">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="ebea9-111">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="ebea9-111">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="ebea9-112">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="ebea9-112">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="ebea9-113">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="ebea9-113">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="ebea9-114">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="ebea9-114">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="ebea9-115">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="ebea9-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="ebea9-116">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="ebea9-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ebea9-117">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="ebea9-117">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="ebea9-118">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="ebea9-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="ebea9-119">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="ebea9-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ebea9-120">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="ebea9-120">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="ebea9-121">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="ebea9-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="ebea9-122">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="ebea9-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ebea9-123">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="ebea9-123">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ebea9-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ebea9-124">Child Elements</span></span>  

 <span data-ttu-id="ebea9-125">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ebea9-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ebea9-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ebea9-126">Parent Elements</span></span>  
  
|<span data-ttu-id="ebea9-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="ebea9-127">Element</span></span>|<span data-ttu-id="ebea9-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="ebea9-128">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="ebea9-129">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="ebea9-129">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ebea9-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="ebea9-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.MexTcpBindingElement>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>
- [<span data-ttu-id="ebea9-131">Como: publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="ebea9-131">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="ebea9-132">Publicando e recuperando metadados através de uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="ebea9-132">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="ebea9-133">Metadados</span><span class="sxs-lookup"><span data-stu-id="ebea9-133">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="ebea9-134">Associações</span><span class="sxs-lookup"><span data-stu-id="ebea9-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ebea9-135">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="ebea9-135">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ebea9-136">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="ebea9-136">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
