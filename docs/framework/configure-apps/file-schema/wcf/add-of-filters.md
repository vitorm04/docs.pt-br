---
title: '&lt;adicionar&gt; &lt;filtros&gt;'
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: fe9ce8bc2a0efb9e20800189cd9f948d5e6a2232
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150741"
---
# <a name="ltaddgt-of-ltfiltersgt"></a><span data-ttu-id="d46d6-102">&lt;adicionar&gt; &lt;filtros&gt;</span><span class="sxs-lookup"><span data-stu-id="d46d6-102">&lt;add&gt; of &lt;filters&gt;</span></span>
<span data-ttu-id="d46d6-103">Um filtro XPath que especifica o tipo de mensagem a ser registrada.</span><span class="sxs-lookup"><span data-stu-id="d46d6-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
 <span data-ttu-id="d46d6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d46d6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d46d6-105">\<diagnóstico ></span><span class="sxs-lookup"><span data-stu-id="d46d6-105">\<diagnostic></span></span>  
<span data-ttu-id="d46d6-106">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="d46d6-106">\<messageLogging></span></span>  
<span data-ttu-id="d46d6-107">\<Filtros ></span><span class="sxs-lookup"><span data-stu-id="d46d6-107">\<filters></span></span>  
<span data-ttu-id="d46d6-108">\<add></span><span class="sxs-lookup"><span data-stu-id="d46d6-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d46d6-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d46d6-109">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d46d6-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d46d6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d46d6-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d46d6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d46d6-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="d46d6-112">Attributes</span></span>  
  
|<span data-ttu-id="d46d6-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="d46d6-113">Attribute</span></span>|<span data-ttu-id="d46d6-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="d46d6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d46d6-115">filtrar</span><span class="sxs-lookup"><span data-stu-id="d46d6-115">filter</span></span>|<span data-ttu-id="d46d6-116">Uma cadeia de caracteres que especifica uma consulta em um documento XML definido por uma expressão XPath 1.0.</span><span class="sxs-lookup"><span data-stu-id="d46d6-116">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="d46d6-117">Para obter mais informações, consulte <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="d46d6-117">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d46d6-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d46d6-118">Child Elements</span></span>  
 <span data-ttu-id="d46d6-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d46d6-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d46d6-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d46d6-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d46d6-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="d46d6-121">Element</span></span>|<span data-ttu-id="d46d6-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="d46d6-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d46d6-123">\<Filtros ></span><span class="sxs-lookup"><span data-stu-id="d46d6-123">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters.md)|<span data-ttu-id="d46d6-124">Contém uma coleção de filtros XPath usados para controlar que tipo de mensagem é registrado.</span><span class="sxs-lookup"><span data-stu-id="d46d6-124">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d46d6-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="d46d6-125">Remarks</span></span>  
 <span data-ttu-id="d46d6-126">Os filtros são aplicados apenas na camada de transporte, especificada por `logMessagesAtTransportLevel` é `true`.</span><span class="sxs-lookup"><span data-stu-id="d46d6-126">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="d46d6-127">Registro em log de mensagem malformada e nível de serviço não são afetadas por filtros.</span><span class="sxs-lookup"><span data-stu-id="d46d6-127">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="d46d6-128">Para adicionar um filtro à coleção, use o `add` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="d46d6-128">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="d46d6-129">Quando um ou mais filtros são definidos, apenas as mensagens que correspondem a pelo menos um dos filtros são registradas.</span><span class="sxs-lookup"><span data-stu-id="d46d6-129">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="d46d6-130">Se nenhum filtro for definido, todas as mensagens passam.</span><span class="sxs-lookup"><span data-stu-id="d46d6-130">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="d46d6-131">Filtros dão suporte a sintaxe completa do XPath e são aplicados na ordem em que aparecem no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d46d6-131">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="d46d6-132">Um filtro sintaticamente incorreto resulta em uma exceção de configuração.</span><span class="sxs-lookup"><span data-stu-id="d46d6-132">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="d46d6-133">O exemplo a seguir é um exemplo de como configurar um filtro que registra apenas mensagens que têm uma seção de cabeçalho SOAP.</span><span class="sxs-lookup"><span data-stu-id="d46d6-133">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d46d6-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d46d6-134">Example</span></span>  
 <span data-ttu-id="d46d6-135">O exemplo a seguir é um exemplo de como configurar um filtro que registra apenas mensagens que têm uma seção de cabeçalho SOAP.</span><span class="sxs-lookup"><span data-stu-id="d46d6-135">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d46d6-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d46d6-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>  
 <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>  
 [<span data-ttu-id="d46d6-137">Configurando registros de mensagens em log</span><span class="sxs-lookup"><span data-stu-id="d46d6-137">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [<span data-ttu-id="d46d6-138">Configurando registros de mensagens em log</span><span class="sxs-lookup"><span data-stu-id="d46d6-138">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [<span data-ttu-id="d46d6-139">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="d46d6-139">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
