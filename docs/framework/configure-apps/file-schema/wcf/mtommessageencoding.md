---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 70a124fda5bc0e52e1271716f7e2166b7717b49a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933197"
---
# <a name="mtommessageencoding"></a><span data-ttu-id="bbf4f-101">\<mtomMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="bbf4f-101">\<mtomMessageEncoding></span></span>
<span data-ttu-id="bbf4f-102">Especifica a codificação e o controle de versão de mensagem usados para mensagens baseadas no mecanismo de otimização de transmissão de mensagens SOAP (MTOM).</span><span class="sxs-lookup"><span data-stu-id="bbf4f-102">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
 <span data-ttu-id="bbf4f-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bbf4f-103">\<system.serviceModel></span></span>  
<span data-ttu-id="bbf4f-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="bbf4f-104">\<bindings></span></span>  
<span data-ttu-id="bbf4f-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="bbf4f-105">\<customBinding></span></span>  
<span data-ttu-id="bbf4f-106">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="bbf4f-106">\<binding></span></span>  
<span data-ttu-id="bbf4f-107">\<mtomMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="bbf4f-107">\<mtomMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbf4f-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bbf4f-108">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbf4f-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bbf4f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bbf4f-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bbf4f-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="bbf4f-111">Attributes</span></span>  
  
|<span data-ttu-id="bbf4f-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="bbf4f-112">Attribute</span></span>|<span data-ttu-id="bbf4f-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="bbf4f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bbf4f-114">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="bbf4f-114">maxBufferSize</span></span>|<span data-ttu-id="bbf4f-115">Um inteiro que especifica o tamanho máximo do buffer que pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-115">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="bbf4f-116">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="bbf4f-116">maxReadPoolSize</span></span>|<span data-ttu-id="bbf4f-117">Um inteiro que especifica quantas mensagens podem ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-117">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="bbf4f-118">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-118">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="bbf4f-119">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-119">The default is 64.</span></span>|  
|<span data-ttu-id="bbf4f-120">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="bbf4f-120">maxWritePoolSize</span></span>|<span data-ttu-id="bbf4f-121">Um inteiro que especifica quantas mensagens podem ser enviadas simultaneamente sem alocar novos gravadores.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-121">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="bbf4f-122">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-122">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="bbf4f-123">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-123">The default is 16.</span></span>|  
|<span data-ttu-id="bbf4f-124">messageVersion</span><span class="sxs-lookup"><span data-stu-id="bbf4f-124">messageVersion</span></span>|<span data-ttu-id="bbf4f-125">Especifica a versão SOAP das mensagens enviadas usando a associação.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-125">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="bbf4f-126">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="bbf4f-126">Valid values are</span></span><br /><br /> <span data-ttu-id="bbf4f-127">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="bbf4f-127">-   Soap11Addressing1</span></span><br /><span data-ttu-id="bbf4f-128">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="bbf4f-128">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="bbf4f-129">O padrão é Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-129">The default is Soap12Addressing10.</span></span> <span data-ttu-id="bbf4f-130">Esse atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-130">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="bbf4f-131">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="bbf4f-131">writeEncoding</span></span>|<span data-ttu-id="bbf4f-132">Especifica a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-132">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="bbf4f-133">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="bbf4f-133">Valid values are</span></span><br /><br /> <span data-ttu-id="bbf4f-134">-   UnicodeFffeTextEncoding: Codificação BigEndian Unicode</span><span class="sxs-lookup"><span data-stu-id="bbf4f-134">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="bbf4f-135">- Utf16TextEncoding: Codificação Unicode</span><span class="sxs-lookup"><span data-stu-id="bbf4f-135">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="bbf4f-136">- Utf8TextEncoding: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="bbf4f-136">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="bbf4f-137">O padrão é Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-137">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="bbf4f-138">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-138">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bbf4f-139">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bbf4f-139">Child Elements</span></span>  
  
|<span data-ttu-id="bbf4f-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="bbf4f-140">Element</span></span>|<span data-ttu-id="bbf4f-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="bbf4f-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bbf4f-142">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bbf4f-142">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="bbf4f-143">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-143">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="bbf4f-144">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-144">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bbf4f-145">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bbf4f-145">Parent Elements</span></span>  
  
|<span data-ttu-id="bbf4f-146">Elemento</span><span class="sxs-lookup"><span data-stu-id="bbf4f-146">Element</span></span>|<span data-ttu-id="bbf4f-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="bbf4f-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bbf4f-148">\<binding></span><span class="sxs-lookup"><span data-stu-id="bbf4f-148">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="bbf4f-149">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-149">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbf4f-150">Comentários</span><span class="sxs-lookup"><span data-stu-id="bbf4f-150">Remarks</span></span>  
 <span data-ttu-id="bbf4f-151">A codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-151">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="bbf4f-152">A decodificação é o processo reverso.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-152">Decoding is the reverse process.</span></span> <span data-ttu-id="bbf4f-153">O Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: O mecanismo de otimização de transmissão de mensagens e de texto, binário e mensagem (MTOM).</span><span class="sxs-lookup"><span data-stu-id="bbf4f-153">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="bbf4f-154">O `MtomMessageEncoding` elemento Especifica a codificação de caracteres e o controle de versão de mensagem e outras configurações usadas para mensagens usando uma codificação MTOM (mecanismo de otimização de transmissão de mensagens).</span><span class="sxs-lookup"><span data-stu-id="bbf4f-154">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="bbf4f-155">O MTOM é uma tecnologia eficiente para transmitir dados binários em mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-155">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="bbf4f-156">O codificador MTOM tenta criar um equilíbrio entre eficiência e interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-156">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="bbf4f-157">A codificação MTOM transmite a maioria dos XML na forma textual, mas otimiza grandes blocos de dados binários transmitindo-os como estão, sem conversão para seu formato codificado em base64.</span><span class="sxs-lookup"><span data-stu-id="bbf4f-157">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbf4f-158">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bbf4f-158">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="bbf4f-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbf4f-159">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="bbf4f-160">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="bbf4f-160">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="bbf4f-161">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="bbf4f-161">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="bbf4f-162">Associações</span><span class="sxs-lookup"><span data-stu-id="bbf4f-162">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bbf4f-163">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="bbf4f-163">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="bbf4f-164">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="bbf4f-164">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="bbf4f-165">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="bbf4f-165">\<customBinding></span></span>](custombinding.md)
