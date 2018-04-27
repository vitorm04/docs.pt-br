---
title: Como atualizar linhas no banco de dados
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 4ca47fb5a522ebcab68544a538064aa5cc3d60d7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-update-rows-in-the-database"></a>Como atualizar linhas no banco de dados
Você pode atualizar linhas em um banco de dados por meio de modificação de valores de membro de objetos associados a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> coleção e, em seguida, enviar as alterações ao banco de dados. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Converte as alterações para o SQL apropriado `UPDATE` comandos.  
  
> [!NOTE]
>  Você pode substituir os métodos padrão do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para as operações de banco de dados `Insert`, `Update` e `Delete`. Para obter mais informações, consulte [personalizando inserir, atualizar e excluir operações](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Os desenvolvedores usando o Visual Studio podem usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para desenvolver os procedimentos armazenados para a mesma finalidade.  
  
 As etapas a seguir presumem que um <xref:System.Data.Linq.DataContext> válido conecta você ao banco de dados Northwind. Para obter mais informações, consulte [como: conectar-se ao banco de dados](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).  
  
### <a name="to-update-a-row-in-the-database"></a>Para atualizar uma linha no banco de dados  
  
1.  Consulte a linha ser atualizada no banco de dados.  
  
2.  Faça as alterações desejadas nos valores dos membros no objeto [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] resultante.  
  
3.  Envie as alterações ao banco de dados.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir consulta a ordem #11000 no banco de dados e modifica os valores de `ShipName` e de `ShipVia` no objeto `Order` resultante. Finalmente, as alterações nesses valores membro são enviadas ao banco de dados como alterações nas colunas `ShipName` e `ShipVia`.  
  
 [!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Como gerenciar conflitos de alteração](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [Como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Object Relational Designer)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [Realizando e enviando alterações de dados](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
