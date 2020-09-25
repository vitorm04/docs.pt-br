---
title: <webMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: b250b64e1f073e00e4047ab6931a00d0b93b55b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177872"
---
# \<webMessageEncoding>

<span data-ttu-id="c2c8b-101">Habilita XML de texto simples, codificações mensagem JSON (JavaScript Object Notation) e conteúdo binário "bruto" para ser lido e gravado quando usado em uma associação WCF (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="c2c8b-101">Enables plain-text XML, JavaScript Object Notation (JSON) message encodings and "raw" binary content to be read and written when used in a Windows Communication Foundation (WCF) binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="c2c8b-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2c8b-102">Syntax</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="Integer"
                    maxWritePoolSize="Integer"
                    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2c8b-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c2c8b-103">Attributes and Elements</span></span>  

 <span data-ttu-id="c2c8b-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2c8b-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="c2c8b-105">Attributes</span></span>  
  
|<span data-ttu-id="c2c8b-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="c2c8b-106">Attribute</span></span>|<span data-ttu-id="c2c8b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2c8b-107">Description</span></span>|  
|---------------|-----------------|  
|`maxReadPoolSize`|<span data-ttu-id="c2c8b-108">A quantidade de mensagens que podem ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-108">The amount of messages that can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="c2c8b-109">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-109">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="c2c8b-110">O padrão é 64 leitores para cada um dos codificadores internos (text, JSON e "RAW").</span><span class="sxs-lookup"><span data-stu-id="c2c8b-110">The default is 64 readers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="c2c8b-111">O aumento desse número aumenta o consumo de memória, mas prepara o codificador para lidar com picos repentinos de mensagens de entrada, pois ele é capaz de usar leitores do pool que já foram criados, em vez de criar novos.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-111">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of incoming messages because it is able to use readers from the pool that are already created instead of creating new ones.</span></span>|  
|`maxWritePoolSize`|<span data-ttu-id="c2c8b-112">A quantidade de mensagens que podem ser enviadas simultaneamente sem alocar novos gravadores.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-112">The amount of messages that can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="c2c8b-113">Tamanhos de pool maiores tornam o sistema mais tolerante a picos de atividade no custo de um conjunto de trabalho maior.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-113">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="c2c8b-114">O padrão é 16 gravadores para cada um dos codificadores internos (text, JSON e "RAW").</span><span class="sxs-lookup"><span data-stu-id="c2c8b-114">The default is 16 writers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="c2c8b-115">O aumento desse número aumenta o consumo de memória, mas prepara o codificador para lidar com picos repentinos de mensagens de saída, pois ele é capaz de usar gravadores do pool que já foram criados, em vez de criar novos.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-115">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of outgoing messages because it is able to use writers from the pool that are already created instead of creating new ones.</span></span>|  
|`writeEncoding`|<span data-ttu-id="c2c8b-116">Especifica a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-116">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="c2c8b-117">Os valores válidos são:</span><span class="sxs-lookup"><span data-stu-id="c2c8b-117">Valid values are:</span></span><br /><br /> <span data-ttu-id="c2c8b-118">-UnicodeFffeTextEncoding: codificação Unicode big endian.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-118">-   UnicodeFffeTextEncoding: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="c2c8b-119">-Utf16TextEncoding: codificação Unicode.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-119">-   Utf16TextEncoding: Unicode encoding.</span></span><br /><span data-ttu-id="c2c8b-120">-Utf8TextEncoding: codificação de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-120">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="c2c8b-121">O padrão é Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-121">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="c2c8b-122">Esse atributo é do tipo <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="c2c8b-122">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2c8b-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c2c8b-123">Child Elements</span></span>  
  
|<span data-ttu-id="c2c8b-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="c2c8b-124">Element</span></span>|<span data-ttu-id="c2c8b-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2c8b-125">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="c2c8b-126">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-126">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="c2c8b-127">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="c2c8b-127">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c2c8b-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c2c8b-128">Parent Elements</span></span>  
  
|<span data-ttu-id="c2c8b-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="c2c8b-129">Element</span></span>|<span data-ttu-id="c2c8b-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2c8b-130">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="c2c8b-131">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2c8b-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2c8b-132">Remarks</span></span>  

 <span data-ttu-id="c2c8b-133">A codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-133">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="c2c8b-134">A decodificação é o processo reverso.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-134">Decoding is the reverse process.</span></span> <span data-ttu-id="c2c8b-135">Esses processos exigem a especificação de uma codificação de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-135">These processes require the specification of a character encoding.</span></span>  
  
 <span data-ttu-id="c2c8b-136">O `webMessageEncoding` elemento funciona delegando a uma série de codificadores internos para manipular as codificações XML e JSON de texto sem formatação e dados binários "brutos".</span><span class="sxs-lookup"><span data-stu-id="c2c8b-136">The `webMessageEncoding` element works by delegating to a series of inner encoders to handle the plain-text XML and JSON encodings, and "raw" binary data.</span></span> <span data-ttu-id="c2c8b-137">Essa delegação é feita por um codificador de mensagem composta.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-137">This delegation is done by a composite message encoder.</span></span>  
  
 <span data-ttu-id="c2c8b-138">Esse elemento Binding e seu codificador composto são usados para controlar a codificação em cenários que não usam mensagens SOAP usadas pelo `webHttpBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-138">This binding element and its composite encoder are used to control the encoding in scenarios that do not use SOAP messaging used by the `webHttpBinding` element.</span></span> <span data-ttu-id="c2c8b-139">Esses cenários incluem "XML antigo" (POX), transferência de estado de reapresentação (REST), agregação real (RSS) e agregação Atom, além de JavaScript e XML assíncronos (AJAX).</span><span class="sxs-lookup"><span data-stu-id="c2c8b-139">These scenarios include "Plain Old XML" (POX), Representational State Transfer (REST), Really Simple Syndication (RSS) and Atom syndication, and Asynchronous JavaScript and XML (AJAX).</span></span> <span data-ttu-id="c2c8b-140">O codificador de mensagens compostas não dá suporte a SOAP ou WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-140">The composite message encoder does not support SOAP or WS-Addressing.</span></span>  
  
 <span data-ttu-id="c2c8b-141">O elemento Binding pode ser configurado com uma codificação Write Character usando o `writeEncoding` atributo.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-141">The binding element can be configured with a write character encoding by using the `writeEncoding` attribute.</span></span> <span data-ttu-id="c2c8b-142">O <xref:System.Text.Encoding> valor fornecido especifica o comportamento na gravação para os casos JSON e XML textual.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-142">The supplied <xref:System.Text.Encoding> value specifies the behavior on write for the JSON and Textual XML cases.</span></span> <span data-ttu-id="c2c8b-143">Na leitura, qualquer codificação de mensagem e codificação de texto válidas são compreendidas.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-143">On read, any valid message encoding and text encoding is understood.</span></span>  
  
 <span data-ttu-id="c2c8b-144">`maxReadPoolSize` e `maxWritePoolSize` também pode ser usado para definir o número máximo de leitores e gravadores a serem alocados, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-144">`maxReadPoolSize` and `maxWritePoolSize` can also be used to set the maximum number of readers and writers to be allocated respectively.</span></span> <span data-ttu-id="c2c8b-145">Por padrão, os leitores 64 e 16 gravadores são alocados.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-145">By default 64 readers and 16 writers are allocated.</span></span>  
  
 <span data-ttu-id="c2c8b-146">As restrições de complexidade padrão também são definidas usando o [\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) elemento para proteger contra uma classe de ataques de dos (negação de serviço) que tentam usar a complexidade da mensagem para vincular os recursos de processamento do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="c2c8b-146">Default complexity constraints are also set using the [\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) element to protect against a class of denial of service (DOS) attacks that attempt to use message complexity to tie up endpoint processing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2c8b-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c2c8b-147">Example</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="256"
                    maxWritePoolSize="128"
                    messageVersion="None"
                    textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="c2c8b-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="c2c8b-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [<span data-ttu-id="c2c8b-149">Decodificador de mensagens</span><span class="sxs-lookup"><span data-stu-id="c2c8b-149">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="c2c8b-150">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="c2c8b-150">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="c2c8b-151">Associações</span><span class="sxs-lookup"><span data-stu-id="c2c8b-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c2c8b-152">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="c2c8b-152">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c2c8b-153">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="c2c8b-153">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
