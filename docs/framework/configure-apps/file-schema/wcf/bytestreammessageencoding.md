---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 1d4109bde9c1668bc0832689b05e5d1dc3b198e9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739065"
---
# \<byteStreamMessageEncoding>
<span data-ttu-id="77015-101">Especifica a codificação de mensagem como um fluxo de bytes, com a opção de especificar a codificação de caracteres.</span><span class="sxs-lookup"><span data-stu-id="77015-101">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<byteStreamMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="77015-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77015-102">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77015-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="77015-103">Attributes and Elements</span></span>  
 <span data-ttu-id="77015-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="77015-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77015-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="77015-105">Attributes</span></span>  
  
|<span data-ttu-id="77015-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="77015-106">Attribute</span></span>|<span data-ttu-id="77015-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="77015-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="77015-108">messageVersion</span><span class="sxs-lookup"><span data-stu-id="77015-108">messageVersion</span></span>|<span data-ttu-id="77015-109">Especifica a versão SOAP das mensagens enviadas usando a associação.</span><span class="sxs-lookup"><span data-stu-id="77015-109">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="77015-110">Essa propriedade só pode ser definida como o valor de versão da mensagem de <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="77015-110">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="77015-111">O codificador de mensagens de fluxo de bytes não oferece suporte a outras versões de mensagem.</span><span class="sxs-lookup"><span data-stu-id="77015-111">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="77015-112">Esse atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion> .</span><span class="sxs-lookup"><span data-stu-id="77015-112">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77015-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="77015-113">Child Elements</span></span>  
  
|<span data-ttu-id="77015-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="77015-114">Element</span></span>|<span data-ttu-id="77015-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="77015-115">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="77015-116">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="77015-116">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="77015-117">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="77015-117">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="77015-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="77015-118">Parent Elements</span></span>  
  
|<span data-ttu-id="77015-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="77015-119">Element</span></span>|<span data-ttu-id="77015-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="77015-120">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="77015-121">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="77015-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77015-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="77015-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="77015-123">Decodificador de mensagens</span><span class="sxs-lookup"><span data-stu-id="77015-123">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="77015-124">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="77015-124">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="77015-125">Associações</span><span class="sxs-lookup"><span data-stu-id="77015-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="77015-126">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="77015-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="77015-127">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="77015-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
