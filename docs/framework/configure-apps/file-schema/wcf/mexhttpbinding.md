---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 8d5b9378bf7769754586d0b13f742659aee18f03
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430914"
---
# <a name="mexhttpbinding"></a><span data-ttu-id="c7473-101">\<mexHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="c7473-101">\<mexHttpBinding></span></span>
<span data-ttu-id="c7473-102">Especifica as configurações para uma associação usada para a troca de mensagens WS-MetadataExchange (WS-MEX) sobre HTTP.</span><span class="sxs-lookup"><span data-stu-id="c7473-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
<span data-ttu-id="c7473-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c7473-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c7473-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c7473-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c7473-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="c7473-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="c7473-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="c7473-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7473-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7473-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7473-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c7473-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c7473-109">As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.</span><span class="sxs-lookup"><span data-stu-id="c7473-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7473-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="c7473-110">Attributes</span></span>  
  
|<span data-ttu-id="c7473-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="c7473-111">Attribute</span></span>|<span data-ttu-id="c7473-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7473-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="c7473-113">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="c7473-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="c7473-114">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c7473-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c7473-115">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c7473-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="c7473-116">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="c7473-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="c7473-117">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="c7473-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="c7473-118">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="c7473-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="c7473-119">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c7473-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="c7473-120">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="c7473-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="c7473-121">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c7473-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c7473-122">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c7473-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="c7473-123">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="c7473-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="c7473-124">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c7473-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c7473-125">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="c7473-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="c7473-126">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="c7473-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="c7473-127">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c7473-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c7473-128">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="c7473-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c7473-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c7473-129">Child Elements</span></span>  
 <span data-ttu-id="c7473-130">None.</span><span class="sxs-lookup"><span data-stu-id="c7473-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c7473-131">Elementos Pai</span><span class="sxs-lookup"><span data-stu-id="c7473-131">Parent Elements</span></span>  
  
|<span data-ttu-id="c7473-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="c7473-132">Element</span></span>|<span data-ttu-id="c7473-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7473-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c7473-134">associações de \<></span><span class="sxs-lookup"><span data-stu-id="c7473-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="c7473-135">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="c7473-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7473-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="c7473-136">Remarks</span></span>  
 <span data-ttu-id="c7473-137">Essa associação é essencialmente uma associação de `WSHttpBinding` com segurança desabilitada.</span><span class="sxs-lookup"><span data-stu-id="c7473-137">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="c7473-138">Ele dá suporte à maioria das solicitações de metadados.</span><span class="sxs-lookup"><span data-stu-id="c7473-138">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7473-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7473-139">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="c7473-140">Como publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="c7473-140">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="c7473-141">Publicando e recuperando metadados através de uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="c7473-141">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="c7473-142">Metadados</span><span class="sxs-lookup"><span data-stu-id="c7473-142">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="c7473-143">Associações</span><span class="sxs-lookup"><span data-stu-id="c7473-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c7473-144">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="c7473-144">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c7473-145">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="c7473-145">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c7473-146">> de associação de \<</span><span class="sxs-lookup"><span data-stu-id="c7473-146">\<binding></span></span>](bindings.md)
