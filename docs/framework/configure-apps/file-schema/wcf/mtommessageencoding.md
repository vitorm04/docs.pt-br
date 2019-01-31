---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: be0a11c71083c713042ab572cb78fbae27d52912
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277687"
---
# <a name="mtommessageencoding"></a><span data-ttu-id="8857e-101">\<mtomMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="8857e-101">\<mtomMessageEncoding></span></span>
<span data-ttu-id="8857e-102">Especifica o controle de versão de codificação e de mensagem usado para mensagens SOAP MTOM Message Transmission Optimization Mechanism () com base.</span><span class="sxs-lookup"><span data-stu-id="8857e-102">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
 <span data-ttu-id="8857e-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8857e-103">\<system.serviceModel></span></span>  
<span data-ttu-id="8857e-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="8857e-104">\<bindings></span></span>  
<span data-ttu-id="8857e-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="8857e-105">\<customBinding></span></span>  
<span data-ttu-id="8857e-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="8857e-106">\<binding></span></span>  
<span data-ttu-id="8857e-107">\<mtomMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="8857e-107">\<mtomMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8857e-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8857e-108">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8857e-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8857e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8857e-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8857e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8857e-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="8857e-111">Attributes</span></span>  
  
|<span data-ttu-id="8857e-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="8857e-112">Attribute</span></span>|<span data-ttu-id="8857e-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="8857e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8857e-114">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="8857e-114">maxBufferSize</span></span>|<span data-ttu-id="8857e-115">Um inteiro que especifica o tamanho máximo do buffer que pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="8857e-115">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="8857e-116">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="8857e-116">maxReadPoolSize</span></span>|<span data-ttu-id="8857e-117">Um inteiro que especifica quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="8857e-117">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="8857e-118">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="8857e-118">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="8857e-119">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="8857e-119">The default is 64.</span></span>|  
|<span data-ttu-id="8857e-120">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="8857e-120">maxWritePoolSize</span></span>|<span data-ttu-id="8857e-121">Um inteiro que especifica quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="8857e-121">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="8857e-122">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="8857e-122">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="8857e-123">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="8857e-123">The default is 16.</span></span>|  
|<span data-ttu-id="8857e-124">messageVersion</span><span class="sxs-lookup"><span data-stu-id="8857e-124">messageVersion</span></span>|<span data-ttu-id="8857e-125">Especifica a versão SOAP das mensagens enviadas usando a associação.</span><span class="sxs-lookup"><span data-stu-id="8857e-125">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="8857e-126">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="8857e-126">Valid values are</span></span><br /><br /> <span data-ttu-id="8857e-127">-Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="8857e-127">-   Soap11Addressing1</span></span><br /><span data-ttu-id="8857e-128">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="8857e-128">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="8857e-129">O padrão é Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="8857e-129">The default is Soap12Addressing10.</span></span> <span data-ttu-id="8857e-130">Esse atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="8857e-130">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="8857e-131">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="8857e-131">writeEncoding</span></span>|<span data-ttu-id="8857e-132">Especifica a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8857e-132">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="8857e-133">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="8857e-133">Valid values are</span></span><br /><br /> <span data-ttu-id="8857e-134">-   UnicodeFffeTextEncoding: Unicode BigEndian de codificação</span><span class="sxs-lookup"><span data-stu-id="8857e-134">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="8857e-135">-Utf16TextEncoding: Codificação Unicode</span><span class="sxs-lookup"><span data-stu-id="8857e-135">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="8857e-136">-   Utf8TextEncoding: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="8857e-136">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="8857e-137">O padrão é Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="8857e-137">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="8857e-138">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="8857e-138">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8857e-139">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8857e-139">Child Elements</span></span>  
  
|<span data-ttu-id="8857e-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="8857e-140">Element</span></span>|<span data-ttu-id="8857e-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="8857e-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8857e-142">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="8857e-142">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="8857e-143">Define as restrições na complexidade das mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="8857e-143">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="8857e-144">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="8857e-144">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8857e-145">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8857e-145">Parent Elements</span></span>  
  
|<span data-ttu-id="8857e-146">Elemento</span><span class="sxs-lookup"><span data-stu-id="8857e-146">Element</span></span>|<span data-ttu-id="8857e-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="8857e-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8857e-148">\<binding></span><span class="sxs-lookup"><span data-stu-id="8857e-148">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="8857e-149">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="8857e-149">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8857e-150">Comentários</span><span class="sxs-lookup"><span data-stu-id="8857e-150">Remarks</span></span>  
 <span data-ttu-id="8857e-151">Codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="8857e-151">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="8857e-152">Decodificação de é o processo inverso.</span><span class="sxs-lookup"><span data-stu-id="8857e-152">Decoding is the reverse process.</span></span> <span data-ttu-id="8857e-153">Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: Texto, binária e mecanismo de otimização de transmissão de mensagens (MTOM).</span><span class="sxs-lookup"><span data-stu-id="8857e-153">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="8857e-154">O `MtomMessageEncoding` elemento Especifica o controle de versão de mensagem e de codificação de caractere e outras configurações usadas para mensagens usando a codificação de MTOM Message Transmission Optimization Mechanism ().</span><span class="sxs-lookup"><span data-stu-id="8857e-154">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="8857e-155">MTOM é uma tecnologia eficiente para a transmissão de dados binários em mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="8857e-155">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="8857e-156">O codificador MTOM tenta criar um equilíbrio entre a eficiência e interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="8857e-156">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="8857e-157">A codificação de MTOM transmite a maioria dos XML no formato textual, mas otimiza blocos grandes de dados binários, transmiti-los como-está, sem a conversão em seu formato codificado na base64.</span><span class="sxs-lookup"><span data-stu-id="8857e-157">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8857e-158">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8857e-158">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="8857e-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8857e-159">See also</span></span>
- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="8857e-160">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="8857e-160">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="8857e-161">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="8857e-161">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="8857e-162">Associações</span><span class="sxs-lookup"><span data-stu-id="8857e-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="8857e-163">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="8857e-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8857e-164">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="8857e-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="8857e-165">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="8857e-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
