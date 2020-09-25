---
title: <add> de <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: c1de0605bc8afc502a85d9b2917b975ee45a3d26
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201649"
---
# <a name="add-of-filters"></a><span data-ttu-id="cb39b-102">\<add> de \<filters></span><span class="sxs-lookup"><span data-stu-id="cb39b-102">\<add> of \<filters></span></span>

<span data-ttu-id="cb39b-103">Um filtro XPath que especifica o tipo de mensagem a ser registrada.</span><span class="sxs-lookup"><span data-stu-id="cb39b-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<messageLogging>**](messagelogging.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="cb39b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb39b-104">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb39b-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cb39b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="cb39b-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cb39b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb39b-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="cb39b-107">Attributes</span></span>  
  
|<span data-ttu-id="cb39b-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="cb39b-108">Attribute</span></span>|<span data-ttu-id="cb39b-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb39b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cb39b-110">filtro</span><span class="sxs-lookup"><span data-stu-id="cb39b-110">filter</span></span>|<span data-ttu-id="cb39b-111">Uma cadeia de caracteres que especifica uma consulta em um documento XML definido por uma expressão XPath 1,0.</span><span class="sxs-lookup"><span data-stu-id="cb39b-111">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="cb39b-112">Para obter mais informações, consulte <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="cb39b-112">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb39b-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cb39b-113">Child Elements</span></span>  

 <span data-ttu-id="cb39b-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="cb39b-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb39b-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cb39b-115">Parent Elements</span></span>  
  
|<span data-ttu-id="cb39b-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="cb39b-116">Element</span></span>|<span data-ttu-id="cb39b-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb39b-117">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters.md)|<span data-ttu-id="cb39b-118">Contém uma coleção de filtros XPath usados para controlar que tipo de mensagem é registrada.</span><span class="sxs-lookup"><span data-stu-id="cb39b-118">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb39b-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="cb39b-119">Remarks</span></span>  

 <span data-ttu-id="cb39b-120">Os filtros são aplicados somente na camada de transporte, especificada por `logMessagesAtTransportLevel` is `true` .</span><span class="sxs-lookup"><span data-stu-id="cb39b-120">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="cb39b-121">O nível de serviço e o log de mensagens malformados não são afetados por filtros.</span><span class="sxs-lookup"><span data-stu-id="cb39b-121">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="cb39b-122">Para adicionar um filtro à coleção, use a `add` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="cb39b-122">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="cb39b-123">Quando um ou mais filtros são definidos, somente as mensagens que correspondem a pelo menos um dos filtros são registradas.</span><span class="sxs-lookup"><span data-stu-id="cb39b-123">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="cb39b-124">Se nenhum filtro for definido, todas as mensagens passarão.</span><span class="sxs-lookup"><span data-stu-id="cb39b-124">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="cb39b-125">Os filtros dão suporte à sintaxe XPath completa e são aplicados na ordem em que aparecem no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="cb39b-125">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="cb39b-126">Um filtro sintaticamente incorreto resulta em uma exceção de configuração.</span><span class="sxs-lookup"><span data-stu-id="cb39b-126">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="cb39b-127">Veja a seguir um exemplo de como configurar um filtro que registra somente as mensagens que têm uma seção de cabeçalho SOAP.</span><span class="sxs-lookup"><span data-stu-id="cb39b-127">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb39b-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cb39b-128">Example</span></span>  

 <span data-ttu-id="cb39b-129">Veja a seguir um exemplo de como configurar um filtro que registra somente as mensagens que têm uma seção de cabeçalho SOAP.</span><span class="sxs-lookup"><span data-stu-id="cb39b-129">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cb39b-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="cb39b-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="cb39b-131">Configurando registros de mensagens em log</span><span class="sxs-lookup"><span data-stu-id="cb39b-131">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging>](messagelogging.md)
