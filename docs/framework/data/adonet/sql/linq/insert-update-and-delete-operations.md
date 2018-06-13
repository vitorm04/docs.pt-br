---
title: Operações de inserção, atualização e exclusão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: 29d87ed22f987a09348cde446d2fd6b11a3c1528
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360498"
---
# <a name="insert-update-and-delete-operations"></a>Operações de inserção, atualização e exclusão
Você executa operações `Insert`, `Update` e `Delete` no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] adicionando, modificando e removendo objetos no seu modelo de objeto. Por padrão, o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converte suas ações para SQL e envia as alterações para o banco de dados.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oferece flexibilidade máxima ao manipular e persistência das alterações feitas aos objetos. Assim que os objetos de entidade estão disponíveis (ou recuperando-os por meio de uma consulta ou com a construção de um novo), você pode alterá-los como típico de objetos em seu aplicativo. Ou seja, você pode alterar seus valores, você pode adicioná-las às coleções e você poderá removê-los de suas coleções. O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] controla as alterações e está pronto para transmiti-las de volta para o banco de dados quando você chama <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não dá suporte ou reconhece as operações de exclusão em cascata. Se você quiser excluir uma linha em uma tabela que tem restrições em relação a ela, você deve definir o `ON DELETE CASCADE` regra na restrição de chave estrangeira no banco de dados ou usar seu próprio código primeiro excluir os objetos filho que impedem que o objeto pai que está sendo excluído. Caso contrário, uma exceção será gerada. Para obter mais informações, consulte [como: excluir linhas do banco de dados](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
 Os seguintes trechos usam as classes `Customer` e `Order` do banco de dados de exemplo Northwind. As definições de classe não são mostradas para abreviar.  
  
 [!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
 [!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]  
  
 Quando você chama <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automaticamente gera e executa comandos SQL de que ele deve passar suas alterações de volta para o banco de dados.  
  
> [!NOTE]
>  Você pode substituir esse comportamento usando sua própria lógica personalizada, geralmente usando um procedimento armazenado. Para obter mais informações, consulte [responsabilidades do desenvolvedor em Substituir padrão comportamento](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).  
>   
>  Os desenvolvedores usando o Visual Studio podem usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para desenvolver os procedimentos armazenados para essa finalidade.  
  
## <a name="see-also"></a>Consulte também  
 [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md) (Baixando bancos de dados de amostra)  
 [Personalizando as operações de inserção, atualização e exclusão](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
