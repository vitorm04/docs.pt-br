---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: d67d623736f3cbf50568356132a74d2b234fdfd9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736212"
---
# <a name="textmessageencoding"></a><span data-ttu-id="84960-101">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="84960-101">\<textMessageEncoding></span></span>
<span data-ttu-id="84960-102">Especifica a codificação de caracteres e o controle de versão de mensagem usados para mensagens XML baseadas em texto.</span><span class="sxs-lookup"><span data-stu-id="84960-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
<span data-ttu-id="84960-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="84960-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="84960-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="84960-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="84960-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="84960-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="84960-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) ></span><span class="sxs-lookup"><span data-stu-id="84960-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="84960-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="84960-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="84960-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<textMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="84960-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<textMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84960-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84960-109">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84960-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="84960-110">Attributes and Elements</span></span>  
 <span data-ttu-id="84960-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="84960-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84960-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="84960-112">Attributes</span></span>  
  
|<span data-ttu-id="84960-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="84960-113">Attribute</span></span>|<span data-ttu-id="84960-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="84960-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="84960-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="84960-115">maxReadPoolSize</span></span>|<span data-ttu-id="84960-116">Um inteiro que especifica quantas mensagens podem ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="84960-116">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="84960-117">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="84960-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="84960-118">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="84960-118">The default is 64.</span></span>|  
|<span data-ttu-id="84960-119">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="84960-119">maxWritePoolSize</span></span>|<span data-ttu-id="84960-120">Um inteiro que especifica quantas mensagens podem ser enviadas simultaneamente sem alocar novos gravadores.</span><span class="sxs-lookup"><span data-stu-id="84960-120">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="84960-121">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="84960-121">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="84960-122">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="84960-122">The default is 16.</span></span>|  
|<span data-ttu-id="84960-123">messageVersion</span><span class="sxs-lookup"><span data-stu-id="84960-123">messageVersion</span></span>|<span data-ttu-id="84960-124">Especifica a versão SOAP das mensagens enviadas usando a associação.</span><span class="sxs-lookup"><span data-stu-id="84960-124">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="84960-125">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="84960-125">Valid values are</span></span><br /><br /> <span data-ttu-id="84960-126">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="84960-126">-   Soap11Addressing10</span></span><br /><span data-ttu-id="84960-127">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="84960-127">-   Soap12Addressing10</span></span><br /><span data-ttu-id="84960-128">-Soap11</span><span class="sxs-lookup"><span data-stu-id="84960-128">-   Soap11</span></span><br /><span data-ttu-id="84960-129">- Soap12</span><span class="sxs-lookup"><span data-stu-id="84960-129">-  Soap12</span></span><br /><br /><span data-ttu-id="84960-130">O padrão é Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="84960-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="84960-131">Este atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="84960-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="84960-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="84960-132">writeEncoding</span></span>|<span data-ttu-id="84960-133">Especifica a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="84960-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="84960-134">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="84960-134">Valid values are</span></span><br /><br /> <span data-ttu-id="84960-135">-UnicodeFffeTextEncoding: codificação BigEndian Unicode</span><span class="sxs-lookup"><span data-stu-id="84960-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="84960-136">-Utf16TextEncoding: codificação Unicode</span><span class="sxs-lookup"><span data-stu-id="84960-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="84960-137">-Utf8TextEncoding: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="84960-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="84960-138">O padrão é Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="84960-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="84960-139">Este atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="84960-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84960-140">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="84960-140">Child Elements</span></span>  
  
|<span data-ttu-id="84960-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="84960-141">Element</span></span>|<span data-ttu-id="84960-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="84960-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="84960-143">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="84960-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="84960-144">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="84960-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="84960-145">Este elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="84960-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="84960-146">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="84960-146">Parent Elements</span></span>  
  
|<span data-ttu-id="84960-147">Elemento</span><span class="sxs-lookup"><span data-stu-id="84960-147">Element</span></span>|<span data-ttu-id="84960-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="84960-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84960-149">\<binding ></span><span class="sxs-lookup"><span data-stu-id="84960-149">\<binding></span></span>](bindings.md)|<span data-ttu-id="84960-150">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="84960-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84960-151">Comentários</span><span class="sxs-lookup"><span data-stu-id="84960-151">Remarks</span></span>  
 <span data-ttu-id="84960-152">A codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="84960-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="84960-153">A decodificação é o processo reverso.</span><span class="sxs-lookup"><span data-stu-id="84960-153">Decoding is the reverse process.</span></span> <span data-ttu-id="84960-154">O Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: texto, binário e MTOM (mecanismo de otimização de transmissão de mensagens).</span><span class="sxs-lookup"><span data-stu-id="84960-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="84960-155">A codificação de texto representada pelo elemento `textMessageEncoding` é a mais interoperável, mas o codificador menos eficiente para mensagens XML.</span><span class="sxs-lookup"><span data-stu-id="84960-155">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="84960-156">O codificador de texto cria mensagens baseadas em texto na conexão.</span><span class="sxs-lookup"><span data-stu-id="84960-156">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="84960-157">As mensagens produzidas por esse codificador são adequadas para a interoperabilidade baseada em WS-\*.</span><span class="sxs-lookup"><span data-stu-id="84960-157">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="84960-158">O serviço Web ou o cliente de serviço Web geralmente pode entender XML textual.</span><span class="sxs-lookup"><span data-stu-id="84960-158">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="84960-159">No entanto, a transmissão de grandes blocos de dados binários como texto é o método menos eficiente para codificar mensagens XML.</span><span class="sxs-lookup"><span data-stu-id="84960-159">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84960-160">Exemplo</span><span class="sxs-lookup"><span data-stu-id="84960-160">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="84960-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84960-161">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="84960-162">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="84960-162">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="84960-163">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="84960-163">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="84960-164">Associações</span><span class="sxs-lookup"><span data-stu-id="84960-164">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="84960-165">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="84960-165">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="84960-166">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="84960-166">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="84960-167">\<CustomBinding</span><span class="sxs-lookup"><span data-stu-id="84960-167">\<customBinding></span></span>](custombinding.md)
