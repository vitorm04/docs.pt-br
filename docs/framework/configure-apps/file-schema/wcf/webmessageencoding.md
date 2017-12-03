---
title: '&lt;webMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e9629ecbe744ac1f4bbd44e22ac42a3e81fff27a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltwebmessageencodinggt"></a><span data-ttu-id="287bd-102">&lt;webMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="287bd-102">&lt;webMessageEncoding&gt;</span></span>
<span data-ttu-id="287bd-103">Permite que o XML de texto sem formatação, codificações de mensagem (JSON JavaScript Object Notation) e conteúdo binário "CRU" para ser lido e escrito quando usado em um [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] associação.</span><span class="sxs-lookup"><span data-stu-id="287bd-103">Enables plain-text XML, JavaScript Object Notation (JSON) message encodings and "raw" binary content to be read and written when used in a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] binding.</span></span>  
  
 <span data-ttu-id="287bd-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="287bd-104">\<system.serviceModel></span></span>  
<span data-ttu-id="287bd-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="287bd-105">\<bindings></span></span>  
<span data-ttu-id="287bd-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="287bd-106">\<customBinding></span></span>  
<span data-ttu-id="287bd-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="287bd-107">\<binding></span></span>  
<span data-ttu-id="287bd-108">\<webMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="287bd-108">\<webMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="287bd-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="287bd-109">Syntax</span></span>  
  
