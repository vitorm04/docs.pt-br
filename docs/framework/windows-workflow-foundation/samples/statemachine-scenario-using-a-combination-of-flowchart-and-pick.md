---
title: Cenário de StateMachine usando uma combinação de fluxograma e de picareta
ms.date: 03/30/2017
ms.assetid: 88d81395-f7a3-41d8-8439-20a425c538a6
ms.openlocfilehash: b0f8e884a8a6c62c4e7edaf5cc9727bf7bfe8603
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485505"
---
# <a name="statemachine-scenario-using-a-combination-of-flowchart-and-pick"></a>Cenário de StateMachine usando uma combinação de fluxograma e de picareta
Este exemplo demonstra como implementar um cenário simples de cronômetro usando uma combinação de atividades de <xref:System.Activities.Statements.Flowchart> e de <xref:System.Activities.Statements.Pick> . Using receber e envia dentro de atividade de picareta para escutar eventos de cronômetro.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para (página de download) Baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 A tabela a seguir lista os projetos neste exemplo.  
  
|Nome do projeto|Descrição|  
|-|-|  
|StopWatchService|Este projeto contém a implementação de um computador de estado para o exemplo do cronômetro usando uma combinação de atividades de <xref:System.Activities.Statements.Flowchart> e de <xref:System.Activities.Statements.Pick> .<br /><br /> A atividade de <xref:System.Activities.Statements.Pick> tem 3 instruções de <xref:System.Activities.Statements.PickBranch> dentro de propriedade de <xref:System.Activities.Statements.Pick.Branches%2A> que escutam `GetStart`, `GetStop` e eventos de `GetOff` . Baseado no evento de entrada, disparadores para um dos ramificações ativam e <xref:System.Activities.Statements.PickBranch.Action%2A> correspondente é disparado. Em <xref:System.Activities.Statements.PickBranch.Action%2A> propriedade, é <xref:System.Activities.Statements.Switch%601> instrução que avalia se a transição é uma transição legítima e se estiver, a propriedade de `currentState` é atualizado para o estado fazer a transição e enviado ao cliente.<br /><br /> A atividade de <xref:System.Activities.Statements.FlowDecision> no final de <xref:System.Activities.Statements.Flowchart> avalia a propriedade de `currentState` para determinar se o estado é terminal. Se for, o fluxo de trabalho; termina se não controle de loop - voltar para o início da atividade de <xref:System.Activities.Statements.Pick> onde o fluxo de trabalho espera mais eventos do cronômetro.|  
|StopWatchClient|Este é um aplicativo de console sequencial simples de fluxo de trabalho que envia vários eventos do cronômetro com enviar simples ou recebe combinações de atividade.|  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], arquivo aberto de solução de StateMachineWithPick.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Iniciar o StopWatchService.exe da [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] como um administrador com o botão direito clicando no arquivo de .exe e selecionando **executar como administrador**.  
  
    1.  Navegue para o StateMachineWithPick CS StopWatchService \ \ \ bin \ debug.  
  
    2.  O arquivo StopWatchService.exe com o botão direito e selecione **executar como administrador**.  
  
4.  Inicie o aplicativo cliente de StopWatchClient de dentro de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    1.  Na **Gerenciador de soluções**, selecione o **StopWatchClient** do projeto e o botão direito do mouse **Set as StartUp Project**.  
  
    2.  Para executar a solução, pressione CTRL+F5.  
  
5.  Alternar de volta para a janela do console para que o StopWatchService.exe exibe o estado transições.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`