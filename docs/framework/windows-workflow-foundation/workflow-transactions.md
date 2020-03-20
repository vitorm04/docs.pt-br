---
title: Transações de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
ms.openlocfilehash: 223c18195c8ffd0b51eb5dff77aa81953f6e47a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182672"
---
# <a name="workflow-transactions"></a>Transações de fluxo de trabalho

[!INCLUDE[wf1](../../../includes/wf1-md.md)] fornece suporte para participar de transações de <xref:System.Transactions> usando a atividade de <xref:System.Activities.Statements.TransactionScope> para definir o escopo uma unidade transacionada de trabalho. Quando <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> deve ser explicitamente concluído chamadas de atividade de <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> implicitamente completos na transação em cima de conclusão com êxito. Todas as atividades que estão contidas em <xref:System.Activities.Statements.TransactionScope.Body%2A> de atividade de <xref:System.Activities.Statements.TransactionScope> participam na transação. WF pode passar transações em um fluxo de trabalho pelo uso de atividade de <xref:System.ServiceModel.Activities.TransactedReceiveScope> . Como a atividade de <xref:System.Activities.Statements.TransactionScope> , quaisquer atividades contida em <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> participa na transação. WF garante que as atividades dependentes em <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> para trabalhar com <xref:System.Activities.Statements.TransactionScope> e <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Se o sistema forneceu as atividades não endereçam todos os requisitos, as atividades personalizados podem ser criadas usando <xref:System.Activities.RuntimeTransactionHandle> para habilitar cenários avançados do controle de fluxo e de transação.  
  
No exemplo a seguir, um fluxo de <xref:System.Activities.Statements.Sequence> trabalho é construído consistindo de uma atividade que contém atividades infantis, incluindo uma <xref:System.Activities.Statements.TransactionScope> atividade. As atividades de <xref:System.Activities.Statements.TransactionScope.Body%2A> de <xref:System.Activities.Statements.TransactionScope> executam sob a transação inicializada pela atividade de <xref:System.Activities.Statements.TransactionScope> .  
  
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
  
Para obter mais informações, consulte sobre o uso, <xref:System.ServiceModel.Activities.TransactedReceiveScope>consulte [Transações fluídas dentro e fora dos Serviços de Fluxo de Trabalho](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Activities.Statements.TransactionScope>
- <xref:System.Transactions.TransactionScope>
- <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
