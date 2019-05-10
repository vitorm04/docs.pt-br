---
title: Transferir
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: c3f9420ac798bf2722f825d14ca64653127432b4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662880"
---
# <a name="transfer"></a>Transferir
Este tópico descreve a transferência no modelo de rastreamento de atividade do Windows Communication Foundation (WCF).  
  
## <a name="transfer-definition"></a>Definição de transferência  
 As transferências entre as atividades representam relações causais entre os eventos nas atividades relacionadas dentro de pontos de extremidade. Duas atividades estão relacionadas com transferências quando fluxos de controle entre essas atividades, por exemplo, uma chamada de método Cruzando os limites de atividade. No WCF, quando bytes são recebidos do serviço, a atividade escutar em é transferida para a atividade receber Bytes no qual o objeto de mensagem é criado. Para obter uma lista de cenários de rastreamento de ponta a ponta e sua respectiva atividade e design de rastreamento, consulte [cenários de rastreamento de ponta a ponta](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).  
  
 Para emitir rastreamentos de transferência, use o `ActivityTracing` configuração sobre a origem de rastreamento, conforme demonstrado pelo código de configuração a seguir.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a>Usar a transferência para correlacionar atividades dentro de pontos de extremidade  
 As atividades e transferências de permitir que o usuário probabilistically localizar a causa raiz de um erro. Por exemplo, se transferirmos e voltar entre as atividades M e N, respectivamente, no componentes M e N, e ocorre uma falha no direito de N após a transferência para M, podemos pode desenhar a conclusão de que ele é provavelmente devido a dados de transmissão do N para M.  
  
 Um rastreamento de transferência é emitido de atividade M a atividade de N quando há um fluxo de controle entre M e N. Por exemplo, N executa algum trabalho para M devido a uma chamada de método Cruzando limites de atividades. N pode já existir ou tiver sido criado. N é gerado por M quando N é uma nova atividade que executa algum trabalho para M.  
  
 Uma transferência de M para N não pode ser seguida por uma transferência de N a M. Isso ocorre porque o M pode gerar algum trabalho em N e não rastrear quando N conclui esse trabalho. Na verdade, M pode terminar antes N conclui sua tarefa. Isso ocorre na atividade de "Abrir ServiceHost" (M) que gera a atividades de ouvinte (N) e, em seguida, termina. Uma transferência de N a M significa que N concluído o trabalho relacionado a M.  
  
 N pode continuar a executar outros tipos de processamento não relacionada a M, por exemplo, uma atividade de autenticador (N) existente que mantém recebendo as solicitações de logon (M) de atividades de logon diferente.  
  
 Uma relação de aninhamento não necessariamente existe entre atividades M e N. Isso pode acontecer devido a duas razões. Executada pela primeira vez, quando a atividade de M não monitora o processamento real em N embora iniciada M N. Segundo, quando N já existe.  
  
## <a name="example-of-transfers"></a>Exemplo de transferências  
 Listas de dois exemplos a seguir transferência.  
  
- Quando você cria um host de serviço, o construtor assume o controle do código de chamada ou transfere o código de chamada para o construtor. Quando o construtor finalizou a execução, ele retorna o controle para o código de chamada ou o construtor transfere para o código de chamada. Esse é o caso de uma relação aninhada.  
  
- Quando um ouvinte começa a processar dados de transporte, ele cria um novo thread e passa para a atividade receber Bytes o contexto apropriado para processamento, passando o controle e dados. Quando esse thread terminou de processar a solicitação, a atividade receber Bytes passa nada volta para o ouvinte. Nesse caso, temos uma transferência em mas nenhuma transferência de fora da nova atividade de thread. As duas atividades estão relacionadas, mas não aninhadas.  
  
## <a name="activity-transfer-sequence"></a>Sequência de transferência de atividade  
 Uma sequência de transferência bem formado de atividade inclui as seguintes etapas.  
  
1. Iniciar uma nova atividade, que consiste em selecionar um novo gAId.  
  
2. Emissão de um rastreamento de transferência para esse novo gAId da ID da atividade atual  
  
3. Definir a nova ID no TLS  
  
4. Emita um rastreamento de início para indicar o início da nova atividade por.  
  
5. Retorne para a atividade original consiste no seguinte:  
  
6. Emissão de um rastreamento de transferência para o gAId original  
  
7. Emissão de um rastreamento de interrupção para indicar o final da nova atividade  
  
8. Defina o TLS para o antigo gAId.  
  
 O exemplo de código a seguir demonstra como fazer isso. Este exemplo supõe que uma chamada de bloqueio é feita ao transferir para a nova atividade e inclui os rastreamentos de suspender/retomar.  
  
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
  
## <a name="see-also"></a>Consulte também

- [Configurando o rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [Usando o Visualizador de Rastreamento de Serviço para exibir rastreamentos correlacionados e solucionar problemas](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Cenários de rastreamento ponta a ponta](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [Ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
