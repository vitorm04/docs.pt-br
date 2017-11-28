---
title: '&lt;messageLogging&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e5b232e3faf1e0e8976b0c08264c8ba03988902a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmessagelogginggt"></a><span data-ttu-id="f8980-102">&lt;messageLogging&gt;</span><span class="sxs-lookup"><span data-stu-id="f8980-102">&lt;messageLogging&gt;</span></span>
<span data-ttu-id="f8980-103">Este elemento define as configurações para os recursos de log de mensagens do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f8980-103">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="f8980-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f8980-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f8980-105">\<diagnóstico ></span><span class="sxs-lookup"><span data-stu-id="f8980-105">\<diagnostic></span></span>  
<span data-ttu-id="f8980-106">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="f8980-106">\<messageLogging></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8980-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f8980-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <messageLogging logEntireMessage="Boolean"  
          logMalformedMessages="Boolean"  
          logMessagesAtServiceLevel="Boolean"  
          logMessagesAtTransportLevel="Boolean"  
                    maxMessagesToLog="Integer"  
          maxSizeOfMessageToLog="Integer" >  
          <filters>  
                            <clear />  
          </filters>  
       </messageLogging>  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8980-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f8980-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f8980-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f8980-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8980-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="f8980-110">Attributes</span></span>  
  
|<span data-ttu-id="f8980-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="f8980-111">Attribute</span></span>|<span data-ttu-id="f8980-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8980-112">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="f8980-113">Um valor booleano que especifica se a mensagem inteira (cabeçalho e corpo) é registrada.</span><span class="sxs-lookup"><span data-stu-id="f8980-113">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="f8980-114">O padrão é `false`, que significa que somente o cabeçalho da mensagem é registrada.</span><span class="sxs-lookup"><span data-stu-id="f8980-114">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="f8980-115">Essa configuração afeta todos os níveis de log de mensagem (serviço, transporte e malformado).</span><span class="sxs-lookup"><span data-stu-id="f8980-115">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="f8980-116">Um valor booleano que especifica se as mensagens malformadas são registradas.</span><span class="sxs-lookup"><span data-stu-id="f8980-116">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="f8980-117">As mensagens malformadas não contam para o `maxMessagesToLog`.</span><span class="sxs-lookup"><span data-stu-id="f8980-117">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="f8980-118">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="f8980-118">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="f8980-119">Um valor booleano que especifica se as mensagens são rastreadas no nível de serviço (antes de transformações relacionadas a criptografia e transporte).</span><span class="sxs-lookup"><span data-stu-id="f8980-119">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="f8980-120">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="f8980-120">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="f8980-121">Um valor booleano que especifica se as mensagens são rastreadas no nível do transporte.</span><span class="sxs-lookup"><span data-stu-id="f8980-121">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="f8980-122">Todos os filtros especificados no arquivo de configuração são aplicados e somente as mensagens que correspondem aos filtros são rastreadas.</span><span class="sxs-lookup"><span data-stu-id="f8980-122">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="f8980-123">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="f8980-123">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="f8980-124">Um inteiro positivo que especifica o número máximo de mensagens a serem registradas.</span><span class="sxs-lookup"><span data-stu-id="f8980-124">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="f8980-125">O padrão é 1000.</span><span class="sxs-lookup"><span data-stu-id="f8980-125">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="f8980-126">Um inteiro positivo que especifica o tamanho máximo, em bytes, de uma mensagem para log.</span><span class="sxs-lookup"><span data-stu-id="f8980-126">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="f8980-127">Maiores que o limite de mensagens não serão registradas.</span><span class="sxs-lookup"><span data-stu-id="f8980-127">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="f8980-128">Essa configuração afeta todos os níveis de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f8980-128">This setting affects all trace levels.</span></span> <span data-ttu-id="f8980-129">O padrão é 262144(0x4000).</span><span class="sxs-lookup"><span data-stu-id="f8980-129">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f8980-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f8980-130">Child Elements</span></span>  
  
