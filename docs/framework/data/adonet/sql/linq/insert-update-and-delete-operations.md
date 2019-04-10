---
title: Operações de inserção, atualização e exclusão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: 6a25ea5fe80da1fed16f44fd3243ebea4d64069f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230663"
---
# <a name="insert-update-and-delete-operations"></a>Operações de inserção, atualização e exclusão
Você executa operações `Insert`, `Update` e `Delete` no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] adicionando, modificando e removendo objetos no seu modelo de objeto. Por padrão, o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converte suas ações para SQL e envia as alterações para o banco de dados.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oferece a máxima flexibilidade em manipular e persistir as alterações feitas aos seus objetos. Assim que os objetos de entidade estiverem disponíveis (Recuperando-os por meio de uma consulta ou construindo-os um novo), você pode alterá-los como objetos típicos em seu aplicativo. Ou seja, você pode alterar seus valores, você pode adicioná-los às coleções e você poderá removê-los de suas coleções. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Controla as alterações e está pronto para transmiti-los no banco de dados quando você chama <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não oferece suporte ou reconhece operações cascade-delete. Se você quiser excluir uma linha em uma tabela que tem restrições em relação a ela, você deve definir o `ON DELETE CASCADE` de regra na restrição de chave estrangeira no banco de dados, ou usar seu próprio código para primeiro excluir os objetos filho que impedem que o objeto pai seja excluído. Caso contrário, uma exceção será gerada. Para obter mais informações, confira [Como: Excluir linhas do banco de dados](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
 Os seguintes trechos usam as classes `Customer` e `Order` do banco de dados de exemplo Northwind. As definições de classe não são mostradas para abreviar.  
  
 [!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
 [!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]  
  
 Quando você chama <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automaticamente gera e executa comandos SQL de que ele deve passar suas alterações de volta para o banco de dados.  
  
> [!NOTE]
>  Você pode substituir esse comportamento usando sua própria lógica personalizada, geralmente usando um procedimento armazenado. Para obter mais informações, consulte [responsabilidades do desenvolvedor em Substituir padrão comportamento](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).  
>   
>  Os desenvolvedores usando o Visual Studio podem usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para desenvolver procedimentos armazenados para essa finalidade.  
  
## <a name="see-also"></a>Consulte também

- [Baixar bancos de dados de amostra](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [Personalizando a inserção, atualiazação, e as operações de exclusão](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
