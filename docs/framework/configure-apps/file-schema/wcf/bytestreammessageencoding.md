---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 1d4109bde9c1668bc0832689b05e5d1dc3b198e9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739065"
---
# <a name="bytestreammessageencoding"></a><span data-ttu-id="e6ba0-101">\<byteStreamMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="e6ba0-101">\<byteStreamMessageEncoding></span></span>
<span data-ttu-id="e6ba0-102">Especifica a codificação de mensagem como um fluxo de bytes, com a opção de especificar a codificação de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e6ba0-102">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
<span data-ttu-id="e6ba0-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e6ba0-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e6ba0-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="e6ba0-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e6ba0-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="e6ba0-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="e6ba0-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) ></span><span class="sxs-lookup"><span data-stu-id="e6ba0-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="e6ba0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="e6ba0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="e6ba0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<byteStreamMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="e6ba0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<byteStreamMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6ba0-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6ba0-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6ba0-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e6ba0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e6ba0-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e6ba0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6ba0-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="e6ba0-112">Attributes</span></span>  
  
|<span data-ttu-id="e6ba0-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="e6ba0-113">Attribute</span></span>|<span data-ttu-id="e6ba0-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6ba0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e6ba0-115">messageVersion</span><span class="sxs-lookup"><span data-stu-id="e6ba0-115">messageVersion</span></span>|<span data-ttu-id="e6ba0-116">Especifica a versão SOAP das mensagens enviadas usando a associação.</span><span class="sxs-lookup"><span data-stu-id="e6ba0-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="e6ba0-117">Essa propriedade só pode ser definida como o valor de versão da mensagem de <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="e6ba0-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="e6ba0-118">O codificador de mensagens de fluxo de bytes não oferece suporte a outras versões de mensagem.</span><span class="sxs-lookup"><span data-stu-id="e6ba0-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="e6ba0-119">Este atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="e6ba0-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6ba0-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e6ba0-120">Child Elements</span></span>  
  
|<span data-ttu-id="e6ba0-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="e6ba0-121">Element</span></span>|<span data-ttu-id="e6ba0-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6ba0-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e6ba0-123">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e6ba0-123">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="e6ba0-124">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="e6ba0-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="e6ba0-125">Este elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="e6ba0-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e6ba0-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e6ba0-126">Parent Elements</span></span>  
  
|<span data-ttu-id="e6ba0-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="e6ba0-127">Element</span></span>|<span data-ttu-id="e6ba0-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6ba0-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6ba0-129">\<binding ></span><span class="sxs-lookup"><span data-stu-id="e6ba0-129">\<binding></span></span>](bindings.md)|<span data-ttu-id="e6ba0-130">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="e6ba0-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6ba0-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6ba0-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="e6ba0-132">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="e6ba0-132">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="e6ba0-133">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="e6ba0-133">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="e6ba0-134">Associações</span><span class="sxs-lookup"><span data-stu-id="e6ba0-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e6ba0-135">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="e6ba0-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e6ba0-136">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="e6ba0-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="e6ba0-137">\<CustomBinding</span><span class="sxs-lookup"><span data-stu-id="e6ba0-137">\<customBinding></span></span>](custombinding.md)
