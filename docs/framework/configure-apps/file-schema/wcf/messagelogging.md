---
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: 70fb2df1d37af23d9ec19932806989ce3329bf3c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191562"
---
# <a name="messagelogging"></a><span data-ttu-id="d2da0-101">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="d2da0-101">\<messageLogging></span></span>
<span data-ttu-id="d2da0-102">Este elemento define as configurações para os recursos de log de mensagens do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d2da0-102">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="d2da0-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d2da0-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d2da0-104">\<diagnóstico ></span><span class="sxs-lookup"><span data-stu-id="d2da0-104">\<diagnostic></span></span>  
<span data-ttu-id="d2da0-105">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="d2da0-105">\<messageLogging></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2da0-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2da0-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2da0-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d2da0-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d2da0-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d2da0-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2da0-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="d2da0-109">Attributes</span></span>  
  
|<span data-ttu-id="d2da0-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="d2da0-110">Attribute</span></span>|<span data-ttu-id="d2da0-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2da0-111">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="d2da0-112">Um valor booliano que especifica se a mensagem inteira (cabeçalho de mensagem e corpo) é registrada.</span><span class="sxs-lookup"><span data-stu-id="d2da0-112">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="d2da0-113">O padrão é `false`, que significa que somente o cabeçalho da mensagem é registrada.</span><span class="sxs-lookup"><span data-stu-id="d2da0-113">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="d2da0-114">Essa configuração afeta todos os níveis de registro em log de mensagem (serviço, transporte, malformados).</span><span class="sxs-lookup"><span data-stu-id="d2da0-114">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="d2da0-115">Um valor booliano que especifica se mensagens malformadas são registradas.</span><span class="sxs-lookup"><span data-stu-id="d2da0-115">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="d2da0-116">Mensagens malformadas não contam para o `maxMessagesToLog`.</span><span class="sxs-lookup"><span data-stu-id="d2da0-116">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="d2da0-117">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="d2da0-117">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="d2da0-118">Um valor booliano que especifica se as mensagens são rastreadas no nível de serviço (antes de transformações relacionadas a criptografia e transporte).</span><span class="sxs-lookup"><span data-stu-id="d2da0-118">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="d2da0-119">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="d2da0-119">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="d2da0-120">Um valor booliano que especifica se as mensagens são rastreadas no nível do transporte.</span><span class="sxs-lookup"><span data-stu-id="d2da0-120">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="d2da0-121">Todos os filtros especificados no arquivo de configuração são aplicados, e apenas as mensagens que correspondem aos filtros são rastreadas.</span><span class="sxs-lookup"><span data-stu-id="d2da0-121">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="d2da0-122">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="d2da0-122">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="d2da0-123">Um inteiro positivo que especifica o número máximo de mensagens para fazer logon.</span><span class="sxs-lookup"><span data-stu-id="d2da0-123">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="d2da0-124">O padrão é 1000.</span><span class="sxs-lookup"><span data-stu-id="d2da0-124">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="d2da0-125">Um inteiro positivo que especifica o tamanho máximo, em bytes, de uma mensagem para fazer logon.</span><span class="sxs-lookup"><span data-stu-id="d2da0-125">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="d2da0-126">Mensagens maiores do que o limite não serão registradas.</span><span class="sxs-lookup"><span data-stu-id="d2da0-126">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="d2da0-127">Essa configuração afeta todos os níveis de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="d2da0-127">This setting affects all trace levels.</span></span> <span data-ttu-id="d2da0-128">O padrão é 262144(0x4000).</span><span class="sxs-lookup"><span data-stu-id="d2da0-128">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2da0-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d2da0-129">Child Elements</span></span>  
  
|<span data-ttu-id="d2da0-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="d2da0-130">Element</span></span>|<span data-ttu-id="d2da0-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2da0-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d2da0-132">filtros</span><span class="sxs-lookup"><span data-stu-id="d2da0-132">filters</span></span>|<span data-ttu-id="d2da0-133">O `filters` elemento contém uma coleção de filtros de XPath.</span><span class="sxs-lookup"><span data-stu-id="d2da0-133">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="d2da0-134">Quando o log de mensagens de transporte está habilitado (`logMessagesAtTransportLevel` é `true`), somente as mensagens que correspondem os filtros serão registradas.</span><span class="sxs-lookup"><span data-stu-id="d2da0-134">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="d2da0-135">Filtros são aplicados apenas na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="d2da0-135">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="d2da0-136">Registro em log de mensagem malformada e nível de serviço não são afetadas por filtros.</span><span class="sxs-lookup"><span data-stu-id="d2da0-136">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="d2da0-137">O único atributo para este elemento `filter`, é um XpathFilter.</span><span class="sxs-lookup"><span data-stu-id="d2da0-137">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="d2da0-138">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d2da0-138">Parent Elements</span></span>  
  
|<span data-ttu-id="d2da0-139">Elemento</span><span class="sxs-lookup"><span data-stu-id="d2da0-139">Element</span></span>|<span data-ttu-id="d2da0-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2da0-140">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d2da0-141">diagnósticos</span><span class="sxs-lookup"><span data-stu-id="d2da0-141">diagnostics</span></span>|<span data-ttu-id="d2da0-142">Define as configurações do WCF para inspeção de tempo de execução e controle para o administrador.</span><span class="sxs-lookup"><span data-stu-id="d2da0-142">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2da0-143">Comentários</span><span class="sxs-lookup"><span data-stu-id="d2da0-143">Remarks</span></span>  
 <span data-ttu-id="d2da0-144">As mensagens são registradas em três diferentes níveis na pilha: serviço, transporte e malformado.</span><span class="sxs-lookup"><span data-stu-id="d2da0-144">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="d2da0-145">Cada nível pode ser ativado separadamente.</span><span class="sxs-lookup"><span data-stu-id="d2da0-145">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="d2da0-146">Filtros de XPath podem ser adicionados para registrar mensagens específicas nos níveis de serviço e de transporte.</span><span class="sxs-lookup"><span data-stu-id="d2da0-146">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="d2da0-147">Se nenhum filtro for definido, todas as mensagens são registradas.</span><span class="sxs-lookup"><span data-stu-id="d2da0-147">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="d2da0-148">Filtros são aplicados somente aos cabeçalhos da mensagem.</span><span class="sxs-lookup"><span data-stu-id="d2da0-148">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="d2da0-149">O corpo é ignorado.</span><span class="sxs-lookup"><span data-stu-id="d2da0-149">The body is ignored.</span></span> <span data-ttu-id="d2da0-150">WCF ignora o corpo da mensagem para melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="d2da0-150">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="d2da0-151">Se você quiser filtrar com base no conteúdo do corpo, você pode criar um ouvinte personalizado com um filtro que faz isso.</span><span class="sxs-lookup"><span data-stu-id="d2da0-151">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="d2da0-152">Você precisa criar um ouvinte de rastreamento para ativar o rastreamento de mensagem.</span><span class="sxs-lookup"><span data-stu-id="d2da0-152">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="d2da0-153">O ouvinte em si pode ser qualquer ouvinte que funciona com o <xref:System.Diagnostics> arquitetura de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="d2da0-153">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="d2da0-154">O exemplo a seguir demonstra como criar um ouvinte desse tipo.</span><span class="sxs-lookup"><span data-stu-id="d2da0-154">The following example demonstrates how to create such a listener.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="d2da0-155">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d2da0-155">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d2da0-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2da0-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [<span data-ttu-id="d2da0-157">Configurando registros de mensagens em log</span><span class="sxs-lookup"><span data-stu-id="d2da0-157">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
