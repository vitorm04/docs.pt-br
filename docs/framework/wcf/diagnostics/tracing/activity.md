---
title: Atividade
ms.date: 03/30/2017
ms.assetid: 70471705-f55f-4da1-919f-4b580f172665
ms.openlocfilehash: 34281647f65157484c1e732bc67a6a4b2cf58db6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="activity"></a>Atividade
Este tópico descreve os rastreamentos de atividades no modelo de rastreamento do Windows Communication Foundation (WCF). Atividades são unidades que ajudam o usuário a restringir o escopo de uma falha de processamento. Erros que ocorrem na mesma atividade estão diretamente relacionados. Por exemplo, uma operação falha porque a descriptografia da mensagem falhou. Os rastreamentos de operação e Falha na descriptografia mensagem aparecem na mesma atividade, mostrando uma correlação direta entre o erro de descriptografia e o erro de solicitação.  
  
## <a name="configuring-activity-tracing"></a>Configurando o rastreamento de atividade  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] oferece atividades predefinidas para aplicativos de processamento (consulte [lista de atividades](../../../../../docs/framework/wcf/diagnostics/tracing/activity-list.md)). Você também pode definir atividades programaticamente para rastreamentos de usuário do grupo. Para obter mais informações, consulte [emitindo rastreamentos de código de usuário](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md).  
  
 Para emitir rastreamentos de atividade em tempo de execução, use o `ActivityTracing` configuração para o `System.ServiceModel` rastreamento fonte ou outros [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ou fontes de rastreamento personalizada, conforme demonstrado pelo código de configuração a seguir.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
 Para saber mais sobre o elemento de configuração e os atributos que estão sendo usados, consulte o [Configurando rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) tópico.  
  
## <a name="viewing-activities"></a>Exibir atividades  
 Você pode exibir as atividades e seu utilitário no [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Quando o rastreamento de atividades está habilitado, essa ferramenta usa os rastreamentos e classifica-os com base na atividade. Você também pode ver as transferências de rastreamento. Uma transferência de rastreamento indica como as diferentes atividades estão relacionados uns aos outros. Você pode ver que uma determinada atividade causado outro iniciar. Por exemplo, uma solicitação de mensagem iniciado um handshake de segurança para obter um Token de conversa de seguro.  
  
### <a name="correlating-activities-in-service-trace-viewer"></a>Correlacionar atividades no Visualizador de rastreamento de serviço  
 A ferramenta do Visualizador de rastreamento de serviço fornece dois modos de exibição de atividades:  
  
-   **Lista** exibição, onde a ID de atividade é usada para correlacionar diretamente rastreamentos entre processos. Rastreamentos de processos diferentes, por exemplo, o cliente e o serviço, mas com a mesma ID de atividade são agrupados na mesma atividade. Portanto, um erro que ocorrem no serviço que causa um erro no cliente ambos aparecerá na mesma exibição da atividade na ferramenta.  
  
-   **Gráfico de** exibição, em que as atividades são agrupadas por outros processos. Nesta exibição, um serviço com a mesma ID de atividade e o cliente tem seus rastreamentos em atividades diferentes. Para correlacionar atividades com a mesma ID de atividade em diferentes processos, a ferramenta mostra os fluxos de mensagens entre as atividades relacionadas.  
  
 Para obter mais informações e para ver uma exibição gráfica da ferramenta do Visualizador de rastreamento de serviço, consulte [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) e [usando o Visualizador de rastreamento de serviço para exibir rastreamentos correlacionados e Solução de problemas](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
## <a name="defining-the-scope-of-an-activity"></a>Definir o escopo de uma atividade  
 Uma atividade é definida em tempo de design e denota uma unidade lógica de trabalho. Emitido rastreamentos com o mesmo identificador de atividade estão diretamente relacionados, elas fazem parte da mesma atividade. Como uma atividade pode atravessar limites de ponto de extremidade (uma solicitação), dois escopos para uma atividade são definidos.  
  
-   `Global` escopo, por aplicativo. Este escopo, a atividade é identificada por seu identificador de atividade exclusivo de 128 bits, o gAId. O gAid é o que é propagado entre pontos de extremidade.  
  
-   `Local` escopo, por ponto de extremidade. Este escopo, a atividade é identificada pelo seu gAId, junto com o nome de origem de rastreamento emitindo os rastreamentos de atividade e o processo de identificação. Este Trio constitui a id de atividade local, apresentada. O perfeitos é usado para definir os limites (locais) de uma atividade.  
  
## <a name="trace-schema"></a>Esquema de rastreamento  
 Rastreamentos podem ser emitidos usando qualquer esquema e entre plataformas da Microsoft. "e2e" (para "ponta a ponta") é um esquema mais usado. Esse esquema inclui um identificador de 128 bits (gAId), o nome de origem de rastreamento e o ID de processo. No código gerenciado, <xref:System.Diagnostics.XmlWriterTraceListener> emite rastreamentos no esquema E2E.  
  
 Os desenvolvedores podem definir o recurso que é emitido com um rastreamento, definindo o <xref:System.Diagnostics.CorrelationManager.ActivityId%2A> propriedade com um Guid no Thread TLS (armazenamento Local). O exemplo a seguir demonstra isso.  
  
```  
// set the current Activity ID to a new GUID.  
CorrelationManager.ActivityId = Guid.NewGuid();  
```  
  
 Definindo o gAId no TLS ficará evidente quando os rastreamentos são emitidos usando uma origem de rastreamento, conforme mostrado pelo exemplo a seguir.  
  
```  
TraceSource traceSource = new TraceSource("myTraceSource");  
traceSource.TraceEvent(TraceEventType.Warning, eventId, "Information");  
```  
  
 O rastreamento emitido conterá o gAId atualmente no TLS, o nome de origem de rastreamento passado como um parâmetro de construtor da origem de rastreamento e a ID. do processo atual  
  
## <a name="activity-lifetime"></a>Tempo de vida da atividade  
 Em termos mais rígidos, evidências de uma atividade inicia na primeira vez em que a ID da atividade é usada em um rastreamento emitido e termina na última vez em que ele é usado em um rastreamento emitido. Um conjunto predefinido de tipos de rastreamento são fornecidos pelo <xref:System.Diagnostics>, incluindo iniciar e parar, marcar explicitamente os limites de tempo de vida da atividade.  
  
-   Início: Indica o início de uma atividade. Um rastreamento de "Início" fornece um registro de início de uma nova etapa de processamento. Ele contém uma nova ID de atividade para uma origem de rastreamento específico em um determinado processo, exceto quando a ID da atividade é propagada por pontos de extremidade, caso em que podemos ver um "Start" por ponto de extremidade. Iniciar uma nova atividade exemplos de criar um novo thread para processar ou inserir um novo método público.  
  
-   STOP: Indica o final de uma atividade. Um rastreamento "Stop" fornece um registro de final de uma etapa de processamento existente. Ele contém uma ID de atividade existente para uma origem de rastreamento específico em um determinado processo, exceto quando a ID da atividade é propagada por pontos de extremidade, caso em que podemos ver um "Stop" por ponto de extremidade.  Encerrando um thread de processamento ou sair de um método cujo início foi marcado com um rastreamento de "Início" são exemplos de parar uma atividade.  
  
-   Suspender: Indica a suspensão do processamento de uma atividade. Um rastreamento do "Suspend" contém uma ID de atividade existente cujo processamento é esperado para reiniciar mais tarde. Nenhum rastreamento é emitido com essa ID entre os eventos de suspender e retomar na origem do rastreamento atual. Os exemplos incluem uma atividade a pausa quando a chamada para uma função de biblioteca externa ou aguardando um recurso como uma porta de conclusão de e/s.  
  
-   Retomar: Indica a continuação do processamento de uma atividade. Um rastreamento de "Continuar" contém uma id de atividade existente cujo último rastreamento emitido na origem do rastreamento atual foi um rastreamento "Suspend". Exemplos de retornar de uma chamada para uma função de biblioteca externa, ou quando sinalizado para retomar o processamento por um recurso, como uma porta de conclusão de e/s.  
  
-   Transferência: Porque algumas atividades são causadas por outras pessoas, ou se relacionam com outras pessoas, atividades podem estar relacionadas a outras atividades por meio de rastreamentos "Transfer". Uma transferência registra a relação direcionada de uma atividade para outra  
  
 Iniciar e parar rastreamentos não são essenciais para a correlação. No entanto, eles podem ajudar a aumentar o desempenho, a criação de perfil e a validação do escopo da atividade.  
  
 Usar esses tipos, as ferramentas podem otimizar navegando os logs de rastreamento para localizar os eventos relacionados imediatamente da mesma atividade ou eventos em atividades relacionadas à se a ferramenta segue rastreamentos de transferência. Por exemplo, as ferramentas irá parar de analisar os logs para uma determinada atividade quando eles veem um rastreamento de iniciar/parar.  
  
 Esses tipos de rastreamento também podem ser usados para criação de perfil. Recursos consumidos entre os marcadores de início e parada representam o tempo inclusivo da atividade, incluindo lógica de atividades contidas. Subtraindo-se os intervalos de tempo entre os rastreamentos de suspender e retomar fornece o tempo de atividade real.  
  
 Parar rastreamento também é particularmente útil para validar o escopo das atividades implementados. Se algum processamento rastreamentos aparecem após o rastreamento de parada em vez de dentro de uma determinada atividade, isso poderá sugere defeito de código.  
  
## <a name="guidelines-for-using-activity-tracing"></a>Diretrizes para usar o rastreamento de atividades  
 A seguir está uma diretriz de como usar rastreamentos ActivityTracing (Iniciar, parar, suspender, continuar e transferência).  
  
-   O rastreamento é um gráfico direcionado cíclico, não uma árvore. Você pode retornar o controle para uma atividade que gerou uma atividade.  
  
-   Uma atividade denota um limite de processamento que pode ser significativo para o administrador do sistema ou a capacidade de suporte.  
  
-   Cada [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] método, tanto no cliente e no servidor, é limitado pela partir de uma nova atividade, depois (depois que o trabalho é realizado) terminando a nova atividade e retornar para a atividade de ambiente.  
  
-   Longa em execução (em andamento) atividades como escutando conexões ou aguardando as mensagens são representadas por marcadores de início/parada correspondente.  
  
-   Atividades disparado por recebimento ou processamento de uma mensagem são representados pelos limites do rastreamento.  
  
-   Atividades representam as atividades, não necessariamente objetos. Uma atividade deve ser interpretada como "isso estava acontecendo quando. . . (emissão de rastreamento significativo ocorreu)."  
  
## <a name="see-also"></a>Consulte também  
 [Configurando o rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [Usando o Visualizador de Rastreamento de Serviço para exibir rastreamentos correlacionados e solucionar problemas](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Cenários de rastreamento ponta a ponta](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [Ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [Emitindo rastreamentos de código do usuário](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md)
