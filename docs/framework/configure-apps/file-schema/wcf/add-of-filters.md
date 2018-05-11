---
title: '&lt;adicionar&gt; &lt;filtros&gt;'
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 2a26a94c01fdb04b8a9e2d381a28cc909bbdac8f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltfiltersgt"></a><span data-ttu-id="cb01d-102">&lt;adicionar&gt; &lt;filtros&gt;</span><span class="sxs-lookup"><span data-stu-id="cb01d-102">&lt;add&gt; of &lt;filters&gt;</span></span>
<span data-ttu-id="cb01d-103">Um filtro XPath que especifica o tipo de mensagem a ser registrada.</span><span class="sxs-lookup"><span data-stu-id="cb01d-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
 <span data-ttu-id="cb01d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cb01d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cb01d-105">\<diagnóstico ></span><span class="sxs-lookup"><span data-stu-id="cb01d-105">\<diagnostic></span></span>  
<span data-ttu-id="cb01d-106">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="cb01d-106">\<messageLogging></span></span>  
<span data-ttu-id="cb01d-107">\<Filtros ></span><span class="sxs-lookup"><span data-stu-id="cb01d-107">\<filters></span></span>  
<span data-ttu-id="cb01d-108">\<add></span><span class="sxs-lookup"><span data-stu-id="cb01d-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb01d-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb01d-109">Syntax</span></span>  
  
```xml  
<filters>  
   <add filter="String"/>  
</filters>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb01d-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cb01d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cb01d-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cb01d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb01d-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="cb01d-112">Attributes</span></span>  
  
|<span data-ttu-id="cb01d-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="cb01d-113">Attribute</span></span>|<span data-ttu-id="cb01d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb01d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cb01d-115">filtrar</span><span class="sxs-lookup"><span data-stu-id="cb01d-115">filter</span></span>|<span data-ttu-id="cb01d-116">Uma cadeia de caracteres que especifica uma consulta em um documento XML definido por uma expressão XPath 1.0.</span><span class="sxs-lookup"><span data-stu-id="cb01d-116">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="cb01d-117">Para obter mais informações, consulte <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="cb01d-117">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb01d-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cb01d-118">Child Elements</span></span>  
 <span data-ttu-id="cb01d-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="cb01d-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb01d-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cb01d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="cb01d-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="cb01d-121">Element</span></span>|<span data-ttu-id="cb01d-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb01d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb01d-123">\<Filtros ></span><span class="sxs-lookup"><span data-stu-id="cb01d-123">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters.md)|<span data-ttu-id="cb01d-124">Contém uma coleção de filtros XPath usados para controlar que tipo de mensagem é registrado.</span><span class="sxs-lookup"><span data-stu-id="cb01d-124">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb01d-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="cb01d-125">Remarks</span></span>  
 <span data-ttu-id="cb01d-126">Os filtros são aplicados apenas na camada de transporte, especificada por `logMessagesAtTransportLevel` é `true`.</span><span class="sxs-lookup"><span data-stu-id="cb01d-126">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="cb01d-127">Log de mensagem malformada e nível de serviço não são afetadas por filtros.</span><span class="sxs-lookup"><span data-stu-id="cb01d-127">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="cb01d-128">Para adicionar um filtro à coleção, use o `add` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="cb01d-128">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="cb01d-129">Quando um ou mais filtros são definidos, apenas as mensagens que correspondem a pelo menos um dos filtros são registradas.</span><span class="sxs-lookup"><span data-stu-id="cb01d-129">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="cb01d-130">Se nenhum filtro for definido, todas as mensagens passam.</span><span class="sxs-lookup"><span data-stu-id="cb01d-130">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="cb01d-131">Os filtros oferece suporte a sintaxe completa do XPath e são aplicados na ordem em que aparecem no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="cb01d-131">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="cb01d-132">Um filtro sintaticamente incorreto resulta em uma exceção de configuração.</span><span class="sxs-lookup"><span data-stu-id="cb01d-132">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="cb01d-133">Este é um exemplo de como configurar um filtro que registra apenas as mensagens que têm uma seção de cabeçalho SOAP.</span><span class="sxs-lookup"><span data-stu-id="cb01d-133">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb01d-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cb01d-134">Example</span></span>  
 <span data-ttu-id="cb01d-135">Este é um exemplo de como configurar um filtro que registra apenas as mensagens que têm uma seção de cabeçalho SOAP.</span><span class="sxs-lookup"><span data-stu-id="cb01d-135">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
```xml  
<messageLogging logEntireMessage="true"  
     logMalformedMessages="true" logMessagesAtServiceLevel="true"  
     logMessagesAtTransportLevel="true" maxMessagesToLog="420">  
     <filters>  
        <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">  
                        /soap:Envelope/soap:Headers  
        </add>  
     </filters>  
</messageLogging>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb01d-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb01d-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>  
 <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>  
 [<span data-ttu-id="cb01d-137">Configurando registros de mensagens em log</span><span class="sxs-lookup"><span data-stu-id="cb01d-137">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [<span data-ttu-id="cb01d-138">Configurando registros de mensagens em log</span><span class="sxs-lookup"><span data-stu-id="cb01d-138">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [<span data-ttu-id="cb01d-139">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="cb01d-139">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
