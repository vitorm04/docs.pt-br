---
title: '&lt;byteStreamMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 3493588d4613131ad9526a8d26912ecdb601ea25
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753268"
---
# <a name="ltbytestreammessageencodinggt"></a><span data-ttu-id="52600-102">&lt;byteStreamMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="52600-102">&lt;byteStreamMessageEncoding&gt;</span></span>
<span data-ttu-id="52600-103">Especifica a codificação de mensagens como um fluxo de bytes, com a opção para especificar a codificação de caracteres.</span><span class="sxs-lookup"><span data-stu-id="52600-103">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="52600-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="52600-104">\<system.serviceModel></span></span>  
<span data-ttu-id="52600-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="52600-105">\<bindings></span></span>  
<span data-ttu-id="52600-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="52600-106">\<customBinding></span></span>  
<span data-ttu-id="52600-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="52600-107">\<binding></span></span>  
<span data-ttu-id="52600-108">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="52600-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52600-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52600-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52600-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="52600-110">Attributes and Elements</span></span>  
 <span data-ttu-id="52600-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="52600-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52600-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="52600-112">Attributes</span></span>  
  
|<span data-ttu-id="52600-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="52600-113">Attribute</span></span>|<span data-ttu-id="52600-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="52600-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52600-115">messageVersion</span><span class="sxs-lookup"><span data-stu-id="52600-115">messageVersion</span></span>|<span data-ttu-id="52600-116">Especifica a versão SOAP das mensagens enviadas usando a associação.</span><span class="sxs-lookup"><span data-stu-id="52600-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="52600-117">Essa propriedade só pode ser definida para o valor da versão de mensagem <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="52600-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="52600-118">O codificador de mensagens do fluxo de bytes não dá suporte a outras versões de mensagem.</span><span class="sxs-lookup"><span data-stu-id="52600-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="52600-119">Esse atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="52600-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52600-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="52600-120">Child Elements</span></span>  
  
|<span data-ttu-id="52600-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="52600-121">Element</span></span>|<span data-ttu-id="52600-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="52600-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52600-123">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="52600-123">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="52600-124">Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="52600-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="52600-125">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="52600-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="52600-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="52600-126">Parent Elements</span></span>  
  
|<span data-ttu-id="52600-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="52600-127">Element</span></span>|<span data-ttu-id="52600-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="52600-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52600-129">\<associação ></span><span class="sxs-lookup"><span data-stu-id="52600-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="52600-130">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="52600-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52600-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52600-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>  
 [<span data-ttu-id="52600-132">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="52600-132">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="52600-133">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="52600-133">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="52600-134">Associações</span><span class="sxs-lookup"><span data-stu-id="52600-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="52600-135">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="52600-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="52600-136">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="52600-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="52600-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="52600-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
