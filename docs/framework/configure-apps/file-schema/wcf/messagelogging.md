---
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: 9291c38af28c18d20e23e34e8316b4a9fe523123
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855126"
---
# \<messageLogging>
<span data-ttu-id="2a86d-101">Esse elemento define as configurações para os recursos de log de mensagens do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2a86d-101">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageLogging>**  
  
## <a name="syntax"></a><span data-ttu-id="2a86d-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a86d-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
      <filters>
        <clear />
      </filters>
    </messageLogging>
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a86d-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2a86d-103">Attributes and Elements</span></span>  
 <span data-ttu-id="2a86d-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2a86d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a86d-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="2a86d-105">Attributes</span></span>  
  
|<span data-ttu-id="2a86d-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="2a86d-106">Attribute</span></span>|<span data-ttu-id="2a86d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a86d-107">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="2a86d-108">Um valor booliano que especifica se a mensagem inteira (cabeçalho e corpo da mensagem) é registrada.</span><span class="sxs-lookup"><span data-stu-id="2a86d-108">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="2a86d-109">O padrão é `false` , o que significa que apenas o cabeçalho da mensagem é registrado.</span><span class="sxs-lookup"><span data-stu-id="2a86d-109">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="2a86d-110">Essa configuração afeta todos os níveis de log de mensagens (serviço, transporte e malformados).</span><span class="sxs-lookup"><span data-stu-id="2a86d-110">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="2a86d-111">Um valor booliano que especifica se as mensagens malformadas são registradas.</span><span class="sxs-lookup"><span data-stu-id="2a86d-111">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="2a86d-112">As mensagens malformadas não contam para o `maxMessagesToLog` .</span><span class="sxs-lookup"><span data-stu-id="2a86d-112">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="2a86d-113">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="2a86d-113">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="2a86d-114">Um valor booliano que especifica se as mensagens são rastreadas no nível de serviço (antes das transformações relacionadas à criptografia e ao transporte).</span><span class="sxs-lookup"><span data-stu-id="2a86d-114">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="2a86d-115">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="2a86d-115">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="2a86d-116">Um valor booliano que especifica se as mensagens são rastreadas no nível de transporte.</span><span class="sxs-lookup"><span data-stu-id="2a86d-116">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="2a86d-117">Todos os filtros especificados no arquivo de configuração são aplicados e somente as mensagens que correspondem aos filtros são rastreadas.</span><span class="sxs-lookup"><span data-stu-id="2a86d-117">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="2a86d-118">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="2a86d-118">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="2a86d-119">Um inteiro positivo que especifica o número máximo de mensagens a serem registradas.</span><span class="sxs-lookup"><span data-stu-id="2a86d-119">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="2a86d-120">O padrão é 1000.</span><span class="sxs-lookup"><span data-stu-id="2a86d-120">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="2a86d-121">Um inteiro positivo que especifica o tamanho máximo, em bytes, de uma mensagem a ser registrada.</span><span class="sxs-lookup"><span data-stu-id="2a86d-121">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="2a86d-122">Mensagens maiores que o limite não serão registradas em log.</span><span class="sxs-lookup"><span data-stu-id="2a86d-122">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="2a86d-123">Essa configuração afeta todos os níveis de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="2a86d-123">This setting affects all trace levels.</span></span> <span data-ttu-id="2a86d-124">O padrão é 262144 (0x4000).</span><span class="sxs-lookup"><span data-stu-id="2a86d-124">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a86d-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2a86d-125">Child Elements</span></span>  
  
