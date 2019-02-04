---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: b6914a195ba0e1934f7a586f5f6bae703a4bb1f9
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675316"
---
# <a name="binarymessageencoding"></a><span data-ttu-id="da573-101">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="da573-101">\<binaryMessageEncoding></span></span>
<span data-ttu-id="da573-102">Define um codificador de mensagem binária que codifica mensagens do Windows Communication Foundation (WCF) em binário no fio.</span><span class="sxs-lookup"><span data-stu-id="da573-102">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
 <span data-ttu-id="da573-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="da573-103">\<system.serviceModel></span></span>  
<span data-ttu-id="da573-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="da573-104">\<bindings></span></span>  
<span data-ttu-id="da573-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="da573-105">\<customBinding></span></span>  
<span data-ttu-id="da573-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="da573-106">\<binding></span></span>  
<span data-ttu-id="da573-107">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="da573-107">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da573-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da573-108">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da573-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="da573-109">Attributes and Elements</span></span>  
 <span data-ttu-id="da573-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="da573-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da573-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="da573-111">Attributes</span></span>  
  
|<span data-ttu-id="da573-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="da573-112">Attribute</span></span>|<span data-ttu-id="da573-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="da573-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="da573-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="da573-114">maxReadPoolSize</span></span>|<span data-ttu-id="da573-115">Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="da573-115">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="da573-116">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="da573-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="da573-117">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="da573-117">The default is 64.</span></span>|  
|<span data-ttu-id="da573-118">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="da573-118">maxSessionSize</span></span>|<span data-ttu-id="da573-119">Um inteiro positivo que define o tamanho, em bytes, do buffer usado para codificação.</span><span class="sxs-lookup"><span data-stu-id="da573-119">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="da573-120">Um buffer maior aumenta a velocidade de codificação às custas o tamanho do conjunto de trabalho.</span><span class="sxs-lookup"><span data-stu-id="da573-120">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="da573-121">O padrão é 2048.</span><span class="sxs-lookup"><span data-stu-id="da573-121">The default is 2048.</span></span>|  
|<span data-ttu-id="da573-122">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="da573-122">maxWritePoolSize</span></span>|<span data-ttu-id="da573-123">Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="da573-123">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="da573-124">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="da573-124">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="da573-125">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="da573-125">The default is 16.</span></span>|  
|<span data-ttu-id="da573-126">messageVersion</span><span class="sxs-lookup"><span data-stu-id="da573-126">messageVersion</span></span>|<span data-ttu-id="da573-127">Especifica a mensagem SOAP e WS-Addressing que usadas ou esperadas.</span><span class="sxs-lookup"><span data-stu-id="da573-127">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="da573-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="da573-128">Child Elements</span></span>  
  
|<span data-ttu-id="da573-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="da573-129">Element</span></span>|<span data-ttu-id="da573-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="da573-130">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="da573-131">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="da573-131">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="da573-132">Define as restrições na complexidade das mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="da573-132">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="da573-133">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="da573-133">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="da573-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="da573-134">Parent Elements</span></span>  
  
|<span data-ttu-id="da573-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="da573-135">Element</span></span>|<span data-ttu-id="da573-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="da573-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da573-137">\<binding></span><span class="sxs-lookup"><span data-stu-id="da573-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="da573-138">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="da573-138">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da573-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="da573-139">Remarks</span></span>  
 <span data-ttu-id="da573-140">Codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="da573-140">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="da573-141">Decodificação de é o processo inverso.</span><span class="sxs-lookup"><span data-stu-id="da573-141">Decoding is the reverse process.</span></span> <span data-ttu-id="da573-142">Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: Texto, binária e mecanismo de otimização de transmissão de mensagens (MTOM).</span><span class="sxs-lookup"><span data-stu-id="da573-142">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="da573-143">O `binaryMessageEncoding` elemento Especifica o formato binário do .NET para o XML e tem opções para especificar a codificação de caracteres e a versão SOAP e WS-Addressing a ser usada.</span><span class="sxs-lookup"><span data-stu-id="da573-143">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="da573-144">O codificador de mensagem binária codifica mensagens do Windows Communication Foundation (WCF) em binário no fio.</span><span class="sxs-lookup"><span data-stu-id="da573-144">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="da573-145">Embora essa codificação resulta em muito rápido transmissão de mensagens, interoperabilidade com base no WS-\* padrões é perdido.</span><span class="sxs-lookup"><span data-stu-id="da573-145">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da573-146">Exemplo</span><span class="sxs-lookup"><span data-stu-id="da573-146">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="da573-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da573-147">See also</span></span>
- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="da573-148">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="da573-148">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="da573-149">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="da573-149">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="da573-150">Associações</span><span class="sxs-lookup"><span data-stu-id="da573-150">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="da573-151">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="da573-151">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="da573-152">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="da573-152">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="da573-153">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="da573-153">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
