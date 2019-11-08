---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: bd38bf812e6d8d9e57d99bf1a5b77ebb776193a5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738842"
---
# <a name="mtommessageencoding"></a><span data-ttu-id="39252-101">\<mtomMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="39252-101">\<mtomMessageEncoding></span></span>
<span data-ttu-id="39252-102">Especifica a codificação e o controle de versão de mensagem usados para mensagens baseadas no mecanismo de otimização de transmissão de mensagens SOAP (MTOM).</span><span class="sxs-lookup"><span data-stu-id="39252-102">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
<span data-ttu-id="39252-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="39252-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="39252-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="39252-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="39252-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="39252-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="39252-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) ></span><span class="sxs-lookup"><span data-stu-id="39252-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="39252-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="39252-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="39252-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mtomMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="39252-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mtomMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39252-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39252-109">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39252-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="39252-110">Attributes and Elements</span></span>  
 <span data-ttu-id="39252-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="39252-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39252-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="39252-112">Attributes</span></span>  
  
|<span data-ttu-id="39252-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="39252-113">Attribute</span></span>|<span data-ttu-id="39252-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="39252-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39252-115">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="39252-115">maxBufferSize</span></span>|<span data-ttu-id="39252-116">Um inteiro que especifica o tamanho máximo do buffer que pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="39252-116">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="39252-117">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="39252-117">maxReadPoolSize</span></span>|<span data-ttu-id="39252-118">Um inteiro que especifica quantas mensagens podem ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="39252-118">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="39252-119">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="39252-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="39252-120">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="39252-120">The default is 64.</span></span>|  
|<span data-ttu-id="39252-121">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="39252-121">maxWritePoolSize</span></span>|<span data-ttu-id="39252-122">Um inteiro que especifica quantas mensagens podem ser enviadas simultaneamente sem alocar novos gravadores.</span><span class="sxs-lookup"><span data-stu-id="39252-122">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="39252-123">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="39252-123">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="39252-124">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="39252-124">The default is 16.</span></span>|  
|<span data-ttu-id="39252-125">messageVersion</span><span class="sxs-lookup"><span data-stu-id="39252-125">messageVersion</span></span>|<span data-ttu-id="39252-126">Especifica a versão SOAP das mensagens enviadas usando a associação.</span><span class="sxs-lookup"><span data-stu-id="39252-126">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="39252-127">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="39252-127">Valid values are</span></span><br /><br /> <span data-ttu-id="39252-128">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="39252-128">-   Soap11Addressing1</span></span><br /><span data-ttu-id="39252-129">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="39252-129">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="39252-130">O padrão é Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="39252-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="39252-131">Este atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="39252-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="39252-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="39252-132">writeEncoding</span></span>|<span data-ttu-id="39252-133">Especifica a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="39252-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="39252-134">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="39252-134">Valid values are</span></span><br /><br /> <span data-ttu-id="39252-135">-UnicodeFffeTextEncoding: codificação BigEndian Unicode</span><span class="sxs-lookup"><span data-stu-id="39252-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="39252-136">-Utf16TextEncoding: codificação Unicode</span><span class="sxs-lookup"><span data-stu-id="39252-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="39252-137">-Utf8TextEncoding: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="39252-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="39252-138">O padrão é Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="39252-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="39252-139">Este atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="39252-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39252-140">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="39252-140">Child Elements</span></span>  
  
|<span data-ttu-id="39252-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="39252-141">Element</span></span>|<span data-ttu-id="39252-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="39252-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="39252-143">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="39252-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="39252-144">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="39252-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="39252-145">Este elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="39252-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39252-146">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="39252-146">Parent Elements</span></span>  
  
|<span data-ttu-id="39252-147">Elemento</span><span class="sxs-lookup"><span data-stu-id="39252-147">Element</span></span>|<span data-ttu-id="39252-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="39252-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39252-149">\<binding ></span><span class="sxs-lookup"><span data-stu-id="39252-149">\<binding></span></span>](bindings.md)|<span data-ttu-id="39252-150">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="39252-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39252-151">Comentários</span><span class="sxs-lookup"><span data-stu-id="39252-151">Remarks</span></span>  
 <span data-ttu-id="39252-152">A codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="39252-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="39252-153">A decodificação é o processo reverso.</span><span class="sxs-lookup"><span data-stu-id="39252-153">Decoding is the reverse process.</span></span> <span data-ttu-id="39252-154">O Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: texto, binário e MTOM (mecanismo de otimização de transmissão de mensagens).</span><span class="sxs-lookup"><span data-stu-id="39252-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="39252-155">O elemento `MtomMessageEncoding` especifica a codificação de caracteres e o controle de versão de mensagem e outras configurações usadas para mensagens usando uma codificação MTOM (mecanismo de otimização de transmissão de mensagens).</span><span class="sxs-lookup"><span data-stu-id="39252-155">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="39252-156">O MTOM é uma tecnologia eficiente para transmitir dados binários em mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="39252-156">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="39252-157">O codificador MTOM tenta criar um equilíbrio entre eficiência e interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="39252-157">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="39252-158">A codificação MTOM transmite a maioria dos XML na forma textual, mas otimiza grandes blocos de dados binários transmitindo-os como estão, sem conversão para seu formato codificado em base64.</span><span class="sxs-lookup"><span data-stu-id="39252-158">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39252-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="39252-159">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="39252-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39252-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="39252-161">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="39252-161">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="39252-162">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="39252-162">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="39252-163">Associações</span><span class="sxs-lookup"><span data-stu-id="39252-163">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="39252-164">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="39252-164">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="39252-165">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="39252-165">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="39252-166">\<CustomBinding</span><span class="sxs-lookup"><span data-stu-id="39252-166">\<customBinding></span></span>](custombinding.md)
