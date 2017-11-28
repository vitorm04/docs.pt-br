---
title: Gerenciamento de simultaneidade com DependentTransaction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b85a97d8-8e02-4555-95df-34c8af095148
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6cb0fa7f328b158613836e6ab20bd33545dc3a5d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="managing-concurrency-with-dependenttransaction"></a><span data-ttu-id="1c672-102">Gerenciamento de simultaneidade com DependentTransaction</span><span class="sxs-lookup"><span data-stu-id="1c672-102">Managing Concurrency with DependentTransaction</span></span>
<span data-ttu-id="1c672-103">O <xref:System.Transactions.Transaction> objeto é criado usando o <xref:System.Transactions.Transaction.DependentClone%2A> método.</span><span class="sxs-lookup"><span data-stu-id="1c672-103">The <xref:System.Transactions.Transaction> object is created using the <xref:System.Transactions.Transaction.DependentClone%2A> method.</span></span> <span data-ttu-id="1c672-104">Sua única finalidade é garantir que a transação não confirmada enquanto alguns outros trechos de código (por exemplo, um thread de trabalho) ainda estão executando o trabalho na transação.</span><span class="sxs-lookup"><span data-stu-id="1c672-104">Its sole purpose is to guarantee that the transaction cannot commit while some other pieces of code (for example, a worker thread) are still performing work on the transaction.</span></span> <span data-ttu-id="1c672-105">Quando o trabalho realizado dentro da transação clonada é concluído e pronto para ser confirmada, ele pode notificar o criador da transação usando o <xref:System.Transactions.DependentTransaction.Complete%2A> método.</span><span class="sxs-lookup"><span data-stu-id="1c672-105">When the work done within the cloned transaction is complete and ready to be committed, it can notify the creator of the transaction using the <xref:System.Transactions.DependentTransaction.Complete%2A> method.</span></span> <span data-ttu-id="1c672-106">Portanto, você pode preservar a consistência e correção dos dados.</span><span class="sxs-lookup"><span data-stu-id="1c672-106">Thus, you can preserve the consistency and correctness of data.</span></span>  
  
 <span data-ttu-id="1c672-107">O <xref:System.Transactions.DependentTransaction> classe também pode ser usada para gerenciar a simultaneidade entre tarefas assíncronas.</span><span class="sxs-lookup"><span data-stu-id="1c672-107">The <xref:System.Transactions.DependentTransaction> class can also be used to manage concurrency between asynchronous tasks.</span></span> <span data-ttu-id="1c672-108">Nesse cenário, o pai pode continuar a executar qualquer código enquanto o clone dependente funciona em suas tarefas.</span><span class="sxs-lookup"><span data-stu-id="1c672-108">In this scenario, the parent can continue to execute any code while the dependent clone works on its own tasks.</span></span> <span data-ttu-id="1c672-109">Em outras palavras, a execução do pai não é bloqueada até que o dependente é concluída.</span><span class="sxs-lookup"><span data-stu-id="1c672-109">In other words, the parent's execution is not blocked until the dependent completes.</span></span>  
  
## <a name="creating-a-dependent-clone"></a><span data-ttu-id="1c672-110">Criando um Clone dependente</span><span class="sxs-lookup"><span data-stu-id="1c672-110">Creating a Dependent Clone</span></span>  
 <span data-ttu-id="1c672-111">Para criar uma transação dependente, chame o <xref:System.Transactions.Transaction.DependentClone%2A> método e passar o <xref:System.Transactions.DependentCloneOption> enumeração como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1c672-111">To create a dependent transaction, call the <xref:System.Transactions.Transaction.DependentClone%2A> method and pass the <xref:System.Transactions.DependentCloneOption> enumeration as a parameter.</span></span> <span data-ttu-id="1c672-112">Esse parâmetro define o comportamento da transação se `Commit` é chamado na transação pai antes que o clone dependente indica que ele está pronto para a transação seja confirmada (chamando o <xref:System.Transactions.DependentTransaction.Complete%2A> método).</span><span class="sxs-lookup"><span data-stu-id="1c672-112">This parameter defines the behavior of the transaction if `Commit` is called on the parent transaction before the dependent clone indicates that it is ready for the transaction to commit (by calling the <xref:System.Transactions.DependentTransaction.Complete%2A> method).</span></span> <span data-ttu-id="1c672-113">Os seguintes valores são válidos para esse parâmetro:</span><span class="sxs-lookup"><span data-stu-id="1c672-113">The following values are valid for this parameter:</span></span>  
  
