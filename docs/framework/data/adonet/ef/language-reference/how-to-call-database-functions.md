---
title: 'Como: Chamar funções de banco de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
ms.openlocfilehash: dd440be3f73eb2f02a269a8cad29f0fe30920836
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936031"
---
# <a name="how-to-call-database-functions"></a>Como: Chamar funções de banco de dados
A classe de <xref:System.Data.Objects.SqlClient.SqlFunctions> contém os métodos que expõe funções do SQL Server para usar em consultas LINQ to Entities. Quando você usa métodos de <xref:System.Data.Objects.SqlClient.SqlFunctions> em consultas LINQ to Entities, as funções de base de dados correspondentes são executadas em base de dados.  
  
> [!NOTE]
> Funções de base de dados que executar um cálculo em um conjunto de valores e retornar um valor único (também conhecido como funções de base de dados agregadas) podem ser chamadas diretamente. Outras funções canônicas só podem ser chamados como parte de uma consulta LINQ to Entities. Para chamar diretamente uma função agregada, você deve passar <xref:System.Data.Objects.ObjectQuery%601> à função. Para obter mais informações, consulte o segundo exemplo abaixo.  
  
> [!NOTE]
> Os métodos na classe de <xref:System.Data.Objects.SqlClient.SqlFunctions> são específicos para funções SQL Server. As classes semelhantes que expõe funções de base de dados podem estar disponíveis através de outros provedores.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o [modelo de vendas AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples). O exemplo executa uma consulta LINQ to entidades que usa o método de <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> para retornar todos os contatos cujo nome começa com “si”:  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o [modelo de vendas AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples). O exemplo chama o método agregado de <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> diretamente. Observe que <xref:System.Data.Objects.ObjectQuery%601> é passado para a função, que permite que é chamado sem ser parte de uma consulta LINQ to Entities.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a>Consulte também

- [Chamando funções em consultas LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [Consultas no LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
