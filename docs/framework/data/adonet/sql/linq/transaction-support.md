---
title: "Suporte a transações"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7c1d438a83f090795a158ade1dfdbb7d2b2df863
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="transaction-support"></a><span data-ttu-id="9e375-102">Suporte a transações</span><span class="sxs-lookup"><span data-stu-id="9e375-102">Transaction Support</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="9e375-103">dá suporte a três modelos de transação distinta.</span><span class="sxs-lookup"><span data-stu-id="9e375-103"> supports three distinct transaction models.</span></span> <span data-ttu-id="9e375-104">Veja a seguir esses modelos na ordem das verificações executadas.</span><span class="sxs-lookup"><span data-stu-id="9e375-104">The following lists these models in the order of checks performed.</span></span>  
  
## <a name="explicit-local-transaction"></a><span data-ttu-id="9e375-105">Transação local explícita</span><span class="sxs-lookup"><span data-stu-id="9e375-105">Explicit Local Transaction</span></span>  
 <span data-ttu-id="9e375-106">Quando o método <xref:System.Data.Linq.DataContext.SubmitChanges%2A> é chamado, se a propriedade <xref:System.Data.Linq.DataContext.Transaction%2A> estiver definida como uma transação (`IDbTransaction`), a chamada <xref:System.Data.Linq.DataContext.SubmitChanges%2A> será executada no contexto da mesma transação.</span><span class="sxs-lookup"><span data-stu-id="9e375-106">When <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called, if the <xref:System.Data.Linq.DataContext.Transaction%2A> property is set to a (`IDbTransaction`) transaction, the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> call is executed in the context of the same transaction.</span></span>  
  
 <span data-ttu-id="9e375-107">Cabe a você confirmar ou reverter a transação após sua execução bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="9e375-107">It is your responsibility to commit or rollback the transaction after successful execution of the transaction.</span></span> <span data-ttu-id="9e375-108">A conexão que corresponde à transação deve corresponder à conexão usada para construir a classe <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="9e375-108">The connection corresponding to the transaction must match the connection used for constructing the <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="9e375-109">Uma exceção será gerada se outra conexão for usada.</span><span class="sxs-lookup"><span data-stu-id="9e375-109">An exception is thrown if a different connection is used.</span></span>  
  
## <a name="explicit-distributable-transaction"></a><span data-ttu-id="9e375-110">Transação distribuível explícita</span><span class="sxs-lookup"><span data-stu-id="9e375-110">Explicit Distributable Transaction</span></span>  
 <span data-ttu-id="9e375-111">Você pode chamar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] APIs (incluindo, mas não limitado a <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) no escopo de um ativo <xref:System.Transactions.Transaction>.</span><span class="sxs-lookup"><span data-stu-id="9e375-111">You can call [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] APIs (including but not limited to <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) in the scope of an active <xref:System.Transactions.Transaction>.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="9e375-112">detecta que a chamada está no escopo de uma transação e não cria uma nova transação.</span><span class="sxs-lookup"><span data-stu-id="9e375-112"> detects that the call is in the scope of a transaction and does not create a new transaction.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="9e375-113">evita também fechando a conexão nesse caso.</span><span class="sxs-lookup"><span data-stu-id="9e375-113"> also avoids closing the connection in this case.</span></span> <span data-ttu-id="9e375-114">Você pode fazer a consulta e executar <xref:System.Data.Linq.DataContext.SubmitChanges%2A> no contexto de uma transação.</span><span class="sxs-lookup"><span data-stu-id="9e375-114">You can perform query and <xref:System.Data.Linq.DataContext.SubmitChanges%2A> executions in the context of such a transaction.</span></span>  
  
## <a name="implicit-transaction"></a><span data-ttu-id="9e375-115">Transação implícita</span><span class="sxs-lookup"><span data-stu-id="9e375-115">Implicit Transaction</span></span>  
 <span data-ttu-id="9e375-116">Quando você chama <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] verifica se a chamada está no escopo de um <xref:System.Transactions.Transaction> ou se o `Transaction` propriedade (`IDbTransaction`) é definido como uma transação local iniciado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="9e375-116">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] checks to see whether the call is in the scope of a <xref:System.Transactions.Transaction> or if the `Transaction` property (`IDbTransaction`) is set to a user-started local transaction.</span></span> <span data-ttu-id="9e375-117">Se ele encontrar nenhuma transação [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] inicia uma transação local (`IDbTransaction`) e o utiliza para executar os comandos SQL gerados.</span><span class="sxs-lookup"><span data-stu-id="9e375-117">If it finds neither transaction, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] starts a local transaction (`IDbTransaction`) and uses it to execute the generated SQL commands.</span></span> <span data-ttu-id="9e375-118">Quando todos os comandos SQL foi concluídos com êxito, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] confirma a transação local e retorna.</span><span class="sxs-lookup"><span data-stu-id="9e375-118">When all SQL commands have been successfully completed, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] commits the local transaction and returns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e375-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e375-119">See Also</span></span>  
 [<span data-ttu-id="9e375-120">Informações de plano de fundo</span><span class="sxs-lookup"><span data-stu-id="9e375-120">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="9e375-121">Como: submissões de dados colchete usando transações</span><span class="sxs-lookup"><span data-stu-id="9e375-121">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
