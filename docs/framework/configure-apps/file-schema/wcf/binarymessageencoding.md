---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: afe0479d9cbf6d754b309c18e23d3a479870177c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739078"
---
# <a name="binarymessageencoding"></a><span data-ttu-id="5aca6-101">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="5aca6-101">\<binaryMessageEncoding></span></span>
<span data-ttu-id="5aca6-102">Define um codificador de mensagem binária que codificará mensagens Windows Communication Foundation (WCF) em binário na conexão.</span><span class="sxs-lookup"><span data-stu-id="5aca6-102">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
<span data-ttu-id="5aca6-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5aca6-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5aca6-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="5aca6-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5aca6-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="5aca6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5aca6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) ></span><span class="sxs-lookup"><span data-stu-id="5aca6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="5aca6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="5aca6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="5aca6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<binaryMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="5aca6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binaryMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5aca6-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5aca6-109">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5aca6-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5aca6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5aca6-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5aca6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5aca6-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="5aca6-112">Attributes</span></span>  
  
|<span data-ttu-id="5aca6-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="5aca6-113">Attribute</span></span>|<span data-ttu-id="5aca6-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5aca6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5aca6-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="5aca6-115">maxReadPoolSize</span></span>|<span data-ttu-id="5aca6-116">Um inteiro que define quantas mensagens podem ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="5aca6-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="5aca6-117">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="5aca6-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="5aca6-118">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="5aca6-118">The default is 64.</span></span>|  
|<span data-ttu-id="5aca6-119">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="5aca6-119">maxSessionSize</span></span>|<span data-ttu-id="5aca6-120">Um inteiro positivo que define o tamanho, em bytes, do buffer usado para codificação.</span><span class="sxs-lookup"><span data-stu-id="5aca6-120">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="5aca6-121">Um buffer maior aumenta a velocidade de codificação às custas do tamanho do conjunto de trabalho.</span><span class="sxs-lookup"><span data-stu-id="5aca6-121">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="5aca6-122">O padrão é 2048.</span><span class="sxs-lookup"><span data-stu-id="5aca6-122">The default is 2048.</span></span>|  
|<span data-ttu-id="5aca6-123">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="5aca6-123">maxWritePoolSize</span></span>|<span data-ttu-id="5aca6-124">Um inteiro que define quantas mensagens podem ser enviadas simultaneamente sem alocar novos gravadores.</span><span class="sxs-lookup"><span data-stu-id="5aca6-124">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="5aca6-125">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="5aca6-125">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="5aca6-126">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="5aca6-126">The default is 16.</span></span>|  
|<span data-ttu-id="5aca6-127">messageVersion</span><span class="sxs-lookup"><span data-stu-id="5aca6-127">messageVersion</span></span>|<span data-ttu-id="5aca6-128">Especifica a mensagem SOAP e as versões WS-Addressing que são usadas ou esperadas.</span><span class="sxs-lookup"><span data-stu-id="5aca6-128">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5aca6-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5aca6-129">Child Elements</span></span>  
  
|<span data-ttu-id="5aca6-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="5aca6-130">Element</span></span>|<span data-ttu-id="5aca6-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="5aca6-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5aca6-132">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5aca6-132">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="5aca6-133">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="5aca6-133">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="5aca6-134">Este elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="5aca6-134">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5aca6-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5aca6-135">Parent Elements</span></span>  
  
|<span data-ttu-id="5aca6-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="5aca6-136">Element</span></span>|<span data-ttu-id="5aca6-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="5aca6-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5aca6-138">\<binding ></span><span class="sxs-lookup"><span data-stu-id="5aca6-138">\<binding></span></span>](bindings.md)|<span data-ttu-id="5aca6-139">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="5aca6-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5aca6-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="5aca6-140">Remarks</span></span>  
 <span data-ttu-id="5aca6-141">A codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="5aca6-141">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="5aca6-142">A decodificação é o processo reverso.</span><span class="sxs-lookup"><span data-stu-id="5aca6-142">Decoding is the reverse process.</span></span> <span data-ttu-id="5aca6-143">O Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: texto, binário e MTOM (mecanismo de otimização de transmissão de mensagens).</span><span class="sxs-lookup"><span data-stu-id="5aca6-143">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="5aca6-144">O elemento `binaryMessageEncoding` especifica o formato binário .NET para XML e tem opções para especificar a codificação de caracteres e a versão SOAP e WS-Addressing a ser usada.</span><span class="sxs-lookup"><span data-stu-id="5aca6-144">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="5aca6-145">O codificador de mensagens binárias codifica as mensagens de Windows Communication Foundation (WCF) em binário na conexão.</span><span class="sxs-lookup"><span data-stu-id="5aca6-145">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="5aca6-146">Embora essa codificação resulte em uma transmissão muito rápida de mensagens, a interoperabilidade baseada em padrões WS-\* é perdida.</span><span class="sxs-lookup"><span data-stu-id="5aca6-146">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5aca6-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5aca6-147">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="5aca6-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5aca6-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="5aca6-149">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="5aca6-149">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="5aca6-150">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="5aca6-150">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="5aca6-151">Associações</span><span class="sxs-lookup"><span data-stu-id="5aca6-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5aca6-152">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="5aca6-152">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5aca6-153">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="5aca6-153">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="5aca6-154">\<CustomBinding</span><span class="sxs-lookup"><span data-stu-id="5aca6-154">\<customBinding></span></span>](custombinding.md)
