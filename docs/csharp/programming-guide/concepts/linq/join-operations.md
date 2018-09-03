---
title: Operações de junção (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
ms.openlocfilehash: 23d1432d32b22964c333640ccd3ac8dc7a2394d4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480303"
---
# <a name="join-operations-c"></a>Operações de junção (C#)
Uma *junção* de duas fontes de dados é a associação de objetos em uma fonte de dados, com objetos que compartilham um atributo comum em outra fonte de dados.  
  
 A junção é uma operação importante em consultas que têm como destino fontes de dados cujas relações entre si não podem ser seguidas diretamente. Na programação orientada a objeto, isso pode significar uma correlação entre objetos que não são modelados, como a direção retroativa de uma relação unidirecional. Um exemplo de uma relação unidirecional é uma classe Cliente que tem uma propriedade do tipo Cidade, mas a classe Cidade ainda não tem uma propriedade que é uma coleção de objetos Cliente. Se você tem uma lista de objetos Cidade e você quer encontrar todos os clientes em cada cidade, você pode usar uma operação de junção para encontrá-los.  
  
 Os métodos de junção fornecidos na estrutura do LINQ são <xref:System.Linq.Enumerable.Join%2A> e <xref:System.Linq.Enumerable.GroupJoin%2A>. Esses métodos executam junção por igualdade ou junções que correspondem duas fontes de dados com base na igualdade de suas chaves. (Para comparação, o Transact-SQL oferece suporte a operadores de junção diferentes de 'equals', por exemplo, o 'less than'.) Em termos de banco de dados relacionais, <xref:System.Linq.Enumerable.Join%2A> implementa uma junção interna, um tipo de associação em que apenas os objetos que têm uma correspondência no outro conjunto de dados são retornados. O método <xref:System.Linq.Enumerable.GroupJoin%2A> não tem equivalente direto em termos de banco de dados relacional, mas ele implementa um superconjunto de junções internas e junções externas esquerdas. Uma junção externa esquerda é uma junção que retorna cada elemento da primeira (esquerda) fonte de dados, mesmo que ele não tenha elementos correlacionados na outra fonte de dados.  
  
 A ilustração a seguir mostra uma visão conceitual de dois conjuntos e os elementos dentro desses conjuntos que estão incluídos em uma junção interna ou externa à esquerda.  
  
 ![Dois círculos sobrepostos mostrando interna&#47;externa.](../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")  
  
## <a name="methods"></a>Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta C#|Mais informações|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|Une duas sequências com base nas funções de seletor de chave e extrai pares de valores.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Une duas sequências baseadas em funções de seletor de chave e agrupa as correspondências resultantes para cada elemento.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq>  
 [Visão geral de operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Tipos Anônimos](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [Formular junções e consultas entre produtos](https://msdn.microsoft.com/library/d8072ede-0521-4670-9bec-1778ceeb875b)  
 [Cláusula join](../../../../csharp/language-reference/keywords/join-clause.md)  
 [Como unir usando chaves compostas](../../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)  
 [Como unir conteúdo de arquivos diferentes (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)  
 [Como ordenar os resultados de uma cláusula join](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)  
 [Como executar operações de junção personalizadas](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md)  
 [Como executar junções agrupadas](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)  
 [Como executar junções internas](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)  
 [Como executar junções externas esquerdas](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)  
 [Como preencher coleções de objetos de várias fontes (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
