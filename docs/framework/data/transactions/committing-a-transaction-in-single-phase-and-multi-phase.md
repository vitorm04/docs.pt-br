---
title: Confirmar uma transação de fase única e de várias fases
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
ms.openlocfilehash: 2abb9c13e9b0cb394546252e0e51e53c8ff9eefb
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206004"
---
# <a name="committing-a-transaction-in-single-phase-and-multi-phase"></a><span data-ttu-id="170ff-102">Confirmar uma transação de fase única e de várias fases</span><span class="sxs-lookup"><span data-stu-id="170ff-102">Committing a Transaction in Single-Phase and Multi-Phase</span></span>
<span data-ttu-id="170ff-103">Cada recurso usado em uma transação é gerenciado por um Gerenciador de recursos (RM), as ações são coordenadas por um Gerenciador de transações (TM).</span><span class="sxs-lookup"><span data-stu-id="170ff-103">Each resource used in a transaction is managed by a resource manager (RM), whose actions are coordinated by a transaction manager (TM).</span></span> <span data-ttu-id="170ff-104">A lista de [recursos como participantes em um](enlisting-resources-as-participants-in-a-transaction.md) tópico de transação discute como um recurso (ou vários recursos) pode ser inscrito em uma transação.</span><span class="sxs-lookup"><span data-stu-id="170ff-104">The [Enlisting Resources as Participants in a Transaction](enlisting-resources-as-participants-in-a-transaction.md) topic discusses how a resource (or multiple resources) can be enlisted in a transaction.</span></span> <span data-ttu-id="170ff-105">Este tópico discute como confirmação de transação pode ser coordenada entre recursos.</span><span class="sxs-lookup"><span data-stu-id="170ff-105">This topic discusses how transaction commitment can be coordinated among enlisted resources.</span></span>  
  
 <span data-ttu-id="170ff-106">No final da transação, o aplicativo solicita a transação seja confirmada ou revertida.</span><span class="sxs-lookup"><span data-stu-id="170ff-106">At the end of the transaction, the application requests the transaction to be either committed or rolled back.</span></span> <span data-ttu-id="170ff-107">O Gerenciador de transações deve eliminar riscos, como alguns gerenciadores de recursos de votação para confirmar quando outro votação para reverter a transação.</span><span class="sxs-lookup"><span data-stu-id="170ff-107">The transaction manager must eliminate risks like some resource managers voting to commit while others voting to roll back the transaction.</span></span>  
  
 <span data-ttu-id="170ff-108">Se a transação envolve mais de um recurso, você deve realizar uma confirmação de duas fases (2PC).</span><span class="sxs-lookup"><span data-stu-id="170ff-108">If your transaction involves more than one resource, you must perform a two-phase commit (2PC).</span></span> <span data-ttu-id="170ff-109">O protocolo de confirmação de duas fases (a fase de preparação e a fase de confirmação) garante que quando a transação termina, todas as alterações a todos os recursos são totalmente confirmadas ou revertidas completamente.</span><span class="sxs-lookup"><span data-stu-id="170ff-109">The two-phase commit protocol (the prepare phase and the commit phase) ensures that when the transaction ends, all changes to all resources are either totally committed or fully rolled back.</span></span> <span data-ttu-id="170ff-110">Todos os participantes, em seguida, são informados do resultado final.</span><span class="sxs-lookup"><span data-stu-id="170ff-110">All the participants are then informed of the final result.</span></span> <span data-ttu-id="170ff-111">Para obter uma discussão detalhada sobre o protocolo de confirmação de duas fases, consulte o livro *"processamento de transações: Conceitos e técnicas (Morgan Kaufmann Series em sistemas gerenciamento de dados) ISBN: 1558601902*"por Jim Gray.</span><span class="sxs-lookup"><span data-stu-id="170ff-111">For a detailed discussion of the two-phase commit protocol, please consult the book "*Transaction Processing : Concepts and Techniques (Morgan Kaufmann Series in Data Management Systems) ISBN:1558601902*" by Jim Gray.</span></span>  
  
 <span data-ttu-id="170ff-112">Você também pode otimizar o desempenho da transação que fazem parte do protocolo de confirmação de fase única.</span><span class="sxs-lookup"><span data-stu-id="170ff-112">You can also optimize your transaction's performance by taking part in the Single Phase Commit protocol.</span></span> <span data-ttu-id="170ff-113">Para obter mais informações, consulte [otimização usando confirmação de fase única e notificação de fase única de promoçãotable](optimization-spc-and-promotable-spn.md).</span><span class="sxs-lookup"><span data-stu-id="170ff-113">For more information, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](optimization-spc-and-promotable-spn.md).</span></span>  
  
 <span data-ttu-id="170ff-114">Se você apenas deseja ser informado do resultado da transação e não quiser participar de votação, você deve se registrar para o <xref:System.Transactions.Transaction.TransactionCompleted> eventos.</span><span class="sxs-lookup"><span data-stu-id="170ff-114">If you just want to be informed of a transaction's outcome, and do not want to participate in voting, you should register for the <xref:System.Transactions.Transaction.TransactionCompleted> event.</span></span>  
  
