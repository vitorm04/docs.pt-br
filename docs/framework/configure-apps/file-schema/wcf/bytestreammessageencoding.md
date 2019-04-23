---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: ce9f282ea1101befe3bf99762efa61e9b47b74cf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109896"
---
# <a name="bytestreammessageencoding"></a><span data-ttu-id="73c83-101">\<byteStreamMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="73c83-101">\<byteStreamMessageEncoding></span></span>
<span data-ttu-id="73c83-102">Especifica a codificação de mensagens como um fluxo de bytes, com a opção de especificar a codificação de caracteres.</span><span class="sxs-lookup"><span data-stu-id="73c83-102">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="73c83-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="73c83-103">\<system.serviceModel></span></span>  
<span data-ttu-id="73c83-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="73c83-104">\<bindings></span></span>  
<span data-ttu-id="73c83-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="73c83-105">\<customBinding></span></span>  
<span data-ttu-id="73c83-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="73c83-106">\<binding></span></span>  
<span data-ttu-id="73c83-107">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="73c83-107">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73c83-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73c83-108">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73c83-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="73c83-109">Attributes and Elements</span></span>  
 <span data-ttu-id="73c83-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="73c83-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73c83-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="73c83-111">Attributes</span></span>  
  
|<span data-ttu-id="73c83-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="73c83-112">Attribute</span></span>|<span data-ttu-id="73c83-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="73c83-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73c83-114">messageVersion</span><span class="sxs-lookup"><span data-stu-id="73c83-114">messageVersion</span></span>|<span data-ttu-id="73c83-115">Especifica a versão SOAP das mensagens enviadas usando a associação.</span><span class="sxs-lookup"><span data-stu-id="73c83-115">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="73c83-116">Essa propriedade só pode ser definida para o valor de versão de mensagem de <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="73c83-116">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="73c83-117">O codificador de mensagem de fluxo de bytes não oferece suporte a qualquer outra versão de mensagem.</span><span class="sxs-lookup"><span data-stu-id="73c83-117">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="73c83-118">Esse atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="73c83-118">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73c83-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="73c83-119">Child Elements</span></span>  
  
|<span data-ttu-id="73c83-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="73c83-120">Element</span></span>|<span data-ttu-id="73c83-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="73c83-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="73c83-122">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="73c83-122">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="73c83-123">Define as restrições na complexidade das mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="73c83-123">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="73c83-124">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="73c83-124">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="73c83-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="73c83-125">Parent Elements</span></span>  
  
|<span data-ttu-id="73c83-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="73c83-126">Element</span></span>|<span data-ttu-id="73c83-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="73c83-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73c83-128">\<binding></span><span class="sxs-lookup"><span data-stu-id="73c83-128">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="73c83-129">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="73c83-129">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73c83-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73c83-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="73c83-131">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="73c83-131">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="73c83-132">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="73c83-132">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="73c83-133">Associações</span><span class="sxs-lookup"><span data-stu-id="73c83-133">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="73c83-134">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="73c83-134">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="73c83-135">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="73c83-135">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="73c83-136">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="73c83-136">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
