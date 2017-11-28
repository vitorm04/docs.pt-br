---
title: '&lt;mtomMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 237891b5f855707f40f4fb58c08b80daa24f4def
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmtommessageencodinggt"></a><span data-ttu-id="f17d2-102">&lt;mtomMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="f17d2-102">&lt;mtomMessageEncoding&gt;</span></span>
<span data-ttu-id="f17d2-103">Especifica o controle de versão de codificação e a mensagem usado para mensagens SOAP mensagem transmissão otimização mecanismo (MTOM) com base.</span><span class="sxs-lookup"><span data-stu-id="f17d2-103">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
 <span data-ttu-id="f17d2-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f17d2-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f17d2-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="f17d2-105">\<bindings></span></span>  
<span data-ttu-id="f17d2-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f17d2-106">\<customBinding></span></span>  
<span data-ttu-id="f17d2-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="f17d2-107">\<binding></span></span>  
<span data-ttu-id="f17d2-108">\<mtomMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="f17d2-108">\<mtomMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f17d2-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f17d2-109">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding   
   maxBufferSize="Integer"  
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing1/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f17d2-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f17d2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f17d2-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f17d2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f17d2-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="f17d2-112">Attributes</span></span>  
  
|<span data-ttu-id="f17d2-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="f17d2-113">Attribute</span></span>|<span data-ttu-id="f17d2-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f17d2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f17d2-115">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="f17d2-115">maxBufferSize</span></span>|<span data-ttu-id="f17d2-116">Um inteiro que especifica o tamanho máximo do buffer que pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="f17d2-116">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="f17d2-117">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="f17d2-117">maxReadPoolSize</span></span>|<span data-ttu-id="f17d2-118">Um inteiro que especifica quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="f17d2-118">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="f17d2-119">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto maior de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f17d2-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="f17d2-120">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="f17d2-120">The default is 64.</span></span>|  
|<span data-ttu-id="f17d2-121">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="f17d2-121">maxWritePoolSize</span></span>|<span data-ttu-id="f17d2-122">Um inteiro que especifica quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="f17d2-122">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="f17d2-123">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto maior de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f17d2-123">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="f17d2-124">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="f17d2-124">The default is 16.</span></span>|  
|<span data-ttu-id="f17d2-125">messageVersion</span><span class="sxs-lookup"><span data-stu-id="f17d2-125">messageVersion</span></span>|<span data-ttu-id="f17d2-126">Especifica a versão SOAP das mensagens enviadas usando a associação.</span><span class="sxs-lookup"><span data-stu-id="f17d2-126">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="f17d2-127">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="f17d2-127">Valid values are</span></span><br /><br /> <span data-ttu-id="f17d2-128">-Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="f17d2-128">-   Soap11Addressing1</span></span><br /><span data-ttu-id="f17d2-129">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="f17d2-129">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="f17d2-130">O padrão é Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="f17d2-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="f17d2-131">Esse atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="f17d2-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="f17d2-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="f17d2-132">writeEncoding</span></span>|<span data-ttu-id="f17d2-133">Especifica a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f17d2-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="f17d2-134">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="f17d2-134">Valid values are</span></span><br /><br /> <span data-ttu-id="f17d2-135">-UnicodeFffeTextEncoding: Unicode BigEndian codificação</span><span class="sxs-lookup"><span data-stu-id="f17d2-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="f17d2-136">-Utf16TextEncoding: Codificação de Unicode</span><span class="sxs-lookup"><span data-stu-id="f17d2-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="f17d2-137">-Utf8TextEncoding: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="f17d2-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="f17d2-138">O padrão é Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="f17d2-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="f17d2-139">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="f17d2-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f17d2-140">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f17d2-140">Child Elements</span></span>  
  
|<span data-ttu-id="f17d2-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="f17d2-141">Element</span></span>|<span data-ttu-id="f17d2-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="f17d2-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f17d2-143">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="f17d2-143">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="f17d2-144">Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="f17d2-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="f17d2-145">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="f17d2-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f17d2-146">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f17d2-146">Parent Elements</span></span>  
  
|<span data-ttu-id="f17d2-147">Elemento</span><span class="sxs-lookup"><span data-stu-id="f17d2-147">Element</span></span>|<span data-ttu-id="f17d2-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="f17d2-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f17d2-149">\<associação ></span><span class="sxs-lookup"><span data-stu-id="f17d2-149">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="f17d2-150">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="f17d2-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f17d2-151">Comentários</span><span class="sxs-lookup"><span data-stu-id="f17d2-151">Remarks</span></span>  
 <span data-ttu-id="f17d2-152">Codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="f17d2-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="f17d2-153">Decodificação de é o processo inverso.</span><span class="sxs-lookup"><span data-stu-id="f17d2-153">Decoding is the reverse process.</span></span> <span data-ttu-id="f17d2-154">Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: texto, binária e mecanismo de otimização de transmissão mensagem (MTOM).</span><span class="sxs-lookup"><span data-stu-id="f17d2-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="f17d2-155">O `MtomMessageEncoding` elemento Especifica o controle de versão de codificação e a mensagem de caractere e outras configurações usadas para mensagens usando uma codificação de mecanismo de otimização de transmissão da mensagem (MTOM).</span><span class="sxs-lookup"><span data-stu-id="f17d2-155">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="f17d2-156">MTOM é uma tecnologia eficiente para transmitir dados binários em mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="f17d2-156">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="f17d2-157">O codificador MTOM tenta criar um equilíbrio entre eficiência e interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="f17d2-157">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="f17d2-158">A codificação de MTOM transmite a maioria dos XML no formato textual, mas otimiza o transmiti-los como blocos grandes de dados binários-é, sem conversão em seu formato codificado na base64.</span><span class="sxs-lookup"><span data-stu-id="f17d2-158">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f17d2-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f17d2-159">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap11Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="f17d2-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f17d2-160">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
 [<span data-ttu-id="f17d2-161">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="f17d2-161">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="f17d2-162">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="f17d2-162">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 <span data-ttu-id="f17d2-163">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="f17d2-163">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="f17d2-164">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="f17d2-164">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="f17d2-165">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="f17d2-165">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="f17d2-166">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f17d2-166">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
