---
title: 'Como: inserir linhas no banco de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: 2852b0593f8b213f8cad6f9a2ab8f08eeb2a4dec
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943643"
---
# <a name="how-to-insert-rows-into-the-database"></a>Como: inserir linhas no banco de dados
Você insere linhas em um banco de dados adicionando objetos à coleção [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] associada <xref:System.Data.Linq.Table%601> e, em seguida, enviando as alterações ao banco de dados. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]traduz as alterações nos comandos SQL `INSERT` apropriados.  
  
> [!NOTE]
> Você pode substituir os métodos padrão do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para as operações de banco de dados `Insert`, `Update` e `Delete`. Para obter mais informações, consulte [Personalizando as operações de inserção, atualização e exclusão](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Os desenvolvedores que usam o Visual Studio podem usar o Object Relational Designer para desenvolver procedimentos armazenados para a mesma finalidade.  
  
 As etapas a seguir presumem que um <xref:System.Data.Linq.DataContext> válido conecta você ao banco de dados Northwind. Para obter mais informações, confira [Como: Conecte-se a](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)um banco de dados.  
  
### <a name="to-insert-a-row-into-the-database"></a>Para inserir uma linha no banco de dados  
  
1. Crie um novo objeto que inclui os dados da coluna a serem enviados.  
  
2. Adicione o novo objeto à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` coleção associada à tabela de destino no banco de dados.  
  
3. Envie a alteração para o banco de dados.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir cria um novo objeto do tipo `Order` e preenche-o com valores apropriados. Ele em seguida adiciona o novo objeto à coleção `Order`. Finalmente, ele envia a alteração para o banco de dados como uma nova linha na tabela `Orders`.  
  
 [!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Como: Gerenciar conflitos de alterações](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Métodos DataContext (Designer Relacional de Objetos)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Como: Atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Realizando e enviando alterações de dados](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
