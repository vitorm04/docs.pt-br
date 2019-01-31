---
title: <add> De <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 0e42766cd94b58562bc5728d517e65e80f558cda
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288789"
---
# <a name="add-of-filters"></a><span data-ttu-id="79807-102">\<Adicionar > de \<filtros ></span><span class="sxs-lookup"><span data-stu-id="79807-102">\<add> of \<filters></span></span>
<span data-ttu-id="79807-103">Um filtro XPath que especifica o tipo de mensagem a ser registrada.</span><span class="sxs-lookup"><span data-stu-id="79807-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
 <span data-ttu-id="79807-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="79807-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="79807-105">\<diagnóstico ></span><span class="sxs-lookup"><span data-stu-id="79807-105">\<diagnostic></span></span>  
<span data-ttu-id="79807-106">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="79807-106">\<messageLogging></span></span>  
<span data-ttu-id="79807-107">\<filters></span><span class="sxs-lookup"><span data-stu-id="79807-107">\<filters></span></span>  
<span data-ttu-id="79807-108">\<add></span><span class="sxs-lookup"><span data-stu-id="79807-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79807-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="79807-109">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79807-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="79807-110">Attributes and Elements</span></span>  
 <span data-ttu-id="79807-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="79807-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79807-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="79807-112">Attributes</span></span>  
  
|<span data-ttu-id="79807-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="79807-113">Attribute</span></span>|<span data-ttu-id="79807-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="79807-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="79807-115">filtrar</span><span class="sxs-lookup"><span data-stu-id="79807-115">filter</span></span>|<span data-ttu-id="79807-116">Uma cadeia de caracteres que especifica uma consulta em um documento XML definido por uma expressão XPath 1.0.</span><span class="sxs-lookup"><span data-stu-id="79807-116">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="79807-117">Para obter mais informações, consulte <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="79807-117">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79807-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="79807-118">Child Elements</span></span>  
 <span data-ttu-id="79807-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="79807-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="79807-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="79807-120">Parent Elements</span></span>  
  
|<span data-ttu-id="79807-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="79807-121">Element</span></span>|<span data-ttu-id="79807-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="79807-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79807-123">\<filters></span><span class="sxs-lookup"><span data-stu-id="79807-123">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters.md)|<span data-ttu-id="79807-124">Contém uma coleção de filtros XPath usados para controlar que tipo de mensagem é registrado.</span><span class="sxs-lookup"><span data-stu-id="79807-124">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79807-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="79807-125">Remarks</span></span>  
 <span data-ttu-id="79807-126">Os filtros são aplicados apenas na camada de transporte, especificada por `logMessagesAtTransportLevel` é `true`.</span><span class="sxs-lookup"><span data-stu-id="79807-126">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="79807-127">Registro em log de mensagem malformada e nível de serviço não são afetadas por filtros.</span><span class="sxs-lookup"><span data-stu-id="79807-127">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="79807-128">Para adicionar um filtro à coleção, use o `add` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="79807-128">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="79807-129">Quando um ou mais filtros são definidos, apenas as mensagens que correspondem a pelo menos um dos filtros são registradas.</span><span class="sxs-lookup"><span data-stu-id="79807-129">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="79807-130">Se nenhum filtro for definido, todas as mensagens passam.</span><span class="sxs-lookup"><span data-stu-id="79807-130">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="79807-131">Filtros dão suporte a sintaxe completa do XPath e são aplicados na ordem em que aparecem no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="79807-131">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="79807-132">Um filtro sintaticamente incorreto resulta em uma exceção de configuração.</span><span class="sxs-lookup"><span data-stu-id="79807-132">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="79807-133">O exemplo a seguir é um exemplo de como configurar um filtro que registra apenas mensagens que têm uma seção de cabeçalho SOAP.</span><span class="sxs-lookup"><span data-stu-id="79807-133">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79807-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="79807-134">Example</span></span>  
 <span data-ttu-id="79807-135">O exemplo a seguir é um exemplo de como configurar um filtro que registra apenas mensagens que têm uma seção de cabeçalho SOAP.</span><span class="sxs-lookup"><span data-stu-id="79807-135">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="79807-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79807-136">See also</span></span>
- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="79807-137">Configurando registros de mensagens em log</span><span class="sxs-lookup"><span data-stu-id="79807-137">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="79807-138">Configurando registros de mensagens em log</span><span class="sxs-lookup"><span data-stu-id="79807-138">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="79807-139">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="79807-139">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
