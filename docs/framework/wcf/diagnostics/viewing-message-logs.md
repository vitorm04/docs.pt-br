---
title: Visualizando logs de mensagem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: df1d796ec5009008e00391eea2987f5256df6c48
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="viewing-message-logs"></a><span data-ttu-id="fa865-102">Visualizando logs de mensagem</span><span class="sxs-lookup"><span data-stu-id="fa865-102">Viewing Message Logs</span></span>
<span data-ttu-id="fa865-103">Este tópico descreve como você pode exibir os logs de mensagem.</span><span class="sxs-lookup"><span data-stu-id="fa865-103">This topic describes how you can view message logs.</span></span>  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a><span data-ttu-id="fa865-104">Exibindo a mensagem de Logs no Visualizador de rastreamento de serviço</span><span class="sxs-lookup"><span data-stu-id="fa865-104">Viewing Message Logs in the Service Trace Viewer</span></span>  
 <span data-ttu-id="fa865-105">Uma mensagem será transformada conforme ela é processada pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fa865-105">A message will be transformed as it is processed by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="fa865-106">Portanto, uma mensagem que está sendo registrada reflete somente a conteúdo da mensagem no ponto em que foi registrado, não o conteúdo na conexão.</span><span class="sxs-lookup"><span data-stu-id="fa865-106">Therefore, a message being logged reflects only the message's content at the point it was logged, not the content on the wire.</span></span>  
  
 <span data-ttu-id="fa865-107">Desde que a saída de log de mensagens não tem relação com o formato de transferência da mensagem, o log de mensagens sempre gera a mensagem decodificada.</span><span class="sxs-lookup"><span data-stu-id="fa865-107">Since the output of message logging has no relationship to the transfer format of the message, message logging always outputs the decoded message.</span></span> <span data-ttu-id="fa865-108">Se você tiver configurado adequadamente o log de mensagem, qualquer mensagem registrada deve ser em texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="fa865-108">If you have configured message logging properly, any logged message should be in plain text.</span></span> <span data-ttu-id="fa865-109">Por exemplo, o formato (texto sem formatação) das mensagens de log não é afetado pelo uso de um codificador de mensagem binária.</span><span class="sxs-lookup"><span data-stu-id="fa865-109">For example, the format (plain text) of the logged messages is not affected by the usage of a binary message encoder.</span></span>  
  
 <span data-ttu-id="fa865-110">A saída de XmlWriterTraceListener é um arquivo que contém uma sequência de fragmentos XML.</span><span class="sxs-lookup"><span data-stu-id="fa865-110">The output of the XmlWriterTraceListener is a file that contains a sequence of XML fragments.</span></span> <span data-ttu-id="fa865-111">Você deve estar ciente de que o arquivo não é um arquivo XML válido.</span><span class="sxs-lookup"><span data-stu-id="fa865-111">You should be aware that the file is not a valid XML file.</span></span> <span data-ttu-id="fa865-112">É recomendável que você use o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) para exibir os arquivos de log de mensagem.</span><span class="sxs-lookup"><span data-stu-id="fa865-112">It is recommended that you use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) to view the message log files.</span></span> <span data-ttu-id="fa865-113">Para obter mais informações sobre como usar essa ferramenta, consulte [usando o Visualizador de rastreamento de serviço para exibir rastreamentos correlacionados e solução de problemas](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="fa865-113">For more information on how to use this tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="fa865-114">No Visualizador de rastreamento de serviço, as mensagens são listadas no **mensagem** guia. Mensagens que causaram ou que estão relacionadas a, um erro de processamento são realçados em amarelo (nível de aviso) ou vermelho (nível de erro), dependendo da gravidade do erro.</span><span class="sxs-lookup"><span data-stu-id="fa865-114">In the Service Trace Viewer, messages are listed in the **Message** tab. Messages that have caused, or are related to, a processing error are highlighted in yellow (warning level) or red (error level), depending on the severity of the error.</span></span> <span data-ttu-id="fa865-115">Clicando duas vezes na mensagem exibe o rastreamento de mensagens no contexto da solicitação de processamento.</span><span class="sxs-lookup"><span data-stu-id="fa865-115">Double-clicking on the message brings up the message trace in the context of the processing request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa865-116">Se uma mensagem não tem nenhum cabeçalho não `<header/>` marca é registrada.</span><span class="sxs-lookup"><span data-stu-id="fa865-116">If a message has no header, no `<header/>` tag is logged.</span></span>  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a><span data-ttu-id="fa865-117">Exibindo mensagens registradas por um cliente, uma retransmissão e um serviço</span><span class="sxs-lookup"><span data-stu-id="fa865-117">Viewing Messages Logged by a Client, a Relay, and a Service</span></span>  
 <span data-ttu-id="fa865-118">Seu ambiente pode conter um cliente, que envia uma mensagem para uma retransmissão, que posteriormente encaminha a mensagem para o serviço.</span><span class="sxs-lookup"><span data-stu-id="fa865-118">Your environment may contain a client, which sends a message to a relay, that subsequently forwards the message to the service.</span></span> <span data-ttu-id="fa865-119">Quando o log de mensagens está habilitado em todos os três locais e todos os três logs de mensagem são exibidos no [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) simultaneamente, as trocas de mensagens do log serão renderizadas corretamente.</span><span class="sxs-lookup"><span data-stu-id="fa865-119">When message logging is enabled on all three locations, and all three message logs are viewed in [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) simultaneously, the message log exchanges will be incorrectly rendered.</span></span> <span data-ttu-id="fa865-120">Isso ocorre porque o `CorrelationId` e `ActivityId` no cabeçalho da mensagem não são exclusivos para cada par de send-receive.</span><span class="sxs-lookup"><span data-stu-id="fa865-120">This is because the `CorrelationId` and `ActivityId` in the Message header are not unique for every send-receive pair.</span></span>  
  
 <span data-ttu-id="fa865-121">Você pode usar um dos seguintes métodos para resolver esse problema.</span><span class="sxs-lookup"><span data-stu-id="fa865-121">You can use either one of the following methods to resolve this problem.</span></span>  
  
-   <span data-ttu-id="fa865-122">Exibir apenas dois dos três logs de mensagem no [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="fa865-122">Only view two of the three message logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) at any time.</span></span>  
  
-   <span data-ttu-id="fa865-123">Se você deve exibir todos os três logs no [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ao mesmo tempo, você pode modificar o serviço de retransmissão, criando um novo <xref:System.ServiceModel.Channels.Message> instância.</span><span class="sxs-lookup"><span data-stu-id="fa865-123">If you must view all three logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) at the same time, you can modify the relay service by creating a new <xref:System.ServiceModel.Channels.Message> instance.</span></span> <span data-ttu-id="fa865-124">Esta instância deve ser uma cópia do corpo da mensagem de entrada, além de todos os cabeçalhos, exceto para o `ActivityId` e `Action` cabeçalhos.</span><span class="sxs-lookup"><span data-stu-id="fa865-124">This instance should be a copy of the body of the incoming message, plus all the headers except for the `ActivityId` and `Action` headers.</span></span> <span data-ttu-id="fa865-125">O exemplo de código a seguir demonstra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="fa865-125">The following example code demonstrates how to do this.</span></span>  
  
```  
Message outgoingMessage = Message.CreateMessage(incomingMessage.Version, incomingMessage.Headers.Action, incomingMessage.GetReaderAtBodyContents());  
  
for (int i = 0; i < incomingMessage.Headers.Count; i++)  
{  
   if (incomingMessage.Headers[i].Name.Equals("ActivityId", StringComparison.InvariantCultureIgnoreCase) ||  
incomingMessage.Headers[i].Name.Equals("Action", StringComparison.InvariantCultureIgnoreCase))  
   {  
      continue;  
    }  
    outgoingMessage.Headers.CopyHeaderFrom(incomingMessage, i);  
}  
```  
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a><span data-ttu-id="fa865-126">Casos excepcionais para conteúdo da mensagem precisas de registro em log</span><span class="sxs-lookup"><span data-stu-id="fa865-126">Exceptional Cases for Inaccurate Message Logging Content</span></span>  
 <span data-ttu-id="fa865-127">Sob as seguintes condições, sendo registradas em log de mensagens podem não ser a representação exata do fluxo de octeto presente na conexão.</span><span class="sxs-lookup"><span data-stu-id="fa865-127">Under the following conditions, messages being logged might not be the exact representation of the octet stream present on the wire.</span></span>  
  
-   <span data-ttu-id="fa865-128">Para BasicHttpBinding, cabeçalhos de envelope são registrados para mensagens de entrada no endereçamento/nenhum namespace.</span><span class="sxs-lookup"><span data-stu-id="fa865-128">For BasicHttpBinding, envelope headers are logged for the incoming messages in the /addressing/none namespace.</span></span>  
  
-   <span data-ttu-id="fa865-129">Espaços em branco podem ser incompatível.</span><span class="sxs-lookup"><span data-stu-id="fa865-129">Whitespaces can be mismatched.</span></span>  
  
-   <span data-ttu-id="fa865-130">Para mensagens de entrada, elementos vazios podem ser representados de maneira diferente.</span><span class="sxs-lookup"><span data-stu-id="fa865-130">For incoming messages, empty elements can be represented differently.</span></span> <span data-ttu-id="fa865-131">Por exemplo, \<marca >\</tag > em vez de \<marca / ></span><span class="sxs-lookup"><span data-stu-id="fa865-131">For example, \<tag>\</tag> instead of  \<tag/></span></span>  
  
-   <span data-ttu-id="fa865-132">Quando o log de PII conhecido está desabilitado por padrão ou a configuração explícita enableLoggingKnownPii = "true".</span><span class="sxs-lookup"><span data-stu-id="fa865-132">When known PII logging is disabled either by default or explicit setting enableLoggingKnownPii="true".</span></span>  
  
-   <span data-ttu-id="fa865-133">Codificação está habilitada para transformação em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="fa865-133">Encoding is enabled for transforming to UTF-8.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa865-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa865-134">See Also</span></span>  
 <span data-ttu-id="fa865-135">[Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) (Ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer.exe))</span><span class="sxs-lookup"><span data-stu-id="fa865-135">[Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)</span></span>  
 [<span data-ttu-id="fa865-136">Usando o Visualizador de Rastreamento de Serviço para exibir rastreamentos correlacionados e solucionar problemas</span><span class="sxs-lookup"><span data-stu-id="fa865-136">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="fa865-137">Log de mensagens</span><span class="sxs-lookup"><span data-stu-id="fa865-137">Message Logging</span></span>](../../../../docs/framework/wcf/diagnostics/message-logging.md)