```xml  
<webMessageEncoding   
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
  
writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="287bd-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="287bd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="287bd-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="287bd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="287bd-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="287bd-112">Attributes</span></span>  
  
|<span data-ttu-id="287bd-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="287bd-113">Attribute</span></span>|<span data-ttu-id="287bd-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="287bd-114">Description</span></span>|  
|---------------|-----------------|  
|`maxReadPoolSize`|<span data-ttu-id="287bd-115">A quantidade de mensagens que podem ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="287bd-115">The amount of messages that can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="287bd-116">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto maior de trabalho.</span><span class="sxs-lookup"><span data-stu-id="287bd-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="287bd-117">O padrão é 64 leitores para cada um dos codificadores internos (texto JSON e "brutos").</span><span class="sxs-lookup"><span data-stu-id="287bd-117">The default is 64 readers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="287bd-118">Aumentar esse número consumo de memória aumenta, mas prepara o codificador para lidar com picos repentinos de mensagens de entrada porque ele é capaz de usar os leitores do pool que já foram criados em vez de criar novos.</span><span class="sxs-lookup"><span data-stu-id="287bd-118">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of incoming messages because it is able to use readers from the pool that are already created instead of creating new ones.</span></span>|  
|`maxWritePoolSize`|<span data-ttu-id="287bd-119">A quantidade de mensagens que podem ser enviadas simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="287bd-119">The amount of messages that can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="287bd-120">Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto maior de trabalho.</span><span class="sxs-lookup"><span data-stu-id="287bd-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="287bd-121">O padrão é 16 gravadores para cada um dos codificadores internos (texto JSON e "brutos").</span><span class="sxs-lookup"><span data-stu-id="287bd-121">The default is 16 writers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="287bd-122">Aumentar esse número consumo de memória aumenta, mas prepara o codificador para lidar com picos repentinos de mensagens de saída porque ele é capaz de usar gravadores do pool que já foram criados em vez de criar novos.</span><span class="sxs-lookup"><span data-stu-id="287bd-122">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of outgoing messages because it is able to use writers from the pool that are already created instead of creating new ones.</span></span>|  
|`writeEncoding`|<span data-ttu-id="287bd-123">Especifica a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="287bd-123">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="287bd-124">Os valores válidos são:</span><span class="sxs-lookup"><span data-stu-id="287bd-124">Valid values are:</span></span><br /><br /> <span data-ttu-id="287bd-125">-UnicodeFffeTextEncoding: Big Endian codificação Unicode.</span><span class="sxs-lookup"><span data-stu-id="287bd-125">-   UnicodeFffeTextEncoding: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="287bd-126">-Utf16TextEncoding: A codificação Unicode.</span><span class="sxs-lookup"><span data-stu-id="287bd-126">-   Utf16TextEncoding: Unicode encoding.</span></span><br /><span data-ttu-id="287bd-127">-Utf8TextEncoding: codificação de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="287bd-127">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="287bd-128">O padrão é Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="287bd-128">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="287bd-129">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="287bd-129">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="287bd-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="287bd-130">Child Elements</span></span>  
  
|<span data-ttu-id="287bd-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="287bd-131">Element</span></span>|<span data-ttu-id="287bd-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="287bd-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="287bd-133">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="287bd-133">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="287bd-134">Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="287bd-134">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="287bd-135">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="287bd-135">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="287bd-136">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="287bd-136">Parent Elements</span></span>  
  
|<span data-ttu-id="287bd-137">Elemento</span><span class="sxs-lookup"><span data-stu-id="287bd-137">Element</span></span>|<span data-ttu-id="287bd-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="287bd-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="287bd-139">\<associação ></span><span class="sxs-lookup"><span data-stu-id="287bd-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="287bd-140">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="287bd-140">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="287bd-141">Comentários</span><span class="sxs-lookup"><span data-stu-id="287bd-141">Remarks</span></span>  
 <span data-ttu-id="287bd-142">Codificação é o processo de transformar uma mensagem em uma sequência de bytes.</span><span class="sxs-lookup"><span data-stu-id="287bd-142">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="287bd-143">Decodificação de é o processo inverso.</span><span class="sxs-lookup"><span data-stu-id="287bd-143">Decoding is the reverse process.</span></span> <span data-ttu-id="287bd-144">Esses processos exigem a especificação de uma codificação de caracteres.</span><span class="sxs-lookup"><span data-stu-id="287bd-144">These processes require the specification of a character encoding.</span></span>  
  
 <span data-ttu-id="287bd-145">O `webMessageEncoding` elemento funciona delegando a uma série de codificadores internas para lidar com codificações XML e JSON em texto sem formatação e dados binários "brutos".</span><span class="sxs-lookup"><span data-stu-id="287bd-145">The `webMessageEncoding` element works by delegating to a series of inner encoders to handle the plain-text XML and JSON encodings, and "raw" binary data.</span></span> <span data-ttu-id="287bd-146">Essa delegação é feita por um codificador de mensagem composto.</span><span class="sxs-lookup"><span data-stu-id="287bd-146">This delegation is done by a composite message encoder.</span></span>  
  
 <span data-ttu-id="287bd-147">Esse elemento de associação e seu codificador composto são usados para controlar a codificação em cenários que não usam mensagens SOAP usada pelo `webHttpBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="287bd-147">This binding element and its composite encoder are used to control the encoding in scenarios that do not use SOAP messaging used by the `webHttpBinding` element.</span></span> <span data-ttu-id="287bd-148">Esses cenários incluem "Plain Old XML" (POX), REST Representational State Transfer (), RSS Really Simple Syndication () e Atom distribuição e JavaScript assíncrono e XML (AJAX).</span><span class="sxs-lookup"><span data-stu-id="287bd-148">These scenarios include "Plain Old XML" (POX), Representational State Transfer (REST), Really Simple Syndication (RSS) and Atom syndication, and Asynchronous JavaScript and XML (AJAX).</span></span> <span data-ttu-id="287bd-149">O codificador de mensagem composto não oferece suporte a SOAP ou WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="287bd-149">The composite message encoder does not support SOAP or WS-Addressing.</span></span>  
  
 <span data-ttu-id="287bd-150">O elemento de associação pode ser configurado com uma codificação de caracteres de gravação usando o `writeEncoding` atributo.</span><span class="sxs-lookup"><span data-stu-id="287bd-150">The binding element can be configured with a write character encoding by using the `writeEncoding` attribute.</span></span> <span data-ttu-id="287bd-151">Fornecido <xref:System.Text.Encoding> valor Especifica o comportamento de gravação para os casos JSON e XML Textual.</span><span class="sxs-lookup"><span data-stu-id="287bd-151">The supplied <xref:System.Text.Encoding> value specifies the behavior on write for the JSON and Textual XML cases.</span></span> <span data-ttu-id="287bd-152">Leitura, qualquer codificação de mensagem válido e a codificação de texto é entendido.</span><span class="sxs-lookup"><span data-stu-id="287bd-152">On read, any valid message encoding and text encoding is understood.</span></span>  
  
 <span data-ttu-id="287bd-153">`maxReadPoolSize`e `maxWritePoolSize` também pode ser usado para definir o número máximo de leitores e gravadores a ser alocada respectivamente.</span><span class="sxs-lookup"><span data-stu-id="287bd-153">`maxReadPoolSize` and `maxWritePoolSize` can also be used to set the maximum number of readers and writers to be allocated respectively.</span></span> <span data-ttu-id="287bd-154">Por padrão, são alocados 64 leitores e 16 gravadores.</span><span class="sxs-lookup"><span data-stu-id="287bd-154">By default 64 readers and 16 writers are allocated.</span></span>  
  
 <span data-ttu-id="287bd-155">Restrições de complexidade padrão também são definidas usando o [ \<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd) elemento para proteger contra uma classe de negação de serviço (DOS) ataques que tentem usar complexidade de mensagem para ligar o processamento do ponto de extremidade recursos.</span><span class="sxs-lookup"><span data-stu-id="287bd-155">Default complexity constraints are also set using the [\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd) element to protect against a class of denial of service (DOS) attacks that attempt to use message complexity to tie up endpoint processing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="287bd-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="287bd-156">Example</span></span>  
  
```xml  
<webMessageEncoding   
    maxReadPoolSize="256"  
    maxWritePoolSize="128"  
    messageVersion="None"  
    textEncoding="utf-8"   
/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="287bd-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="287bd-157">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>  
 [<span data-ttu-id="287bd-158">Codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="287bd-158">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="287bd-159">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="287bd-159">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 <span data-ttu-id="287bd-160">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="287bd-160">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="287bd-161">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="287bd-161">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="287bd-162">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="287bd-162">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="287bd-163">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="287bd-163">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
