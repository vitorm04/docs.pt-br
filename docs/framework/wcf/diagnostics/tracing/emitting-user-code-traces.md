---
title: Emitindo traços de código de usuário
ms.date: 03/30/2017
ms.assetid: fa54186a-8ffa-4332-b0e7-63867126fd49
ms.openlocfilehash: 0664c11d8020ee5e712ce6d4843c85a1f30b11a3
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200581"
---
# <a name="emitting-user-code-traces"></a>Emitindo traços de código de usuário
Além de habilitar o rastreamento na configuração para coletar dados de instrumentação gerados pelo Windows Communication Foundation (WCF), você também pode emitir rastreamentos programaticamente no código do usuário. Dessa forma, você pode criar proativamente os dados de instrumentação que você pode analisar posteriormente para fins de diagnóstico. Este tópico discute como você pode fazer isso.  
  
 Além disso, o [estendendo rastreamento](../../../../../docs/framework/wcf/samples/extending-tracing.md) exemplo inclui todo o código demonstrado nas seções a seguir.  
  
## <a name="creating-a-trace-source"></a>Criação de uma origem de rastreamento  
 Você pode usar o código a seguir para criar uma origem de rastreamento de usuário.  
  
```csharp
TraceSource ts = new TraceSource("myUserTraceSource");  
```  
  
## <a name="creating-activities"></a>Criação de atividades  
 As atividades são a unidade lógica de processamento. Você pode criar uma atividade para cada unidade de processamento principal no qual você deseja que os rastreamentos a serem agrupados. Por exemplo, você pode criar uma atividade para cada solicitação para o serviço. Para fazer isso, execute as seguintes etapas.  
  
1.  Salve a ID de atividade no escopo.  
  
2.  Criar uma nova ID de atividade.  
  
3.  Transferência da atividade no escopo para a nova, defina a nova atividade no escopo e emitir um rastreamento de início para a atividade.  
  
 O código a seguir demonstra como fazer isso.  
  
```csharp
Guid oldID = Trace.CorrelationManager.ActivityId;  
Guid traceID = Guid.NewGuid();  
ts.TraceTransfer(0, "transfer", traceID);  
Trace.CorrelationManager.ActivityId = traceID; // Trace is static  
ts.TraceEvent(TraceEventType.Start, 0, "Add request");  
```  
  
## <a name="emitting-traces-within-a-user-activity"></a>Emitindo rastreamentos de dentro de uma atividade de usuário  
 O código a seguir emite rastreamentos dentro de uma atividade de usuário.  
  
```csharp
double value1 = 100.00D;  
double value2 = 15.99D;  
ts.TraceInformation("Client sends message to Add " + value1 + ", " + value2);  
double result = client.Add(value1, value2);  
ts.TraceInformation("Client receives Add response '" + result + "'");  
```  
  
## <a name="stopping-the-activities"></a>Interromper as atividades  
 Para interromper as atividades, transfira de volta à atividade antiga, parar a id da atividade atual e redefinir a id de atividade antigo no escopo.  
  
 O código a seguir demonstra como fazer isso.  
  
```csharp
ts.TraceTransfer(0, "transfer", oldID);  
ts.TraceEvent(TraceEventType.Stop, 0, "Add request");  
Trace.CorrelationManager.ActivityId = oldID;  
```  
  
## <a name="propagating-the-activity-id-to-a-service"></a>Propagando a ID de atividade a um serviço  
 Se você definir a `propagateActivity` de atributo para `true` para o `System.ServiceModel` arquivos de origem de rastreamento na configuração de serviço e cliente, o serviço de processamento para a solicitação para adicionar ocorre na mesma atividade como aquele definido no cliente. Se o serviço define suas próprias atividades e transferências, os rastreamentos de serviço não aparecem na atividade propagada pelo cliente. Em vez disso, eles aparecem em uma atividade correlacionada por rastreamentos de transferência para a atividade cuja ID é propagada pelo cliente.  
  
> [!NOTE]
>  Se o `propagateActivity` atributo é definido como `true` sobre o cliente e o serviço, a atividade de ambiente no escopo de operação do serviço é definida pelo WCF.  
  
 Você pode usar o código a seguir para verificar se uma atividade foi definida no escopo pelo WCF.  
  
