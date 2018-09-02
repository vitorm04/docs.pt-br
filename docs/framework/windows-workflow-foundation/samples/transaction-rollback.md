---
title: Reversão de transação
ms.date: 03/30/2017
ms.assetid: 7f377147-7529-4689-a588-608cee87fdf8
ms.openlocfilehash: 8134623248b072ec5a095ab9b10840e94a09243c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43464117"
---
# <a name="transaction-rollback"></a>Reversão de transação
Este exemplo mostra como criar um personalizado <xref:System.Activities.NativeActivity> que acessa <xref:System.Activities.RuntimeTransactionHandle> ambiente para obter a transação e ambiente para rolar explicitamente novamente.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 No fluxo de trabalho, uma transação é concluída automaticamente quando <xref:System.Activities.Statements.TransactionScope> mais externo ou <xref:System.ServiceModel.Activities.TransactedReceiveScope> concluírem.  Uma transação reverte implicitamente quando se propaga de uma exceção sem tratamento pelo limite de escopo. No entanto, pode haver ocasiões em que faz sentido reverter explicitamente uma transação sem ter que acionar uma exceção. Nesse caso, você pode usar a atividade personalizado de reversão como essa nesse exemplo para nulo a transação ambiente e fornecer explicitamente uma razão opcional de exceção.  
  
 `RollbackActivity` é <xref:System.Activities.NativeActivity> porque requer acesso às propriedades de execução obter <xref:System.Activities.RuntimeTransactionHandle>ambiente. No método de `Execute` , obtém <xref:System.Activities.RuntimeTransactionHandle> e verifique se é `null`, que indica que a atividade foi usada sem uma transação ambiente de tempo de execução. Obtém a transação, verificando novamente se `null` presente. É possível ter <xref:System.Activities.RuntimeTransactionHandle> ambiente sem nunca inicializar uma transação de tempo de execução. Finalmente anula a transação chamando <xref:System.Transactions.Transaction.Rollback%2A> e especificar ou de forneceu a exceção ou uma exceção genérico que indica que a atividade mudou a transação.  
  
 O fluxo de trabalho de demonstração consiste em <xref:System.Activities.Statements.TransactionScope> cujo corpo imprime o status de transação antes e após `RollbackActivity` executa. Observe que embora a transação é revertida, <xref:System.Activities.Statements.TransactionScope> executa a conclusão e não anula o fluxo de trabalho até que o corpo terminar. O fluxo de trabalho é anuladas porque a propriedade de <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> tem como padrão a `true`.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Carregar a solução de TransactionRollback.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Pressione CTRL+SHIFT+B para criar a solução.  
  
3.  Pressione CTRL+F5 para executar o aplicativo.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactionRollback`  
  
## <a name="see-also"></a>Consulte também  
 [Transações](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)
