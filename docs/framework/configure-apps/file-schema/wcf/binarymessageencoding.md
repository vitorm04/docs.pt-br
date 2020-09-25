---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: 1b72b73f0d9d312fd54ea6a5517d55bf251c0e05
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201467"
---
# \<binaryMessageEncoding>

<span data-ttu-id="2648b-101">Define um codificador de mensagem binária que codificará mensagens Windows Communication Foundation (WCF) em binário na conexão.</span><span class="sxs-lookup"><span data-stu-id="2648b-101">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binaryMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="2648b-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2648b-102">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2648b-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2648b-103">Attributes and Elements</span></span>  

 <span data-ttu-id="2648b-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2648b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2648b-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="2648b-105">Attributes</span></span>  
  
|<span data-ttu-id="2648b-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="2648b-106">Attribute</span></span>|<span data-ttu-id="2648b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2648b-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2648b-108">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="2648b-108">maxReadPoolSize</span></span>|<span data-ttu-id="2648b-109">Um inteiro que define quantas mensagens podem ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="2648b-109">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="2648b-110">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="2648b-110">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="2648b-111">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="2648b-111">The default is 64.</span></span>|  
|<span data-ttu-id="2648b-112">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="2648b-112">maxSessionSize</span></span>|<span data-ttu-id="2648b-113">Um inteiro positivo que define o tamanho, em bytes, do buffer usado para codificação.</span><span class="sxs-lookup"><span data-stu-id="2648b-113">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="2648b-114">Um buffer maior aumenta a velocidade de codificação às custas do tamanho do conjunto de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2648b-114">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="2648b-115">O padrão é 2048.</span><span class="sxs-lookup"><span data-stu-id="2648b-115">The default is 2048.</span></span>|  
|<span data-ttu-id="2648b-116">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="2648b-116">maxWritePoolSize</span></span>|<span data-ttu-id="2648b-117">Um inteiro que define quantas mensagens podem ser enviadas simultaneamente sem alocar novos gravadores.</span><span class="sxs-lookup"><span data-stu-id="2648b-117">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="2648b-118">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="2648b-118">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="2648b-119">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="2648b-119">The default is 16.</span></span>|  
|<span data-ttu-id="2648b-120">messageVersion</span><span class="sxs-lookup"><span data-stu-id="2648b-120">messageVersion</span></span>|<span data-ttu-id="2648b-121">Especifica a mensagem SOAP e as versões WS-Addressing que são usadas ou esperadas.</span><span class="sxs-lookup"><span data-stu-id="2648b-121">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2648b-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2648b-122">Child Elements</span></span>  
  
|<span data-ttu-id="2648b-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="2648b-123">Element</span></span>|<span data-ttu-id="2648b-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="2648b-124">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="2648b-125">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="2648b-125">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="2648b-126">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="2648b-126">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2648b-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2648b-127">Parent Elements</span></span>  
  
|<span data-ttu-id="2648b-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="2648b-128">Element</span></span>|<span data-ttu-id="2648b-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="2648b-129">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="2648b-130">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="2648b-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2648b-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="2648b-131">Remarks</span></span>  

 <span data-ttu-id="2648b-132">A codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="2648b-132">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="2648b-133">A decodificação é o processo reverso.</span><span class="sxs-lookup"><span data-stu-id="2648b-133">Decoding is the reverse process.</span></span> <span data-ttu-id="2648b-134">O Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: texto, binário e MTOM (mecanismo de otimização de transmissão de mensagens).</span><span class="sxs-lookup"><span data-stu-id="2648b-134">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="2648b-135">O `binaryMessageEncoding` elemento Especifica o formato binário .net para XML e tem opções para especificar a codificação de caracteres e a versão SOAP e WS-Addressing a ser usada.</span><span class="sxs-lookup"><span data-stu-id="2648b-135">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="2648b-136">O codificador de mensagens binárias codifica as mensagens de Windows Communication Foundation (WCF) em binário na conexão.</span><span class="sxs-lookup"><span data-stu-id="2648b-136">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="2648b-137">Embora essa codificação resulte em uma transmissão muito rápida de mensagens, a interoperabilidade baseada em padrões WS-\* é perdida.</span><span class="sxs-lookup"><span data-stu-id="2648b-137">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2648b-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2648b-138">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="2648b-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="2648b-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="2648b-140">Decodificador de mensagens</span><span class="sxs-lookup"><span data-stu-id="2648b-140">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="2648b-141">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="2648b-141">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="2648b-142">Associações</span><span class="sxs-lookup"><span data-stu-id="2648b-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2648b-143">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="2648b-143">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="2648b-144">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="2648b-144">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
