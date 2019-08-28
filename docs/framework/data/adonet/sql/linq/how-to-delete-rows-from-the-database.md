---
title: 'Como: excluir linhas do banco de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: 48377aed85aebcf83cb61b4d4dcf9bb732d0cb0e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041175"
---
# <a name="how-to-delete-rows-from-the-database"></a>Como: excluir linhas do banco de dados

Você pode excluir linhas em um banco de dados removendo [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] os objetos correspondentes de sua coleção relacionada à tabela. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]traduz as alterações nos comandos SQL `DELETE` apropriados.

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Não dá suporte ou reconhece operações de exclusão em cascata. Se você deseja excluir uma linha em uma tabela com restrições, deverá concluir uma das seguintes tarefas:

- Defina a regra `ON DELETE CASCADE` na restrição de chave estrangeira no banco de dados.

- Use seu próprio código para excluir primeiro os objetos filho que impedem que o objeto pai seja excluído.

 Caso contrário, uma exceção será gerada. Consulte o segundo exemplo de código posteriormente neste tópico.

> [!NOTE]
> Você pode substituir os métodos padrão do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para as operações de banco de dados `Insert`, `Update` e `Delete`. Para obter mais informações, consulte [Personalizando as operações de inserção, atualização e exclusão](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).
>
> Os desenvolvedores que usam o Visual Studio podem usar o Object Relational Designer para desenvolver procedimentos armazenados para a mesma finalidade.

As etapas a seguir presumem que um <xref:System.Data.Linq.DataContext> válido conecta você ao banco de dados Northwind. Para obter mais informações, confira [Como: Conecte-se a](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)um banco de dados.

### <a name="to-delete-a-row-in-the-database"></a>Para excluir uma linha no banco de dados

1. Consulte o banco de dados para a linha ser excluída.

2. Chame o método <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>.

3. Envie a alteração para o banco de dados.

## <a name="example"></a>Exemplo

O primeiro exemplo de código consulta o banco de dados para obter os detalhes do pedido que pertencem ao Pedido #11000, marca esses detalhes do pedido para exclusão e envia estas alterações para o banco de dados.

[!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
[!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]

## <a name="example"></a>Exemplo

No segundo exemplo, o objetivo é remover uma pedido (#10250). O código primeiro examina a tabela `OrderDetails` para ver se o pedido a ser removido tem filhos nela. Se o pedido tiver filhos, primeiro os filhos e, em seguida, o pedido serão marcados para remoção. O <xref:System.Data.Linq.DataContext> coloca as exclusões reais na ordem correta de modo que os comandos de exclusão enviados para o banco de dados aceitem as restrições do banco de dados.

[!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
[!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]

## <a name="see-also"></a>Consulte também

- [Como: Gerenciar conflitos de alterações](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Como: Atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Realizando e enviando alterações de dados](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
