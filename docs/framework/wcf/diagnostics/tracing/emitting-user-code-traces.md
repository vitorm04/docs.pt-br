---
title: "Emitindo traços de código de usuário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa54186a-8ffa-4332-b0e7-63867126fd49
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d743ae68955bba844f84fed71047d9331fd349af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="emitting-user-code-traces"></a>Emitindo traços de código de usuário
Além de habilitar o rastreamento na configuração para coletar dados de instrumentação gerados por [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], você também pode emitir rastreamentos programaticamente no código do usuário. Dessa forma, você pode criar proativamente dados de instrumentação que você pode examinar posteriormente para fins de diagnóstico. Este tópico discute como você pode fazer isso.  
  
 Além disso, o [estendendo rastreamento](../../../../../docs/framework/wcf/samples/extending-tracing.md) exemplo inclui todo o código demonstrado nas seções a seguir.  
  
## <a name="creating-a-trace-source"></a>Criação de uma origem de rastreamento  
 Você pode usar o código a seguir para criar uma fonte de rastreamento do usuário.  
  
```  
TraceSource ts = new TraceSource("myUserTraceSource");  
```  
  
## <a name="creating-activities"></a>Criação de atividades  
 As atividades são a unidade lógica de processamento. Você pode criar uma atividade para cada unidade de processamento principal no qual você deseja que os rastreamentos são agrupados. Por exemplo, você pode criar uma atividade para cada solicitação para o serviço. Para fazer isso, execute as etapas a seguir.  
  
1.  Salve a ID de atividade no escopo.  
  
2.  Criar uma nova ID de atividade.  
  
3.  Transferência da atividade no escopo para a nova, defina a nova atividade no escopo e emitir um rastreamento de início para a atividade.  
  
 O código a seguir demonstra como fazer isso.  
  
```  
Guid oldID = Trace.CorrelationManager.ActivityId;  
Guid traceID = Guid.NewGuid();  
ts.TraceTransfer(0, "transfer", traceID);  
Trace.CorrelationManager.ActivityId = traceID; // Trace is static  
ts.TraceEvent(TraceEventType.Start, 0, "Add request");  
```  
  
## <a name="emitting-traces-within-a-user-activity"></a>Emitindo traços de dentro de uma atividade de usuário  
 O código a seguir emite rastreamentos em uma atividade de usuário.  
  
```  
double value1 = 100.00D;  
double value2 = 15.99D;  
ts.TraceInformation("Client sends message to Add " + value1 + ", " + value2);  
double result = client.Add(value1, value2);  
ts.TraceInformation("Client receives Add response '" + result + "'");  
```  
  
## <a name="stopping-the-activities"></a>Parar as atividades  
 Para interromper as atividades, transferir de volta para a antiga atividade, parar a id da atividade atual e redefinir a id da atividade anterior no escopo.  
  
 O código a seguir demonstra como fazer isso.  
  
```  
ts.TraceTransfer(0, "transfer", oldID);  
ts.TraceEvent(TraceEventType.Stop, 0, "Add request");  
Trace.CorrelationManager.ActivityId = oldID;  
```  
  
## <a name="propagating-the-activity-id-to-a-service"></a>Propagando a ID de atividade a um serviço  
 Se você definir o `propagateActivity` atributo `true` para o `System.ServiceModel` arquivos de origem do rastreamento na configuração de serviço e o cliente, o serviço de processamento de solicitação para adicionar ocorre na mesma atividade como definido no cliente. Se o serviço define suas próprias atividades e transferências, os rastreamentos de serviço não aparecem na atividade propagadas pelo cliente. Em vez disso, eles aparecem em uma atividade correlacionada por rastreamentos de transferência para a atividade cuja ID é propagada pelo cliente.  
  
> [!NOTE]
>  Se o `propagateActivity` atributo é definido como `true` no cliente e no serviço, a atividade de ambiente no escopo de operação do serviço é definida por [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].  
  
 Você pode usar o código a seguir para verificar se uma atividade foi definida no escopo por [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].  
  
```  
// Check if an activity was set in scope by WCF, if it was   
// propagated from the client. If not, ( ambient activity is   
// equal to Guid.Empty), create a new one.  
if(Trace.CorrelationManager.ActivityId == Guid.Empty)  
{  
    Guid newGuid = Guid.NewGuid();  
    Trace.CorrelationManager.ActivityId = newGuid;  
}  
// Emit your Start trace.  
ts.TraceEvent(TraceEventType.Start, 0, "Add Activity");  
  
// Emit the processing traces for that request.  
serviceTs.TraceInformation("Service receives Add "   
                            + n1 + ", " + n2);  
// double result = n1 + n2;  
serviceTs.TraceInformation("Service sends Add result" + result);  
  
// Emit the Stop trace and exit the method scope.  
ts.TraceEvent(TraceEventType.Stop, 0, "Add Activity");  
// return result;  
```  
  
## <a name="tracing-exceptions-thrown-in-code"></a>Exceções geradas no código de rastreamento  
 Quando você gera uma exceção no código, você também pode rastrear a exceção no nível de aviso ou usando o código a seguir.  
  
