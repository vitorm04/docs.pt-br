---
title: 'Como: delimitar submissões de dados entre colchetes usando transações'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: 4d3efedbf15be55fa7a9ab235f881f1c97758953
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161354"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a><span data-ttu-id="319c1-102">Como: delimitar submissões de dados entre colchetes usando transações</span><span class="sxs-lookup"><span data-stu-id="319c1-102">How to: Bracket Data Submissions by Using Transactions</span></span>

<span data-ttu-id="319c1-103">Você pode usar <xref:System.Transactions.TransactionScope> para suportar suas submissões a base de dados.</span><span class="sxs-lookup"><span data-stu-id="319c1-103">You can use <xref:System.Transactions.TransactionScope> to bracket your submissions to the database.</span></span> <span data-ttu-id="319c1-104">Para obter mais informações, consulte [suporte a transações](transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="319c1-104">For more information, see [Transaction Support](transaction-support.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="319c1-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="319c1-105">Example</span></span>  

 <span data-ttu-id="319c1-106">O código a seguir inclui o envio de base de dados em <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="319c1-106">The following code encloses the database submission in a <xref:System.Transactions.TransactionScope>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="319c1-107">Confira também</span><span class="sxs-lookup"><span data-stu-id="319c1-107">See also</span></span>

- [<span data-ttu-id="319c1-108">Baixar bancos de dados de amostra</span><span class="sxs-lookup"><span data-stu-id="319c1-108">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="319c1-109">Fazendo e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="319c1-109">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="319c1-110">Suporte a transações</span><span class="sxs-lookup"><span data-stu-id="319c1-110">Transaction Support</span></span>](transaction-support.md)