```csharp
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
  
## <a name="tracing-exceptions-thrown-in-code"></a>Exceções geradas em código de rastreamento  
 Ao lançar uma exceção no código, você também pode rastrear a exceção no nível de aviso ou usando o código a seguir.  
  
```csharp
ts.TraceEvent(TraceEventType.Warning, 0, "Throwing exception " + "exceptionMessage");  
```  
  
## <a name="viewing-user-traces-in-the-service-trace-viewer-tool"></a>Exibindo rastreamentos de usuário na ferramenta de Visualizador de rastreamento de serviço  
 Esta seção contém as capturas de tela de gerado pela execução de rastreamentos a [estendendo rastreamento](../../../../../docs/framework/wcf/samples/extending-tracing.md) de exemplo, quando exibido usando o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
 No diagrama a seguir, a atividade de "Solicitação para adicionar" criada anteriormente está selecionada no painel à esquerda. Ele é listado com três outras matemática operação atividades (dividir, subtrair, multiplicar) que constituem o programa de cliente do aplicativo. O código do usuário definiu uma nova atividade para cada operação isolar possíveis ocorrências do erro em diferentes solicitações.  
  
 Para demonstrar o uso de transferências na [estendendo rastreamento](../../../../../docs/framework/wcf/samples/extending-tracing.md) exemplo, uma atividade de calculadora que encapsula as solicitações de quatro operação também é criada. Para cada solicitação, há uma transferência de e para trás da atividade de Calculadora para a atividade de solicitação (o rastreamento é realçado no painel superior direito na figura).  
  
 Quando você seleciona uma atividade no painel à esquerda, os rastreamentos incluídos por essa atividade são mostrados no painel à direita superior. Se `propagateActivity` é `true` em cada ponto de extremidade no caminho da solicitação, os rastreamentos na atividade de solicitação são de todos os processos que participam da solicitação. Neste exemplo, você pode ver os rastreamentos do cliente e de serviço na coluna 4º no painel.  
  
 Essa atividade mostra a ordem de processamento a seguir:  
  
1.  Cliente envia a mensagem a ser adicionada.  
  
2.  Serviço recebe a mensagem de solicitação de adicionar.  
  
3.  Serviço envia a resposta de adicionar.  
  
4.  Cliente recebe a resposta de adicionar.  
  
 Todos esses rastreamentos foram emitidos no nível de informações. Clicar em um rastreamento no painel superior direito mostra os detalhes de que o rastreamento no painel inferior direito.  
  
 No diagrama a seguir, também vemos os rastreamentos de transferência de e para a atividade de Calculadora, bem como dois pares de iniciar e parar rastreamentos por atividade de solicitação, um para o cliente e outra para o serviço (uma para cada origem de rastreamento).  
  
 ![Visualizador de rastreamento: Emitindo o usuário&#45;rastreamentos de código](../../../../../docs/framework/wcf/diagnostics/tracing/media/242c9358-475a-4baf-83f3-4227aa942fcd.gif "242c9358-475a-4baf-83f3-4227aa942fcd")  
Lista de atividades por hora de criação (painel esquerdo) e suas atividades aninhadas (o painel superior direito)  
  
 Se o código de serviço gera uma exceção que faz com que o cliente gere também (por exemplo, quando o cliente não obteve resposta à sua solicitação), o serviço e cliente de aviso ou mensagens de erro ocorrerem na mesma atividade para correlação direta. No diagrama a seguir, o serviço gera uma exceção afirmando que "o serviço se recusará a processar essa solicitação no código do usuário." O cliente também gerará uma exceção informando que "o servidor foi capaz de processar a solicitação devido a um erro interno."  
  
 ![Usando o Visualizador de rastreamento para emitir o usuário&#45;rastreamentos de código](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace2.gif "e2eTrace2")  
Erros entre pontos de extremidade para uma determinada solicitação aparecem na mesma atividade se a id de atividade de solicitação foi propagada  
  
 Clicando duas vezes o Multiply atividade no painel à esquerda mostra o gráfico a seguir, com os rastreamentos para o multiplicar a atividade para cada processo envolvido. Podemos ver que um aviso ocorreu pela primeira vez no serviço (exceção lançada), que é seguido por erros e avisos no cliente porque não foi possível processar a solicitação. Portanto, podemos implica o relacionamento causal com erro entre pontos de extremidade e derivar a causa do erro.  
  
 ![Usando o Visualizador de rastreamento para emitir o usuário&#45;rastreamentos de código](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace3.gif "e2eTrace3")  
Modo de exibição de gráfico de correlação de erro  
  
 Para obter os rastreamentos anteriores, definimos `ActivityTracing` para as fontes de rastreamento de usuário e `propagateActivity=true` para o `System.ServiceModel` origem de rastreamento. Nós não definimos `ActivityTracing` para o `System.ServiceModel` origem de rastreamento para habilitar o código de usuário para a propagação de atividade de código do usuário. (Quando o rastreamento de atividade de ServiceModel está ativado, a ID da atividade definida no cliente não é propagada para o código de usuário do serviço; No entanto, as transferências, correlacionam as atividades de código do usuário cliente e serviço para as atividades do WCF intermediárias.)  
  
 Definir as atividades e propagação de ID de atividade nos permite executar a correlação de erro direto entre pontos de extremidade. Dessa forma, podemos localizar a causa raiz de um erro mais rapidamente.  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo o rastreamento](../../../../../docs/framework/wcf/samples/extending-tracing.md)
