---
title: '&lt;adicionar&gt; &lt;filtros&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1ca0d5ae73d01e5bbb719f7bcc9a3f5a19fc291
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltfiltersgt"></a><span data-ttu-id="fcea4-102">&lt;adicionar&gt; &lt;filtros&gt;</span><span class="sxs-lookup"><span data-stu-id="fcea4-102">&lt;add&gt; of &lt;filters&gt;</span></span>
<span data-ttu-id="fcea4-103">Um filtro XPath que especifica o tipo de mensagem a ser registrada.</span><span class="sxs-lookup"><span data-stu-id="fcea4-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
 <span data-ttu-id="fcea4-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="fcea4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fcea4-105">\<diagnóstico ></span><span class="sxs-lookup"><span data-stu-id="fcea4-105">\<diagnostic></span></span>  
<span data-ttu-id="fcea4-106">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="fcea4-106">\<messageLogging></span></span>  
<span data-ttu-id="fcea4-107">\<Filtros ></span><span class="sxs-lookup"><span data-stu-id="fcea4-107">\<filters></span></span>  
<span data-ttu-id="fcea4-108">\<add></span><span class="sxs-lookup"><span data-stu-id="fcea4-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcea4-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fcea4-109">Syntax</span></span>  
  
```xml  
<filters>  
   <add filter="String"/>  
</filters>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fcea4-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fcea4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fcea4-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fcea4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fcea4-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="fcea4-112">Attributes</span></span>  
  
|<span data-ttu-id="fcea4-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="fcea4-113">Attribute</span></span>|<span data-ttu-id="fcea4-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="fcea4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fcea4-115">filtrar</span><span class="sxs-lookup"><span data-stu-id="fcea4-115">filter</span></span>|<span data-ttu-id="fcea4-116">Uma cadeia de caracteres que especifica uma consulta em um documento XML definido por uma expressão XPath 1.0.</span><span class="sxs-lookup"><span data-stu-id="fcea4-116">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="fcea4-117">Para obter mais informações, consulte <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="fcea4-117">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fcea4-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fcea4-118">Child Elements</span></span>  
 <span data-ttu-id="fcea4-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="fcea4-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fcea4-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fcea4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="fcea4-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="fcea4-121">Element</span></span>|<span data-ttu-id="fcea4-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="fcea4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fcea4-123">\<Filtros ></span><span class="sxs-lookup"><span data-stu-id="fcea4-123">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters.md)|<span data-ttu-id="fcea4-124">Contém uma coleção de filtros XPath usados para controlar que tipo de mensagem é registrado.</span><span class="sxs-lookup"><span data-stu-id="fcea4-124">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcea4-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="fcea4-125">Remarks</span></span>  
 <span data-ttu-id="fcea4-126">Os filtros são aplicados apenas na camada de transporte, especificada por `logMessagesAtTransportLevel` é `true`.</span><span class="sxs-lookup"><span data-stu-id="fcea4-126">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="fcea4-127">Log de mensagem malformada e nível de serviço não são afetadas por filtros.</span><span class="sxs-lookup"><span data-stu-id="fcea4-127">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="fcea4-128">Para adicionar um filtro à coleção, use o `add` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="fcea4-128">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="fcea4-129">Quando um ou mais filtros são definidos, apenas as mensagens que correspondem a pelo menos um dos filtros são registradas.</span><span class="sxs-lookup"><span data-stu-id="fcea4-129">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="fcea4-130">Se nenhum filtro for definido, todas as mensagens passam.</span><span class="sxs-lookup"><span data-stu-id="fcea4-130">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="fcea4-131">Os filtros oferece suporte a sintaxe completa do XPath e são aplicados na ordem em que aparecem no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="fcea4-131">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="fcea4-132">Um filtro sintaticamente incorreto resulta em uma exceção de configuração.</span><span class="sxs-lookup"><span data-stu-id="fcea4-132">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="fcea4-133">Este é um exemplo de como configurar um filtro que registra apenas as mensagens que têm uma seção de cabeçalho SOAP.</span><span class="sxs-lookup"><span data-stu-id="fcea4-133">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcea4-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fcea4-134">Example</span></span>  
 <span data-ttu-id="fcea4-135">Este é um exemplo de como configurar um filtro que registra apenas as mensagens que têm uma seção de cabeçalho SOAP.</span><span class="sxs-lookup"><span data-stu-id="fcea4-135">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fcea4-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fcea4-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>  
 <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>  
 [<span data-ttu-id="fcea4-137">Configurando registros de mensagens em log</span><span class="sxs-lookup"><span data-stu-id="fcea4-137">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [<span data-ttu-id="fcea4-138">Configurando registros de mensagens em log</span><span class="sxs-lookup"><span data-stu-id="fcea4-138">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [<span data-ttu-id="fcea4-139">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="fcea4-139">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
