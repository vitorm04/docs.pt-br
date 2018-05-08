---
title: Executar um fluxo de trabalho em um TransactionScope obrigatório
ms.date: 03/30/2017
ms.assetid: bd0e8686-c1d0-4400-a541-da94ed03afc7
ms.openlocfilehash: 44efc13efaa45274068fb44cc154b515bd774a35
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="execute-a-workflow-in-an-imperative-transactionscope"></a>Executar um fluxo de trabalho em um TransactionScope obrigatório
Este exemplo mostra como executar um fluxo de trabalho usando <xref:System.Activities.WorkflowInvoker> em <xref:System.Transactions.Transaction> de código em c obrigatório.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 No código em c obrigatório, <xref:System.Transactions.TransactionScope> é usado para encapsular um conjunto de trabalho que executa sob a mesma transação. <xref:System.Transactions.TransactionScope> funciona criando uma transação ambiente e inicializando a propriedade de <xref:System.Transactions.Transaction.Current%2A> , que pode ser acessada por todo o trabalho que está sendo executado naquele segmento.  
  
 Para obter o comportamento equivalente no fluxo de trabalho, o tempo de execução tem que fazer o trabalho adicional de inicializar <xref:System.Transactions.Transaction.Current%2A> antes de executar cada atividade como um fluxo de trabalho não mantém afinidade de threads entre atividades. Com esse suporte em tempo de execução, o comportamento resultante é que a execução de um fluxo de trabalho com <xref:System.Activities.WorkflowInvoker> dentro de <xref:System.Transactions.TransactionScope>, todas as atividades são garantidas para ser executado no contexto de transação ambiente criada por <xref:System.Transactions.TransactionScope>.  
  
 Um fluxo de trabalho pode ter apenas uma única transação ambiente para cada instância de fluxo de trabalho; as transações aninhadas não estão disponíveis. Mesmo se o fluxo de trabalho contém uma atividade de <xref:System.Activities.Statements.TransactionScope> , isso não cria uma nova transação interna. Em vez disso, reutiliza a transação ambiente que foi criada fora de fluxo de trabalho.  
  
 O exemplo inicia novo <xref:System.Transactions.TransactionScope>, imprime o ID de transação e inicia um fluxo de trabalho usando <xref:System.Activities.WorkflowInvoker>. O fluxo de trabalho imprime o ID de transação novamente, mostrando que é a mesma transação, então executar <xref:System.Activities.Statements.TransactionScope>, então termina. <xref:System.Activities.WorkflowInvoker.Invoke%2A> chama <xref:System.Activities.WorkflowInvoker> é síncrona para que os blocos originais de segmento até o fluxo de trabalho terminar. Uma vez que o fluxo de trabalho estiver concluída, a transação está concluída e recursos são descartados.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de ImperativeTransactionSample.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\ImperativeTransaction`