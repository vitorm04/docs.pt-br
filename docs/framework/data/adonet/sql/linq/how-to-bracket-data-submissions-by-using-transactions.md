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
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a>Como: delimitar submissões de dados entre colchetes usando transações

Você pode usar <xref:System.Transactions.TransactionScope> para suportar suas submissões a base de dados. Para obter mais informações, consulte [suporte a transações](transaction-support.md).  
  
## <a name="example"></a>Exemplo  

 O código a seguir inclui o envio de base de dados em <xref:System.Transactions.TransactionScope>.  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Confira também

- [Baixar bancos de dados de amostra](downloading-sample-databases.md)
- [Fazendo e enviando alterações de dados](making-and-submitting-data-changes.md)
- [Suporte a transações](transaction-support.md)
