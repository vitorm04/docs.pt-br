---
title: 'Como: reutilizar uma conexão entre um comando ADO.NET e um DataContext'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: 89c9a12399d3d76487d1fdc2bd82aa037c167710
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197346"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a>Como: reutilizar uma conexão entre um comando ADO.NET e um DataContext

Como [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] o faz parte da família de tecnologias ADO.net e é baseado em serviços fornecidos pelo ADO.net, você pode reutilizar uma conexão entre um comando ADO.net e um <xref:System.Data.Linq.DataContext> .  
  
## <a name="example"></a>Exemplo  

 O exemplo a seguir mostra como reutilizar a mesma conexão entre um comando ADO.NET e o <xref:System.Data.Linq.DataContext> .  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Veja também

- [Informações gerais](background-information.md)
- [O ADO.NET e LINQ to SQL](ado-net-and-linq-to-sql.md)
- [Comunicação com o banco de dados](communicating-with-the-database.md)
