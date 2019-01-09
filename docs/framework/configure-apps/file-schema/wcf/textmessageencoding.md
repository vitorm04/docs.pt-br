---
title: '&lt;textMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: 0ee50a4b5adeede2dd531ba734ac9fb420f3b713
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150234"
---
# <a name="lttextmessageencodinggt"></a><span data-ttu-id="ca58b-102">&lt;textMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="ca58b-102">&lt;textMessageEncoding&gt;</span></span>
<span data-ttu-id="ca58b-103">Especifica a codificação de caracteres e a mensagem de controle de versão usado para mensagens XML baseadas em texto.</span><span class="sxs-lookup"><span data-stu-id="ca58b-103">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="ca58b-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ca58b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="ca58b-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="ca58b-105">\<bindings></span></span>  
<span data-ttu-id="ca58b-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ca58b-106">\<customBinding></span></span>  
<span data-ttu-id="ca58b-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="ca58b-107">\<binding></span></span>  
<span data-ttu-id="ca58b-108">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="ca58b-108">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca58b-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca58b-109">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca58b-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ca58b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ca58b-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ca58b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca58b-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="ca58b-112">Attributes</span></span>  
  
|<span data-ttu-id="ca58b-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="ca58b-113">Attribute</span></span>|<span data-ttu-id="ca58b-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca58b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ca58b-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="ca58b-115">maxReadPoolSize</span></span>|<span data-ttu-id="ca58b-116">Um inteiro que especifica quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="ca58b-116">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="ca58b-117">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="ca58b-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="ca58b-118">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="ca58b-118">The default is 64.</span></span>|  
|<span data-ttu-id="ca58b-119">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="ca58b-119">maxWritePoolSize</span></span>|<span data-ttu-id="ca58b-120">Um inteiro que especifica quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="ca58b-120">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="ca58b-121">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="ca58b-121">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="ca58b-122">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="ca58b-122">The default is 16.</span></span>|  
|<span data-ttu-id="ca58b-123">messageVersion</span><span class="sxs-lookup"><span data-stu-id="ca58b-123">messageVersion</span></span>|<span data-ttu-id="ca58b-124">Especifica a versão SOAP das mensagens enviadas usando a associação.</span><span class="sxs-lookup"><span data-stu-id="ca58b-124">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="ca58b-125">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="ca58b-125">Valid values are</span></span><br /><br /> <span data-ttu-id="ca58b-126">-Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="ca58b-126">-   Soap11Addressing10</span></span><br /><span data-ttu-id="ca58b-127">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="ca58b-127">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="ca58b-128">O padrão é Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="ca58b-128">The default is Soap12Addressing10.</span></span> <span data-ttu-id="ca58b-129">Esse atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="ca58b-129">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="ca58b-130">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="ca58b-130">writeEncoding</span></span>|<span data-ttu-id="ca58b-131">Especifica a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ca58b-131">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="ca58b-132">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="ca58b-132">Valid values are</span></span><br /><br /> <span data-ttu-id="ca58b-133">-UnicodeFffeTextEncoding: Unicode BigEndian de codificação</span><span class="sxs-lookup"><span data-stu-id="ca58b-133">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="ca58b-134">-Utf16TextEncoding: Codificação Unicode</span><span class="sxs-lookup"><span data-stu-id="ca58b-134">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="ca58b-135">-Utf8TextEncoding: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="ca58b-135">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="ca58b-136">O padrão é Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="ca58b-136">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="ca58b-137">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="ca58b-137">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca58b-138">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ca58b-138">Child Elements</span></span>  
  
|<span data-ttu-id="ca58b-139">Elemento</span><span class="sxs-lookup"><span data-stu-id="ca58b-139">Element</span></span>|<span data-ttu-id="ca58b-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca58b-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca58b-141">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="ca58b-141">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="ca58b-142">Define as restrições na complexidade das mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="ca58b-142">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="ca58b-143">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="ca58b-143">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca58b-144">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ca58b-144">Parent Elements</span></span>  
  
|<span data-ttu-id="ca58b-145">Elemento</span><span class="sxs-lookup"><span data-stu-id="ca58b-145">Element</span></span>|<span data-ttu-id="ca58b-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca58b-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca58b-147">\<associação ></span><span class="sxs-lookup"><span data-stu-id="ca58b-147">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="ca58b-148">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="ca58b-148">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca58b-149">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca58b-149">Remarks</span></span>  
 <span data-ttu-id="ca58b-150">Codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="ca58b-150">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="ca58b-151">Decodificação de é o processo inverso.</span><span class="sxs-lookup"><span data-stu-id="ca58b-151">Decoding is the reverse process.</span></span> <span data-ttu-id="ca58b-152">Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: Texto, binária e mecanismo de otimização de transmissão de mensagens (MTOM).</span><span class="sxs-lookup"><span data-stu-id="ca58b-152">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="ca58b-153">A codificação de texto representado pelo `textMessageEncoding` elemento é o mais interoperável, mas o codificador menos eficiente para mensagens XML.</span><span class="sxs-lookup"><span data-stu-id="ca58b-153">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="ca58b-154">O codificador de texto cria mensagens baseadas em texto durante a transmissão.</span><span class="sxs-lookup"><span data-stu-id="ca58b-154">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="ca58b-155">As mensagens geradas por esse codificador são adequadas para WS-\* com base em interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="ca58b-155">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="ca58b-156">Serviço Web ou o cliente do serviço Web geralmente pode compreender XML textual.</span><span class="sxs-lookup"><span data-stu-id="ca58b-156">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="ca58b-157">No entanto, a transmissão de blocos grandes de dados binários como texto é o método menos eficiente para codificação de mensagens XML.</span><span class="sxs-lookup"><span data-stu-id="ca58b-157">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca58b-158">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ca58b-158">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="ca58b-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca58b-159">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 [<span data-ttu-id="ca58b-160">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="ca58b-160">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="ca58b-161">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="ca58b-161">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="ca58b-162">Associações</span><span class="sxs-lookup"><span data-stu-id="ca58b-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="ca58b-163">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="ca58b-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="ca58b-164">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="ca58b-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="ca58b-165">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ca58b-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
