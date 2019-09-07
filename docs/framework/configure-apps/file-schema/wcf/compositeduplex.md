---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: a73085320eaf248887422316e1b7787b8654d71d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400483"
---
# <a name="compositeduplex"></a><span data-ttu-id="5ffea-101">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="5ffea-101">\<compositeDuplex></span></span>
<span data-ttu-id="5ffea-102">Define o elemento de associação que é usado quando o cliente deve expor um ponto de extremidade para que o serviço envie mensagens de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="5ffea-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
<span data-ttu-id="5ffea-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5ffea-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5ffea-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5ffea-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5ffea-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="5ffea-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5ffea-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de CustomBinding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="5ffea-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="5ffea-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="5ffea-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="5ffea-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> compositeDuplex**</span><span class="sxs-lookup"><span data-stu-id="5ffea-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ffea-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ffea-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ffea-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5ffea-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5ffea-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5ffea-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ffea-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="5ffea-112">Attributes</span></span>  
  
|<span data-ttu-id="5ffea-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="5ffea-113">Attribute</span></span>|<span data-ttu-id="5ffea-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ffea-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ffea-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="5ffea-115">clientBaseAddress</span></span>|<span data-ttu-id="5ffea-116">Um URI que define o endereço do canal traseiro no modo duplex.</span><span class="sxs-lookup"><span data-stu-id="5ffea-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="5ffea-117">O serviço usa esse endereço para fazer contato e estabelecer uma conexão com o cliente.</span><span class="sxs-lookup"><span data-stu-id="5ffea-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="5ffea-118">Se esse atributo não estiver definido, um endereço padrão "`full qualified name+default port\TemporaryIndigoAddress\guid`" será gerado.</span><span class="sxs-lookup"><span data-stu-id="5ffea-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="5ffea-119">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="5ffea-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ffea-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5ffea-120">Child Elements</span></span>  
 <span data-ttu-id="5ffea-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5ffea-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ffea-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5ffea-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5ffea-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ffea-123">Element</span></span>|<span data-ttu-id="5ffea-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ffea-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ffea-125">\<binding></span><span class="sxs-lookup"><span data-stu-id="5ffea-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="5ffea-126">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="5ffea-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ffea-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ffea-127">Remarks</span></span>  
 <span data-ttu-id="5ffea-128">Esse elemento de configuração é usado com transportes que não permitem comunicações de duplex nativamente, por exemplo, HTTP.</span><span class="sxs-lookup"><span data-stu-id="5ffea-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="5ffea-129">O TCP, por outro lado, permite comunicações duplex nativamente e não requer o uso desse elemento de ligação para que o serviço envie mensagens de volta para um cliente.</span><span class="sxs-lookup"><span data-stu-id="5ffea-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="5ffea-130">O cliente deve expor um endereço para que o serviço faça contato e estabeleça uma conexão.</span><span class="sxs-lookup"><span data-stu-id="5ffea-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="5ffea-131">Esse endereço de `clientBaseAddress` cliente é fornecido pelo atributo.</span><span class="sxs-lookup"><span data-stu-id="5ffea-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="5ffea-132">Observe que Windows Communication Foundation (WCF) gera automaticamente um ClientBaseAddress se um não é definido explicitamente pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="5ffea-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ffea-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ffea-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="5ffea-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ffea-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="5ffea-135">Associações</span><span class="sxs-lookup"><span data-stu-id="5ffea-135">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5ffea-136">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="5ffea-136">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5ffea-137">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="5ffea-137">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="5ffea-138">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="5ffea-138">\<customBinding></span></span>](custombinding.md)
