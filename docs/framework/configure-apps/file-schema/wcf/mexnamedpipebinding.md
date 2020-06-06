---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: 41f5b19f5067d9ac7faa2c7329dd07dd9d48e9b3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74430878"
---
# \<mexNamedPipeBinding>
<span data-ttu-id="010e4-101">Especifica as configurações para uma associação usada para a troca de mensagens WS-MetadataExchange (WS-MEX) sobre o pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="010e4-101">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexNamedPipeBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="010e4-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="010e4-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="010e4-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="010e4-103">Attributes and Elements</span></span>  
 <span data-ttu-id="010e4-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="010e4-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="010e4-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="010e4-105">Attributes</span></span>  
  
|<span data-ttu-id="010e4-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="010e4-106">Attribute</span></span>|<span data-ttu-id="010e4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="010e4-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="010e4-108">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="010e4-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="010e4-109">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="010e4-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="010e4-110">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="010e4-110">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="010e4-111">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="010e4-111">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="010e4-112">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="010e4-112">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="010e4-113">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="010e4-113">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="010e4-114">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="010e4-114">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="010e4-115">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="010e4-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="010e4-116">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="010e4-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="010e4-117">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="010e4-117">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="010e4-118">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="010e4-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="010e4-119">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="010e4-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="010e4-120">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="010e4-120">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="010e4-121">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="010e4-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="010e4-122">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="010e4-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="010e4-123">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="010e4-123">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="010e4-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="010e4-124">Child Elements</span></span>  
 <span data-ttu-id="010e4-125">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="010e4-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="010e4-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="010e4-126">Parent Elements</span></span>  
  
|<span data-ttu-id="010e4-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="010e4-127">Element</span></span>|<span data-ttu-id="010e4-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="010e4-128">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="010e4-129">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="010e4-129">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="010e4-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="010e4-130">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="010e4-131">Como publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="010e4-131">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="010e4-132">Publicando e recuperando metadados através de uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="010e4-132">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="010e4-133">Metadados</span><span class="sxs-lookup"><span data-stu-id="010e4-133">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="010e4-134">Associações</span><span class="sxs-lookup"><span data-stu-id="010e4-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="010e4-135">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="010e4-135">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="010e4-136">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="010e4-136">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
