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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1788300407ad84a5ff7e3929eaa728f5399961ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltbytestreammessageencodinggt"></a><span data-ttu-id="d0e7a-102">&lt;byteStreamMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="d0e7a-102">&lt;byteStreamMessageEncoding&gt;</span></span>
<span data-ttu-id="d0e7a-103">Especifica a codificação de mensagens como um fluxo de bytes, com a opção para especificar a codificação de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d0e7a-103">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="d0e7a-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d0e7a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d0e7a-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="d0e7a-105">\<bindings></span></span>  
<span data-ttu-id="d0e7a-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="d0e7a-106">\<customBinding></span></span>  
<span data-ttu-id="d0e7a-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="d0e7a-107">\<binding></span></span>  
<span data-ttu-id="d0e7a-108">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="d0e7a-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0e7a-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0e7a-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0e7a-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d0e7a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d0e7a-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d0e7a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0e7a-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="d0e7a-112">Attributes</span></span>  
  
|<span data-ttu-id="d0e7a-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="d0e7a-113">Attribute</span></span>|<span data-ttu-id="d0e7a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0e7a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0e7a-115">messageVersion</span><span class="sxs-lookup"><span data-stu-id="d0e7a-115">messageVersion</span></span>|<span data-ttu-id="d0e7a-116">Especifica a versão SOAP das mensagens enviadas usando a associação.</span><span class="sxs-lookup"><span data-stu-id="d0e7a-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="d0e7a-117">Essa propriedade só pode ser definida para o valor da versão de mensagem <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="d0e7a-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="d0e7a-118">O codificador de mensagens do fluxo de bytes não dá suporte a outras versões de mensagem.</span><span class="sxs-lookup"><span data-stu-id="d0e7a-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="d0e7a-119">Esse atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="d0e7a-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0e7a-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d0e7a-120">Child Elements</span></span>  
  
|<span data-ttu-id="d0e7a-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="d0e7a-121">Element</span></span>|<span data-ttu-id="d0e7a-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0e7a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0e7a-123">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="d0e7a-123">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="d0e7a-124">Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="d0e7a-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="d0e7a-125">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="d0e7a-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d0e7a-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d0e7a-126">Parent Elements</span></span>  
  
|<span data-ttu-id="d0e7a-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="d0e7a-127">Element</span></span>|<span data-ttu-id="d0e7a-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0e7a-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0e7a-129">\<associação ></span><span class="sxs-lookup"><span data-stu-id="d0e7a-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="d0e7a-130">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="d0e7a-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0e7a-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0e7a-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>  
 [<span data-ttu-id="d0e7a-132">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="d0e7a-132">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="d0e7a-133">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="d0e7a-133">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 <span data-ttu-id="d0e7a-134">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="d0e7a-134">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="d0e7a-135">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="d0e7a-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="d0e7a-136">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="d0e7a-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="d0e7a-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="d0e7a-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