|<span data-ttu-id="f8980-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="f8980-131">Element</span></span>|<span data-ttu-id="f8980-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8980-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f8980-133">filtros</span><span class="sxs-lookup"><span data-stu-id="f8980-133">filters</span></span>|<span data-ttu-id="f8980-134">O `filters` elemento contém uma coleção de filtros de XPath.</span><span class="sxs-lookup"><span data-stu-id="f8980-134">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="f8980-135">Quando o log de mensagens de transporte está habilitado (`logMessagesAtTransportLevel` é `true`), somente as mensagens que correspondem os filtros serão registradas.</span><span class="sxs-lookup"><span data-stu-id="f8980-135">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="f8980-136">Os filtros são aplicados apenas na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="f8980-136">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="f8980-137">Log de mensagem malformada e nível de serviço não são afetadas por filtros.</span><span class="sxs-lookup"><span data-stu-id="f8980-137">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="f8980-138">O atributo somente para esse elemento, `filter`, é um XpathFilter.</span><span class="sxs-lookup"><span data-stu-id="f8980-138">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="f8980-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f8980-139">Parent Elements</span></span>  
  
|<span data-ttu-id="f8980-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="f8980-140">Element</span></span>|<span data-ttu-id="f8980-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8980-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f8980-142">diagnósticos</span><span class="sxs-lookup"><span data-stu-id="f8980-142">diagnostics</span></span>|<span data-ttu-id="f8980-143">Define as configurações de WCF para inspeção de tempo de execução e o controle para o administrador.</span><span class="sxs-lookup"><span data-stu-id="f8980-143">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8980-144">Comentários</span><span class="sxs-lookup"><span data-stu-id="f8980-144">Remarks</span></span>  
 <span data-ttu-id="f8980-145">As mensagens são registradas em três diferentes níveis da pilha: serviço, transporte e malformado.</span><span class="sxs-lookup"><span data-stu-id="f8980-145">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="f8980-146">Cada nível pode ser ativado separadamente.</span><span class="sxs-lookup"><span data-stu-id="f8980-146">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="f8980-147">Filtros de XPath podem ser adicionados para registrar mensagens específicas nos níveis de serviço e transporte.</span><span class="sxs-lookup"><span data-stu-id="f8980-147">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="f8980-148">Se nenhum filtro é definido, todas as mensagens são registradas.</span><span class="sxs-lookup"><span data-stu-id="f8980-148">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="f8980-149">Filtros são aplicados somente aos cabeçalhos da mensagem.</span><span class="sxs-lookup"><span data-stu-id="f8980-149">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="f8980-150">O corpo é ignorado.</span><span class="sxs-lookup"><span data-stu-id="f8980-150">The body is ignored.</span></span> <span data-ttu-id="f8980-151">WCF ignora o corpo da mensagem para melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="f8980-151">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="f8980-152">Se você deseja filtrar com base no conteúdo do corpo, você pode criar um ouvinte personalizado com um filtro que faz isso.</span><span class="sxs-lookup"><span data-stu-id="f8980-152">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="f8980-153">Você precisa criar um ouvinte de rastreamento para ativar o rastreamento de mensagem.</span><span class="sxs-lookup"><span data-stu-id="f8980-153">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="f8980-154">O ouvinte em si pode ser qualquer ouvinte que funciona com o <xref:System.Diagnostics> arquitetura de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f8980-154">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="f8980-155">O exemplo a seguir demonstra como criar um ouvinte tal.</span><span class="sxs-lookup"><span data-stu-id="f8980-155">The following example demonstrates how to create such a listener.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
          <source name="System.ServiceModel" switchValue="Verbose">  
              <listeners>  
                    <clear />  
                    <add type="System.Diagnostics.DefaultTraceListener" name="Default"  
                        traceOutputOptions="None" />  
                    <add name="ServiceModel Listener" traceOutputOptions="None" />  
               </listeners>  
        </source>  
            <source name="System.ServiceModel.MessageLogging">  
                <listeners>  
                    <clear />  
                    <add type="System.Diagnostics.DefaultTraceListener" name="Default"  
                        traceOutputOptions="None" />  
                    <add name="MessageLogging Listener" traceOutputOptions="None"/>  
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
  
## <a name="example"></a><span data-ttu-id="f8980-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f8980-156">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f8980-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8980-157">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>  
 [<span data-ttu-id="f8980-158">Configurando o log de mensagem</span><span class="sxs-lookup"><span data-stu-id="f8980-158">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
