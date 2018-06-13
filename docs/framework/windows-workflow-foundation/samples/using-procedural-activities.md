---
title: Usando atividades procedurais
ms.date: 03/30/2017
ms.assetid: 1c67f739-3878-48ad-806c-b2ce0d6733a0
ms.openlocfilehash: 787e61a989cb5769461f5155738520dea4609d1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516003"
---
# <a name="using-procedural-activities"></a>Usando atividades procedurais
O exemplo usa <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, e atividades de <xref:System.Activities.Statements.WriteLine> para implementar um jogo de estimativa. O jogo de estimativa seleciona um número aleatório e o jogador tem que descobrir esse número. Quando o jogador envia uma estimativa incorreta, o fluxo de trabalho fornece uma dica descobrir se maior ou menor. Se o jogador suponha o número em menos de 7 tentativas, as parabéns especiais são exibidas ao usuário.  
  
## <a name="custom-activities-in-this-sample"></a>Atividades personalizados nesse exemplo  
  
### <a name="readline"></a>ReadLine  
 Ler uma linha de texto de console. Esta atividade deriva da classe de <xref:System.Activities.NativeActivity> e cria-se um indexador que é que o aplicativo de console quando uma linha é lido.  
  
### <a name="promptint"></a>PromptInt  
 Solicita ao usuário digite um número e depois lê de uma janela de console. A atividade deriva de <xref:System.Activities.Activity%601> e usa as atividades de <xref:System.Activities.Statements.WriteLine> e de `ReadLine` .  
  
##### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de GuessingGame.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Procedurals`