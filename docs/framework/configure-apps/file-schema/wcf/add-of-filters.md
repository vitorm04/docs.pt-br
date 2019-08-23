---
title: <add> de <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: e7975bea1435abdb77528628e7b96c65a72cbbc2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926693"
---
# <a name="add-of-filters"></a><span data-ttu-id="cc8b3-102">\<Adicionar > de \<filtros ></span><span class="sxs-lookup"><span data-stu-id="cc8b3-102">\<add> of \<filters></span></span>
<span data-ttu-id="cc8b3-103">Um filtro XPath que especifica o tipo de mensagem a ser registrada.</span><span class="sxs-lookup"><span data-stu-id="cc8b3-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
 <span data-ttu-id="cc8b3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cc8b3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cc8b3-105">\<> de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="cc8b3-105">\<diagnostic></span></span>  
<span data-ttu-id="cc8b3-106">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="cc8b3-106">\<messageLogging></span></span>  
<span data-ttu-id="cc8b3-107">\<Filtros ></span><span class="sxs-lookup"><span data-stu-id="cc8b3-107">\<filters></span></span>  
<span data-ttu-id="cc8b3-108">\<add></span><span class="sxs-lookup"><span data-stu-id="cc8b3-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc8b3-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc8b3-109">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc8b3-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cc8b3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cc8b3-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cc8b3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc8b3-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="cc8b3-112">Attributes</span></span>  
  
|<span data-ttu-id="cc8b3-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="cc8b3-113">Attribute</span></span>|<span data-ttu-id="cc8b3-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc8b3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cc8b3-115">filtrar</span><span class="sxs-lookup"><span data-stu-id="cc8b3-115">filter</span></span>|<span data-ttu-id="cc8b3-116">Uma cadeia de caracteres que especifica uma consulta em um documento XML definido por uma expressão XPath 1,0.</span><span class="sxs-lookup"><span data-stu-id="cc8b3-116">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="cc8b3-117">Para obter mais informações, consulte <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="cc8b3-117">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc8b3-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cc8b3-118">Child Elements</span></span>  
 <span data-ttu-id="cc8b3-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="cc8b3-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cc8b3-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cc8b3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="cc8b3-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="cc8b3-121">Element</span></span>|<span data-ttu-id="cc8b3-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc8b3-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc8b3-123">\<filters></span><span class="sxs-lookup"><span data-stu-id="cc8b3-123">\<filters></span></span>](filters.md)|<span data-ttu-id="cc8b3-124">Contém uma coleção de filtros XPath usados para controlar que tipo de mensagem é registrada.</span><span class="sxs-lookup"><span data-stu-id="cc8b3-124">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc8b3-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="cc8b3-125">Remarks</span></span>  
 <span data-ttu-id="cc8b3-126">Os filtros são aplicados somente na camada de transporte, especificada `logMessagesAtTransportLevel` por `true`is.</span><span class="sxs-lookup"><span data-stu-id="cc8b3-126">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="cc8b3-127">O nível de serviço e o log de mensagens malformados não são afetados por filtros.</span><span class="sxs-lookup"><span data-stu-id="cc8b3-127">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="cc8b3-128">Para adicionar um filtro à coleção, use a `add` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="cc8b3-128">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="cc8b3-129">Quando um ou mais filtros são definidos, somente as mensagens que correspondem a pelo menos um dos filtros são registradas.</span><span class="sxs-lookup"><span data-stu-id="cc8b3-129">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="cc8b3-130">Se nenhum filtro for definido, todas as mensagens passarão.</span><span class="sxs-lookup"><span data-stu-id="cc8b3-130">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="cc8b3-131">Os filtros dão suporte à sintaxe XPath completa e são aplicados na ordem em que aparecem no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="cc8b3-131">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="cc8b3-132">Um filtro sintaticamente incorreto resulta em uma exceção de configuração.</span><span class="sxs-lookup"><span data-stu-id="cc8b3-132">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="cc8b3-133">Veja a seguir um exemplo de como configurar um filtro que registra somente as mensagens que têm uma seção de cabeçalho SOAP.</span><span class="sxs-lookup"><span data-stu-id="cc8b3-133">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc8b3-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cc8b3-134">Example</span></span>  
 <span data-ttu-id="cc8b3-135">Veja a seguir um exemplo de como configurar um filtro que registra somente as mensagens que têm uma seção de cabeçalho SOAP.</span><span class="sxs-lookup"><span data-stu-id="cc8b3-135">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cc8b3-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc8b3-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="cc8b3-137">Configurando registros de mensagens em log</span><span class="sxs-lookup"><span data-stu-id="cc8b3-137">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="cc8b3-138">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="cc8b3-138">\<messageLogging></span></span>](messagelogging.md)
