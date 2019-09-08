---
title: Operações de inserção, atualização e exclusão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: fac89f905b85493bc0ec36a85635f369bb354266
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793052"
---
# <a name="insert-update-and-delete-operations"></a>Operações de inserção, atualização e exclusão

Você executa operações `Insert`, `Update` e `Delete` no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] adicionando, modificando e removendo objetos no seu modelo de objeto. Por padrão, o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converte suas ações para SQL e envia as alterações para o banco de dados.

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]oferece flexibilidade máxima na manipulação e persistência de alterações feitas em seus objetos. Assim que os objetos de entidade estão disponíveis (recuperando-os por meio de uma consulta ou construindo-os de uma nova), você pode alterá-los como objetos típicos em seu aplicativo. Ou seja, você pode alterar seus valores, pode adicioná-los às coleções e pode removê-los de suas coleções. O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] controla as alterações e está pronto para transmiti-las de volta para o banco de dados quando você chama <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Não dá suporte ou reconhece operações de exclusão em cascata. Se você quiser excluir uma linha em uma tabela que tenha restrições em relação a ela, você deve definir a `ON DELETE CASCADE` regra na restrição FOREIGN-KEY no banco de dados ou usar seu próprio código para primeiro excluir os objetos filho que impedem que o objeto pai seja excluído. Caso contrário, uma exceção será gerada. Para obter mais informações, confira [Como: Excluir linhas do banco de](how-to-delete-rows-from-the-database.md)dados.

Os seguintes trechos usam as classes `Customer` e `Order` do banco de dados de exemplo Northwind. As definições de classe não são mostradas para abreviar.

[!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
[!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]

Quando você chama <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automaticamente gera e executa comandos SQL de que ele deve passar suas alterações de volta para o banco de dados.

> [!NOTE]
> Você pode substituir esse comportamento usando sua própria lógica personalizada, geralmente usando um procedimento armazenado. Para obter mais informações, consulte [responsabilidades do desenvolvedor ao substituir o comportamento padrão](responsibilities-of-the-developer-in-overriding-default-behavior.md).
>
> Os desenvolvedores que usam o Visual Studio podem usar o Object Relational Designer para desenvolver procedimentos armazenados para essa finalidade.

## <a name="see-also"></a>Consulte também

- [Downloading Sample Databases](downloading-sample-databases.md) (Baixando bancos de dados de amostra)
- [Personalizando as operações de inserção, atualização e exclusão](customizing-insert-update-and-delete-operations.md)
