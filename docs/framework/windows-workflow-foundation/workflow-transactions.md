---
title: Transações de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
ms.openlocfilehash: 2bb5f6498b365f3b773eea9a5adce1ec1158a289
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="workflow-transactions"></a>Transações de fluxo de trabalho
[!INCLUDE[wf1](../../../includes/wf1-md.md)] fornece suporte para participar de transações de <xref:System.Transactions> usando a atividade de <xref:System.Activities.Statements.TransactionScope> para definir o escopo uma unidade transacionada de trabalho. Quando <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> deve ser explicitamente concluído chamadas de atividade de <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> implicitamente completos na transação em cima de conclusão com êxito. Todas as atividades que estão contidas em <xref:System.Activities.Statements.TransactionScope.Body%2A> de atividade de <xref:System.Activities.Statements.TransactionScope> participam na transação. WF pode passar transações em um fluxo de trabalho pelo uso de atividade de <xref:System.ServiceModel.Activities.TransactedReceiveScope> . Como a atividade de <xref:System.Activities.Statements.TransactionScope> , quaisquer atividades contida em <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> participa na transação. WF garante que as atividades dependentes em <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> para trabalhar com <xref:System.Activities.Statements.TransactionScope> e <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Se o sistema forneceu as atividades não endereçam todos os requisitos, as atividades personalizados podem ser criadas usando <xref:System.Activities.RuntimeTransactionHandle> para habilitar cenários avançados do controle de fluxo e de transação.  
  
 No exemplo a seguir, retirado de [TransactionScope básico](../../../docs/framework/windows-workflow-foundation/samples/basic-transactionscope.md) exemplo, um fluxo de trabalho é construído consiste em uma <xref:System.Activities.Statements.Sequence> atividade que contém atividades filho incluindo um <xref:System.Activities.Statements.TransactionScope> atividade. As atividades de <xref:System.Activities.Statements.TransactionScope.Body%2A> de <xref:System.Activities.Statements.TransactionScope> executam sob a transação inicializada pela atividade de <xref:System.Activities.Statements.TransactionScope> .  
  
```csharp  
static Activity ScenarioOne()  
{  
    return new Sequence  
    {  
        Activities =  
        {  
            new WriteLine { Text = "    Begin workflow" },  
  
            new TransactionScope  
            {  
                Body = new Sequence  
                {  
                    Activities =   
                    {  
                        new WriteLine { Text = "    Begin TransactionScope" },  
  
                        new PrintTransactionId(),  
  
                        new TransactionScopeTest(),  
  
                        new WriteLine { Text = "    End TransactionScope" },  
                    },  
                },  
            },  
  
            new WriteLine { Text = "    End workflow" },  
        }  
    };  
}  
```  
  
 Para obter mais informações, consulte o basic [transações](../../../docs/framework/windows-workflow-foundation/samples/transactions.md) exemplos e o cenário com base em [transações](../../../docs/framework/windows-workflow-foundation/samples/transactions.md) exemplos. Para obter mais informações, consulte sobre como usar <xref:System.ServiceModel.Activities.TransactedReceiveScope>, consulte [transações que passam dentro e fora de serviços de fluxo de trabalho](../../../docs/framework/wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Activities.Statements.TransactionScope>  
 <xref:System.Transactions.TransactionScope>  
 <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
