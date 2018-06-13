---
title: TransactionScope básico
ms.date: 03/30/2017
ms.assetid: 1e22b76a-76de-43b4-9be7-7a86ed3d5a44
ms.openlocfilehash: fe6877c4b2d72dc3d571740395fd4dc92ca8e99c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516793"
---
# <a name="basic-transactionscope"></a>TransactionScope básico
Esse exemplo consiste em quatro cenários que executam a visualização como aninhar instâncias de <xref:System.Activities.Statements.TransactionScope> . O primeiro cenário mostra aninhar uma atividade de terceiro parte do autor não tem nenhum conhecimento de compilação. O segundo e terceiro cenários mostram como os intervalos são respeitados e mostra finais cenário de configuração de <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> .  
  
## <a name="nesting-of-transactionscopeactivity"></a>Aninhamento de TransactionScopeActivity  
 O fluxo de trabalho para o primeiro cenário consiste em uma sequência de duas atividades de <xref:System.Activities.Statements.WriteLine> e de <xref:System.Activities.Statements.TransactionScope>. O corpo de <xref:System.Activities.Statements.TransactionScope> é uma sequência de duas mais atividades de <xref:System.Activities.Statements.WriteLine> , uma atividade personalizado que imprimir o identificador local de transação e uma atividade de terceiros. A atividade `TransactionScopeTest` de terceiros contém <xref:System.Activities.Statements.TransactionScope> embora o autor de fluxo de trabalho não tem nenhuma maneira de aprender. Este cenário que mostra as atividades de <xref:System.Activities.Statements.TransactionScope> podem ser aninhadas.  
  
## <a name="time-outs"></a>Intervalos  
 O fluxo de trabalho para o segundo cenário é quase idêntico ao primeiro. `TransactionScopeTest` foi substituído por <xref:System.Activities.Statements.TransactionScope>. O corpo de <xref:System.Activities.Statements.TransactionScope> é um cinco atraso e o tempo limite para a transação é definido como dois segundos. O tempo limite para <xref:System.Activities.Statements.TransactionScope> externo é definido como 10 segundos. Observe que o tempo limite no menor escopo é respeitado e o tempo limite de transação.  
  
 O fluxo de trabalho para o terceiro cenário é quase idêntico ao cenário dois. A atividade do atraso foi movido do corpo de <xref:System.Activities.Statements.TransactionScope> interno imediatamente após a ela na sequência que é o corpo de <xref:System.Activities.Statements.TransactionScope>externo. Transação do tempo limite mas ainda porque o segundo tempo limite de dois <xref:System.Activities.Statements.TransactionScope> interno não se aplica. O tempo limite de transação em 10 segundos em que o tempo limite externa de <xref:System.Activities.Statements.TransactionScope> é excedido.  
  
## <a name="aborting-on-transaction-failure"></a>Nula na falha de transação  
 Este fluxo de trabalho é semelhante ao cenário três a não ser que os intervalos são substituídos pela propriedade de <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> . Observe que os sinalizadores de todos os filhos internos, se definido, devem corresponder <xref:System.Activities.Statements.TransactionScope>externo. Nesse cenário, não fazem e uma exceção é lançada quando o fluxo de trabalho abre.  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Abra a solução de BasicTransactionScopeSample.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Para criar a solução, pressione CTRL + SHIFT + B ou selecione **compilar solução** do **criar** menu.  
  
3.  Depois que a compilação foi bem-sucedida, pressione F5 ou selecione **iniciar depuração** do **depurar** menu. Como alternativa, você pode pressionar CTRL + F5 ou selecionar **Start Without Debugging** do **depurar** menu para executar sem depuração.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\BasicTransactionScope`