---
title: Atividade
ms.date: 03/30/2017
ms.assetid: 70471705-f55f-4da1-919f-4b580f172665
ms.openlocfilehash: b93960d4006499c935c27ee18e066d091632d3d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170203"
---
# <a name="activity"></a>Atividade
Este tópico descreve os rastreamentos de atividade no modelo de rastreamento do Windows Communication Foundation (WCF). As atividades são unidades que ajudam o usuário a restringir o escopo de uma falha de processamento. Erros que ocorrem na mesma atividade estão diretamente relacionados. Por exemplo, uma operação falhará porque a falha na descriptografia mensagem. Os rastreamentos para a operação e a falha na descriptografia mensagem aparecem na mesma atividade, mostrando uma correlação direta entre o erro de descriptografia e o erro da solicitação.  
  
## <a name="configuring-activity-tracing"></a>Configurando o rastreamento de atividade  
 O WCF fornece atividades predefinidas para aplicativos de processamento (consulte [lista de atividades](../../../../../docs/framework/wcf/diagnostics/tracing/activity-list.md)). Você também pode definir as atividades por meio de programação para rastreamentos de usuário do grupo. Para obter mais informações, consulte [emitindo rastreamentos de código do usuário](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md).  
  
 Para emitir rastreamentos de atividade em tempo de execução, use o `ActivityTracing` definindo para o `System.ServiceModel` rastrear a origem, ou outros WCF ou fontes de rastreamento personalizado, conforme demonstrado pelo código de configuração a seguir.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
 Para saber mais sobre o elemento de configuração e os atributos que está sendo usados, consulte a [Configurando o rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) tópico.  
  