-   <span data-ttu-id="1c672-114"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>cria uma transação dependente que bloqueia o processo de confirmação da transação pai até os tempos de transação do pai, limite ou até <xref:System.Transactions.DependentTransaction.Complete%2A> é chamado em todos os dependentes indicando sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="1c672-114"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> creates a dependent transaction that blocks the commit process of the parent transaction until the parent transaction times out, or until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on all dependents indicating their completion.</span></span> <span data-ttu-id="1c672-115">Isso é útil quando o cliente não deseja que a transação do pai seja confirmada até que as transações dependentes sejam concluídas.</span><span class="sxs-lookup"><span data-stu-id="1c672-115">This is useful when the client does not want the parent transaction to commit until the dependent transactions have completed.</span></span> <span data-ttu-id="1c672-116">Se o pai concluir seu trabalho antes que a transação dependente e chamadas <xref:System.Transactions.CommittableTransaction.Commit%2A> na transação, o processo de confirmação será bloqueado em um estado onde trabalho adicional pode ser feito na transação e novas inscrições podem ser criadas, até que todos os da chamada dependentes <xref:System.Transactions.DependentTransaction.Complete%2A>.</span><span class="sxs-lookup"><span data-stu-id="1c672-116">If the parent finishes its work earlier than the dependent transaction and calls <xref:System.Transactions.CommittableTransaction.Commit%2A> on the transaction, the commit process is blocked in a state where additional work can be done on the transaction and new enlistments can be created, until all of the dependents call <xref:System.Transactions.DependentTransaction.Complete%2A>.</span></span> <span data-ttu-id="1c672-117">Assim que todos eles concluiu seu trabalho e chame <xref:System.Transactions.DependentTransaction.Complete%2A>, inicia o processo de confirmação da transação.</span><span class="sxs-lookup"><span data-stu-id="1c672-117">As soon as all of them have finished their work and call <xref:System.Transactions.DependentTransaction.Complete%2A>, the commit process for the transaction begins.</span></span>  
  
-   <span data-ttu-id="1c672-118"><xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, por outro lado, cria uma transação dependente automaticamente será anulada se <xref:System.Transactions.CommittableTransaction.Commit%2A> é chamado na transação pai antes de <xref:System.Transactions.DependentTransaction.Complete%2A> é chamado.</span><span class="sxs-lookup"><span data-stu-id="1c672-118"><xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, on the other hand, creates a dependent transaction that automatically aborts if <xref:System.Transactions.CommittableTransaction.Commit%2A> is called on the parent transaction before <xref:System.Transactions.DependentTransaction.Complete%2A> is called.</span></span> <span data-ttu-id="1c672-119">Nesse caso, todo o trabalho feito na transação dependente está intacto no tempo de vida de uma transação e não tem a oportunidade de confirmar apenas uma parte dele.</span><span class="sxs-lookup"><span data-stu-id="1c672-119">In this case, all the work done in the dependent transaction is intact within one transaction lifetime, and no one has a chance to commit just a portion of it.</span></span>  
  
 <span data-ttu-id="1c672-120">O <xref:System.Transactions.DependentTransaction.Complete%2A> método deve ser chamado apenas uma vez quando seu aplicativo termina seu trabalho na transação dependente; Caso contrário, um <xref:System.InvalidOperationException> é lançada.</span><span class="sxs-lookup"><span data-stu-id="1c672-120">The <xref:System.Transactions.DependentTransaction.Complete%2A> method must be called only once when your application finishes its work on the dependent transaction; otherwise, a <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="1c672-121">Depois que essa chamada é invocada, você não deve tentar qualquer trabalho adicional na transação ou uma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="1c672-121">After this call is invoked, you must not attempt any additional work on the transaction, or an exception is thrown.</span></span>  
  
 <span data-ttu-id="1c672-122">O exemplo de código a seguir mostra como criar uma transação dependente para gerenciar duas tarefas simultâneas por uma transação dependente de clonagem e passá-la para um thread de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1c672-122">The following code example shows how to create a dependent transaction to manage two concurrent tasks by cloning a dependent transaction and passing it to a worker thread.</span></span>  
  
