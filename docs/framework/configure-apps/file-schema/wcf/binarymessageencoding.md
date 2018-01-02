---
title: '&lt;binaryMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 503c0edf3a21b3fb0f57b5199aa2a1a17df4222d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbinarymessageencodinggt"></a><span data-ttu-id="c5571-102">&lt;binaryMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="c5571-102">&lt;binaryMessageEncoding&gt;</span></span>
<span data-ttu-id="c5571-103">Define um codificador de mensagem binária que codifica mensagens do Windows Communication Foundation (WCF) em binário no fio.</span><span class="sxs-lookup"><span data-stu-id="c5571-103">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
 <span data-ttu-id="c5571-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c5571-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c5571-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="c5571-105">\<bindings></span></span>  
<span data-ttu-id="c5571-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c5571-106">\<customBinding></span></span>  
<span data-ttu-id="c5571-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="c5571-107">\<binding></span></span>  
<span data-ttu-id="c5571-108">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="c5571-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5571-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5571-109">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding   
      maxReadPoolSize="Integer"  
   maxSessionSize="Integer"   
   maxWritePoolSize="Integer"   messageVersion="Soap11Addressing10/Soap12Addressing10" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5571-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c5571-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c5571-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c5571-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5571-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="c5571-112">Attributes</span></span>  
  
|<span data-ttu-id="c5571-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="c5571-113">Attribute</span></span>|<span data-ttu-id="c5571-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5571-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5571-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="c5571-115">maxReadPoolSize</span></span>|<span data-ttu-id="c5571-116">Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="c5571-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="c5571-117">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto maior de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c5571-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="c5571-118">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="c5571-118">The default is 64.</span></span>|  
|<span data-ttu-id="c5571-119">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="c5571-119">maxSessionSize</span></span>|<span data-ttu-id="c5571-120">Um inteiro positivo que define o tamanho, em bytes, do buffer usado para codificação.</span><span class="sxs-lookup"><span data-stu-id="c5571-120">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="c5571-121">Um buffer maior aumenta a velocidade de codificação às custas de tamanho do conjunto de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c5571-121">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="c5571-122">O padrão é 2048.</span><span class="sxs-lookup"><span data-stu-id="c5571-122">The default is 2048.</span></span>|  
|<span data-ttu-id="c5571-123">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="c5571-123">maxWritePoolSize</span></span>|<span data-ttu-id="c5571-124">Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="c5571-124">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="c5571-125">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto maior de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c5571-125">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="c5571-126">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="c5571-126">The default is 16.</span></span>|  
|<span data-ttu-id="c5571-127">messageVersion</span><span class="sxs-lookup"><span data-stu-id="c5571-127">messageVersion</span></span>|<span data-ttu-id="c5571-128">Especifica a mensagem SOAP e WS-Addressing que são usados ou esperado.</span><span class="sxs-lookup"><span data-stu-id="c5571-128">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5571-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c5571-129">Child Elements</span></span>  
  
|<span data-ttu-id="c5571-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="c5571-130">Element</span></span>|<span data-ttu-id="c5571-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5571-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5571-132">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="c5571-132">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="c5571-133">Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="c5571-133">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="c5571-134">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="c5571-134">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c5571-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c5571-135">Parent Elements</span></span>  
  
|<span data-ttu-id="c5571-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="c5571-136">Element</span></span>|<span data-ttu-id="c5571-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5571-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5571-138">\<associação ></span><span class="sxs-lookup"><span data-stu-id="c5571-138">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c5571-139">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="c5571-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5571-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="c5571-140">Remarks</span></span>  
 <span data-ttu-id="c5571-141">Codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="c5571-141">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="c5571-142">Decodificação de é o processo inverso.</span><span class="sxs-lookup"><span data-stu-id="c5571-142">Decoding is the reverse process.</span></span> <span data-ttu-id="c5571-143">Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: texto, binária e mecanismo de otimização de transmissão mensagem (MTOM).</span><span class="sxs-lookup"><span data-stu-id="c5571-143">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="c5571-144">O `binaryMessageEncoding` elemento Especifica o formato binário do .NET para o XML e possui opções para especificar a codificação de caracteres e a versão SOAP e WS-Addressing a ser usada.</span><span class="sxs-lookup"><span data-stu-id="c5571-144">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="c5571-145">O codificador de mensagem binária codifica mensagens do Windows Communication Foundation (WCF) em binário no fio.</span><span class="sxs-lookup"><span data-stu-id="c5571-145">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="c5571-146">Embora essa codificação resulta em muito rápido transmissão de mensagens, interoperabilidade com base em WS-* padrões serão perdidos.</span><span class="sxs-lookup"><span data-stu-id="c5571-146">While this encoding results in very fast transmission of messages, interoperability based on the WS-* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5571-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c5571-147">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"  
   maxWritePoolSize="2132"  
   maxSessionSize="3141" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5571-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5571-148">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
 [<span data-ttu-id="c5571-149">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="c5571-149">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="c5571-150">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="c5571-150">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="c5571-151">Associações</span><span class="sxs-lookup"><span data-stu-id="c5571-151">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c5571-152">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="c5571-152">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="c5571-153">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="c5571-153">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="c5571-154">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c5571-154">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
