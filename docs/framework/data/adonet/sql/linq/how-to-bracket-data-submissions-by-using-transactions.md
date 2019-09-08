---
title: 'Como: delimitar submissões de dados entre colchetes usando transações'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: 6a4c5ba7c4938b48fe489e43ff4a3ff806bd8916
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793809"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a><span data-ttu-id="fe66d-102">Como: delimitar submissões de dados entre colchetes usando transações</span><span class="sxs-lookup"><span data-stu-id="fe66d-102">How to: Bracket Data Submissions by Using Transactions</span></span>
<span data-ttu-id="fe66d-103">Você pode usar <xref:System.Transactions.TransactionScope> para suportar suas submissões a base de dados.</span><span class="sxs-lookup"><span data-stu-id="fe66d-103">You can use <xref:System.Transactions.TransactionScope> to bracket your submissions to the database.</span></span> <span data-ttu-id="fe66d-104">Para obter mais informações, consulte [suporte a transações](transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="fe66d-104">For more information, see [Transaction Support](transaction-support.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe66d-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fe66d-105">Example</span></span>  
 <span data-ttu-id="fe66d-106">O código a seguir inclui o envio de base de dados em <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="fe66d-106">The following code encloses the database submission in a <xref:System.Transactions.TransactionScope>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="fe66d-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe66d-107">See also</span></span>

- <span data-ttu-id="fe66d-108">[Downloading Sample Databases](downloading-sample-databases.md) (Baixando bancos de dados de amostra)</span><span class="sxs-lookup"><span data-stu-id="fe66d-108">[Downloading Sample Databases](downloading-sample-databases.md)</span></span>
- [<span data-ttu-id="fe66d-109">Realizando e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="fe66d-109">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="fe66d-110">Suporte a transações</span><span class="sxs-lookup"><span data-stu-id="fe66d-110">Transaction Support</span></span>](transaction-support.md)
