---
title: '&lt;textMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ac17ead3c7054f0125527e3992fe865624770a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="lttextmessageencodinggt"></a><span data-ttu-id="af9bf-102">&lt;textMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="af9bf-102">&lt;textMessageEncoding&gt;</span></span>
<span data-ttu-id="af9bf-103">Especifica a codificação de caracteres e a mensagem de controle de versão é usada para mensagens XML baseadas em texto.</span><span class="sxs-lookup"><span data-stu-id="af9bf-103">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="af9bf-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="af9bf-104">\<system.serviceModel></span></span>  
<span data-ttu-id="af9bf-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="af9bf-105">\<bindings></span></span>  
<span data-ttu-id="af9bf-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="af9bf-106">\<customBinding></span></span>  
<span data-ttu-id="af9bf-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="af9bf-107">\<binding></span></span>  
<span data-ttu-id="af9bf-108">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="af9bf-108">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af9bf-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af9bf-109">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing10/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af9bf-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="af9bf-110">Attributes and Elements</span></span>  
 <span data-ttu-id="af9bf-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="af9bf-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af9bf-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="af9bf-112">Attributes</span></span>  
  
|<span data-ttu-id="af9bf-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="af9bf-113">Attribute</span></span>|<span data-ttu-id="af9bf-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="af9bf-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="af9bf-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="af9bf-115">maxReadPoolSize</span></span>|<span data-ttu-id="af9bf-116">Um inteiro que especifica quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="af9bf-116">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="af9bf-117">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto maior de trabalho.</span><span class="sxs-lookup"><span data-stu-id="af9bf-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="af9bf-118">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="af9bf-118">The default is 64.</span></span>|  
|<span data-ttu-id="af9bf-119">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="af9bf-119">maxWritePoolSize</span></span>|<span data-ttu-id="af9bf-120">Um inteiro que especifica quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="af9bf-120">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="af9bf-121">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto maior de trabalho.</span><span class="sxs-lookup"><span data-stu-id="af9bf-121">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="af9bf-122">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="af9bf-122">The default is 16.</span></span>|  
|<span data-ttu-id="af9bf-123">messageVersion</span><span class="sxs-lookup"><span data-stu-id="af9bf-123">messageVersion</span></span>|<span data-ttu-id="af9bf-124">Especifica a versão SOAP das mensagens enviadas usando a associação.</span><span class="sxs-lookup"><span data-stu-id="af9bf-124">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="af9bf-125">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="af9bf-125">Valid values are</span></span><br /><br /> <span data-ttu-id="af9bf-126">-Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="af9bf-126">-   Soap11Addressing10</span></span><br /><span data-ttu-id="af9bf-127">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="af9bf-127">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="af9bf-128">O padrão é Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="af9bf-128">The default is Soap12Addressing10.</span></span> <span data-ttu-id="af9bf-129">Esse atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="af9bf-129">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="af9bf-130">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="af9bf-130">writeEncoding</span></span>|<span data-ttu-id="af9bf-131">Especifica a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="af9bf-131">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="af9bf-132">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="af9bf-132">Valid values are</span></span><br /><br /> <span data-ttu-id="af9bf-133">-UnicodeFffeTextEncoding: Unicode BigEndian codificação</span><span class="sxs-lookup"><span data-stu-id="af9bf-133">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="af9bf-134">-Utf16TextEncoding: Codificação de Unicode</span><span class="sxs-lookup"><span data-stu-id="af9bf-134">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="af9bf-135">-Utf8TextEncoding: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="af9bf-135">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="af9bf-136">O padrão é Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="af9bf-136">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="af9bf-137">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="af9bf-137">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="af9bf-138">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="af9bf-138">Child Elements</span></span>  
  
|<span data-ttu-id="af9bf-139">Elemento</span><span class="sxs-lookup"><span data-stu-id="af9bf-139">Element</span></span>|<span data-ttu-id="af9bf-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="af9bf-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af9bf-141">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="af9bf-141">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="af9bf-142">Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="af9bf-142">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="af9bf-143">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="af9bf-143">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="af9bf-144">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="af9bf-144">Parent Elements</span></span>  
  
|<span data-ttu-id="af9bf-145">Elemento</span><span class="sxs-lookup"><span data-stu-id="af9bf-145">Element</span></span>|<span data-ttu-id="af9bf-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="af9bf-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af9bf-147">\<associação ></span><span class="sxs-lookup"><span data-stu-id="af9bf-147">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="af9bf-148">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="af9bf-148">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af9bf-149">Comentários</span><span class="sxs-lookup"><span data-stu-id="af9bf-149">Remarks</span></span>  
 <span data-ttu-id="af9bf-150">Codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="af9bf-150">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="af9bf-151">Decodificação de é o processo inverso.</span><span class="sxs-lookup"><span data-stu-id="af9bf-151">Decoding is the reverse process.</span></span> <span data-ttu-id="af9bf-152">Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: texto, binária e mecanismo de otimização de transmissão mensagem (MTOM).</span><span class="sxs-lookup"><span data-stu-id="af9bf-152">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="af9bf-153">A codificação de texto representado pelo `textMessageEncoding` elemento é o mais interoperável, mas o codificador menos eficiente para mensagens XML.</span><span class="sxs-lookup"><span data-stu-id="af9bf-153">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="af9bf-154">O codificador de texto cria mensagens de baseado em texto no meio físico.</span><span class="sxs-lookup"><span data-stu-id="af9bf-154">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="af9bf-155">Produzido por esse codificador de mensagens são adequadas para WS-* com base em interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="af9bf-155">Messages produced by this encoder are suitable for WS-* based interop.</span></span> <span data-ttu-id="af9bf-156">Serviço Web ou cliente de serviço Web geralmente pode entender XML textual.</span><span class="sxs-lookup"><span data-stu-id="af9bf-156">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="af9bf-157">No entanto, a transmissão de grandes blocos de dados binários como texto é o método menos eficiente para codificação de mensagens XML.</span><span class="sxs-lookup"><span data-stu-id="af9bf-157">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af9bf-158">Exemplo</span><span class="sxs-lookup"><span data-stu-id="af9bf-158">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap12Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="af9bf-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af9bf-159">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 [<span data-ttu-id="af9bf-160">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="af9bf-160">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="af9bf-161">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="af9bf-161">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="af9bf-162">Associações</span><span class="sxs-lookup"><span data-stu-id="af9bf-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="af9bf-163">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="af9bf-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="af9bf-164">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="af9bf-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="af9bf-165">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="af9bf-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
