---
title: '&lt;Filtros&gt;'
ms.date: 03/30/2017
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
ms.openlocfilehash: aae70fbe873eee10fcf95dcdd443dfa9ae6efb57
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148962"
---
# <a name="ltfiltersgt"></a><span data-ttu-id="7fe14-102">&lt;Filtros&gt;</span><span class="sxs-lookup"><span data-stu-id="7fe14-102">&lt;filters&gt;</span></span>

<span data-ttu-id="7fe14-103">O `filters` elemento contém uma coleção de filtros XPath usados para controlar que tipo de mensagem é registrado.</span><span class="sxs-lookup"><span data-stu-id="7fe14-103">The `filters` element holds a collection of XPath filters used to control what kind of message is logged.</span></span>

<span data-ttu-id="7fe14-104">Os filtros são aplicados apenas na camada de transporte, especificada por `logMessagesAtTransportLevel` é `true`.</span><span class="sxs-lookup"><span data-stu-id="7fe14-104">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="7fe14-105">Registro em log de mensagem malformada e nível de serviço não são afetadas por filtros.</span><span class="sxs-lookup"><span data-stu-id="7fe14-105">Service level and malformed message logging are not affected by filters.</span></span>

<span data-ttu-id="7fe14-106">Para adicionar um filtro à coleção, use o `add` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="7fe14-106">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="7fe14-107">Quando um ou mais filtros são definidos, apenas as mensagens que correspondem a pelo menos um dos filtros são registradas.</span><span class="sxs-lookup"><span data-stu-id="7fe14-107">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="7fe14-108">Se nenhum filtro for definido, todas as mensagens passam.</span><span class="sxs-lookup"><span data-stu-id="7fe14-108">If no filter is defined, all messages pass through.</span></span>

<span data-ttu-id="7fe14-109">Filtros dão suporte a sintaxe completa do XPath e são aplicados na ordem em que aparecem no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="7fe14-109">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="7fe14-110">Um filtro sintaticamente incorreto resulta em uma exceção de configuração.</span><span class="sxs-lookup"><span data-stu-id="7fe14-110">A syntactically incorrect filter results in a configuration exception.</span></span>

<span data-ttu-id="7fe14-111">O exemplo a seguir é um exemplo de como configurar um filtro que registra apenas mensagens que têm uma seção de cabeçalho SOAP.</span><span class="sxs-lookup"><span data-stu-id="7fe14-111">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="7fe14-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fe14-112">See also</span></span>

 <span data-ttu-id="7fe14-113"><xref:System.ServiceModel.Configuration.DiagnosticSection> <xref:System.ServiceModel.Diagnostics></span><span class="sxs-lookup"><span data-stu-id="7fe14-113"><xref:System.ServiceModel.Configuration.DiagnosticSection> <xref:System.ServiceModel.Diagnostics></span></span>
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>
 <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
 <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection>
 <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
 <span data-ttu-id="7fe14-114">[Configurando o log de mensagens](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) [ \<messageLogging >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)</span><span class="sxs-lookup"><span data-stu-id="7fe14-114">[Configuring Message Logging](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) [\<messageLogging>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)</span></span>
