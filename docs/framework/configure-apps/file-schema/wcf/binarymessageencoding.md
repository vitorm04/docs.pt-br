---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: 9b6b74200c807e6523ed3f7250945040bd12658d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919802"
---
# <a name="binarymessageencoding"></a><span data-ttu-id="d35aa-101">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="d35aa-101">\<binaryMessageEncoding></span></span>
<span data-ttu-id="d35aa-102">Define um codificador de mensagem binária que codificará mensagens Windows Communication Foundation (WCF) em binário na conexão.</span><span class="sxs-lookup"><span data-stu-id="d35aa-102">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
 <span data-ttu-id="d35aa-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d35aa-103">\<system.serviceModel></span></span>  
<span data-ttu-id="d35aa-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="d35aa-104">\<bindings></span></span>  
<span data-ttu-id="d35aa-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d35aa-105">\<customBinding></span></span>  
<span data-ttu-id="d35aa-106">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="d35aa-106">\<binding></span></span>  
<span data-ttu-id="d35aa-107">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="d35aa-107">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d35aa-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d35aa-108">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d35aa-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d35aa-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d35aa-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d35aa-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d35aa-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="d35aa-111">Attributes</span></span>  
  
|<span data-ttu-id="d35aa-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="d35aa-112">Attribute</span></span>|<span data-ttu-id="d35aa-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="d35aa-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d35aa-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="d35aa-114">maxReadPoolSize</span></span>|<span data-ttu-id="d35aa-115">Um inteiro que define quantas mensagens podem ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="d35aa-115">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="d35aa-116">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="d35aa-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="d35aa-117">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="d35aa-117">The default is 64.</span></span>|  
|<span data-ttu-id="d35aa-118">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="d35aa-118">maxSessionSize</span></span>|<span data-ttu-id="d35aa-119">Um inteiro positivo que define o tamanho, em bytes, do buffer usado para codificação.</span><span class="sxs-lookup"><span data-stu-id="d35aa-119">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="d35aa-120">Um buffer maior aumenta a velocidade de codificação às custas do tamanho do conjunto de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d35aa-120">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="d35aa-121">O padrão é 2048.</span><span class="sxs-lookup"><span data-stu-id="d35aa-121">The default is 2048.</span></span>|  
|<span data-ttu-id="d35aa-122">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="d35aa-122">maxWritePoolSize</span></span>|<span data-ttu-id="d35aa-123">Um inteiro que define quantas mensagens podem ser enviadas simultaneamente sem alocar novos gravadores.</span><span class="sxs-lookup"><span data-stu-id="d35aa-123">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="d35aa-124">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="d35aa-124">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="d35aa-125">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="d35aa-125">The default is 16.</span></span>|  
|<span data-ttu-id="d35aa-126">messageVersion</span><span class="sxs-lookup"><span data-stu-id="d35aa-126">messageVersion</span></span>|<span data-ttu-id="d35aa-127">Especifica a mensagem SOAP e as versões WS-Addressing que são usadas ou esperadas.</span><span class="sxs-lookup"><span data-stu-id="d35aa-127">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d35aa-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d35aa-128">Child Elements</span></span>  
  
|<span data-ttu-id="d35aa-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="d35aa-129">Element</span></span>|<span data-ttu-id="d35aa-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="d35aa-130">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d35aa-131">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d35aa-131">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="d35aa-132">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="d35aa-132">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="d35aa-133">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="d35aa-133">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d35aa-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d35aa-134">Parent Elements</span></span>  
  
|<span data-ttu-id="d35aa-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="d35aa-135">Element</span></span>|<span data-ttu-id="d35aa-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="d35aa-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d35aa-137">\<binding></span><span class="sxs-lookup"><span data-stu-id="d35aa-137">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="d35aa-138">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="d35aa-138">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d35aa-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="d35aa-139">Remarks</span></span>  
 <span data-ttu-id="d35aa-140">A codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="d35aa-140">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="d35aa-141">A decodificação é o processo reverso.</span><span class="sxs-lookup"><span data-stu-id="d35aa-141">Decoding is the reverse process.</span></span> <span data-ttu-id="d35aa-142">O Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: O mecanismo de otimização de transmissão de mensagens e de texto, binário e mensagem (MTOM).</span><span class="sxs-lookup"><span data-stu-id="d35aa-142">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="d35aa-143">O `binaryMessageEncoding` elemento Especifica o formato binário .net para XML e tem opções para especificar a codificação de caracteres e a versão SOAP e WS-Addressing a ser usada.</span><span class="sxs-lookup"><span data-stu-id="d35aa-143">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="d35aa-144">O codificador de mensagens binárias codifica as mensagens de Windows Communication Foundation (WCF) em binário na conexão.</span><span class="sxs-lookup"><span data-stu-id="d35aa-144">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="d35aa-145">Embora essa codificação resulte em uma transmissão muito rápida de mensagens, a interoperabilidade baseada em padrões WS-\* é perdida.</span><span class="sxs-lookup"><span data-stu-id="d35aa-145">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d35aa-146">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d35aa-146">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="d35aa-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d35aa-147">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="d35aa-148">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="d35aa-148">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="d35aa-149">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="d35aa-149">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="d35aa-150">Associações</span><span class="sxs-lookup"><span data-stu-id="d35aa-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d35aa-151">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="d35aa-151">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d35aa-152">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="d35aa-152">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="d35aa-153">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d35aa-153">\<customBinding></span></span>](custombinding.md)
