---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: cffde19c8fd06836eaaedb5c4fc8687b97ae0afe
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556174"
---
# \<mtomMessageEncoding>
<span data-ttu-id="17998-101">Especifica a codificação e o controle de versão de mensagem usados para mensagens baseadas no mecanismo de otimização de transmissão de mensagens SOAP (MTOM).</span><span class="sxs-lookup"><span data-stu-id="17998-101">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mtomMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="17998-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="17998-102">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17998-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="17998-103">Attributes and Elements</span></span>  
 <span data-ttu-id="17998-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="17998-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17998-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="17998-105">Attributes</span></span>  
  
|<span data-ttu-id="17998-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="17998-106">Attribute</span></span>|<span data-ttu-id="17998-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="17998-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="17998-108">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="17998-108">maxBufferSize</span></span>|<span data-ttu-id="17998-109">Um inteiro que especifica o tamanho máximo do buffer que pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="17998-109">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="17998-110">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="17998-110">maxReadPoolSize</span></span>|<span data-ttu-id="17998-111">Um inteiro que especifica quantas mensagens podem ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="17998-111">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="17998-112">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="17998-112">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="17998-113">O padrão é 64.</span><span class="sxs-lookup"><span data-stu-id="17998-113">The default is 64.</span></span>|  
|<span data-ttu-id="17998-114">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="17998-114">maxWritePoolSize</span></span>|<span data-ttu-id="17998-115">Um inteiro que especifica quantas mensagens podem ser enviadas simultaneamente sem alocar novos gravadores.</span><span class="sxs-lookup"><span data-stu-id="17998-115">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="17998-116">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="17998-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="17998-117">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="17998-117">The default is 16.</span></span>|  
|<span data-ttu-id="17998-118">messageVersion</span><span class="sxs-lookup"><span data-stu-id="17998-118">messageVersion</span></span>|<span data-ttu-id="17998-119">Especifica a versão SOAP das mensagens enviadas usando a associação.</span><span class="sxs-lookup"><span data-stu-id="17998-119">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="17998-120">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="17998-120">Valid values are</span></span><br /><br /> <span data-ttu-id="17998-121">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="17998-121">-   Soap11Addressing1</span></span><br /><span data-ttu-id="17998-122">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="17998-122">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="17998-123">O padrão é Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="17998-123">The default is Soap12Addressing10.</span></span> <span data-ttu-id="17998-124">Esse atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion> .</span><span class="sxs-lookup"><span data-stu-id="17998-124">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="17998-125">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="17998-125">writeEncoding</span></span>|<span data-ttu-id="17998-126">Especifica a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="17998-126">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="17998-127">Os valores válidos são</span><span class="sxs-lookup"><span data-stu-id="17998-127">Valid values are</span></span><br /><br /> <span data-ttu-id="17998-128">-UnicodeFffeTextEncoding: codificação BigEndian Unicode</span><span class="sxs-lookup"><span data-stu-id="17998-128">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="17998-129">-Utf16TextEncoding: codificação Unicode</span><span class="sxs-lookup"><span data-stu-id="17998-129">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="17998-130">-Utf8TextEncoding: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="17998-130">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="17998-131">O padrão é Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="17998-131">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="17998-132">Esse atributo é do tipo <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="17998-132">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17998-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="17998-133">Child Elements</span></span>  
  
|<span data-ttu-id="17998-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="17998-134">Element</span></span>|<span data-ttu-id="17998-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="17998-135">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="17998-136">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="17998-136">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="17998-137">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="17998-137">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="17998-138">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="17998-138">Parent Elements</span></span>  
  
|<span data-ttu-id="17998-139">Elemento</span><span class="sxs-lookup"><span data-stu-id="17998-139">Element</span></span>|<span data-ttu-id="17998-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="17998-140">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="17998-141">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="17998-141">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17998-142">Comentários</span><span class="sxs-lookup"><span data-stu-id="17998-142">Remarks</span></span>  
 <span data-ttu-id="17998-143">A codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="17998-143">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="17998-144">A decodificação é o processo reverso.</span><span class="sxs-lookup"><span data-stu-id="17998-144">Decoding is the reverse process.</span></span> <span data-ttu-id="17998-145">O Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: texto, binário e MTOM (mecanismo de otimização de transmissão de mensagens).</span><span class="sxs-lookup"><span data-stu-id="17998-145">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="17998-146">O `MtomMessageEncoding` elemento Especifica a codificação de caracteres e o controle de versão de mensagem e outras configurações usadas para mensagens usando uma codificação MTOM (mecanismo de otimização de transmissão de mensagens).</span><span class="sxs-lookup"><span data-stu-id="17998-146">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="17998-147">O MTOM é uma tecnologia eficiente para transmitir dados binários em mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="17998-147">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="17998-148">O codificador MTOM tenta criar um equilíbrio entre eficiência e interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="17998-148">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="17998-149">A codificação MTOM transmite a maioria dos XML na forma textual, mas otimiza grandes blocos de dados binários transmitindo-os como estão, sem conversão para seu formato codificado em base64.</span><span class="sxs-lookup"><span data-stu-id="17998-149">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17998-150">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17998-150">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="17998-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="17998-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="17998-152">Decodificador de mensagens</span><span class="sxs-lookup"><span data-stu-id="17998-152">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="17998-153">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="17998-153">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="17998-154">Associações</span><span class="sxs-lookup"><span data-stu-id="17998-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="17998-155">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="17998-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="17998-156">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="17998-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
