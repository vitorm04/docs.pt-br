---
title: 'Como: Reutilizar uma Conexão entre um comando ADO.NET e um DataContext'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: 079b4b28a613ce6a9ae525514b89ea9e316a7c66
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54613669"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a>Como: Reutilizar uma Conexão entre um comando ADO.NET e um DataContext
Porque [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] é uma parte do [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] família de tecnologias e se baseia em serviços fornecidos pelo [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], você pode reutilizar uma conexão entre um [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] comando e um <xref:System.Data.Linq.DataContext>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como reutilizar a mesma conexão entre um comando de [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] e <xref:System.Data.Linq.DataContext>.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Consulte também
- [Informações gerais](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [ADO.NET e LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/ado-net-and-linq-to-sql.md)
- [Comunicação com o banco de dados](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
