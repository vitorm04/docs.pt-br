---
title: Transferir
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 40cd80b2b4e2f949b92f4c89cde6b271a502d047
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="transfer"></a>Transferir
Este tópico descreve a transferência de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] modelo de rastreamento de atividade.  
  
## <a name="transfer-definition"></a>Definição de transferência  
 As transferências entre atividades representam causais relações entre eventos em que as atividades relacionadas em pontos de extremidade. Duas atividades estão relacionadas com transferências quando fluxos de controle entre essas atividades, por exemplo, uma chamada de método Cruzando os limites de atividade. Em [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], quando os bytes são recebidos do serviço, a escuta na atividade é transferida para a atividade receber Bytes em que o objeto de mensagem é criado. Para obter uma lista de cenários de rastreamento ponta a ponta e sua respectiva atividade e design de rastreamento, consulte [cenários de rastreamento ponta a ponta](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).  
  
 Para emitir rastreamentos de transferência, use o `ActivityTracing` configuração da origem de rastreamento, conforme demonstrado pelo código de configuração a seguir.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a>Usar a transferência para correlacionar atividades dentro de pontos de extremidade  
 Atividades e transferências de permitem que o usuário com probabilidade localizar a causa do erro. Por exemplo, se é transferir e voltar entre as atividades M e N respectivamente de componentes M e N, e uma falha ocorre no direito de N após a transferência M, podemos pode desenhar final que é provavelmente devido a dados de transmissão do N para M.  
  
 Um rastreamento de transferência é emitido de atividade M a atividade de N quando há um fluxo de controle entre M e N. Por exemplo, N executa algum trabalho para M devido a uma chamada de método Cruzando os limites das atividades. N pode já existir ou tiver sido criada. N é gerado pelo M quando N é uma nova atividade que executa um trabalho para M.  
  
 Uma transferência de M a N não pode ser seguida por uma transferência de N a M. Isso ocorre porque o M pode gerar algum trabalho N e não rastrear quando N de que o trabalho for concluído. Na verdade, M pode terminar antes N concluir sua tarefa. Isso ocorre na atividade "Abrir ServiceHost" (M) que gera a atividades de ouvinte (N) e, em seguida, termina. Uma transferência de N a M significa que N concluído o trabalho relacionado a M.  
  
 N pode continuar a executar outro processamento não relacionado a M, por exemplo, uma atividade de autenticador existente (N) que mantém receber solicitações de logon (M) de atividades de logon diferente.  
  
 Uma relação de aninhamento não necessariamente existe entre atividades M e N. Isso pode acontecer devido a duas razões. Primeiro, quando a atividade M não monitora o processamento real realizadas em N embora iniciada M s. Segundo, quando N já existe.  
  
## <a name="example-of-transfers"></a>Exemplo de transferências  
 Listas de dois exemplos a seguir transferência.  
  
-   Quando você cria um host de serviço, o construtor de assumir o controle do código de chamada ou o código de chamada é transferida para o construtor. Quando o construtor concluiu a execução, ele retorna o controle para o código de chamada ou o construtor de transferências de volta para o código de chamada. Esse é o caso de uma relação aninhada.  
  
-   Quando um ouvinte de processamento de dados de transporte é iniciado, ele cria um novo thread e passa para a atividade receber Bytes o contexto apropriado para processamento, passando o controle e dados. Quando esse thread terminou de processar a solicitação, a atividade receber Bytes passa nada de volta para o ouvinte. Nesse caso, temos uma transferência em mas nenhuma transferência de nova atividade de thread. As duas atividades estão relacionadas, mas não aninhadas.  
  
## <a name="activity-transfer-sequence"></a>Sequência de transferência de atividade  
 Uma sequência de transferência de atividade válido inclui as seguintes etapas.  
  
1.  Iniciar uma nova atividade, que consiste em selecionar um novo gAId.  
  
2.  Emissão de um rastreamento de transferência para esse novo gAId da ID da atividade atual  
  
3.  Definir a nova ID de TLS  
  
4.  Emita um rastreamento de início para indicar o início da nova atividade por.  
  
5.  Voltar para a atividade original consiste no seguinte:  
  
6.  Emissão de um rastreamento de transferência para o gAId original  
  
7.  Emissão de um rastreamento de parada para indicar o fim da nova atividade  
  
8.  Defina o TLS para o antigo gAId.  
  
 O exemplo de código a seguir demonstra como fazer isso. Este exemplo supõe que uma chamada de bloqueio é feita ao transferir para a nova atividade e inclui os rastreamentos de suspender/retomar.  
  
```  
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
 [Configurando o rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [Usando o Visualizador de Rastreamento de Serviço para exibir rastreamentos correlacionados e solucionar problemas](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Cenários de rastreamento ponta a ponta](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) (Ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer.exe))
