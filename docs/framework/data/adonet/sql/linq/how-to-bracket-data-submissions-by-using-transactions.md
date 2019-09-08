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
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a>Como: delimitar submissões de dados entre colchetes usando transações
Você pode usar <xref:System.Transactions.TransactionScope> para suportar suas submissões a base de dados. Para obter mais informações, consulte [suporte a transações](transaction-support.md).  
  
## <a name="example"></a>Exemplo  
 O código a seguir inclui o envio de base de dados em <xref:System.Transactions.TransactionScope>.  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- [Downloading Sample Databases](downloading-sample-databases.md) (Baixando bancos de dados de amostra)
- [Realizando e enviando alterações de dados](making-and-submitting-data-changes.md)
- [Suporte a transações](transaction-support.md)