## <a name="two-phase-commit-2pc"></a><span data-ttu-id="170ff-115">Confirmação de duas fases (2PC)</span><span class="sxs-lookup"><span data-stu-id="170ff-115">Two-phase Commit (2PC)</span></span>  
 <span data-ttu-id="170ff-116">Na primeira fase da transação, o Gerenciador de transações consulta cada recurso para determinar se uma transação deve ser confirmada ou revertida.</span><span class="sxs-lookup"><span data-stu-id="170ff-116">In the first transaction phase, the transaction manager queries each resource to determine whether a transaction should be committed or rolled back.</span></span> <span data-ttu-id="170ff-117">A segunda fase da transação, o Gerenciador de transações informa cada recurso do resultado de suas consultas, permitindo que ele execute qualquer limpeza necessária.</span><span class="sxs-lookup"><span data-stu-id="170ff-117">In the second transaction phase, the transaction manager notifies each resource of the outcome of its queries, allowing it to perform any necessary cleanup.</span></span>  
  
 <span data-ttu-id="170ff-118">Para participar desse tipo de transação, um Gerenciador de recursos deve implementar o <xref:System.Transactions.IEnlistmentNotification> interface, que fornece métodos que são chamados pelo TM como notificações durante um 2PC.</span><span class="sxs-lookup"><span data-stu-id="170ff-118">To participate in this kind of transaction, a resource manager must implement the <xref:System.Transactions.IEnlistmentNotification> interface, which provides methods that are called by the TM as notifications during a 2PC.</span></span>  <span data-ttu-id="170ff-119">O exemplo a seguir mostra um exemplo dessa implementação.</span><span class="sxs-lookup"><span data-stu-id="170ff-119">The following sample shows an example of such implementation.</span></span>  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### <a name="prepare-phase-phase-1"></a><span data-ttu-id="170ff-120">Preparar fase (fase 1)</span><span class="sxs-lookup"><span data-stu-id="170ff-120">Prepare phase (Phase 1)</span></span>  
 <span data-ttu-id="170ff-121">Ao receber um <xref:System.Transactions.CommittableTransaction.Commit%2A> solicitação do aplicativo, o Gerenciador de transações começa a fase de preparação de todos os participantes inscrita chamando o <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> método em cada inscrito recurso, para obter um voto de cada recurso na transação.</span><span class="sxs-lookup"><span data-stu-id="170ff-121">Upon receiving a <xref:System.Transactions.CommittableTransaction.Commit%2A> request from the application, the transaction manager begins the Prepare phase of all the enlisted participants by calling the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method on each enlisted resource, in order to obtain each resource's vote on the transaction.</span></span>  
  
 <span data-ttu-id="170ff-122">O Gerenciador de recursos que implementa o <xref:System.Transactions.IEnlistmentNotification> primeiro deve implementar a interface a <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> método como mostra o seguinte exemplo simples.</span><span class="sxs-lookup"><span data-stu-id="170ff-122">Your resource manager that implements the <xref:System.Transactions.IEnlistmentNotification> interface should first implement the <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> method as the following simple example shows.</span></span>  
  
