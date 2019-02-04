---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: c8dfd6824877d6f9e5b089a538cce35ffe51320b
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674276"
---
# <a name="bytestreammessageencoding"></a><span data-ttu-id="70e5b-101">\<byteStreamMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="70e5b-101">\<byteStreamMessageEncoding></span></span>
<span data-ttu-id="70e5b-102">Especifica a codificação de mensagens como um fluxo de bytes, com a opção de especificar a codificação de caracteres.</span><span class="sxs-lookup"><span data-stu-id="70e5b-102">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="70e5b-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="70e5b-103">\<system.serviceModel></span></span>  
<span data-ttu-id="70e5b-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="70e5b-104">\<bindings></span></span>  
<span data-ttu-id="70e5b-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="70e5b-105">\<customBinding></span></span>  
<span data-ttu-id="70e5b-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="70e5b-106">\<binding></span></span>  
<span data-ttu-id="70e5b-107">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="70e5b-107">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70e5b-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70e5b-108">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70e5b-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="70e5b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="70e5b-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="70e5b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70e5b-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="70e5b-111">Attributes</span></span>  
  
|<span data-ttu-id="70e5b-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="70e5b-112">Attribute</span></span>|<span data-ttu-id="70e5b-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="70e5b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="70e5b-114">messageVersion</span><span class="sxs-lookup"><span data-stu-id="70e5b-114">messageVersion</span></span>|<span data-ttu-id="70e5b-115">Especifica a versão SOAP das mensagens enviadas usando a associação.</span><span class="sxs-lookup"><span data-stu-id="70e5b-115">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="70e5b-116">Essa propriedade só pode ser definida para o valor de versão de mensagem de <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="70e5b-116">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="70e5b-117">O codificador de mensagem de fluxo de bytes não oferece suporte a qualquer outra versão de mensagem.</span><span class="sxs-lookup"><span data-stu-id="70e5b-117">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="70e5b-118">Esse atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="70e5b-118">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70e5b-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="70e5b-119">Child Elements</span></span>  
  
|<span data-ttu-id="70e5b-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="70e5b-120">Element</span></span>|<span data-ttu-id="70e5b-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="70e5b-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="70e5b-122">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="70e5b-122">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="70e5b-123">Define as restrições na complexidade das mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="70e5b-123">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="70e5b-124">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="70e5b-124">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="70e5b-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="70e5b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="70e5b-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="70e5b-126">Element</span></span>|<span data-ttu-id="70e5b-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="70e5b-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70e5b-128">\<binding></span><span class="sxs-lookup"><span data-stu-id="70e5b-128">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="70e5b-129">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="70e5b-129">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="70e5b-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70e5b-130">See also</span></span>
- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="70e5b-131">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="70e5b-131">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="70e5b-132">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="70e5b-132">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="70e5b-133">Associações</span><span class="sxs-lookup"><span data-stu-id="70e5b-133">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="70e5b-134">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="70e5b-134">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="70e5b-135">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="70e5b-135">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="70e5b-136">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="70e5b-136">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