```csharp  
public class WorkerThread  
{  
    public void DoWork(DependentTransaction dependentTransaction)  
    {  
        Thread thread = new Thread(ThreadMethod);  
        thread.Start(dependentTransaction);   
    }  
  
    public void ThreadMethod(object transaction)   
    {   
        DependentTransaction dependentTransaction = transaction as DependentTransaction;  
        Debug.Assert(dependentTransaction != null);   
        try  
        {  
            using(TransactionScope ts = new TransactionScope(dependentTransaction))  
            {  
                /* Perform transactional work here */   
                ts.Complete();  
            }  
        }  
        finally  
        {  
            dependentTransaction.Complete();   
             dependentTransaction.Dispose();   
        }  
    }  
  
//Client code   
using(TransactionScope scope = new TransactionScope())  
{  
    Transaction currentTransaction = Transaction.Current;  
    DependentTransaction dependentTransaction;      
    dependentTransaction = currentTransaction.DependentClone(DependentCloneOption.BlockCommitUntilComplete);  
    WorkerThread workerThread = new WorkerThread();  
    workerThread.DoWork(dependentTransaction);  
    /* Do some transactional work here, then: */  
    scope.Complete();  
}  
```  
  
 <span data-ttu-id="1c672-123">O código do cliente cria um escopo transacional que também define a transação de ambiente.</span><span class="sxs-lookup"><span data-stu-id="1c672-123">The client code creates a transactional scope that also sets the ambient transaction.</span></span> <span data-ttu-id="1c672-124">Você não deve passar a transação de ambiente para o thread de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1c672-124">You should not pass the ambient transaction to the worker thread.</span></span> <span data-ttu-id="1c672-125">Em vez disso, você deve clonar a transação (ambiente) atual chamando o <xref:System.Transactions.Transaction.DependentClone%2A> método na transação atual e passe o dependente para o thread de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1c672-125">Instead, you should clone the current (ambient) transaction by calling the <xref:System.Transactions.Transaction.DependentClone%2A> method on the current transaction, and pass the dependent to the worker thread.</span></span>  
  
 <span data-ttu-id="1c672-126">O `ThreadMethod` método é executado no novo segmento.</span><span class="sxs-lookup"><span data-stu-id="1c672-126">The `ThreadMethod` method executes on the new thread.</span></span> <span data-ttu-id="1c672-127">O cliente inicia um novo thread, passando a transação dependente como o `ThreadMethod` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1c672-127">The client starts a new thread, passing the dependent transaction as the `ThreadMethod` parameter.</span></span>  
  
 <span data-ttu-id="1c672-128">Como a transação dependente é criada com <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, terá a garantia de que a transação não pode ser confirmada até que todos os do trabalho transacional feito no segundo thread é concluído e <xref:System.Transactions.DependentTransaction.Complete%2A> é chamado na transação dependente.</span><span class="sxs-lookup"><span data-stu-id="1c672-128">Because the dependent transaction is created with <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, you are guaranteed that the transaction cannot be committed until all of the transactional work done on the second thread is finished and <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent transaction.</span></span> <span data-ttu-id="1c672-129">Isso significa que, se o escopo do cliente termina (quando ele tenta descartar o objeto de transação no final de **usando** instrução) antes da chamada de thread novo <xref:System.Transactions.DependentTransaction.Complete%2A> na transação dependente, o código do cliente bloqueia até <xref:System.Transactions.DependentTransaction.Complete%2A> é chamado em dependente.</span><span class="sxs-lookup"><span data-stu-id="1c672-129">This means that if the client's scope ends (when it tries to dispose of the transaction object at the end of the **using** statement) before the new thread calls <xref:System.Transactions.DependentTransaction.Complete%2A> on the dependent transaction, the client code blocks until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent.</span></span> <span data-ttu-id="1c672-130">Em seguida, a transação pode concluir a confirmação ou anulação.</span><span class="sxs-lookup"><span data-stu-id="1c672-130">Then the transaction can finish committing or aborting.</span></span>  
  
## <a name="concurrency-issues"></a><span data-ttu-id="1c672-131">Problemas de simultaneidade</span><span class="sxs-lookup"><span data-stu-id="1c672-131">Concurrency Issues</span></span>  
 <span data-ttu-id="1c672-132">Existem alguns problemas de simultaneidade adicionais que precisam ser consideradas ao usar o <xref:System.Transactions.DependentTransaction> classe:</span><span class="sxs-lookup"><span data-stu-id="1c672-132">There are a few additional concurrency issues that you need to be aware of when using the <xref:System.Transactions.DependentTransaction> class:</span></span>  
  
-   <span data-ttu-id="1c672-133">Se o thread de trabalho reverte a transação, mas o pai tenta confirmar, um <xref:System.Transactions.TransactionAbortedException> é lançada.</span><span class="sxs-lookup"><span data-stu-id="1c672-133">If the worker thread rolls back the transaction but the parent tries to commit it, a <xref:System.Transactions.TransactionAbortedException> is thrown.</span></span>  
  
-   <span data-ttu-id="1c672-134">Você deve criar um novo clone dependente para cada thread de trabalho na transação.</span><span class="sxs-lookup"><span data-stu-id="1c672-134">You should create a new dependent clone for each worker thread in the transaction.</span></span> <span data-ttu-id="1c672-135">Não passam o mesmo clone dependente em vários threads, porque apenas um deles pode chamar <xref:System.Transactions.DependentTransaction.Complete%2A> nele.</span><span class="sxs-lookup"><span data-stu-id="1c672-135">Do not pass the same dependent clone to multiple threads, because only one of them can call <xref:System.Transactions.DependentTransaction.Complete%2A> on it.</span></span>  
  
-   <span data-ttu-id="1c672-136">Se o thread de trabalho gera um novo thread de trabalho, certifique-se de criar um clone dependente do clone dependente e passá-lo para o novo thread.</span><span class="sxs-lookup"><span data-stu-id="1c672-136">If the worker thread spawns a new worker thread, make sure to create a dependent clone from the dependent clone and pass it to the new thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c672-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c672-137">See Also</span></span>  
 <xref:System.Transactions.DependentTransaction>
