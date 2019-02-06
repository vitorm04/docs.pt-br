---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: 6485bbd751d6467628f2191c3f5f0c6cc8a3db2f
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55758645"
---
# <a name="textmessageencoding"></a><span data-ttu-id="3f835-101">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="3f835-101">\<textMessageEncoding></span></span>
<span data-ttu-id="3f835-102">Especifica a codificação de caracteres e a mensagem de controle de versão usado para mensagens XML baseadas em texto.</span><span class="sxs-lookup"><span data-stu-id="3f835-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="3f835-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3f835-103">\<system.serviceModel></span></span>  
<span data-ttu-id="3f835-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="3f835-104">\<bindings></span></span>  
<span data-ttu-id="3f835-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3f835-105">\<customBinding></span></span>  
<span data-ttu-id="3f835-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="3f835-106">\<binding></span></span>  
<span data-ttu-id="3f835-107">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="3f835-107">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f835-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3f835-108">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f835-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3f835-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3f835-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3f835-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f835-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="3f835-111">Attributes</span></span>  
  
|<span data-ttu-id="3f835-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="3f835-112">Attribute</span></span>|<span data-ttu-id="3f835-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3f835-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3f835-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="3f835-114">maxReadPoolSize</span></span>|<span data-ttu-id="3f835-115">Um inteiro que especifica quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="3f835-115">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="3f835-116">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="3f835-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="3f835-117">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="3f835-117">The default is 64.</span></span>|  
|<span data-ttu-id="3f835-118">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="3f835-118">maxWritePoolSize</span></span>|<span data-ttu-id="3f835-119">Um inteiro que especifica quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="3f835-119">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="3f835-120">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="3f835-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="3f835-121">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="3f835-121">The default is 16.</span></span>|  
|<span data-ttu-id="3f835-122">messageVersion</span><span class="sxs-lookup"><span data-stu-id="3f835-122">messageVersion</span></span>|<span data-ttu-id="3f835-123">Especifica a versão SOAP das mensagens enviadas usando a associação.</span><span class="sxs-lookup"><span data-stu-id="3f835-123">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="3f835-124">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="3f835-124">Valid values are</span></span><br /><br /> <span data-ttu-id="3f835-125">-Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="3f835-125">-   Soap11Addressing10</span></span><br /><span data-ttu-id="3f835-126">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="3f835-126">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="3f835-127">O padrão é Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="3f835-127">The default is Soap12Addressing10.</span></span> <span data-ttu-id="3f835-128">Esse atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="3f835-128">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="3f835-129">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="3f835-129">writeEncoding</span></span>|<span data-ttu-id="3f835-130">Especifica a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3f835-130">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="3f835-131">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="3f835-131">Valid values are</span></span><br /><br /> <span data-ttu-id="3f835-132">-   UnicodeFffeTextEncoding: Unicode BigEndian de codificação</span><span class="sxs-lookup"><span data-stu-id="3f835-132">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="3f835-133">-Utf16TextEncoding: Codificação Unicode</span><span class="sxs-lookup"><span data-stu-id="3f835-133">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="3f835-134">-   Utf8TextEncoding: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="3f835-134">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="3f835-135">O padrão é Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="3f835-135">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="3f835-136">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="3f835-136">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f835-137">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3f835-137">Child Elements</span></span>  
  
|<span data-ttu-id="3f835-138">Elemento</span><span class="sxs-lookup"><span data-stu-id="3f835-138">Element</span></span>|<span data-ttu-id="3f835-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="3f835-139">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3f835-140">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3f835-140">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="3f835-141">Define as restrições na complexidade das mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="3f835-141">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="3f835-142">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="3f835-142">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3f835-143">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3f835-143">Parent Elements</span></span>  
  
|<span data-ttu-id="3f835-144">Elemento</span><span class="sxs-lookup"><span data-stu-id="3f835-144">Element</span></span>|<span data-ttu-id="3f835-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="3f835-145">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f835-146">\<binding></span><span class="sxs-lookup"><span data-stu-id="3f835-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="3f835-147">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="3f835-147">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f835-148">Comentários</span><span class="sxs-lookup"><span data-stu-id="3f835-148">Remarks</span></span>  
 <span data-ttu-id="3f835-149">Codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="3f835-149">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="3f835-150">Decodificação de é o processo inverso.</span><span class="sxs-lookup"><span data-stu-id="3f835-150">Decoding is the reverse process.</span></span> <span data-ttu-id="3f835-151">Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: Texto, binária e mecanismo de otimização de transmissão de mensagens (MTOM).</span><span class="sxs-lookup"><span data-stu-id="3f835-151">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="3f835-152">A codificação de texto representado pelo `textMessageEncoding` elemento é o mais interoperável, mas o codificador menos eficiente para mensagens XML.</span><span class="sxs-lookup"><span data-stu-id="3f835-152">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="3f835-153">O codificador de texto cria mensagens baseadas em texto durante a transmissão.</span><span class="sxs-lookup"><span data-stu-id="3f835-153">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="3f835-154">As mensagens geradas por esse codificador são adequadas para WS-\* com base em interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="3f835-154">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="3f835-155">Serviço Web ou o cliente do serviço Web geralmente pode compreender XML textual.</span><span class="sxs-lookup"><span data-stu-id="3f835-155">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="3f835-156">No entanto, a transmissão de blocos grandes de dados binários como texto é o método menos eficiente para codificação de mensagens XML.</span><span class="sxs-lookup"><span data-stu-id="3f835-156">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f835-157">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3f835-157">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="3f835-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f835-158">See also</span></span>
- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="3f835-159">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="3f835-159">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="3f835-160">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="3f835-160">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="3f835-161">Associações</span><span class="sxs-lookup"><span data-stu-id="3f835-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="3f835-162">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="3f835-162">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3f835-163">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="3f835-163">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="3f835-164">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3f835-164">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
