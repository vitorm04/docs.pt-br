---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: e6e6d1907d89a09a72594a836f2192e9ad9c4290
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758282"
---
# <a name="textmessageencoding"></a><span data-ttu-id="a5c24-101">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="a5c24-101">\<textMessageEncoding></span></span>
<span data-ttu-id="a5c24-102">Especifica a codificação de caracteres e a mensagem de controle de versão usado para mensagens XML baseadas em texto.</span><span class="sxs-lookup"><span data-stu-id="a5c24-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="a5c24-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a5c24-103">\<system.serviceModel></span></span>  
<span data-ttu-id="a5c24-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a5c24-104">\<bindings></span></span>  
<span data-ttu-id="a5c24-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a5c24-105">\<customBinding></span></span>  
<span data-ttu-id="a5c24-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="a5c24-106">\<binding></span></span>  
<span data-ttu-id="a5c24-107">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="a5c24-107">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5c24-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a5c24-108">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5c24-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a5c24-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a5c24-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a5c24-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5c24-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="a5c24-111">Attributes</span></span>  
  
|<span data-ttu-id="a5c24-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="a5c24-112">Attribute</span></span>|<span data-ttu-id="a5c24-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5c24-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a5c24-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="a5c24-114">maxReadPoolSize</span></span>|<span data-ttu-id="a5c24-115">Um inteiro que especifica quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="a5c24-115">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="a5c24-116">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="a5c24-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="a5c24-117">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="a5c24-117">The default is 64.</span></span>|  
|<span data-ttu-id="a5c24-118">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="a5c24-118">maxWritePoolSize</span></span>|<span data-ttu-id="a5c24-119">Um inteiro que especifica quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="a5c24-119">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="a5c24-120">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="a5c24-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="a5c24-121">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="a5c24-121">The default is 16.</span></span>|  
|<span data-ttu-id="a5c24-122">messageVersion</span><span class="sxs-lookup"><span data-stu-id="a5c24-122">messageVersion</span></span>|<span data-ttu-id="a5c24-123">Especifica a versão SOAP das mensagens enviadas usando a associação.</span><span class="sxs-lookup"><span data-stu-id="a5c24-123">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="a5c24-124">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="a5c24-124">Valid values are</span></span><br /><br /> <span data-ttu-id="a5c24-125">-Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="a5c24-125">-   Soap11Addressing10</span></span><br /><span data-ttu-id="a5c24-126">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="a5c24-126">-   Soap12Addressing10</span></span><br /><span data-ttu-id="a5c24-127">-Soap11</span><span class="sxs-lookup"><span data-stu-id="a5c24-127">-   Soap11</span></span><br /><span data-ttu-id="a5c24-128">-  Soap12</span><span class="sxs-lookup"><span data-stu-id="a5c24-128">-  Soap12</span></span><br /><br /><span data-ttu-id="a5c24-129">O padrão é Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="a5c24-129">The default is Soap12Addressing10.</span></span> <span data-ttu-id="a5c24-130">Esse atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="a5c24-130">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="a5c24-131">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="a5c24-131">writeEncoding</span></span>|<span data-ttu-id="a5c24-132">Especifica a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a5c24-132">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="a5c24-133">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="a5c24-133">Valid values are</span></span><br /><br /> <span data-ttu-id="a5c24-134">-   UnicodeFffeTextEncoding: Unicode BigEndian de codificação</span><span class="sxs-lookup"><span data-stu-id="a5c24-134">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="a5c24-135">-Utf16TextEncoding: Codificação Unicode</span><span class="sxs-lookup"><span data-stu-id="a5c24-135">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="a5c24-136">-   Utf8TextEncoding: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="a5c24-136">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="a5c24-137">O padrão é Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="a5c24-137">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="a5c24-138">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="a5c24-138">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5c24-139">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a5c24-139">Child Elements</span></span>  
  
|<span data-ttu-id="a5c24-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="a5c24-140">Element</span></span>|<span data-ttu-id="a5c24-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5c24-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a5c24-142">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a5c24-142">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="a5c24-143">Define as restrições na complexidade das mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="a5c24-143">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="a5c24-144">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="a5c24-144">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a5c24-145">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a5c24-145">Parent Elements</span></span>  
  
|<span data-ttu-id="a5c24-146">Elemento</span><span class="sxs-lookup"><span data-stu-id="a5c24-146">Element</span></span>|<span data-ttu-id="a5c24-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5c24-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5c24-148">\<binding></span><span class="sxs-lookup"><span data-stu-id="a5c24-148">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a5c24-149">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="a5c24-149">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5c24-150">Comentários</span><span class="sxs-lookup"><span data-stu-id="a5c24-150">Remarks</span></span>  
 <span data-ttu-id="a5c24-151">Codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="a5c24-151">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="a5c24-152">Decodificação de é o processo inverso.</span><span class="sxs-lookup"><span data-stu-id="a5c24-152">Decoding is the reverse process.</span></span> <span data-ttu-id="a5c24-153">Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: Texto, binária e mecanismo de otimização de transmissão de mensagens (MTOM).</span><span class="sxs-lookup"><span data-stu-id="a5c24-153">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="a5c24-154">A codificação de texto representado pelo `textMessageEncoding` elemento é o mais interoperável, mas o codificador menos eficiente para mensagens XML.</span><span class="sxs-lookup"><span data-stu-id="a5c24-154">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="a5c24-155">O codificador de texto cria mensagens baseadas em texto durante a transmissão.</span><span class="sxs-lookup"><span data-stu-id="a5c24-155">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="a5c24-156">As mensagens geradas por esse codificador são adequadas para WS-\* com base em interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="a5c24-156">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="a5c24-157">Serviço Web ou o cliente do serviço Web geralmente pode compreender XML textual.</span><span class="sxs-lookup"><span data-stu-id="a5c24-157">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="a5c24-158">No entanto, a transmissão de blocos grandes de dados binários como texto é o método menos eficiente para codificação de mensagens XML.</span><span class="sxs-lookup"><span data-stu-id="a5c24-158">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5c24-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a5c24-159">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="a5c24-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5c24-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="a5c24-161">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="a5c24-161">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="a5c24-162">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="a5c24-162">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="a5c24-163">Associações</span><span class="sxs-lookup"><span data-stu-id="a5c24-163">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="a5c24-164">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="a5c24-164">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a5c24-165">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="a5c24-165">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="a5c24-166">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a5c24-166">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
