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
# <a name="mexhttpbinding"></a><span data-ttu-id="bc800-101">\<mexHttpBinding></span><span class="sxs-lookup"><span data-stu-id="bc800-101">\<mexHttpBinding></span></span>
<span data-ttu-id="bc800-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span><span class="sxs-lookup"><span data-stu-id="bc800-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
<span data-ttu-id="bc800-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bc800-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bc800-104">&nbsp;&nbsp;[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bc800-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bc800-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bindings>** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="bc800-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="bc800-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpBinding>**</span><span class="sxs-lookup"><span data-stu-id="bc800-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc800-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bc800-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc800-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bc800-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bc800-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bc800-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc800-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="bc800-110">Attributes</span></span>  
  
|<span data-ttu-id="bc800-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="bc800-111">Attribute</span></span>|<span data-ttu-id="bc800-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc800-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="bc800-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span><span class="sxs-lookup"><span data-stu-id="bc800-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="bc800-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bc800-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bc800-115">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bc800-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="bc800-116">A string that contains the configuration name of the binding.</span><span class="sxs-lookup"><span data-stu-id="bc800-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="bc800-117">This value should be unique because it is used as an identification for the binding.</span><span class="sxs-lookup"><span data-stu-id="bc800-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="bc800-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span><span class="sxs-lookup"><span data-stu-id="bc800-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="bc800-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="bc800-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="bc800-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span><span class="sxs-lookup"><span data-stu-id="bc800-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="bc800-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bc800-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bc800-122">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bc800-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="bc800-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span><span class="sxs-lookup"><span data-stu-id="bc800-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="bc800-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bc800-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bc800-125">The default is 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="bc800-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="bc800-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span><span class="sxs-lookup"><span data-stu-id="bc800-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="bc800-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bc800-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bc800-128">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bc800-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc800-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bc800-129">Child Elements</span></span>  
 <span data-ttu-id="bc800-130">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="bc800-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc800-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bc800-131">Parent Elements</span></span>  
  
|<span data-ttu-id="bc800-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="bc800-132">Element</span></span>|<span data-ttu-id="bc800-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc800-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc800-134">\<bindings></span><span class="sxs-lookup"><span data-stu-id="bc800-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="bc800-135">This element holds a collection of standard and custom bindings.</span><span class="sxs-lookup"><span data-stu-id="bc800-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc800-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="bc800-136">Remarks</span></span>  
 <span data-ttu-id="bc800-137">This binding is essentially a `WSHttpBinding` binding with security disabled.</span><span class="sxs-lookup"><span data-stu-id="bc800-137">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="bc800-138">It supports most metadata requests.</span><span class="sxs-lookup"><span data-stu-id="bc800-138">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc800-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc800-139">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="bc800-140">Como publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="bc800-140">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="bc800-141">Publicando e recuperando metadados através de uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="bc800-141">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="bc800-142">Metadados</span><span class="sxs-lookup"><span data-stu-id="bc800-142">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="bc800-143">Associações</span><span class="sxs-lookup"><span data-stu-id="bc800-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bc800-144">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="bc800-144">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="bc800-145">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="bc800-145">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="bc800-146">\<binding></span><span class="sxs-lookup"><span data-stu-id="bc800-146">\<binding></span></span>](bindings.md)