```  
ts.TraceEvent(TraceEventType.Warning, 0, "Throwing exception " + "exceptionMessage");  
```  
  
## <a name="viewing-user-traces-in-the-service-trace-viewer-tool"></a>Exibindo rastreamentos de usuário na ferramenta de Visualizador de rastreamento de serviço  
 Esta seção contém capturas de tela de rastreamentos gerados pela execução de [estendendo rastreamento](../../../../../docs/framework/wcf/samples/extending-tracing.md) de exemplo, quando exibido usando o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
 O diagrama a seguir, a atividade de "Solicitação para adicionar" criada anteriormente está selecionada no painel esquerdo. Ele é listado com três outros matemática atividades de operação (divisão, subtrair, multiplicar) que constituem o programa de cliente de aplicativo. O código do usuário tiver definido uma nova atividade para cada operação isolar possíveis ocorrências do erro nas solicitações diferentes.  
  
 Para demonstrar o uso de transferências no [estendendo rastreamento](../../../../../docs/framework/wcf/samples/extending-tracing.md) exemplo, uma atividade de cálculo que encapsula as solicitações de quatro operação também é criada. Para cada solicitação, há uma transferência de e para trás da atividade de cálculo para a atividade de solicitação (o rastreamento é realçado no painel superior à direita na figura).  
  
 Quando você seleciona uma atividade no painel esquerdo, os rastreamentos incluídos por esta atividade são mostrados no painel superior direito. Se `propagateActivity` é `true` em cada ponto de extremidade no caminho da solicitação, os rastreamentos na atividade de solicitação são de todos os processos que participam da solicitação. Neste exemplo, você pode ver os rastreamentos do cliente e de serviço na coluna 4º no painel.  
  
 Essa atividade mostra a seguinte ordem de processamento:  
  
1.  Cliente envia a mensagem a ser adicionada.  
  
2.  Serviço recebe a mensagem de solicitação de adicionar.  
  
3.  Serviço envia a resposta de adicionar.  
  
4.  Cliente recebe a resposta de adicionar.  
  
 Todos os rastreamentos foram emitidos no nível de informações. Clicar em um rastreamento no painel superior direito mostra os detalhes do que o rastreamento no painel inferior direito.  
  
 No diagrama a seguir, podemos também ver rastreamentos de transferência de e para a atividade de cálculo, bem como dois pares de iniciar e parar rastreamentos por atividade de solicitação, um para o cliente e um para o serviço (uma para cada fonte de rastreamento).  
  
 ![Rastreamentos de código do Visualizador de rastreamento: Emitindo usuário &#45;](../../../../../docs/framework/wcf/diagnostics/tracing/media/242c9358-475a-4baf-83f3-4227aa942fcd.gif "242c9358-475a-4baf-83f3-4227aa942fcd")  
Lista de atividades por hora de criação (painel esquerdo) e suas atividades aninhadas (painel superior direito)  
  
 Se o código de serviço gera uma exceção que faz com que o cliente lançar também (por exemplo, quando o cliente não obteve resposta à sua solicitação), o serviço e cliente de aviso ou mensagens de erro ocorrerem na mesma atividade de correlação direta. No diagrama a seguir, o serviço gera uma exceção indicando "o serviço se recusa a processar essa solicitação no código do usuário." O cliente também gera uma exceção que declara que "o servidor não pôde processar a solicitação devido a um erro interno."  
  
 ![Rastreamentos de código usando o Visualizador de rastreamento para emitir usuário &#45;](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace2.gif "e2eTrace2")  
Erros em pontos de extremidade para uma determinada solicitação serão exibidos na mesma atividade se a id de atividade de solicitação foi propagada  
  
 Clicando duas vezes o multiplicar atividade no painel à esquerda mostra o gráfico a seguir, com os rastreamentos da multiplicação de atividade para cada processo envolvido. Podemos ver que um aviso ocorreu primeiro o serviço (exceção lançada), que é seguido por erros e avisos no cliente porque não foi possível processar a solicitação. Portanto, podemos implica a relação de erro causal entre pontos de extremidade e derivar a causa do erro.  
  
 ![Rastreamentos de código usando o Visualizador de rastreamento para emitir usuário &#45;](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace3.gif "e2eTrace3")  
Modo de exibição de gráfico de correlação de erro  
  
 Para obter os rastreamentos anteriores, definimos `ActivityTracing` para as fontes de rastreamento de usuário e `propagateActivity=true` para o `System.ServiceModel` origem do rastreamento. Nós não definimos `ActivityTracing` para o `System.ServiceModel` origem de rastreamento para habilitar o código de usuário a propagação de atividade de código do usuário. (Ao rastreamento de atividades de ServiceModel está ativado, a ID de atividade definida no cliente não será propagada para o código de usuário do serviço; Transferências de, no entanto, correlacionam as atividades de código do usuário cliente e de serviço para o intermediário [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] atividades.)  
  
 Definir atividades e propagação a ID de atividade nos permitem realizar correlação erro direto entre pontos de extremidade. Dessa forma, pode localizar a causa de um erro mais rapidamente.  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo rastreamento](../../../../../docs/framework/wcf/samples/extending-tracing.md)
