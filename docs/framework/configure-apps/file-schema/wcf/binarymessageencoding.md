---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: afe0479d9cbf6d754b309c18e23d3a479870177c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739078"
---
# \<binaryMessageEncoding>
<span data-ttu-id="364c8-101">Define um codificador de mensagem binária que codificará mensagens Windows Communication Foundation (WCF) em binário na conexão.</span><span class="sxs-lookup"><span data-stu-id="364c8-101">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binaryMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="364c8-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="364c8-102">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="364c8-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="364c8-103">Attributes and Elements</span></span>  
 <span data-ttu-id="364c8-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="364c8-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="364c8-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="364c8-105">Attributes</span></span>  
  
|<span data-ttu-id="364c8-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="364c8-106">Attribute</span></span>|<span data-ttu-id="364c8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="364c8-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="364c8-108">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="364c8-108">maxReadPoolSize</span></span>|<span data-ttu-id="364c8-109">Um inteiro que define quantas mensagens podem ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="364c8-109">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="364c8-110">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="364c8-110">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="364c8-111">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="364c8-111">The default is 64.</span></span>|  
|<span data-ttu-id="364c8-112">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="364c8-112">maxSessionSize</span></span>|<span data-ttu-id="364c8-113">Um inteiro positivo que define o tamanho, em bytes, do buffer usado para codificação.</span><span class="sxs-lookup"><span data-stu-id="364c8-113">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="364c8-114">Um buffer maior aumenta a velocidade de codificação às custas do tamanho do conjunto de trabalho.</span><span class="sxs-lookup"><span data-stu-id="364c8-114">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="364c8-115">O padrão é 2048.</span><span class="sxs-lookup"><span data-stu-id="364c8-115">The default is 2048.</span></span>|  
|<span data-ttu-id="364c8-116">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="364c8-116">maxWritePoolSize</span></span>|<span data-ttu-id="364c8-117">Um inteiro que define quantas mensagens podem ser enviadas simultaneamente sem alocar novos gravadores.</span><span class="sxs-lookup"><span data-stu-id="364c8-117">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="364c8-118">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="364c8-118">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="364c8-119">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="364c8-119">The default is 16.</span></span>|  
|<span data-ttu-id="364c8-120">messageVersion</span><span class="sxs-lookup"><span data-stu-id="364c8-120">messageVersion</span></span>|<span data-ttu-id="364c8-121">Especifica a mensagem SOAP e as versões WS-Addressing que são usadas ou esperadas.</span><span class="sxs-lookup"><span data-stu-id="364c8-121">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="364c8-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="364c8-122">Child Elements</span></span>  
  
|<span data-ttu-id="364c8-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="364c8-123">Element</span></span>|<span data-ttu-id="364c8-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="364c8-124">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="364c8-125">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="364c8-125">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="364c8-126">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="364c8-126">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="364c8-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="364c8-127">Parent Elements</span></span>  
  
|<span data-ttu-id="364c8-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="364c8-128">Element</span></span>|<span data-ttu-id="364c8-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="364c8-129">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="364c8-130">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="364c8-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="364c8-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="364c8-131">Remarks</span></span>  
 <span data-ttu-id="364c8-132">A codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="364c8-132">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="364c8-133">A decodificação é o processo reverso.</span><span class="sxs-lookup"><span data-stu-id="364c8-133">Decoding is the reverse process.</span></span> <span data-ttu-id="364c8-134">O Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: texto, binário e MTOM (mecanismo de otimização de transmissão de mensagens).</span><span class="sxs-lookup"><span data-stu-id="364c8-134">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="364c8-135">O `binaryMessageEncoding` elemento Especifica o formato binário .net para XML e tem opções para especificar a codificação de caracteres e a versão SOAP e WS-Addressing a ser usada.</span><span class="sxs-lookup"><span data-stu-id="364c8-135">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="364c8-136">O codificador de mensagens binárias codifica as mensagens de Windows Communication Foundation (WCF) em binário na conexão.</span><span class="sxs-lookup"><span data-stu-id="364c8-136">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="364c8-137">Embora essa codificação resulte em uma transmissão muito rápida de mensagens, a interoperabilidade baseada em padrões WS-\* é perdida.</span><span class="sxs-lookup"><span data-stu-id="364c8-137">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="364c8-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="364c8-138">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="364c8-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="364c8-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="364c8-140">Decodificador de mensagens</span><span class="sxs-lookup"><span data-stu-id="364c8-140">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="364c8-141">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="364c8-141">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="364c8-142">Associações</span><span class="sxs-lookup"><span data-stu-id="364c8-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="364c8-143">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="364c8-143">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="364c8-144">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="364c8-144">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
