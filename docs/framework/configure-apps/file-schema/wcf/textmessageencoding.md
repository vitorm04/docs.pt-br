---
title: '&lt;textMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: e684c21c0b1360a9b270214ebe7b3ad00b42657f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43554494"
---
# <a name="lttextmessageencodinggt"></a><span data-ttu-id="71f37-102">&lt;textMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="71f37-102">&lt;textMessageEncoding&gt;</span></span>
<span data-ttu-id="71f37-103">Especifica a codificação de caracteres e a mensagem de controle de versão usado para mensagens XML baseadas em texto.</span><span class="sxs-lookup"><span data-stu-id="71f37-103">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="71f37-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="71f37-104">\<system.serviceModel></span></span>  
<span data-ttu-id="71f37-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="71f37-105">\<bindings></span></span>  
<span data-ttu-id="71f37-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="71f37-106">\<customBinding></span></span>  
<span data-ttu-id="71f37-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="71f37-107">\<binding></span></span>  
<span data-ttu-id="71f37-108">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="71f37-108">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71f37-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="71f37-109">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing10/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71f37-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="71f37-110">Attributes and Elements</span></span>  
 <span data-ttu-id="71f37-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="71f37-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71f37-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="71f37-112">Attributes</span></span>  
  
|<span data-ttu-id="71f37-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="71f37-113">Attribute</span></span>|<span data-ttu-id="71f37-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="71f37-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="71f37-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="71f37-115">maxReadPoolSize</span></span>|<span data-ttu-id="71f37-116">Um inteiro que especifica quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="71f37-116">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="71f37-117">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="71f37-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="71f37-118">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="71f37-118">The default is 64.</span></span>|  
|<span data-ttu-id="71f37-119">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="71f37-119">maxWritePoolSize</span></span>|<span data-ttu-id="71f37-120">Um inteiro que especifica quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="71f37-120">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="71f37-121">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="71f37-121">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="71f37-122">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="71f37-122">The default is 16.</span></span>|  
|<span data-ttu-id="71f37-123">messageVersion</span><span class="sxs-lookup"><span data-stu-id="71f37-123">messageVersion</span></span>|<span data-ttu-id="71f37-124">Especifica a versão SOAP das mensagens enviadas usando a associação.</span><span class="sxs-lookup"><span data-stu-id="71f37-124">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="71f37-125">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="71f37-125">Valid values are</span></span><br /><br /> <span data-ttu-id="71f37-126">-Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="71f37-126">-   Soap11Addressing10</span></span><br /><span data-ttu-id="71f37-127">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="71f37-127">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="71f37-128">O padrão é Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="71f37-128">The default is Soap12Addressing10.</span></span> <span data-ttu-id="71f37-129">Esse atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="71f37-129">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="71f37-130">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="71f37-130">writeEncoding</span></span>|<span data-ttu-id="71f37-131">Especifica a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="71f37-131">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="71f37-132">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="71f37-132">Valid values are</span></span><br /><br /> <span data-ttu-id="71f37-133">-UnicodeFffeTextEncoding: Unicode BigEndian codificação</span><span class="sxs-lookup"><span data-stu-id="71f37-133">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="71f37-134">-Utf16TextEncoding: Codificação de Unicode</span><span class="sxs-lookup"><span data-stu-id="71f37-134">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="71f37-135">-Utf8TextEncoding: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="71f37-135">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="71f37-136">O padrão é Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="71f37-136">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="71f37-137">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="71f37-137">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71f37-138">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="71f37-138">Child Elements</span></span>  
  
|<span data-ttu-id="71f37-139">Elemento</span><span class="sxs-lookup"><span data-stu-id="71f37-139">Element</span></span>|<span data-ttu-id="71f37-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="71f37-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="71f37-141">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="71f37-141">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="71f37-142">Define as restrições na complexidade das mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="71f37-142">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="71f37-143">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="71f37-143">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="71f37-144">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="71f37-144">Parent Elements</span></span>  
  
|<span data-ttu-id="71f37-145">Elemento</span><span class="sxs-lookup"><span data-stu-id="71f37-145">Element</span></span>|<span data-ttu-id="71f37-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="71f37-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="71f37-147">\<associação ></span><span class="sxs-lookup"><span data-stu-id="71f37-147">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="71f37-148">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="71f37-148">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71f37-149">Comentários</span><span class="sxs-lookup"><span data-stu-id="71f37-149">Remarks</span></span>  
 <span data-ttu-id="71f37-150">Codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="71f37-150">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="71f37-151">Decodificação de é o processo inverso.</span><span class="sxs-lookup"><span data-stu-id="71f37-151">Decoding is the reverse process.</span></span> <span data-ttu-id="71f37-152">Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: texto, binária e MTOM Message Transmission Optimization Mechanism ().</span><span class="sxs-lookup"><span data-stu-id="71f37-152">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="71f37-153">A codificação de texto representado pelo `textMessageEncoding` elemento é o mais interoperável, mas o codificador menos eficiente para mensagens XML.</span><span class="sxs-lookup"><span data-stu-id="71f37-153">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="71f37-154">O codificador de texto cria mensagens baseadas em texto durante a transmissão.</span><span class="sxs-lookup"><span data-stu-id="71f37-154">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="71f37-155">As mensagens geradas por esse codificador são adequadas para WS-\* com base em interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="71f37-155">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="71f37-156">Serviço Web ou o cliente do serviço Web geralmente pode compreender XML textual.</span><span class="sxs-lookup"><span data-stu-id="71f37-156">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="71f37-157">No entanto, a transmissão de blocos grandes de dados binários como texto é o método menos eficiente para codificação de mensagens XML.</span><span class="sxs-lookup"><span data-stu-id="71f37-157">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71f37-158">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71f37-158">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap12Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="71f37-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71f37-159">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 [<span data-ttu-id="71f37-160">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="71f37-160">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="71f37-161">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="71f37-161">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="71f37-162">Associações</span><span class="sxs-lookup"><span data-stu-id="71f37-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="71f37-163">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="71f37-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="71f37-164">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="71f37-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="71f37-165">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="71f37-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
