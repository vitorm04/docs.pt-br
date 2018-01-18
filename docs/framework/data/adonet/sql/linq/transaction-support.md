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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 543ea3d1a0f767a10b36e040155e7e9304aca5a9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="transaction-support"></a><span data-ttu-id="a96ef-102">Suporte a transações</span><span class="sxs-lookup"><span data-stu-id="a96ef-102">Transaction Support</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="a96ef-103">dá suporte a três modelos de transação distinta.</span><span class="sxs-lookup"><span data-stu-id="a96ef-103"> supports three distinct transaction models.</span></span> <span data-ttu-id="a96ef-104">Veja a seguir esses modelos na ordem das verificações executadas.</span><span class="sxs-lookup"><span data-stu-id="a96ef-104">The following lists these models in the order of checks performed.</span></span>  
  
## <a name="explicit-local-transaction"></a><span data-ttu-id="a96ef-105">Transação local explícita</span><span class="sxs-lookup"><span data-stu-id="a96ef-105">Explicit Local Transaction</span></span>  
 <span data-ttu-id="a96ef-106">Quando o método <xref:System.Data.Linq.DataContext.SubmitChanges%2A> é chamado, se a propriedade <xref:System.Data.Linq.DataContext.Transaction%2A> estiver definida como uma transação (`IDbTransaction`), a chamada <xref:System.Data.Linq.DataContext.SubmitChanges%2A> será executada no contexto da mesma transação.</span><span class="sxs-lookup"><span data-stu-id="a96ef-106">When <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called, if the <xref:System.Data.Linq.DataContext.Transaction%2A> property is set to a (`IDbTransaction`) transaction, the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> call is executed in the context of the same transaction.</span></span>  
  
 <span data-ttu-id="a96ef-107">Cabe a você confirmar ou reverter a transação após sua execução bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="a96ef-107">It is your responsibility to commit or rollback the transaction after successful execution of the transaction.</span></span> <span data-ttu-id="a96ef-108">A conexão que corresponde à transação deve corresponder à conexão usada para construir a classe <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="a96ef-108">The connection corresponding to the transaction must match the connection used for constructing the <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="a96ef-109">Uma exceção será gerada se outra conexão for usada.</span><span class="sxs-lookup"><span data-stu-id="a96ef-109">An exception is thrown if a different connection is used.</span></span>  
  
## <a name="explicit-distributable-transaction"></a><span data-ttu-id="a96ef-110">Transação distribuível explícita</span><span class="sxs-lookup"><span data-stu-id="a96ef-110">Explicit Distributable Transaction</span></span>  
 <span data-ttu-id="a96ef-111">Você pode chamar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] APIs (incluindo, mas não limitado a <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) no escopo de um ativo <xref:System.Transactions.Transaction>.</span><span class="sxs-lookup"><span data-stu-id="a96ef-111">You can call [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] APIs (including but not limited to <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) in the scope of an active <xref:System.Transactions.Transaction>.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="a96ef-112">detecta que a chamada está no escopo de uma transação e não cria uma nova transação.</span><span class="sxs-lookup"><span data-stu-id="a96ef-112"> detects that the call is in the scope of a transaction and does not create a new transaction.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="a96ef-113">evita também fechando a conexão nesse caso.</span><span class="sxs-lookup"><span data-stu-id="a96ef-113"> also avoids closing the connection in this case.</span></span> <span data-ttu-id="a96ef-114">Você pode fazer a consulta e executar <xref:System.Data.Linq.DataContext.SubmitChanges%2A> no contexto de uma transação.</span><span class="sxs-lookup"><span data-stu-id="a96ef-114">You can perform query and <xref:System.Data.Linq.DataContext.SubmitChanges%2A> executions in the context of such a transaction.</span></span>  
  
## <a name="implicit-transaction"></a><span data-ttu-id="a96ef-115">Transação implícita</span><span class="sxs-lookup"><span data-stu-id="a96ef-115">Implicit Transaction</span></span>  
 <span data-ttu-id="a96ef-116">Quando você chama <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] verifica se a chamada está no escopo de um <xref:System.Transactions.Transaction> ou se o `Transaction` propriedade (`IDbTransaction`) é definido como uma transação local iniciado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="a96ef-116">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] checks to see whether the call is in the scope of a <xref:System.Transactions.Transaction> or if the `Transaction` property (`IDbTransaction`) is set to a user-started local transaction.</span></span> <span data-ttu-id="a96ef-117">Se ele encontrar nenhuma transação [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] inicia uma transação local (`IDbTransaction`) e o utiliza para executar os comandos SQL gerados.</span><span class="sxs-lookup"><span data-stu-id="a96ef-117">If it finds neither transaction, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] starts a local transaction (`IDbTransaction`) and uses it to execute the generated SQL commands.</span></span> <span data-ttu-id="a96ef-118">Quando todos os comandos SQL foi concluídos com êxito, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] confirma a transação local e retorna.</span><span class="sxs-lookup"><span data-stu-id="a96ef-118">When all SQL commands have been successfully completed, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] commits the local transaction and returns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a96ef-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a96ef-119">See Also</span></span>  
 [<span data-ttu-id="a96ef-120">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="a96ef-120">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="a96ef-121">Como delimitar submissões de dados entre colchetes usando transações</span><span class="sxs-lookup"><span data-stu-id="a96ef-121">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
