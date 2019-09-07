---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: 1494cee0e412bebc6637ad73354f7c91dc636e15
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399439"
---
# <a name="textmessageencoding"></a><span data-ttu-id="287e5-101">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="287e5-101">\<textMessageEncoding></span></span>
<span data-ttu-id="287e5-102">Especifica a codificação de caracteres e o controle de versão de mensagem usados para mensagens XML baseadas em texto.</span><span class="sxs-lookup"><span data-stu-id="287e5-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
<span data-ttu-id="287e5-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="287e5-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="287e5-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="287e5-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="287e5-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="287e5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="287e5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de CustomBinding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="287e5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="287e5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="287e5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="287e5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> textMessageEncoding**</span><span class="sxs-lookup"><span data-stu-id="287e5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<textMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="287e5-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="287e5-109">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="287e5-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="287e5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="287e5-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="287e5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="287e5-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="287e5-112">Attributes</span></span>  
  
|<span data-ttu-id="287e5-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="287e5-113">Attribute</span></span>|<span data-ttu-id="287e5-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="287e5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="287e5-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="287e5-115">maxReadPoolSize</span></span>|<span data-ttu-id="287e5-116">Um inteiro que especifica quantas mensagens podem ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="287e5-116">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="287e5-117">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="287e5-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="287e5-118">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="287e5-118">The default is 64.</span></span>|  
|<span data-ttu-id="287e5-119">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="287e5-119">maxWritePoolSize</span></span>|<span data-ttu-id="287e5-120">Um inteiro que especifica quantas mensagens podem ser enviadas simultaneamente sem alocar novos gravadores.</span><span class="sxs-lookup"><span data-stu-id="287e5-120">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="287e5-121">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="287e5-121">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="287e5-122">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="287e5-122">The default is 16.</span></span>|  
|<span data-ttu-id="287e5-123">messageVersion</span><span class="sxs-lookup"><span data-stu-id="287e5-123">messageVersion</span></span>|<span data-ttu-id="287e5-124">Especifica a versão SOAP das mensagens enviadas usando a associação.</span><span class="sxs-lookup"><span data-stu-id="287e5-124">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="287e5-125">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="287e5-125">Valid values are</span></span><br /><br /> <span data-ttu-id="287e5-126">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="287e5-126">-   Soap11Addressing10</span></span><br /><span data-ttu-id="287e5-127">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="287e5-127">-   Soap12Addressing10</span></span><br /><span data-ttu-id="287e5-128">-Soap11</span><span class="sxs-lookup"><span data-stu-id="287e5-128">-   Soap11</span></span><br /><span data-ttu-id="287e5-129">- Soap12</span><span class="sxs-lookup"><span data-stu-id="287e5-129">-  Soap12</span></span><br /><br /><span data-ttu-id="287e5-130">O padrão é Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="287e5-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="287e5-131">Esse atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="287e5-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="287e5-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="287e5-132">writeEncoding</span></span>|<span data-ttu-id="287e5-133">Especifica a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="287e5-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="287e5-134">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="287e5-134">Valid values are</span></span><br /><br /> <span data-ttu-id="287e5-135">-   UnicodeFffeTextEncoding: Codificação BigEndian Unicode</span><span class="sxs-lookup"><span data-stu-id="287e5-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="287e5-136">- Utf16TextEncoding: Codificação Unicode</span><span class="sxs-lookup"><span data-stu-id="287e5-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="287e5-137">- Utf8TextEncoding: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="287e5-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="287e5-138">O padrão é Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="287e5-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="287e5-139">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="287e5-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="287e5-140">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="287e5-140">Child Elements</span></span>  
  
|<span data-ttu-id="287e5-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="287e5-141">Element</span></span>|<span data-ttu-id="287e5-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="287e5-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="287e5-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="287e5-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="287e5-144">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="287e5-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="287e5-145">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="287e5-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="287e5-146">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="287e5-146">Parent Elements</span></span>  
  
|<span data-ttu-id="287e5-147">Elemento</span><span class="sxs-lookup"><span data-stu-id="287e5-147">Element</span></span>|<span data-ttu-id="287e5-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="287e5-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="287e5-149">\<binding></span><span class="sxs-lookup"><span data-stu-id="287e5-149">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="287e5-150">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="287e5-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="287e5-151">Comentários</span><span class="sxs-lookup"><span data-stu-id="287e5-151">Remarks</span></span>  
 <span data-ttu-id="287e5-152">A codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="287e5-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="287e5-153">A decodificação é o processo reverso.</span><span class="sxs-lookup"><span data-stu-id="287e5-153">Decoding is the reverse process.</span></span> <span data-ttu-id="287e5-154">O Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: O mecanismo de otimização de transmissão de mensagens e de texto, binário e mensagem (MTOM).</span><span class="sxs-lookup"><span data-stu-id="287e5-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="287e5-155">A codificação de texto representada pelo `textMessageEncoding` elemento é o mais interoperável, mas o codificador menos eficiente para mensagens XML.</span><span class="sxs-lookup"><span data-stu-id="287e5-155">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="287e5-156">O codificador de texto cria mensagens baseadas em texto na conexão.</span><span class="sxs-lookup"><span data-stu-id="287e5-156">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="287e5-157">As mensagens produzidas por esse codificador são adequadas para a interoperabilidade baseada em WS-\*.</span><span class="sxs-lookup"><span data-stu-id="287e5-157">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="287e5-158">O serviço Web ou o cliente de serviço Web geralmente pode entender XML textual.</span><span class="sxs-lookup"><span data-stu-id="287e5-158">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="287e5-159">No entanto, a transmissão de grandes blocos de dados binários como texto é o método menos eficiente para codificar mensagens XML.</span><span class="sxs-lookup"><span data-stu-id="287e5-159">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="287e5-160">Exemplo</span><span class="sxs-lookup"><span data-stu-id="287e5-160">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="287e5-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="287e5-161">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="287e5-162">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="287e5-162">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="287e5-163">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="287e5-163">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="287e5-164">Associações</span><span class="sxs-lookup"><span data-stu-id="287e5-164">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="287e5-165">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="287e5-165">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="287e5-166">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="287e5-166">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="287e5-167">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="287e5-167">\<customBinding></span></span>](custombinding.md)
