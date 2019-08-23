---
title: 'Como: atualizar linhas no banco de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: 2819cd5d2533e8e289735c3df2b39df952968e66
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938727"
---
# <a name="how-to-update-rows-in-the-database"></a>Como: atualizar linhas no banco de dados
Você pode atualizar linhas em um banco de dados modificando valores de membro dos objetos associados [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> à coleção e, em seguida, enviando as alterações para o banco de dados. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]traduz as alterações nos comandos SQL `UPDATE` apropriados.  
  
> [!NOTE]
> Você pode substituir os métodos padrão do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para as operações de banco de dados `Insert`, `Update` e `Delete`. Para obter mais informações, consulte [Personalizando as operações de inserção, atualização e exclusão](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Os desenvolvedores que usam o Visual Studio podem usar o Object Relational Designer para desenvolver procedimentos armazenados para a mesma finalidade.  
  
 As etapas a seguir presumem que um <xref:System.Data.Linq.DataContext> válido conecta você ao banco de dados Northwind. Para obter mais informações, confira [Como: Conecte-se a](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)um banco de dados.  
  
### <a name="to-update-a-row-in-the-database"></a>Para atualizar uma linha no banco de dados  
  
1. Consulte a linha ser atualizada no banco de dados.  
  
2. Faça as alterações desejadas nos valores dos membros no objeto [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] resultante.  
  
3. Envie as alterações ao banco de dados.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir consulta a ordem #11000 no banco de dados e modifica os valores de `ShipName` e de `ShipVia` no objeto `Order` resultante. Finalmente, as alterações nesses valores membro são enviadas ao banco de dados como alterações nas colunas `ShipName` e `ShipVia`.  
  
 [!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- [Como: Gerenciar conflitos de alterações](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Como: Atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Realizando e enviando alterações de dados](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
