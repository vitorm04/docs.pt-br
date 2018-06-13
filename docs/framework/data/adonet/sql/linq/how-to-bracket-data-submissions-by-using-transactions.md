---
title: 'Como: Submissões de dados colchete usando transações'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: aa77d364d1ee4efc09386dd7e889914aeb2f3f26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361521"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a><span data-ttu-id="1da7f-102">Como: Submissões de dados colchete usando transações</span><span class="sxs-lookup"><span data-stu-id="1da7f-102">How to: Bracket Data Submissions by Using Transactions</span></span>
<span data-ttu-id="1da7f-103">Você pode usar <xref:System.Transactions.TransactionScope> para suportar suas submissões a base de dados.</span><span class="sxs-lookup"><span data-stu-id="1da7f-103">You can use <xref:System.Transactions.TransactionScope> to bracket your submissions to the database.</span></span> <span data-ttu-id="1da7f-104">Para obter mais informações, consulte [suporte a transações](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="1da7f-104">For more information, see [Transaction Support](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1da7f-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1da7f-105">Example</span></span>  
 <span data-ttu-id="1da7f-106">O código a seguir inclui o envio de base de dados em <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="1da7f-106">The following code encloses the database submission in a <xref:System.Transactions.TransactionScope>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="1da7f-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1da7f-107">See Also</span></span>  
 <span data-ttu-id="1da7f-108">[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md) (Baixando bancos de dados de amostra)</span><span class="sxs-lookup"><span data-stu-id="1da7f-108">[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)</span></span>  
 [<span data-ttu-id="1da7f-109">Realizando e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="1da7f-109">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [<span data-ttu-id="1da7f-110">Suporte a transações</span><span class="sxs-lookup"><span data-stu-id="1da7f-110">Transaction Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)
