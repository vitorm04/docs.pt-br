---
title: Visualizando logs de mensagem
ms.date: 03/30/2017
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
ms.openlocfilehash: 4fa205b52e3d19d2421d93297b5689422775f719
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33802971"
---
# <a name="viewing-message-logs"></a>Visualizando logs de mensagem
Este tópico descreve como você pode exibir os logs de mensagem.  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a>Exibindo a mensagem de Logs no Visualizador de rastreamento de serviço  
 Uma mensagem será transformada conforme ela é processada pelo WCF. Portanto, uma mensagem que está sendo registrada reflete somente a conteúdo da mensagem no ponto em que foi registrado, não o conteúdo na conexão.  
  
 Desde que a saída de log de mensagens não tem relação com o formato de transferência da mensagem, o log de mensagens sempre gera a mensagem decodificada. Se você tiver configurado adequadamente o log de mensagem, qualquer mensagem registrada deve ser em texto sem formatação. Por exemplo, o formato (texto sem formatação) das mensagens de log não é afetado pelo uso de um codificador de mensagem binária.  
  
 A saída de XmlWriterTraceListener é um arquivo que contém uma sequência de fragmentos XML. Você deve estar ciente de que o arquivo não é um arquivo XML válido. É recomendável que você use o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) para exibir os arquivos de log de mensagem. Para obter mais informações sobre como usar essa ferramenta, consulte [usando o Visualizador de rastreamento de serviço para exibir rastreamentos correlacionados e solução de problemas](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 No Visualizador de rastreamento de serviço, as mensagens são listadas no **mensagem** guia. Mensagens que causaram ou que estão relacionadas a, um erro de processamento são realçados em amarelo (nível de aviso) ou vermelho (nível de erro), dependendo da gravidade do erro. Clicando duas vezes na mensagem exibe o rastreamento de mensagens no contexto da solicitação de processamento.  
  
> [!NOTE]
>  Se uma mensagem não tem nenhum cabeçalho não `<header/>` marca é registrada.  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a>Exibindo mensagens registradas por um cliente, uma retransmissão e um serviço  
 Seu ambiente pode conter um cliente, que envia uma mensagem para uma retransmissão, que posteriormente encaminha a mensagem para o serviço. Quando o log de mensagens está habilitado em todos os três locais e todos os três logs de mensagem são exibidos no [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) simultaneamente, as trocas de mensagens do log serão renderizadas corretamente. Isso ocorre porque o `CorrelationId` e `ActivityId` no cabeçalho da mensagem não são exclusivos para cada par de send-receive.  
  
 Você pode usar um dos seguintes métodos para resolver esse problema.  
  
-   Exibir apenas dois dos três logs de mensagem no [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) a qualquer momento.  
  
-   Se você deve exibir todos os três logs no [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ao mesmo tempo, você pode modificar o serviço de retransmissão, criando um novo <xref:System.ServiceModel.Channels.Message> instância. Esta instância deve ser uma cópia do corpo da mensagem de entrada, além de todos os cabeçalhos, exceto para o `ActivityId` e `Action` cabeçalhos. O exemplo de código a seguir demonstra como fazer isso.  
  
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
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a>Casos excepcionais para conteúdo da mensagem precisas de registro em log  
 Sob as seguintes condições, sendo registradas em log de mensagens podem não ser a representação exata do fluxo de octeto presente na conexão.  
  
-   Para BasicHttpBinding, cabeçalhos de envelope são registrados para mensagens de entrada no endereçamento/nenhum namespace.  
  
-   Espaços em branco podem ser incompatível.  
  
-   Para mensagens de entrada, elementos vazios podem ser representados de maneira diferente. Por exemplo, \<marca >\</tag > em vez de \<marca / >  
  
-   Quando o log de PII conhecido está desabilitado por padrão ou a configuração explícita enableLoggingKnownPii = "true".  
  
-   Codificação está habilitada para transformação em UTF-8.  
  
## <a name="see-also"></a>Consulte também  
 [Ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [Usando o Visualizador de Rastreamento de Serviço para exibir rastreamentos correlacionados e solucionar problemas](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Registro de mensagens em log](../../../../docs/framework/wcf/diagnostics/message-logging.md)