## <a name="viewing-activities"></a>Exibir atividades  
 Você pode exibir as atividades e seu utilitário na [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Quando ActivityTracing estiver habilitado, essa ferramenta usa os rastreamentos e classifica-os com base na atividade. Você também pode ver as transferências de rastreamento. Uma transferência de rastreamento indica como as diferentes atividades estão relacionados uns aos outros. Você pode ver que uma determinada atividade causado outro iniciar. Por exemplo, uma solicitação de mensagem iniciado um handshake de segurança para obter um Token de conversa de seguro.  
  
### <a name="correlating-activities-in-service-trace-viewer"></a>Correlacionar atividades no Visualizador de rastreamento de serviço  
 A ferramenta Visualizador de rastreamento de serviço fornece dois modos de exibição de atividades:  
  
-   **Lista** exibição, onde a ID de atividade é usada para correlacionar diretamente rastreamentos entre processos. Rastreamentos de processos diferentes, por exemplo, o cliente e o serviço, mas com a mesma ID de atividade são agrupados na mesma atividade. Portanto, um erro que ocorre no serviço que, em seguida, faz com que um erro no cliente ambos aparecerão na mesma exibição da atividade na ferramenta.  
  
-   **Gráfico** modo de exibição, em que as atividades são agrupadas por processos. Nessa exibição, um serviço com a mesma ID de atividade e o cliente tem seus rastreamentos em atividades diferentes. Para correlacionar atividades com a mesma ID de atividade em diferentes processos, a ferramenta mostra a fluxos de mensagens entre as atividades relacionadas.  
  
 Para obter mais informações e para ver uma exibição gráfica da ferramenta do Visualizador de rastreamento de serviço, consulte [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) e [usando o Visualizador de rastreamento de serviço para exibir rastreamentos correlacionados e Solução de problemas](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
## <a name="defining-the-scope-of-an-activity"></a>Definir o escopo de uma atividade  
 Uma atividade é definida em tempo de design e denota uma unidade lógica de trabalho. Os rastreamentos emitidos com o mesmo identificador de atividade estão diretamente relacionados, eles fazem parte da mesma atividade. Como uma atividade pode cruzar os limites do ponto de extremidade (uma solicitação), dois escopos para uma atividade são definidos.  
  
-   `Global` escopo, por aplicativo. Nesse escopo, a atividade é identificada por seu identificador de atividade exclusivo de 128 bits, o gAId. O gAid é o que é propagado entre pontos de extremidade.  
  
-   `Local` escopo, por ponto de extremidade. Nesse escopo, a atividade é identificada por seu gAId, juntamente com o nome de origem de rastreamento emitindo rastreamentos de atividade e o processo de identificação. Este triplet constitui a id de atividade local, apresentada. O apresentado é usado para definir os limites (locais) de uma atividade.  
  
## <a name="trace-schema"></a>Esquema de rastreamento  
 Rastreamentos podem ser emitidos usando qualquer esquema e entre plataformas da Microsoft. "e2e" (para "ponta a ponta") é um esquema comumente usado. Esse esquema inclui um identificador de 128 bits (gAId), o nome da origem de rastreamento e a ID de processo. No código gerenciado, <xref:System.Diagnostics.XmlWriterTraceListener> emite rastreamentos no esquema de E2E.  
  
 Os desenvolvedores podem definir a Ajuda que é emitida com um rastreamento, definindo o <xref:System.Diagnostics.CorrelationManager.ActivityId%2A> propriedade com um Guid no Thread TLS (armazenamento Local). O exemplo a seguir demonstra isso.  
  
```csharp
// set the current Activity ID to a new GUID.  
CorrelationManager.ActivityId = Guid.NewGuid();  
```
  
 Definindo o gAId no TLS ficará evidente quando os rastreamentos são emitidos usando uma origem de rastreamento, conforme mostrado no exemplo a seguir.  
  
```csharp
TraceSource traceSource = new TraceSource("myTraceSource");  
traceSource.TraceEvent(TraceEventType.Warning, eventId, "Information");  
```  
  
 O rastreamento emitido conterá o gAId atualmente em TLS, o nome da origem de rastreamento passado como um parâmetro ao construtor da origem de rastreamento e a ID. do processo atual  
  
## <a name="activity-lifetime"></a>Tempo de vida de atividade  
 Em termos mais rígidos, evidências de uma atividade começa na primeira vez em que a ID de atividade é usada em um rastreamento emitido e termina na última vez em que ele é usado em um rastreamento emitido. Um conjunto predefinido de tipos de rastreamento são fornecidos pelo <xref:System.Diagnostics>, incluindo o início e parada, marcar explicitamente os limites de tempo de vida da atividade.  
  
-   Início: Indica o início de uma atividade. Um rastreamento "Start" fornece um registro do início de uma nova etapa de processamento. Ele contém uma nova ID de atividade para uma determinada origem em um determinado processo, exceto quando a ID de atividade for propagada entre pontos de extremidade, nesse caso, podemos ver um "Start" por ponto de extremidade. Exemplos de iniciar uma nova atividade incluem a criação de um novo thread para processamento, ou inserindo um novo método público.  
  
-   Parar: Indica o final de uma atividade. Um rastreamento de "Parar" fornece um registro de encerramento de uma etapa de processamento existente. Ele contém uma ID de atividade existente para uma determinada origem em um determinado processo, exceto quando a ID de atividade for propagada entre pontos de extremidade, nesse caso, podemos ver um "Stop" por ponto de extremidade.  Encerrar um thread de processamento ou sair de um método cujo início foi marcado com um rastreamento "Start" são exemplos de parar uma atividade.  
  
-   Suspenda: Indica a suspensão de processamento de uma atividade. Um rastreamento de "Suspender" contém uma ID de atividade existente cujo processamento é esperado para retomar um momento posterior. Nenhum rastreamento é emitido com essa ID entre os eventos suspender e retomar da origem de rastreamento atual. Exemplos de pausar uma atividade durante uma chamada a uma função de biblioteca externa ou ao esperar em um recurso como uma porta de conclusão de e/s.  
  
-   Retomar: Indica a retomada do processamento de uma atividade. Um rastreamento de "Continuação" contém uma id de atividade existente cujo último rastreamento emitido da origem de rastreamento atual foi um rastreamento de "Suspender". Exemplos de retornar de uma chamada para uma função de biblioteca externa, ou quando sinalizado para retomar o processamento por um recurso, como uma porta de conclusão de e/s.  
  
-   Transferência: Como algumas atividades são causadas por outras pessoas, ou se relacionam com outras pessoas, as atividades podem estar relacionadas a outras atividades por meio de rastreamentos "Transferir". Uma transferência registra o relacionamento direcionado de uma atividade para outra  
  
 Iniciar e parar rastreamentos não são essenciais para a correlação. No entanto, eles podem ajudar a aumentar o desempenho, a criação de perfil e validação de escopo de atividades.  
  
 Usar esses tipos, as ferramentas podem otimizar os logs de rastreamento para localizar os eventos relacionados imediatamente da mesma atividade de navegação ou eventos em atividades relacionadas se a ferramenta segue os rastreamentos de transferência. Por exemplo, as ferramentas irá parar de analisar os logs para uma determinada atividade quando eles veem um rastreamento de início/parada.  
  
 Esses tipos de rastreamento também podem ser usados para criação de perfil. Recursos consumidos entre os marcadores de início e parada representam o tempo inclusivo da atividade, incluindo lógica de atividades contidas. Subtrair os intervalos de tempo entre os rastreamentos de suspender e retomar fornece o tempo de atividade real.  
  
 O rastreamento de interrupção também é particularmente útil para validar o escopo das atividades de implementado. Se alguns rastreamentos de processamento aparecem após o rastreamento de interrupção em vez de dentro de uma determinada atividade, isso poderá sugere defeito de código.  
  
## <a name="guidelines-for-using-activity-tracing"></a>Diretrizes para usar o rastreamento de atividades  
 A seguir está uma diretriz de uso ActivityTracing rastreamentos (Iniciar, parar, suspender, retomar e transferência).  
  
-   O rastreamento é um gráfico direcionado cíclico, não uma árvore. Você pode retornar o controle para uma atividade que é gerado de uma atividade.  
  
-   Uma atividade denota um limite de processamento que pode ser significativo para o administrador do sistema ou capacidade de suporte.  
  
-   Cada método WCF, tanto no cliente e servidor, é limitado pela partir de uma nova atividade, depois (após o trabalho ser concluído) terminando a nova atividade e retornar para a atividade de ambiente.  
  
-   Longa em execução (contínua) atividades como ouvindo as conexões ou aguardando as mensagens são representadas por marcadores de início/parada correspondente.  
  
-   Atividades disparado pelo recebimento de mensagem ou processamento de uma mensagem são representadas pelos limites do rastreamento.  
  
-   As atividades representam atividades, não necessariamente objetos. Uma atividade deve ser interpretada como "isso estava acontecendo quando. . . (emissão de rastreamento significativo ocorreu)."  
  
## <a name="see-also"></a>Consulte também

- [Configurando o rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [Utilizando o visualizador de rastreamento de serviço para visualização de rastreamento correlacionados e soluções de problemas](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Cenários de rastreamento ponta a ponta](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [Ferramenta Visualizador de Rastreamento de Serviço (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [Emitindo traços de código de usuário](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md)
