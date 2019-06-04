---
title: Consultas em tabelas cruzadas (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
ms.openlocfilehash: e974f643fd1515b701d2e81048725b88055b57dc
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489563"
---
# <a name="cross-table-queries-linq-to-dataset"></a>Consultas em tabelas cruzadas (LINQ to DataSet)
Além de consultar uma única tabela, você também pode executar consultas em tabelas cruzadas no [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Isso é feito usando um *junção*. Uma junção é a associação de objetos em uma fonte de dados com objetos que compartilham um atributo comum em outra fonte de dados, como um produto ou ID de contato. Na programação orientada a objeto, as relações entre objetos são relativamente fáceis de navegar porque cada objeto tem um membro que faz referência a outro objeto. Nas tabelas de banco de dados externo, no entanto, navegar em relações não é tão simples. Tabelas de banco de dados não contêm relações internas. Nesses casos, a operação de junção pode ser usada para corresponder os elementos de cada fonte. Por exemplo, considerando duas tabelas que contêm informações de produto e de vendas, você pode usar uma operação de união para corresponder as informações de vendas e produtos para a mesma ordem de venda.  
  
 O [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] framework fornece dois operadores, de união <xref:System.Linq.Enumerable.Join%2A> e <xref:System.Linq.Enumerable.GroupJoin%2A>. Esses operadores executam *junções*: isto é, junções que correspondem a duas fontes somente quando suas chaves são iguais. (Por outro lado, Transact-SQL oferece suporte a operadores de junção diferente de `equals`, como o `less than` operador.)  
  
 Em termos de banco de dados relacional, o <xref:System.Linq.Enumerable.Join%2A> implementa uma junção interna. Uma junção interna é um tipo de junção na qual apenas os objetos que têm uma correspondência no conjunto de dados oposto são retornados.  
  
 O <xref:System.Linq.Enumerable.GroupJoin%2A> operadores não têm equivalente direto em termos de banco de dados relacional; eles implementam um superconjunto de junções internas e junções externas esquerdas. Uma junção externa esquerda é uma junção que retorna cada elemento da primeira (à esquerda) coleção, mesmo se ele não tenha elementos correlacionados na segunda coleção.  
  
 Para obter mais informações sobre junções, consulte [operações de junção](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120)).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir executa um junção tradicional de tabelas `SalesOrderHeader` e `SalesOrderDetail` do banco de dados de exemplo AdventureWorks para obter pedidos online do mês de agosto.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>Consulte também

- [Consultando DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [Consultas de tabela única](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
- [Consultando DataSets tipados](../../../../docs/framework/data/adonet/querying-typed-datasets.md)
- [Operações join](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120))
- [Exemplos de LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