```csharp
public void Prepare(PreparingEnlistment preparingEnlistment)  
{  
     Console.WriteLine("Prepare notification received");  
     //Perform work  
  
     Console.Write("reply with prepared? [Y|N] ");  
     c = Console.ReadKey();  
     Console.WriteLine();  
  
     //If work finished correctly, reply with prepared  
     if ((c.KeyChar == 'Y') || (c.KeyChar == 'y'))  
     {  
          preparingEnlistment.Prepared();  
          break;  
     }  
  
     // otherwise, do a ForceRollback  
     else if ((c.KeyChar == 'N') || (c.KeyChar == 'n'))  
     {  
          preparingEnlistment.ForceRollback();  
          break;  
     }  
}  
```  
  
 <span data-ttu-id="170ff-123">Quando o Gerenciador de recursos duráveis recebe essa chamada, ele deverá registrar informações de recuperação da transação (disponível ao recuperar o <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> propriedade) e qualquer informação é necessária para concluir a transação de confirmação.</span><span class="sxs-lookup"><span data-stu-id="170ff-123">When the durable resource manager receives this call, it should log the transaction's recovery information (available by retrieving the <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> property) and whatever information is necessary to complete the transaction on commit.</span></span> <span data-ttu-id="170ff-124">Isso não precisa ser executada dentro do <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> método porque o Gerenciador de recursos pode fazer isso em um thread de trabalho.</span><span class="sxs-lookup"><span data-stu-id="170ff-124">This does not need to be performed within the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method because the RM can do this on a worker thread.</span></span>  
  
 <span data-ttu-id="170ff-125">Quando o RM terminou seu trabalho de preparação, devem votar para confirmar ou reverter chamando o <xref:System.Transactions.PreparingEnlistment.Prepared%2A> ou <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> método.</span><span class="sxs-lookup"><span data-stu-id="170ff-125">When the RM has finished its prepare work, it should vote to commit or roll back by calling the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> or <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> method.</span></span> <span data-ttu-id="170ff-126">Observe que o <xref:System.Transactions.PreparingEnlistment> classe herda um <xref:System.Transactions.Enlistment.Done%2A> método a partir de <xref:System.Transactions.Enlistment> classe.</span><span class="sxs-lookup"><span data-stu-id="170ff-126">Notice that the <xref:System.Transactions.PreparingEnlistment> class inherits a <xref:System.Transactions.Enlistment.Done%2A> method from the <xref:System.Transactions.Enlistment> class.</span></span> <span data-ttu-id="170ff-127">Se você chamar esse método no <xref:System.Transactions.PreparingEnlistment> o retorno de chamada durante a fase de preparação, ele informa o TM que é uma inscrição de somente leitura (ou seja, gerenciadores de recursos que pode ler, mas não é possível atualizar dados protegidos por transação) e o RM não recebe nenhuma notificação adicional do Gerenciador de transações sobre o resultado da transação na fase 2.</span><span class="sxs-lookup"><span data-stu-id="170ff-127">If you call this method on the <xref:System.Transactions.PreparingEnlistment> callback during the Prepare phase, it informs the TM that it is a Read-Only enlistment (that is, resource managers that can read but cannot update transaction-protected data) and the RM receives no further notifications from the transaction manager as to the outcome of the transaction in phase 2.</span></span>  
  
 <span data-ttu-id="170ff-128">O aplicativo é informado do compromisso bem-sucedida da transação depois que todos os gerenciadores de recursos votam <xref:System.Transactions.PreparingEnlistment.Prepared%2A>.</span><span class="sxs-lookup"><span data-stu-id="170ff-128">The application is told of the successful commitment of the transaction after all the resource managers vote <xref:System.Transactions.PreparingEnlistment.Prepared%2A>.</span></span>  
  
### <a name="commit-phase-phase-2"></a><span data-ttu-id="170ff-129">Confirmar fase (fase 2)</span><span class="sxs-lookup"><span data-stu-id="170ff-129">Commit phase (Phase 2)</span></span>  
 <span data-ttu-id="170ff-130">Na segunda fase da transação, se o Gerenciador de transações recebe bem-sucedida prepara de todos os gerenciadores de recursos (todos os gerenciadores de recursos invocado <xref:System.Transactions.PreparingEnlistment.Prepared%2A> no final da fase 1), ele invoca o <xref:System.Transactions.IEnlistmentNotification.Commit%2A> método para cada Gerenciador de recursos.</span><span class="sxs-lookup"><span data-stu-id="170ff-130">In the second phase of the transaction, if the transaction manager receives successful prepares from all the resource managers (all the resource managers have invoked <xref:System.Transactions.PreparingEnlistment.Prepared%2A> at the end of phase 1), it invokes the <xref:System.Transactions.IEnlistmentNotification.Commit%2A> method for each resource manager.</span></span> <span data-ttu-id="170ff-131">Os gerenciadores de recursos, faça as alterações durável e concluir a confirmação.</span><span class="sxs-lookup"><span data-stu-id="170ff-131">The resource managers can then make the changes durable and complete the commit.</span></span>  
  
 <span data-ttu-id="170ff-132">Se o Gerenciador de recursos relatou uma falha ao preparar na fase 1, o Gerenciador de transações invoca o <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> método para cada Gerenciador de recursos e indica a falha da confirmação ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="170ff-132">If any resource manager reported a failure to prepare in phase 1, the transaction manager invokes the <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> method for each resource manager and indicates the failure of the commit to the application.</span></span>  
  
 <span data-ttu-id="170ff-133">Assim, o Gerenciador de recursos deve implementar os métodos a seguir.</span><span class="sxs-lookup"><span data-stu-id="170ff-133">Thus, your resource manager should implement the following methods.</span></span>  
  
