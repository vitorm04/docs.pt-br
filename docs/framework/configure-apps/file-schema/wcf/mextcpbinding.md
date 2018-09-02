---
title: '&lt;mexTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: 8c2b149f983c0674b51c2242600a451ff71fc9b5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420356"
---
# <a name="ltmextcpbindinggt"></a><span data-ttu-id="97be9-102">&lt;mexTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="97be9-102">&lt;mexTcpBinding&gt;</span></span>
<span data-ttu-id="97be9-103">Especifica as configurações para uma associação usada para a troca de mensagens WS-MetadataExchange (WS-MEX) sobre TCP.</span><span class="sxs-lookup"><span data-stu-id="97be9-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
 <span data-ttu-id="97be9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="97be9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="97be9-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="97be9-105">\<bindings></span></span>  
<span data-ttu-id="97be9-106">\<mexTcpBinding></span><span class="sxs-lookup"><span data-stu-id="97be9-106">\<mexTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97be9-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="97be9-107">Syntax</span></span>  
  
```xml  
<mexTcpBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan">  
   </binding>  
</mexTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97be9-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="97be9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="97be9-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="97be9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97be9-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="97be9-110">Attributes</span></span>  
  
|<span data-ttu-id="97be9-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="97be9-111">Attribute</span></span>|<span data-ttu-id="97be9-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="97be9-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="97be9-113">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação close.</span><span class="sxs-lookup"><span data-stu-id="97be9-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="97be9-114">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="97be9-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="97be9-115">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="97be9-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="97be9-116">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="97be9-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="97be9-117">Esse valor deve ser exclusivo porque ele é usado como identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="97be9-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="97be9-118">Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="97be9-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="97be9-119">Além disso, esse nome é exclusivo entre as associações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="97be9-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="97be9-120">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="97be9-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="97be9-121">Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="97be9-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="97be9-122">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação open.</span><span class="sxs-lookup"><span data-stu-id="97be9-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="97be9-123">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="97be9-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="97be9-124">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="97be9-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="97be9-125">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento ser concluída.</span><span class="sxs-lookup"><span data-stu-id="97be9-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="97be9-126">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="97be9-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="97be9-127">O padrão é 10:00:00.</span><span class="sxs-lookup"><span data-stu-id="97be9-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="97be9-128">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio ser concluída.</span><span class="sxs-lookup"><span data-stu-id="97be9-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="97be9-129">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="97be9-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="97be9-130">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="97be9-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97be9-131">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="97be9-131">Child Elements</span></span>  
 <span data-ttu-id="97be9-132">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="97be9-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="97be9-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="97be9-133">Parent Elements</span></span>  
  
|<span data-ttu-id="97be9-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="97be9-134">Element</span></span>|<span data-ttu-id="97be9-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="97be9-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97be9-136">\<associações ></span><span class="sxs-lookup"><span data-stu-id="97be9-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="97be9-137">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="97be9-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="97be9-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97be9-138">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MexTcpBindingElement>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>  
 [<span data-ttu-id="97be9-139">Como publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="97be9-139">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="97be9-140">Publicando e recuperando metadados através de uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="97be9-140">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="97be9-141">Metadados</span><span class="sxs-lookup"><span data-stu-id="97be9-141">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="97be9-142">Associações</span><span class="sxs-lookup"><span data-stu-id="97be9-142">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="97be9-143">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="97be9-143">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="97be9-144">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="97be9-144">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="97be9-145">\<associação ></span><span class="sxs-lookup"><span data-stu-id="97be9-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
