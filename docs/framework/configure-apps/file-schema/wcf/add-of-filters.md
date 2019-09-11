---
title: <add> de <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 280c516b17a133930bc4b6621a8c9bc7f4781085
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850558"
---
# <a name="add-of-filters"></a><span data-ttu-id="27a18-102">\<Adicionar > de \<filtros ></span><span class="sxs-lookup"><span data-stu-id="27a18-102">\<add> of \<filters></span></span>
<span data-ttu-id="27a18-103">Um filtro XPath que especifica o tipo de mensagem a ser registrada.</span><span class="sxs-lookup"><span data-stu-id="27a18-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
<span data-ttu-id="27a18-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="27a18-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="27a18-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="27a18-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="27a18-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de diagnóstico**](diagnostics.md)</span><span class="sxs-lookup"><span data-stu-id="27a18-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)</span></span>\
<span data-ttu-id="27a18-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> messageLogging**](messagelogging.md)</span><span class="sxs-lookup"><span data-stu-id="27a18-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<messageLogging>**](messagelogging.md)</span></span>\
<span data-ttu-id="27a18-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Filtros >** ](filters.md)</span><span class="sxs-lookup"><span data-stu-id="27a18-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters.md)</span></span>\
<span data-ttu-id="27a18-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**</span><span class="sxs-lookup"><span data-stu-id="27a18-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27a18-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27a18-110">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27a18-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="27a18-111">Attributes and Elements</span></span>  
 <span data-ttu-id="27a18-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="27a18-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27a18-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="27a18-113">Attributes</span></span>  
  
|<span data-ttu-id="27a18-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="27a18-114">Attribute</span></span>|<span data-ttu-id="27a18-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="27a18-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="27a18-116">filtrar</span><span class="sxs-lookup"><span data-stu-id="27a18-116">filter</span></span>|<span data-ttu-id="27a18-117">Uma cadeia de caracteres que especifica uma consulta em um documento XML definido por uma expressão XPath 1,0.</span><span class="sxs-lookup"><span data-stu-id="27a18-117">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="27a18-118">Para obter mais informações, consulte <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="27a18-118">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27a18-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="27a18-119">Child Elements</span></span>  
 <span data-ttu-id="27a18-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="27a18-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27a18-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="27a18-121">Parent Elements</span></span>  
  
|<span data-ttu-id="27a18-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="27a18-122">Element</span></span>|<span data-ttu-id="27a18-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="27a18-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27a18-124">\<filters></span><span class="sxs-lookup"><span data-stu-id="27a18-124">\<filters></span></span>](filters.md)|<span data-ttu-id="27a18-125">Contém uma coleção de filtros XPath usados para controlar que tipo de mensagem é registrada.</span><span class="sxs-lookup"><span data-stu-id="27a18-125">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27a18-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="27a18-126">Remarks</span></span>  
 <span data-ttu-id="27a18-127">Os filtros são aplicados somente na camada de transporte, especificada `logMessagesAtTransportLevel` por `true`is.</span><span class="sxs-lookup"><span data-stu-id="27a18-127">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="27a18-128">O nível de serviço e o log de mensagens malformados não são afetados por filtros.</span><span class="sxs-lookup"><span data-stu-id="27a18-128">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="27a18-129">Para adicionar um filtro à coleção, use a `add` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="27a18-129">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="27a18-130">Quando um ou mais filtros são definidos, somente as mensagens que correspondem a pelo menos um dos filtros são registradas.</span><span class="sxs-lookup"><span data-stu-id="27a18-130">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="27a18-131">Se nenhum filtro for definido, todas as mensagens passarão.</span><span class="sxs-lookup"><span data-stu-id="27a18-131">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="27a18-132">Os filtros dão suporte à sintaxe XPath completa e são aplicados na ordem em que aparecem no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="27a18-132">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="27a18-133">Um filtro sintaticamente incorreto resulta em uma exceção de configuração.</span><span class="sxs-lookup"><span data-stu-id="27a18-133">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="27a18-134">Veja a seguir um exemplo de como configurar um filtro que registra somente as mensagens que têm uma seção de cabeçalho SOAP.</span><span class="sxs-lookup"><span data-stu-id="27a18-134">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27a18-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="27a18-135">Example</span></span>  
 <span data-ttu-id="27a18-136">Veja a seguir um exemplo de como configurar um filtro que registra somente as mensagens que têm uma seção de cabeçalho SOAP.</span><span class="sxs-lookup"><span data-stu-id="27a18-136">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
```xml  
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="420">
  <filters>
    <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
      /soap:Envelope/soap:Headers
    </add>
  </filters>
</messageLogging>
```  
  
## <a name="see-also"></a><span data-ttu-id="27a18-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27a18-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="27a18-138">Configurando registros de mensagens em log</span><span class="sxs-lookup"><span data-stu-id="27a18-138">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="27a18-139">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="27a18-139">\<messageLogging></span></span>](messagelogging.md)
