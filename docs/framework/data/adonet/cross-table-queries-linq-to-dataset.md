---
title: Consultas em tabelas cruzadas (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
ms.openlocfilehash: 8f9a538482580134fa876866dfe394c3dfc7de2a
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634879"
---
# <a name="cross-table-queries-linq-to-dataset"></a>Consultas em tabelas cruzadas (LINQ to DataSet)
Além de consultar uma única tabela, você também pode executar consultas de tabela cruzada no LINQ to DataSet. Isso é feito usando uma *junção*. Uma junção é a associação de objetos em uma fonte de dados com objetos que compartilham um atributo comum em outra fonte de dados, como um produto ou uma ID de contato. Na programação orientada a objeto, as relações entre objetos são relativamente fáceis de navegar, pois cada objeto tem um membro que faz referência a outro objeto. No entanto, em tabelas de banco de dados externas, as relações de navegação não são tão simples. As tabelas de banco de dados não contêm relações internas. Nesses casos, a operação de junção pode ser usada para corresponder elementos de cada fonte. Por exemplo, considerando duas tabelas que contêm informações de produto e de vendas, você pode usar uma operação de união para corresponder as informações de vendas e produtos para a mesma ordem de venda.  
  
 A estrutura de consulta integrada à linguagem (LINQ) fornece dois operadores de junção, <xref:System.Linq.Enumerable.Join%2A> e <xref:System.Linq.Enumerable.GroupJoin%2A>. Esses operadores executam *junções de equivalência*: ou seja, junções que correspondem a duas fontes de dados somente quando suas chaves são iguais. (Por outro lado, o Transact-SQL dá suporte a operadores de junção diferentes de `equals`, como o operador de `less than`.)  
  
 Em termos de banco de dados relacional, o <xref:System.Linq.Enumerable.Join%2A> implementa uma junção interna. Uma junção interna é um tipo de junção na qual apenas os objetos que têm uma correspondência no conjunto de dados oposto são retornados.  
  
 Os operadores de <xref:System.Linq.Enumerable.GroupJoin%2A> não têm equivalente direto em termos de banco de dados relacional; Eles implementam um superconjunto de junções internas e junções externas à esquerda. Uma junção externa esquerda é uma junção que retorna cada elemento da primeira coleção (esquerda), mesmo que não tenha nenhum elemento correlacionado na segunda coleção.  
  
 Para obter mais informações sobre junções, consulte [operações de junção](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120)).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir executa um junção tradicional de tabelas `SalesOrderHeader` e `SalesOrderDetail` do banco de dados de exemplo AdventureWorks para obter pedidos online do mês de agosto.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>Veja também

- [Consultando DataSets](querying-datasets-linq-to-dataset.md)
- [Consultas de tabela única](single-table-queries-linq-to-dataset.md)
- [Consultando DataSets tipados](querying-typed-datasets.md)
- [Operações join](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120))
- [Exemplos de LINQ to DataSet](linq-to-dataset-examples.md)
