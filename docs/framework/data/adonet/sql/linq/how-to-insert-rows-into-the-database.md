---
title: 'Como: inserir linhas no banco de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: cc9f276cc278d4a9c376d72f1ab38d89ea6dd5b4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169592"
---
# <a name="how-to-insert-rows-into-the-database"></a>Como: inserir linhas no banco de dados
Inserir linhas em um banco de dados adicionando objetos associados [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> coleção e, em seguida, enviar as alterações no banco de dados. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converte suas alterações em apropriados do SQL `INSERT` comandos.  
  
> [!NOTE]
>  Você pode substituir os métodos padrão do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para as operações de banco de dados `Insert`, `Update` e `Delete`. Para obter mais informações, consulte [personalizando inserir, atualizar e excluir operações](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Os desenvolvedores usando o Visual Studio podem usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para desenvolver procedimentos armazenados para a mesma finalidade.  
  
 As etapas a seguir presumem que um <xref:System.Data.Linq.DataContext> válido conecta você ao banco de dados Northwind. Para obter mais informações, confira [Como: Conectar-se ao banco de dados](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).  
  
### <a name="to-insert-a-row-into-the-database"></a>Para inserir uma linha no banco de dados  
  
1.  Crie um novo objeto que inclui os dados da coluna a serem enviados.  
  
2.  Adicionar o novo objeto para o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` coleção associada à tabela de destino no banco de dados.  
  
3.  Envie a alteração para o banco de dados.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir cria um novo objeto do tipo `Order` e preenche-o com valores apropriados. Ele em seguida adiciona o novo objeto à coleção `Order`. Finalmente, ele envia a alteração para o banco de dados como uma nova linha na tabela `Orders`.  
  
 [!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Como: gerenciar conflitos de alteração](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Métodos de DataContext (Designer de Objeto Relacional)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Como: Atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Fazendo e enviando alterações de dados](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
