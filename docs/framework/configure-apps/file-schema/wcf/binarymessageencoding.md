---
title: '&lt;binaryMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: 2e29721104400c8a0352ebf5cd292689de0d6b14
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150117"
---
# <a name="ltbinarymessageencodinggt"></a><span data-ttu-id="856a5-102">&lt;binaryMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="856a5-102">&lt;binaryMessageEncoding&gt;</span></span>
<span data-ttu-id="856a5-103">Define um codificador de mensagem binária que codifica mensagens do Windows Communication Foundation (WCF) em binário no fio.</span><span class="sxs-lookup"><span data-stu-id="856a5-103">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
 <span data-ttu-id="856a5-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="856a5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="856a5-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="856a5-105">\<bindings></span></span>  
<span data-ttu-id="856a5-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="856a5-106">\<customBinding></span></span>  
<span data-ttu-id="856a5-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="856a5-107">\<binding></span></span>  
<span data-ttu-id="856a5-108">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="856a5-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="856a5-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="856a5-109">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="856a5-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="856a5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="856a5-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="856a5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="856a5-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="856a5-112">Attributes</span></span>  
  
|<span data-ttu-id="856a5-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="856a5-113">Attribute</span></span>|<span data-ttu-id="856a5-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="856a5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="856a5-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="856a5-115">maxReadPoolSize</span></span>|<span data-ttu-id="856a5-116">Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="856a5-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="856a5-117">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="856a5-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="856a5-118">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="856a5-118">The default is 64.</span></span>|  
|<span data-ttu-id="856a5-119">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="856a5-119">maxSessionSize</span></span>|<span data-ttu-id="856a5-120">Um inteiro positivo que define o tamanho, em bytes, do buffer usado para codificação.</span><span class="sxs-lookup"><span data-stu-id="856a5-120">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="856a5-121">Um buffer maior aumenta a velocidade de codificação às custas o tamanho do conjunto de trabalho.</span><span class="sxs-lookup"><span data-stu-id="856a5-121">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="856a5-122">O padrão é 2048.</span><span class="sxs-lookup"><span data-stu-id="856a5-122">The default is 2048.</span></span>|  
|<span data-ttu-id="856a5-123">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="856a5-123">maxWritePoolSize</span></span>|<span data-ttu-id="856a5-124">Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="856a5-124">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="856a5-125">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="856a5-125">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="856a5-126">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="856a5-126">The default is 16.</span></span>|  
|<span data-ttu-id="856a5-127">messageVersion</span><span class="sxs-lookup"><span data-stu-id="856a5-127">messageVersion</span></span>|<span data-ttu-id="856a5-128">Especifica a mensagem SOAP e WS-Addressing que usadas ou esperadas.</span><span class="sxs-lookup"><span data-stu-id="856a5-128">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="856a5-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="856a5-129">Child Elements</span></span>  
  
|<span data-ttu-id="856a5-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="856a5-130">Element</span></span>|<span data-ttu-id="856a5-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="856a5-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="856a5-132">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="856a5-132">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="856a5-133">Define as restrições na complexidade das mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="856a5-133">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="856a5-134">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="856a5-134">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="856a5-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="856a5-135">Parent Elements</span></span>  
  
|<span data-ttu-id="856a5-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="856a5-136">Element</span></span>|<span data-ttu-id="856a5-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="856a5-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="856a5-138">\<associação ></span><span class="sxs-lookup"><span data-stu-id="856a5-138">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="856a5-139">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="856a5-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="856a5-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="856a5-140">Remarks</span></span>  
 <span data-ttu-id="856a5-141">Codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="856a5-141">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="856a5-142">Decodificação de é o processo inverso.</span><span class="sxs-lookup"><span data-stu-id="856a5-142">Decoding is the reverse process.</span></span> <span data-ttu-id="856a5-143">Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: Texto, binária e mecanismo de otimização de transmissão de mensagens (MTOM).</span><span class="sxs-lookup"><span data-stu-id="856a5-143">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="856a5-144">O `binaryMessageEncoding` elemento Especifica o formato binário do .NET para o XML e tem opções para especificar a codificação de caracteres e a versão SOAP e WS-Addressing a ser usada.</span><span class="sxs-lookup"><span data-stu-id="856a5-144">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="856a5-145">O codificador de mensagem binária codifica mensagens do Windows Communication Foundation (WCF) em binário no fio.</span><span class="sxs-lookup"><span data-stu-id="856a5-145">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="856a5-146">Embora essa codificação resulta em muito rápido transmissão de mensagens, interoperabilidade com base no WS-\* padrões é perdido.</span><span class="sxs-lookup"><span data-stu-id="856a5-146">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="856a5-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="856a5-147">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="856a5-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="856a5-148">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
 [<span data-ttu-id="856a5-149">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="856a5-149">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="856a5-150">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="856a5-150">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="856a5-151">Associações</span><span class="sxs-lookup"><span data-stu-id="856a5-151">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="856a5-152">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="856a5-152">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="856a5-153">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="856a5-153">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="856a5-154">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="856a5-154">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
