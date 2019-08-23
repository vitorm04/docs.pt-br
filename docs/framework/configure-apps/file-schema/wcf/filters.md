---
title: <filters>
ms.date: 03/30/2017
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
ms.openlocfilehash: e4ce0452cc46a8f29334fa67f51f14b83290b1c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918882"
---
# <a name="filters"></a><span data-ttu-id="8610b-101">\<Filtros ></span><span class="sxs-lookup"><span data-stu-id="8610b-101">\<filters></span></span>

<span data-ttu-id="8610b-102">O `filters` elemento contém uma coleção de filtros XPath usados para controlar que tipo de mensagem é registrada.</span><span class="sxs-lookup"><span data-stu-id="8610b-102">The `filters` element holds a collection of XPath filters used to control what kind of message is logged.</span></span>

<span data-ttu-id="8610b-103">Os filtros são aplicados somente na camada de transporte, especificada `logMessagesAtTransportLevel` por `true`is.</span><span class="sxs-lookup"><span data-stu-id="8610b-103">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="8610b-104">O nível de serviço e o log de mensagens malformados não são afetados por filtros.</span><span class="sxs-lookup"><span data-stu-id="8610b-104">Service level and malformed message logging are not affected by filters.</span></span>

<span data-ttu-id="8610b-105">Para adicionar um filtro à coleção, use a `add` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="8610b-105">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="8610b-106">Quando um ou mais filtros são definidos, somente as mensagens que correspondem a pelo menos um dos filtros são registradas.</span><span class="sxs-lookup"><span data-stu-id="8610b-106">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="8610b-107">Se nenhum filtro for definido, todas as mensagens passarão.</span><span class="sxs-lookup"><span data-stu-id="8610b-107">If no filter is defined, all messages pass through.</span></span>

<span data-ttu-id="8610b-108">Os filtros dão suporte à sintaxe XPath completa e são aplicados na ordem em que aparecem no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="8610b-108">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="8610b-109">Um filtro sintaticamente incorreto resulta em uma exceção de configuração.</span><span class="sxs-lookup"><span data-stu-id="8610b-109">A syntactically incorrect filter results in a configuration exception.</span></span>

<span data-ttu-id="8610b-110">Veja a seguir um exemplo de como configurar um filtro que registra somente as mensagens que têm uma seção de cabeçalho SOAP.</span><span class="sxs-lookup"><span data-stu-id="8610b-110">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="8610b-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8610b-111">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="8610b-112">Configurando registros de mensagens em log</span><span class="sxs-lookup"><span data-stu-id="8610b-112">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="8610b-113">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="8610b-113">\<messageLogging></span></span>](messagelogging.md)
