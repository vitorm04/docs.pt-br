---
title: Determinando a duração da execução de fluxo de trabalho usando rastreamento
ms.date: 03/30/2017
ms.assetid: f04ad0fd-edc7-4cbc-8979-356f2a1131c4
ms.openlocfilehash: 9f9c65f2c873d54da443db14e7f5797ef1e14174
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="determining-workflow-execution-duration-using-tracing"></a>Determinando a duração da execução de fluxo de trabalho usando rastreamento
Este tópico demonstra como determinar o tempo necessário para que um fluxo de trabalho com êxito concluído, são hospedado é executado usando o rastreamento de fluxo de trabalho.  
  
### <a name="to-determine-workflow-application-execution-duration-by-using-workflow-tracing"></a>Para determinar a duração de execução do aplicativo de fluxo de trabalho usando o rastreamento de fluxo de trabalho  
  
1.  Abra [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  Selecione **arquivo**, **novo**, **projeto**.  Em **c#**, selecione o **fluxo de trabalho** nó.  Selecione **aplicativo de Console do fluxo de trabalho** da lista de modelos.  Nomeie o novo projeto `WorkflowDurationTracing` e clique em **Okey**.  
  
2.  Abra Workflow1.xaml.  Arraste uma atividade de <xref:System.Activities.Statements.Delay> na superfície de designer. Atribua o valor de 00:00: (dez 10 segundos) para a propriedade duração da atividade.  
  
3.  Abra o Visualizador de eventos clicando **iniciar**, **executar**e digitando `eventvwr.exe`.  
  
4.  Se você ainda não ativou o rastreamento de fluxo de trabalho, expanda **Applications and Services Logs**, **Microsoft**, **Windows**, **aplicativos de servidor de aplicativo** . Selecione **exibição**, **Mostrar analítica e Logs de depuração**. Clique com botão direito **depurar** e selecione **Habilitar Log**. Deixe o visualizador de eventos aberto de modo que os rastreamentos podem ser exibidos após o fluxo de trabalho é executado.  
  
5.  Execute o aplicativo de fluxo de trabalho pressionando CTRL+SHIFT+B.  
  
6.  No visualizador de eventos, localize um evento mais recente com ID 1009 e uma mensagem semelhante ao seguinte. Anote de tempo que a mensagem foi registrado.  
  
 **Atividade pai ', DisplayName: ', InstanceId: ' filho agendado atividade 'WorkflowDurationTracking.Workflow1', DisplayName: 'Workflow1', InstanceId: '1'.**  
  
7.  Localizar outro evento mais recente com ID 1001 e uma mensagem semelhante ao seguinte.  Subtrair o tempo de mensagem anteriores do valor efetuado logon esta mensagem de determinar a duração da execução de fluxo de trabalho, que deve ser aproximadamente 10 segundos.  
  
 **WorkflowInstance Id: '1bbac57b-3322-498e-9e27-8833fda3a5bf' foi concluída no estado fechado.**  
  
## <a name="see-also"></a>Consulte também  
 [Acompanhamento de fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md)  
 [Monitoramento do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitoramento de aplicativos com App Fabric](http://go.microsoft.com/fwlink/?LinkId=201275)
