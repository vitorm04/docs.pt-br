---
title: "Reversão de transação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f377147-7529-4689-a588-608cee87fdf8
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aaebbb7fa2e6e0420243c32cb70c64092ea86fa7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="transaction-rollback"></a><span data-ttu-id="ecce6-102">Reversão de transação</span><span class="sxs-lookup"><span data-stu-id="ecce6-102">Transaction Rollback</span></span>
<span data-ttu-id="ecce6-103">Este exemplo mostra como criar um personalizado <xref:System.Activities.NativeActivity> que acessa <xref:System.Activities.RuntimeTransactionHandle> ambiente para obter a transação e ambiente para rolar explicitamente novamente.</span><span class="sxs-lookup"><span data-stu-id="ecce6-103">This sample shows how to create a custom <xref:System.Activities.NativeActivity> that accesses the ambient <xref:System.Activities.RuntimeTransactionHandle> to get the ambient transaction and explicitly roll it back.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="ecce6-104">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="ecce6-104">Sample Details</span></span>  
 <span data-ttu-id="ecce6-105">No fluxo de trabalho, uma transação é concluída automaticamente quando <xref:System.Activities.Statements.TransactionScope> mais externo ou <xref:System.ServiceModel.Activities.TransactedReceiveScope> concluírem.</span><span class="sxs-lookup"><span data-stu-id="ecce6-105">In workflow, a transaction is automatically completed when the outermost <xref:System.Activities.Statements.TransactionScope> or <xref:System.ServiceModel.Activities.TransactedReceiveScope> completes.</span></span>  <span data-ttu-id="ecce6-106">Uma transação reverte implicitamente quando se propaga de uma exceção sem tratamento pelo limite de escopo.</span><span class="sxs-lookup"><span data-stu-id="ecce6-106">A transaction implicitly rolls back when an unhandled exception propagates across the scope boundary.</span></span> <span data-ttu-id="ecce6-107">No entanto, pode haver ocasiões em que faz sentido reverter explicitamente uma transação sem ter que acionar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="ecce6-107">However, there may be times when it makes sense to explicitly roll back a transaction without having to throw an exception.</span></span> <span data-ttu-id="ecce6-108">Nesse caso, você pode usar a atividade personalizado de reversão como essa nesse exemplo para nulo a transação ambiente e fornecer explicitamente uma razão opcional de exceção.</span><span class="sxs-lookup"><span data-stu-id="ecce6-108">In this case, you can use the custom rollback activity like the one in this sample to explicitly abort the ambient transaction and provide an optional exception reason.</span></span>  
  
 <span data-ttu-id="ecce6-109">`RollbackActivity` é <xref:System.Activities.NativeActivity> porque requer acesso às propriedades de execução obter <xref:System.Activities.RuntimeTransactionHandle>ambiente.</span><span class="sxs-lookup"><span data-stu-id="ecce6-109">The `RollbackActivity` is a <xref:System.Activities.NativeActivity> as it requires access to the execution properties to get the ambient <xref:System.Activities.RuntimeTransactionHandle>.</span></span> <span data-ttu-id="ecce6-110">No método de `Execute` , obtém <xref:System.Activities.RuntimeTransactionHandle> e verifique se é `null`, que indica que a atividade foi usada sem uma transação ambiente de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ecce6-110">In the `Execute` method, it obtains the <xref:System.Activities.RuntimeTransactionHandle> and checks whether it is `null`, which indicates that the activity was used without an ambient run-time transaction.</span></span> <span data-ttu-id="ecce6-111">Obtém a transação, verificando novamente se `null` presente.</span><span class="sxs-lookup"><span data-stu-id="ecce6-111">It then obtains the transaction, again checking whether `null` is present.</span></span> <span data-ttu-id="ecce6-112">É possível ter <xref:System.Activities.RuntimeTransactionHandle> ambiente sem nunca inicializar uma transação de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ecce6-112">It is possible to have an ambient <xref:System.Activities.RuntimeTransactionHandle> without ever initializing a run-time transaction.</span></span> <span data-ttu-id="ecce6-113">Finalmente anula a transação chamando <xref:System.Transactions.Transaction.Rollback%2A> e especificar ou de forneceu a exceção ou uma exceção genérico que indica que a atividade mudou a transação.</span><span class="sxs-lookup"><span data-stu-id="ecce6-113">Finally it aborts the transaction by calling <xref:System.Transactions.Transaction.Rollback%2A> and specifying either a user-provided exception or a generic exception that states that the activity rolled back the transaction.</span></span>  
  
 <span data-ttu-id="ecce6-114">O fluxo de trabalho de demonstração consiste em <xref:System.Activities.Statements.TransactionScope> cujo corpo imprime o status de transação antes e após `RollbackActivity` executa.</span><span class="sxs-lookup"><span data-stu-id="ecce6-114">The demonstration workflow consists of a <xref:System.Activities.Statements.TransactionScope> whose body prints the transaction status before and after the `RollbackActivity` executes.</span></span> <span data-ttu-id="ecce6-115">Observe que embora a transação é revertida, <xref:System.Activities.Statements.TransactionScope> executa a conclusão e não anula o fluxo de trabalho até que o corpo terminar.</span><span class="sxs-lookup"><span data-stu-id="ecce6-115">Note that even though the transaction has been rolled back, the <xref:System.Activities.Statements.TransactionScope> executes to completion and does not abort the workflow until the body completes.</span></span> <span data-ttu-id="ecce6-116">O fluxo de trabalho é anuladas porque a propriedade de <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> tem como padrão a `true`.</span><span class="sxs-lookup"><span data-stu-id="ecce6-116">The workflow is aborted because the <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> property defaults to `true`.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="ecce6-117">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="ecce6-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="ecce6-118">Carregar a solução de TransactionRollback.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ecce6-118">Load the TransactionRollback.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="ecce6-119">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="ecce6-119">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="ecce6-120">Pressione CTRL+F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ecce6-120">Press CTRL+F5 to run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ecce6-121">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ecce6-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ecce6-122">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ecce6-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ecce6-123">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="ecce6-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ecce6-124">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ecce6-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactionRollback`  
  
## <a name="see-also"></a><span data-ttu-id="ecce6-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ecce6-125">See Also</span></span>  
 [<span data-ttu-id="ecce6-126">Transações</span><span class="sxs-lookup"><span data-stu-id="ecce6-126">Transactions</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)
