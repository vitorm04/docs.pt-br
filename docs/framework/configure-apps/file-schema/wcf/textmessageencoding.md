---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: e2fec2c2e5979b08ed0d832f636b3d0847b9a5dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915653"
---
# <a name="textmessageencoding"></a><span data-ttu-id="e9f6d-101">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="e9f6d-101">\<textMessageEncoding></span></span>
<span data-ttu-id="e9f6d-102">Especifica a codificação de caracteres e o controle de versão de mensagem usados para mensagens XML baseadas em texto.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="e9f6d-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e9f6d-103">\<system.serviceModel></span></span>  
<span data-ttu-id="e9f6d-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="e9f6d-104">\<bindings></span></span>  
<span data-ttu-id="e9f6d-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="e9f6d-105">\<customBinding></span></span>  
<span data-ttu-id="e9f6d-106">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="e9f6d-106">\<binding></span></span>  
<span data-ttu-id="e9f6d-107">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="e9f6d-107">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9f6d-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9f6d-108">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9f6d-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e9f6d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e9f6d-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9f6d-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="e9f6d-111">Attributes</span></span>  
  
|<span data-ttu-id="e9f6d-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="e9f6d-112">Attribute</span></span>|<span data-ttu-id="e9f6d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9f6d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e9f6d-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="e9f6d-114">maxReadPoolSize</span></span>|<span data-ttu-id="e9f6d-115">Um inteiro que especifica quantas mensagens podem ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-115">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="e9f6d-116">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="e9f6d-117">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-117">The default is 64.</span></span>|  
|<span data-ttu-id="e9f6d-118">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="e9f6d-118">maxWritePoolSize</span></span>|<span data-ttu-id="e9f6d-119">Um inteiro que especifica quantas mensagens podem ser enviadas simultaneamente sem alocar novos gravadores.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-119">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="e9f6d-120">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="e9f6d-121">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-121">The default is 16.</span></span>|  
|<span data-ttu-id="e9f6d-122">messageVersion</span><span class="sxs-lookup"><span data-stu-id="e9f6d-122">messageVersion</span></span>|<span data-ttu-id="e9f6d-123">Especifica a versão SOAP das mensagens enviadas usando a associação.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-123">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="e9f6d-124">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="e9f6d-124">Valid values are</span></span><br /><br /> <span data-ttu-id="e9f6d-125">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="e9f6d-125">-   Soap11Addressing10</span></span><br /><span data-ttu-id="e9f6d-126">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="e9f6d-126">-   Soap12Addressing10</span></span><br /><span data-ttu-id="e9f6d-127">-Soap11</span><span class="sxs-lookup"><span data-stu-id="e9f6d-127">-   Soap11</span></span><br /><span data-ttu-id="e9f6d-128">- Soap12</span><span class="sxs-lookup"><span data-stu-id="e9f6d-128">-  Soap12</span></span><br /><br /><span data-ttu-id="e9f6d-129">O padrão é Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-129">The default is Soap12Addressing10.</span></span> <span data-ttu-id="e9f6d-130">Esse atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-130">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="e9f6d-131">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="e9f6d-131">writeEncoding</span></span>|<span data-ttu-id="e9f6d-132">Especifica a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-132">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="e9f6d-133">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="e9f6d-133">Valid values are</span></span><br /><br /> <span data-ttu-id="e9f6d-134">-   UnicodeFffeTextEncoding: Codificação BigEndian Unicode</span><span class="sxs-lookup"><span data-stu-id="e9f6d-134">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="e9f6d-135">- Utf16TextEncoding: Codificação Unicode</span><span class="sxs-lookup"><span data-stu-id="e9f6d-135">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="e9f6d-136">- Utf8TextEncoding: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="e9f6d-136">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="e9f6d-137">O padrão é Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-137">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="e9f6d-138">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-138">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9f6d-139">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e9f6d-139">Child Elements</span></span>  
  
|<span data-ttu-id="e9f6d-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="e9f6d-140">Element</span></span>|<span data-ttu-id="e9f6d-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9f6d-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9f6d-142">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e9f6d-142">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="e9f6d-143">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-143">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="e9f6d-144">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-144">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9f6d-145">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e9f6d-145">Parent Elements</span></span>  
  
|<span data-ttu-id="e9f6d-146">Elemento</span><span class="sxs-lookup"><span data-stu-id="e9f6d-146">Element</span></span>|<span data-ttu-id="e9f6d-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9f6d-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9f6d-148">\<binding></span><span class="sxs-lookup"><span data-stu-id="e9f6d-148">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="e9f6d-149">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-149">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9f6d-150">Comentários</span><span class="sxs-lookup"><span data-stu-id="e9f6d-150">Remarks</span></span>  
 <span data-ttu-id="e9f6d-151">A codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-151">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="e9f6d-152">A decodificação é o processo reverso.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-152">Decoding is the reverse process.</span></span> <span data-ttu-id="e9f6d-153">O Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: O mecanismo de otimização de transmissão de mensagens e de texto, binário e mensagem (MTOM).</span><span class="sxs-lookup"><span data-stu-id="e9f6d-153">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="e9f6d-154">A codificação de texto representada pelo `textMessageEncoding` elemento é o mais interoperável, mas o codificador menos eficiente para mensagens XML.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-154">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="e9f6d-155">O codificador de texto cria mensagens baseadas em texto na conexão.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-155">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="e9f6d-156">As mensagens produzidas por esse codificador são adequadas para a interoperabilidade baseada em WS-\*.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-156">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="e9f6d-157">O serviço Web ou o cliente de serviço Web geralmente pode entender XML textual.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-157">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="e9f6d-158">No entanto, a transmissão de grandes blocos de dados binários como texto é o método menos eficiente para codificar mensagens XML.</span><span class="sxs-lookup"><span data-stu-id="e9f6d-158">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9f6d-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e9f6d-159">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="e9f6d-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9f6d-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="e9f6d-161">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="e9f6d-161">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="e9f6d-162">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="e9f6d-162">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="e9f6d-163">Associações</span><span class="sxs-lookup"><span data-stu-id="e9f6d-163">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e9f6d-164">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="e9f6d-164">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e9f6d-165">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="e9f6d-165">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="e9f6d-166">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="e9f6d-166">\<customBinding></span></span>](custombinding.md)
