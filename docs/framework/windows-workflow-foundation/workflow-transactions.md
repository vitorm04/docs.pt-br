---
title: Transações de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
ms.openlocfilehash: 17e4b712f5b6955ab777168d60d8a28e8b0ebd63
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153290"
---
# <a name="workflow-transactions"></a><span data-ttu-id="172de-102">Transações de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="172de-102">Workflow Transactions</span></span>

[!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="172de-103">fornece suporte para participar de transações de <xref:System.Transactions> usando a atividade de <xref:System.Activities.Statements.TransactionScope> para definir o escopo uma unidade transacionada de trabalho.</span><span class="sxs-lookup"><span data-stu-id="172de-103">provides support for participating in <xref:System.Transactions> transactions by using the <xref:System.Activities.Statements.TransactionScope> activity to scope a transacted unit of work.</span></span> <span data-ttu-id="172de-104">Quando <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> deve ser explicitamente concluído chamadas de atividade de <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> implicitamente completos na transação em cima de conclusão com êxito.</span><span class="sxs-lookup"><span data-stu-id="172de-104">While the <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> must be explicitly completed the <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> activity implicitly calls complete on the transaction upon successful completion.</span></span> <span data-ttu-id="172de-105">Todas as atividades que estão contidas em <xref:System.Activities.Statements.TransactionScope.Body%2A> de atividade de <xref:System.Activities.Statements.TransactionScope> participam na transação.</span><span class="sxs-lookup"><span data-stu-id="172de-105">Any activities that are contained in the <xref:System.Activities.Statements.TransactionScope.Body%2A> of the <xref:System.Activities.Statements.TransactionScope> activity participate in the transaction.</span></span> <span data-ttu-id="172de-106">WF pode passar transações em um fluxo de trabalho pelo uso de atividade de <xref:System.ServiceModel.Activities.TransactedReceiveScope> .</span><span class="sxs-lookup"><span data-stu-id="172de-106">WF can to flow transactions into a workflow through the use of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity.</span></span> <span data-ttu-id="172de-107">Como a atividade de <xref:System.Activities.Statements.TransactionScope> , quaisquer atividades contida em <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> participa na transação.</span><span class="sxs-lookup"><span data-stu-id="172de-107">Like the <xref:System.Activities.Statements.TransactionScope> activity, any activity contained in the <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> participates in the transaction.</span></span> <span data-ttu-id="172de-108">WF garante que as atividades dependentes em <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> para trabalhar com <xref:System.Activities.Statements.TransactionScope> e <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="172de-108">WF ensures that activities dependent on <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> works with both <xref:System.Activities.Statements.TransactionScope> and <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span> <span data-ttu-id="172de-109">Se o sistema forneceu as atividades não endereçam todos os requisitos, as atividades personalizados podem ser criadas usando <xref:System.Activities.RuntimeTransactionHandle> para habilitar cenários avançados do controle de fluxo e de transação.</span><span class="sxs-lookup"><span data-stu-id="172de-109">If the system-provided activities do not address all requirements, custom activities can be built using the <xref:System.Activities.RuntimeTransactionHandle> to enable advanced flow and transaction control scenarios.</span></span>  
  
<span data-ttu-id="172de-110">No exemplo a seguir, um fluxo de trabalho é construído que consiste uma <xref:System.Activities.Statements.Sequence> atividade que contém atividades filho incluindo um <xref:System.Activities.Statements.TransactionScope> atividade.</span><span class="sxs-lookup"><span data-stu-id="172de-110">In the following example, a workflow is constructed consisting of a <xref:System.Activities.Statements.Sequence> activity that contains child activities including a <xref:System.Activities.Statements.TransactionScope> activity.</span></span> <span data-ttu-id="172de-111">As atividades de <xref:System.Activities.Statements.TransactionScope.Body%2A> de <xref:System.Activities.Statements.TransactionScope> executam sob a transação inicializada pela atividade de <xref:System.Activities.Statements.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="172de-111">The <xref:System.Activities.Statements.TransactionScope.Body%2A> activities of the <xref:System.Activities.Statements.TransactionScope> execute under the transaction initialized by the <xref:System.Activities.Statements.TransactionScope> activity.</span></span>  
  
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
  
<span data-ttu-id="172de-112">Para obter mais informações, consulte sobre como usar <xref:System.ServiceModel.Activities.TransactedReceiveScope>, consulte [transações que fluem para dentro e fora dos serviços de fluxo de trabalho](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="172de-112">For more information, see about using <xref:System.ServiceModel.Activities.TransactedReceiveScope>, see [Flowing Transactions into and out of Workflow Services](../wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="172de-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="172de-113">See also</span></span>

- <xref:System.Activities.Statements.TransactionScope>
- <xref:System.Transactions.TransactionScope>
- <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>