```csharp
public void Commit (Enlistment enlistment)  
{  
     // Do any work necessary when commit notification is received  
  
     // Declare done on the enlistment  
     enlistment.Done();  
}  
  
public void Rollback (Enlistment enlistment)  
{  
     // Do any work necessary when rollback notification is received  
  
     // Declare done on the enlistment    
     enlistment.Done();    
}  
```  
  
 <span data-ttu-id="170ff-134">O Gerenciador de recursos deve executar qualquer trabalho necessário para concluir a transação com base no tipo de notificação e informar o TM concluiu chamando <xref:System.Transactions.Enlistment.Done%2A> método o <xref:System.Transactions.Enlistment> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="170ff-134">The RM should perform any work necessary to finish the transaction based on the notification type, and inform the TM that it has finished by calling <xref:System.Transactions.Enlistment.Done%2A> method on the <xref:System.Transactions.Enlistment> parameter.</span></span> <span data-ttu-id="170ff-135">Esse trabalho pode ser feito em um thread de trabalho.</span><span class="sxs-lookup"><span data-stu-id="170ff-135">This work can be done on a worker thread.</span></span> <span data-ttu-id="170ff-136">Observe que as notificações de fase 2 podem acontecer embutido no mesmo thread que chamou o <xref:System.Transactions.PreparingEnlistment.Prepared%2A> método na fase 1.</span><span class="sxs-lookup"><span data-stu-id="170ff-136">Note that the phase 2 notifications can happen inline on the same thread that called the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> method in phase 1.</span></span> <span data-ttu-id="170ff-137">Assim, você não deve fazer qualquer trabalho após o <xref:System.Transactions.PreparingEnlistment.Prepared%2A> chamada (por exemplo, liberar bloqueios) que você esperaria ter concluído antes de receber as notificações de fase 2.</span><span class="sxs-lookup"><span data-stu-id="170ff-137">As such, you should not do any work after the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> call (for example, releasing locks) that you would expect to have completed before receiving the phase 2 notifications.</span></span>  
  
### <a name="implementing-indoubt"></a><span data-ttu-id="170ff-138">Implementando incertas</span><span class="sxs-lookup"><span data-stu-id="170ff-138">Implementing InDoubt</span></span>  
 <span data-ttu-id="170ff-139">Por fim, você deve implementar o <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> método para o Gerenciador de recursos volátil.</span><span class="sxs-lookup"><span data-stu-id="170ff-139">Finally, you should implement the <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> method for the volatile resource manager.</span></span> <span data-ttu-id="170ff-140">Esse método é chamado se o Gerenciador de transações perder o contato com um ou mais participantes, portanto, seu status é desconhecido.</span><span class="sxs-lookup"><span data-stu-id="170ff-140">This method is called if the transaction manager loses contact with one or more participants, so their status is unknown.</span></span> <span data-ttu-id="170ff-141">Se isso ocorrer, você deve registrar esse fato para que você possa investigar mais tarde se qualquer um dos participantes da transação foi deixado em um estado inconsistente.</span><span class="sxs-lookup"><span data-stu-id="170ff-141">If this occurs, you should log this fact so that you can investigate later whether any of the transaction participants has been left in an inconsistent state.</span></span>  
  
```csharp
public void InDoubt (Enlistment enlistment)  
{  
     // log this  
     enlistment.Done();  
}  
```  
  
## <a name="single-phase-commit-optimization"></a><span data-ttu-id="170ff-142">Otimização de confirmação de fase única</span><span class="sxs-lookup"><span data-stu-id="170ff-142">Single Phase Commit Optimization</span></span>  
 <span data-ttu-id="170ff-143">O protocolo de confirmação de fase única é mais eficiente em tempo de execução porque todas as atualizações são feitas sem qualquer coordenação explícita.</span><span class="sxs-lookup"><span data-stu-id="170ff-143">The Single Phase Commit protocol is more efficient at run time because all updates are done without any explicit coordination.</span></span> <span data-ttu-id="170ff-144">Para obter mais informações sobre esse protocolo, consulte [otimização usando confirmação de fase única e notificação de fase única de promoçãotable](optimization-spc-and-promotable-spn.md).</span><span class="sxs-lookup"><span data-stu-id="170ff-144">For more information on this protocol, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](optimization-spc-and-promotable-spn.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="170ff-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="170ff-145">See also</span></span>

- [<span data-ttu-id="170ff-146">Otimização usando confirmação de fase única e notificação de fase única promovível</span><span class="sxs-lookup"><span data-stu-id="170ff-146">Optimization using Single Phase Commit and Promotable Single Phase Notification</span></span>](optimization-spc-and-promotable-spn.md)
- [<span data-ttu-id="170ff-147">Inscrição de recursos como participantes em uma transação</span><span class="sxs-lookup"><span data-stu-id="170ff-147">Enlisting Resources as Participants in a Transaction</span></span>](enlisting-resources-as-participants-in-a-transaction.md)
