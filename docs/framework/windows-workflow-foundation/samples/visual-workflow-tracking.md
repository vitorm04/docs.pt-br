---
title: Rastreamento visual de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 0143448f-2044-40a0-8a3d-941f6d12468b
ms.openlocfilehash: f010bdcf6004e84fd346d0e8649c87c008cad122
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="visual-workflow-tracking"></a>Rastreamento visual de fluxo de trabalho
Este exemplo demonstra como escrever um aplicativo visual de acompanhamento de fluxo de trabalho usando a funcionalidade de depuração disponível com [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 O aplicativo executa um trabalho simples do fluxograma (definidos em Workflow.xaml) e que o host designer de trabalho para exibir o fluxo de trabalho em execução no momento. Como o fluxo de trabalho é executado, a atividade atualmente em execução é mostrada com uma seta amarela de estrutura e de depuração. Além disso, através dos registros gerados pelo fluxo de trabalho também são exibidos na janela do aplicativo. Para obter mais informações sobre o controle de fluxo de trabalho, consulte [fluxo de trabalho de rastreamento e rastreamento](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Para obter mais informações sobre como hospedar novamente o designer de fluxo de trabalho, consulte [nova hospedagem o Designer de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md).  
  
 O simulador de fluxo de trabalho funciona mantendo dois dicionários. Um contém um mapeamento entre o objeto atualmente executando de atividade e o número da linha XAML em que a atividade é instanciada. O outro contém um mapeamento entre o ID de instância de atividade e o objeto de atividade. Para controlar os registros são emitidas usando um perfil personalizado de rastreamento, o aplicativo determina o ID de instância de atividade atualmente em execução e mapear-lo de volta para o arquivo XAML que o criou uma instância. O designer rehosted de fluxo de trabalho é instruído para realçar a atividade na superfície do designer e usar o mesmo método que o depurador de fluxo de trabalho, desenhando especificamente uma borda amarela em torno de atividade e exibindo uma seta amarela ao longo do lado esquerdo do designer.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Abra o arquivo de WorkflowSimulator.sln do diretório de exemplo em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Pressione CTRL+SHIFT+B para criar a solução.  
  
3.  O pressionar o CTRL + F5 para executar o exemplo. Isso exibe o arquivo de Workflow.xaml em uma janela rehosted de designer de fluxo de trabalho.  
  
4.  Clique o **arquivo** menu e selecione **executar o fluxo de trabalho...** .  
  
5.  Observe que a atividade atualmente executando realçada como descrito anteriormente e os registros de rastreamento são exibidos no lado direito da janela do aplicativo.  
  
6.  Quando o fluxo de trabalho concluído, você pode clicar em alguns dos registros de rastreamento verificar que a atividade ele corresponde.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\VisualWorkflowTracking`