|<span data-ttu-id="2a86d-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="2a86d-126">Element</span></span>|<span data-ttu-id="2a86d-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a86d-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2a86d-128">filtros</span><span class="sxs-lookup"><span data-stu-id="2a86d-128">filters</span></span>|<span data-ttu-id="2a86d-129">O `filters` elemento contém uma coleção de filtros XPath.</span><span class="sxs-lookup"><span data-stu-id="2a86d-129">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="2a86d-130">Quando o log de mensagens de transporte estiver habilitado ( `logMessagesAtTransportLevel` is `true` ), somente as mensagens correspondentes aos filtros serão registradas em log.</span><span class="sxs-lookup"><span data-stu-id="2a86d-130">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="2a86d-131">Os filtros são aplicados somente na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="2a86d-131">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="2a86d-132">O nível de serviço e o log de mensagens malformados não são afetados por filtros.</span><span class="sxs-lookup"><span data-stu-id="2a86d-132">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="2a86d-133">O único atributo para esse elemento, `filter` , é um XpathFilter.</span><span class="sxs-lookup"><span data-stu-id="2a86d-133">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="2a86d-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2a86d-134">Parent Elements</span></span>  
  
|<span data-ttu-id="2a86d-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="2a86d-135">Element</span></span>|<span data-ttu-id="2a86d-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a86d-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2a86d-137">diagnóstico</span><span class="sxs-lookup"><span data-stu-id="2a86d-137">diagnostics</span></span>|<span data-ttu-id="2a86d-138">Define as configurações do WCF para inspeção e controle de tempo de execução para o administrador.</span><span class="sxs-lookup"><span data-stu-id="2a86d-138">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a86d-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a86d-139">Remarks</span></span>  
 <span data-ttu-id="2a86d-140">As mensagens são registradas em três níveis diferentes na pilha: serviço, transporte e malformados.</span><span class="sxs-lookup"><span data-stu-id="2a86d-140">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="2a86d-141">Cada nível pode ser ativado separadamente.</span><span class="sxs-lookup"><span data-stu-id="2a86d-141">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="2a86d-142">Os filtros XPath podem ser adicionados para registrar mensagens específicas de log nos níveis de transporte e de serviço.</span><span class="sxs-lookup"><span data-stu-id="2a86d-142">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="2a86d-143">Se nenhum filtro for definido, todas as mensagens serão registradas.</span><span class="sxs-lookup"><span data-stu-id="2a86d-143">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="2a86d-144">Os filtros são aplicados somente aos cabeçalhos da mensagem.</span><span class="sxs-lookup"><span data-stu-id="2a86d-144">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="2a86d-145">O corpo é ignorado.</span><span class="sxs-lookup"><span data-stu-id="2a86d-145">The body is ignored.</span></span> <span data-ttu-id="2a86d-146">O WCF ignora o corpo da mensagem para melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="2a86d-146">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="2a86d-147">Se você quiser filtrar com base no conteúdo do corpo, poderá criar um ouvinte personalizado com um filtro que faça isso.</span><span class="sxs-lookup"><span data-stu-id="2a86d-147">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="2a86d-148">Você precisa criar um ouvinte de rastreamento para ativar o rastreamento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="2a86d-148">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="2a86d-149">O ouvinte em si pode ser qualquer ouvinte que funcione com a <xref:System.Diagnostics> arquitetura de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="2a86d-149">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="2a86d-150">O exemplo a seguir demonstra como criar um ouvinte desse tipo.</span><span class="sxs-lookup"><span data-stu-id="2a86d-150">The following example demonstrates how to create such a listener.</span></span>  
  
```xml  
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel"
            switchValue="Verbose">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="ServiceModel Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
    <source name="System.ServiceModel.MessageLogging">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="MessageLogging Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
  </sources>
  <sharedListeners>
    <add initializeData="C:\ItProTools\TraceLog.xml"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="ServiceModel Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
    <add initializeData="C:\ItProTools\MessageLog.log"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="MessageLogging Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
  </sharedListeners>
</system.diagnostics>
```  
  
## <a name="example"></a><span data-ttu-id="2a86d-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a86d-151">Example</span></span>  
  
```xml  
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="42"
                maxSizeOfMessageToLog="42">
  <filters>
    <clear />
  </filters>
</messageLogging>
```  
  
## <a name="see-also"></a><span data-ttu-id="2a86d-152">Confira também</span><span class="sxs-lookup"><span data-stu-id="2a86d-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [<span data-ttu-id="2a86d-153">Configurando registros de mensagens em log</span><span class="sxs-lookup"><span data-stu-id="2a86d-153">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
