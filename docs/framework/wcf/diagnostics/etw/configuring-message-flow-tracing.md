---
title: Configurando rastreamento de fluxo de mensagem
ms.date: 03/30/2017
ms.assetid: 15571ca2-bee2-47fb-ba10-fcbc09152ad0
ms.openlocfilehash: 02c43b152cb1aef1684185e56eb7f172036ac46b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61999512"
---
# <a name="configuring-message-flow-tracing"></a>Configurando rastreamento de fluxo de mensagem
Quando o rastreamento de atividades do Windows Communication Foundation (WCF) é habilitado, as IDs de atividade de ponta a ponta são atribuídas a lógicas atividades em toda a pilha do WCF. No [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)], agora há uma versão posterior do desempenho desse recurso que funciona com o ETW rastreamento de eventos para Windows () chamado de rastreamento de fluxo de mensagem. Quando habilitado, IDs de atividade de ponta a ponta são tiradas (ou atribuídas a, se estiver vazia) mensagens de entrada e são propagadas para todos os eventos de rastreamento que são emitidos depois que a mensagem tiver sido decodificada pelo canal. Os clientes podem usar esse recurso para reconstruir os fluxos de mensagens com os logs de rastreamento de serviços diferentes após a decodificação.  
  
 O rastreamento pode ser habilitado depois que for detectado um problema com o aplicativo e, em seguida, desabilitado depois que o problema seja resolvido.  
  
## <a name="enabling-tracing"></a>A habilitação do rastreamento  
 Você pode habilitar o rastreamento de fluxo de mensagens, definindo o .NET Framework 4 `messageFlowTracing` elemento de configuração para `true`, conforme mostrado no exemplo a seguir.  
  
```xml  
<system.servicemodel>  
  <diagnostics>  
    <endToEndTracing propagateActivity="true" messageFlowTracing="true" />  
  </diagnostics>  
</system.servicemodel>  
```  
  
> [!NOTE]
>  Porque o `endToEndTracing` elemento de configuração reside em um arquivo Web. config, não pode ser configurado dinamicamente da mesma maneira como o ETW. Para o `endToEndTracing` elemento de configuração entrem em vigor, o aplicativo deve ser reciclado.  
  
 As atividades estão correlacionadas por intercâmbio de um identificador chamado de ID de atividade. Esse identificador é um GUID e é gerado pela classe System.Diagnostics.CorrelationManager. Se você manipular System.Diagnostics.Trace.CorrelationManager.ActivityID, certifique-se de que o valor é definido para original quando transfere o controle de execução para código do WCF.  Além disso, se você usar um modelo de programação assíncrona do WCF Certifique-se de que System.Diagnostics.Trace.CorrelationManager.ActivityID é transferida entre os threads.  
  
## <a name="message-flow-tracing-and-rest-services"></a>Rastreamento de fluxo de mensagens e serviços REST  
 Rastreamento de fluxo de mensagem permite que você rastrear uma solicitação de ponta a ponta.  Com serviços baseados em SOAP, uma ID de atividade é enviada em um cabeçalho de mensagem SOAP. Solicitações REST não contêm esse cabeçalho para que um cabeçalho especial de evento HTTP é usado em vez disso. O trecho de código a seguir mostra como você pode recuperar programaticamente o valor da ID de atividade:  
  
```csharp
Object output = null;
if (OperationContext.Current.IncomingMessageProperties.TryGetValue(HttpRequestMessageProperty.Name, out output))
{
   HttpRequestMessageProperty httpHeaders = output as HttpRequestMessageProperty;
   // Retrieve the Activity Id from the HTTP header    string e2eId = httpHeaders.Headers["E2EActivity"];
   // ...
}
```

 Você pode adicionar programaticamente o cabeçalho usando o código a seguir:  
  
```csharp  
HttpContent content = new StreamContent(contentStream);  
Guid correlation = Guid.NewGuid();  
content.Headers.Add("E2EActivity", Convert.ToBase64String(correlation.ToByteArray()));  
```
