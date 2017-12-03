---
title: '&lt;byteStreamMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 165bf4cd1c0c5c1a6adae91650d38984bc47ef6e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbytestreammessageencodinggt"></a><span data-ttu-id="3804d-102">&lt;byteStreamMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="3804d-102">&lt;byteStreamMessageEncoding&gt;</span></span>
<span data-ttu-id="3804d-103">Especifica a codificação de mensagens como um fluxo de bytes, com a opção para especificar a codificação de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3804d-103">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="3804d-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="3804d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3804d-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="3804d-105">\<bindings></span></span>  
<span data-ttu-id="3804d-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="3804d-106">\<customBinding></span></span>  
<span data-ttu-id="3804d-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="3804d-107">\<binding></span></span>  
<span data-ttu-id="3804d-108">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="3804d-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3804d-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3804d-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3804d-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3804d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3804d-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3804d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3804d-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="3804d-112">Attributes</span></span>  
  
|<span data-ttu-id="3804d-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="3804d-113">Attribute</span></span>|<span data-ttu-id="3804d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="3804d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3804d-115">messageVersion</span><span class="sxs-lookup"><span data-stu-id="3804d-115">messageVersion</span></span>|<span data-ttu-id="3804d-116">Especifica a versão SOAP das mensagens enviadas usando a associação.</span><span class="sxs-lookup"><span data-stu-id="3804d-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="3804d-117">Essa propriedade só pode ser definida para o valor da versão de mensagem <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="3804d-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="3804d-118">O codificador de mensagens do fluxo de bytes não dá suporte a outras versões de mensagem.</span><span class="sxs-lookup"><span data-stu-id="3804d-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="3804d-119">Esse atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="3804d-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3804d-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3804d-120">Child Elements</span></span>  
  
|<span data-ttu-id="3804d-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="3804d-121">Element</span></span>|<span data-ttu-id="3804d-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="3804d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3804d-123">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="3804d-123">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="3804d-124">Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="3804d-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="3804d-125">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="3804d-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3804d-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3804d-126">Parent Elements</span></span>  
  
|<span data-ttu-id="3804d-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="3804d-127">Element</span></span>|<span data-ttu-id="3804d-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="3804d-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3804d-129">\<associação ></span><span class="sxs-lookup"><span data-stu-id="3804d-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="3804d-130">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="3804d-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3804d-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3804d-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>  
 [<span data-ttu-id="3804d-132">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="3804d-132">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="3804d-133">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="3804d-133">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 <span data-ttu-id="3804d-134">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="3804d-134">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="3804d-135">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="3804d-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="3804d-136">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="3804d-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="3804d-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="3804d-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
