---
title: '&lt;compositeDuplex&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80c8f3954cccbce8e93ab9d8c516fdfd6c7bff10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcompositeduplexgt"></a><span data-ttu-id="b85ae-102">&lt;compositeDuplex&gt;</span><span class="sxs-lookup"><span data-stu-id="b85ae-102">&lt;compositeDuplex&gt;</span></span>
<span data-ttu-id="b85ae-103">Define o elemento de associação que é usado quando o cliente deve expor um ponto de extremidade para o serviço enviar mensagens de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="b85ae-103">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="b85ae-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b85ae-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b85ae-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="b85ae-105">\<bindings></span></span>  
<span data-ttu-id="b85ae-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b85ae-106">\<customBinding></span></span>  
<span data-ttu-id="b85ae-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="b85ae-107">\<binding></span></span>  
<span data-ttu-id="b85ae-108">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="b85ae-108">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b85ae-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b85ae-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b85ae-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b85ae-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b85ae-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b85ae-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b85ae-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="b85ae-112">Attributes</span></span>  
  
|<span data-ttu-id="b85ae-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="b85ae-113">Attribute</span></span>|<span data-ttu-id="b85ae-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b85ae-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b85ae-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="b85ae-115">clientBaseAddress</span></span>|<span data-ttu-id="b85ae-116">Um URI que define o endereço do canal de retorno no modo duplex.</span><span class="sxs-lookup"><span data-stu-id="b85ae-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="b85ae-117">O serviço usa este endereço para contato e estabelecer uma conexão com o cliente.</span><span class="sxs-lookup"><span data-stu-id="b85ae-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="b85ae-118">Se esse atributo não estiver definido, um endereço padrão "`full qualified name+default port\TemporaryIndigoAddress\guid`" é gerado.</span><span class="sxs-lookup"><span data-stu-id="b85ae-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="b85ae-119">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="b85ae-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b85ae-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b85ae-120">Child Elements</span></span>  
 <span data-ttu-id="b85ae-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b85ae-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b85ae-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b85ae-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b85ae-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="b85ae-123">Element</span></span>|<span data-ttu-id="b85ae-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="b85ae-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b85ae-125">\<associação ></span><span class="sxs-lookup"><span data-stu-id="b85ae-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="b85ae-126">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="b85ae-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b85ae-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="b85ae-127">Remarks</span></span>  
 <span data-ttu-id="b85ae-128">Este elemento de configuração é usado com transportes que não permitem a comunicação duplex nativamente, por exemplo, HTTP.</span><span class="sxs-lookup"><span data-stu-id="b85ae-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="b85ae-129">TCP, por outro lado, permite a comunicação duplex nativamente e não requer o uso desse elemento de associação para o serviço enviar mensagens para um cliente.</span><span class="sxs-lookup"><span data-stu-id="b85ae-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="b85ae-130">O cliente deve expor um endereço para o serviço fazer contato e estabelecer uma conexão.</span><span class="sxs-lookup"><span data-stu-id="b85ae-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="b85ae-131">Este endereço de cliente é fornecido pelo `clientBaseAddress` atributo.</span><span class="sxs-lookup"><span data-stu-id="b85ae-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="b85ae-132">Observe que Windows Communication Foundation (WCF) gera automaticamente um ClientBaseAddress se um não for explicitamente definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="b85ae-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b85ae-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b85ae-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="b85ae-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b85ae-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CompositeDuplexElement>  
 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="b85ae-135">Associações</span><span class="sxs-lookup"><span data-stu-id="b85ae-135">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b85ae-136">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="b85ae-136">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="b85ae-137">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="b85ae-137">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="b85ae-138">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b85ae-138">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
