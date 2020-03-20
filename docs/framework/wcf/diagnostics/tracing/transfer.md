---
title: Transferir
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: e0ebfff97cd33e7a588a1ab92399a97a0fbec039
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185701"
---
# <a name="transfer"></a>Transferir
Este tópico descreve a transferência no modelo de rastreamento de atividades da Windows Communication Foundation (WCF).  
  
## <a name="transfer-definition"></a>Definição de transferência  
 As transferências entre as atividades representam relações causais entre eventos nas atividades relacionadas dentro dos pontos finais. Duas atividades estão relacionadas com transferências quando o controle flui entre essas atividades, por exemplo, uma chamada de método que cruza os limites da atividade. No WCF, quando os bytes estão chegando ao serviço, a atividade Listen At é transferida para a atividade Receive Bytes onde o objeto de mensagem é criado. Para obter uma lista de cenários de rastreamento de ponta a ponta e suas respectivas atividades e desenho de rastreamento, consulte [Cenários de rastreamento de ponta a ponta](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).  
  
 Para emitir vestígios `ActivityTracing` de transferência, use a configuração na fonte de rastreamento, conforme demonstrado pelo seguinte código de configuração.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a>Usando transferência para correlacionar atividades dentro de endpoints  
 Atividades e transferências permitem que o usuário localize probaticamente a causa raiz de um erro. Por exemplo, se transferirmos para frente e para trás entre as atividades M e N respectivamente nos componentes M e N, e um acidente acontecer em N logo após a transferência de volta para M, podemos chegar à conclusão de que é provável que seja devido ao repasse de dados de N de volta para M.  
  
 Um traço de transferência é emitido da atividade M para a atividade N quando há um fluxo de controle entre M e N. Por exemplo, N realiza alguns trabalhos para M por causa de uma chamada de método que cruza os limites das atividades. N pode já existir ou ter sido criado. N é gerado por M quando N é uma nova atividade que realiza algum trabalho para M.  
  
 Uma transferência de M para N pode não ser seguida por uma transferência de volta de N para M. Isso porque M pode gerar algum trabalho em N e não rastrear quando N completa esse trabalho. Na verdade, M pode terminar antes que N complete sua tarefa. Isso acontece na atividade "Open ServiceHost" (M) que gera atividades do Ouvinte (N) e, em seguida, termina. Uma transferência de Volta de N para M significa que N completou o trabalho relacionado a M.  
  
 N pode continuar realizando outros processamentos não relacionados a M, por exemplo, uma atividade autenticadora (N) existente que continua recebendo solicitações de login (M) de diferentes atividades de login.  
  
 Uma relação de aninhamento não existe necessariamente entre as atividades M e N. Isso pode acontecer por duas razões. Primeiro, quando a atividade M não monitora o processamento real realizado em N, embora M tenha iniciado N. Segundo, quando N já existe.  
  
## <a name="example-of-transfers"></a>Exemplo de Transferências  
 A seguir lista dois exemplos de transferência.  
  
- Quando você cria um host de serviço, o construtor obtém o controle do código de chamada ou do código de chamada transfere para o construtor. Quando o construtor terminar de executar, ele retorna o controle para o código de chamada, ou o construtor transfere de volta para o código de chamada. É o caso de uma relação aninhada.  
  
- Quando um ouvinte começa a processar dados de transporte, ele cria um novo segmento e mãos para a atividade Receive Bytes o contexto apropriado para processamento, controle de passagem e dados. Quando esse segmento tiver terminado o processamento da solicitação, a atividade Receber Bytes não repassa nada para o ouvinte. Neste caso, temos uma transferência, mas nenhuma transferência para fora da nova atividade de thread. As duas atividades estão relacionadas, mas não estão aninhadas.  
  
## <a name="activity-transfer-sequence"></a>Sequência de transferência de atividades  
 Uma seqüência de transferência de atividade bem formada inclui as seguintes etapas.  
  
1. Inicie uma nova atividade, que consiste em selecionar um novo gAId.  
  
2. Emita um traço de transferência para esse novo gAId do ID de atividade atual  
  
3. Defina o novo ID em TLS  
  
4. Emita um traço de início para indicar o início da nova atividade por.  
  
5. O retorno à atividade original consiste no seguinte:  
  
6. Emita um traço de transferência para o gAId original  
  
7. Emita um rastreamento stop para indicar o fim da nova atividade  
  
8. Defina O TLS para o antigo gAId.  
  
 O exemplo de código a seguir demonstra como fazer isso. Esta amostra assume que uma chamada de bloqueio é feita ao transferir para a nova atividade, e inclui rastreamentos de suspensão/currículo.  
  
```csharp
// 0. Create a trace source  
TraceSource ts = new TraceSource("myTS");  

// 1. remember existing ("ambient") activity for clean up  
Guid oldGuid = Trace.CorrelationManager.ActivityId;  
// this will be our new activity  
Guid newGuid = Guid.NewGuid();

// 2. call transfer, indicating that we are switching to the new AID  
ts.TraceTransfer(667, "Transferring.", newGuid);  

// 3. Suspend the current activity.  
ts.TraceEvent(TraceEventType.Suspend, 667, "Suspend: Activity " + i-1);  

// 4. set the new AID in TLS  
Trace.CorrelationManager.ActivityId = newGuid;  

// 5. Emit the start trace  
ts.TraceEvent(TraceEventType.Start, 667, "Boundary: Activity " + i);  

// trace something  
ts.TraceEvent(TraceEventType.Information, 667, "Hello from activity " + i);  

// Perform Work  
// some work.  
// Return  
ts.TraceEvent(TraceEventType.Information, 667, "Work complete on activity " + i);

// 6. Emit the transfer returning to the original activity  
ts.TraceTransfer(667, "Transferring Back.", oldGuid);  

// 7. Emit the End trace  
ts.TraceEvent(TraceEventType.Stop, 667, "Boundary: Activity " + i);  

// 8. Change the tls variable to the original AID  
Trace.CorrelationManager.ActivityId = oldGuid;

// 9. Resume the old activity  
ts.TraceEvent(TraceEventType.Resume, 667, "Resume: Activity " + i-1);  
```  
  
## <a name="see-also"></a>Confira também

- [Configurando o rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [Utilizando o visualizador de rastreamento de serviço para visualização de rastreamento correlacionados e soluções de problemas](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Cenários de rastreamento ponta a ponta](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [Ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
