---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: d67d623736f3cbf50568356132a74d2b234fdfd9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736212"
---
# \<textMessageEncoding>
<span data-ttu-id="ddff1-101">Especifica a codificação de caracteres e o controle de versão de mensagem usados para mensagens XML baseadas em texto.</span><span class="sxs-lookup"><span data-stu-id="ddff1-101">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<textMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="ddff1-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ddff1-102">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ddff1-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ddff1-103">Attributes and Elements</span></span>  
 <span data-ttu-id="ddff1-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ddff1-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ddff1-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="ddff1-105">Attributes</span></span>  
  
|<span data-ttu-id="ddff1-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="ddff1-106">Attribute</span></span>|<span data-ttu-id="ddff1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ddff1-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ddff1-108">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="ddff1-108">maxReadPoolSize</span></span>|<span data-ttu-id="ddff1-109">Um inteiro que especifica quantas mensagens podem ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="ddff1-109">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="ddff1-110">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="ddff1-110">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="ddff1-111">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="ddff1-111">The default is 64.</span></span>|  
|<span data-ttu-id="ddff1-112">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="ddff1-112">maxWritePoolSize</span></span>|<span data-ttu-id="ddff1-113">Um inteiro que especifica quantas mensagens podem ser enviadas simultaneamente sem alocar novos gravadores.</span><span class="sxs-lookup"><span data-stu-id="ddff1-113">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="ddff1-114">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="ddff1-114">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="ddff1-115">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="ddff1-115">The default is 16.</span></span>|  
|<span data-ttu-id="ddff1-116">messageVersion</span><span class="sxs-lookup"><span data-stu-id="ddff1-116">messageVersion</span></span>|<span data-ttu-id="ddff1-117">Especifica a versão SOAP das mensagens enviadas usando a associação.</span><span class="sxs-lookup"><span data-stu-id="ddff1-117">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="ddff1-118">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="ddff1-118">Valid values are</span></span><br /><br /> <span data-ttu-id="ddff1-119">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="ddff1-119">-   Soap11Addressing10</span></span><br /><span data-ttu-id="ddff1-120">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="ddff1-120">-   Soap12Addressing10</span></span><br /><span data-ttu-id="ddff1-121">-Soap11</span><span class="sxs-lookup"><span data-stu-id="ddff1-121">-   Soap11</span></span><br /><span data-ttu-id="ddff1-122">- Soap12</span><span class="sxs-lookup"><span data-stu-id="ddff1-122">-  Soap12</span></span><br /><br /><span data-ttu-id="ddff1-123">O padrão é Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="ddff1-123">The default is Soap12Addressing10.</span></span> <span data-ttu-id="ddff1-124">Esse atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion> .</span><span class="sxs-lookup"><span data-stu-id="ddff1-124">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="ddff1-125">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="ddff1-125">writeEncoding</span></span>|<span data-ttu-id="ddff1-126">Especifica a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="ddff1-126">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="ddff1-127">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="ddff1-127">Valid values are</span></span><br /><br /> <span data-ttu-id="ddff1-128">-UnicodeFffeTextEncoding: codificação BigEndian Unicode</span><span class="sxs-lookup"><span data-stu-id="ddff1-128">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="ddff1-129">-Utf16TextEncoding: codificação Unicode</span><span class="sxs-lookup"><span data-stu-id="ddff1-129">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="ddff1-130">-Utf8TextEncoding: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="ddff1-130">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="ddff1-131">O padrão é Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="ddff1-131">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="ddff1-132">Esse atributo é do tipo <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="ddff1-132">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ddff1-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ddff1-133">Child Elements</span></span>  
  
|<span data-ttu-id="ddff1-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="ddff1-134">Element</span></span>|<span data-ttu-id="ddff1-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="ddff1-135">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="ddff1-136">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="ddff1-136">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="ddff1-137">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="ddff1-137">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ddff1-138">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ddff1-138">Parent Elements</span></span>  
  
|<span data-ttu-id="ddff1-139">Elemento</span><span class="sxs-lookup"><span data-stu-id="ddff1-139">Element</span></span>|<span data-ttu-id="ddff1-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="ddff1-140">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="ddff1-141">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="ddff1-141">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddff1-142">Comentários</span><span class="sxs-lookup"><span data-stu-id="ddff1-142">Remarks</span></span>  
 <span data-ttu-id="ddff1-143">A codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="ddff1-143">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="ddff1-144">A decodificação é o processo reverso.</span><span class="sxs-lookup"><span data-stu-id="ddff1-144">Decoding is the reverse process.</span></span> <span data-ttu-id="ddff1-145">O Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: texto, binário e MTOM (mecanismo de otimização de transmissão de mensagens).</span><span class="sxs-lookup"><span data-stu-id="ddff1-145">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="ddff1-146">A codificação de texto representada pelo `textMessageEncoding` elemento é o mais interoperável, mas o codificador menos eficiente para mensagens XML.</span><span class="sxs-lookup"><span data-stu-id="ddff1-146">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="ddff1-147">O codificador de texto cria mensagens baseadas em texto na conexão.</span><span class="sxs-lookup"><span data-stu-id="ddff1-147">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="ddff1-148">As mensagens produzidas por esse codificador são adequadas para a interoperabilidade baseada em WS-\*.</span><span class="sxs-lookup"><span data-stu-id="ddff1-148">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="ddff1-149">O serviço Web ou o cliente de serviço Web geralmente pode entender XML textual.</span><span class="sxs-lookup"><span data-stu-id="ddff1-149">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="ddff1-150">No entanto, a transmissão de grandes blocos de dados binários como texto é o método menos eficiente para codificar mensagens XML.</span><span class="sxs-lookup"><span data-stu-id="ddff1-150">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddff1-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ddff1-151">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="ddff1-152">Confira também</span><span class="sxs-lookup"><span data-stu-id="ddff1-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="ddff1-153">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="ddff1-153">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="ddff1-154">Decodificador de mensagens</span><span class="sxs-lookup"><span data-stu-id="ddff1-154">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="ddff1-155">Associações</span><span class="sxs-lookup"><span data-stu-id="ddff1-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ddff1-156">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="ddff1-156">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ddff1-157">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="ddff1-157">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
