---
title: Operações de JoinC#()
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- Join
- GroupJoin
ms.openlocfilehash: d4bf9fe76238d8824c5255df8910c1000503dcdf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746964"
---
# <a name="opno-locjoin-operations-c"></a>Operações de [!OP.NO-LOC(Join)]C#()
Uma *junção* de duas fontes de dados é a associação de objetos em uma fonte de dados, com objetos que compartilham um atributo comum em outra fonte de dados.  
  
 A junção é uma operação importante em consultas que têm como destino fontes de dados cujas relações entre si não podem ser seguidas diretamente. Na programação orientada a objeto, isso pode significar uma correlação entre objetos que não são modelados, como a direção retroativa de uma relação unidirecional. Um exemplo de uma relação unidirecional é uma classe Cliente que tem uma propriedade do tipo Cidade, mas a classe Cidade ainda não tem uma propriedade que é uma coleção de objetos Cliente. Se você tem uma lista de objetos Cidade e você quer encontrar todos os clientes em cada cidade, você pode usar uma operação de junção para encontrá-los.  
  
 Os métodos de junção fornecidos na estrutura do LINQ são <xref:System.Linq.Enumerable.[!OP.NO-LOC(Join)]%2A> e <xref:System.Linq.Enumerable.[!OP.NO-LOC(GroupJoin)]%2A>. Esses métodos executam junção por igualdade ou junções que correspondem duas fontes de dados com base na igualdade de suas chaves. (Para comparação, o Transact-SQL dá suporte a operadores de junção diferentes de ' Equals ', por exemplo, o operador ' less than '.) Em termos de banco de dados relacional, <xref:System.Linq.Enumerable.[!OP.NO-LOC(Join)]%2A> implementa uma junção interna, um tipo de junção em que somente os objetos que têm uma correspondência no outro conjunto de dado são retornados. O método <xref:System.Linq.Enumerable.[!OP.NO-LOC(GroupJoin)]%2A> não tem equivalente direto em termos de banco de dados relacional, mas ele implementa um superconjunto de junções internas e junções externas esquerdas. Uma junção externa esquerda é uma junção que retorna cada elemento da primeira (esquerda) fonte de dados, mesmo que ele não tenha elementos correlacionados na outra fonte de dados.  
  
 A ilustração a seguir mostra uma visão conceitual de dois conjuntos e os elementos dentro desses conjuntos que estão incluídos em uma junção interna ou externa à esquerda.  
  
 ![Dois círculos sobrepostos mostrando interna/externa.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta C#|Mais Informações|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|Une duas sequências com base nas funções de seletor de chave e extrai pares de valores.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Une duas sequências baseadas em funções de seletor de chave e agrupa as correspondências resultantes para cada elemento.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Exemplos de sintaxe de expressão de consulta
  
### Join  
  
O exemplo a seguir usa a cláusula `join … in … on … equals …` para unir duas sequências com base no valor específico:
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQJoin/CS/JoinOperation.cs#Join)]  

### GroupJoin  

O exemplo a seguir usa a cláusula `join … in … on … equals … into …` para unir duas sequências com base em um valor específico e agrupa as correspondências resultantes para cada elemento:
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQJoin/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a>Veja também

- <xref:System.Linq>
- [Visão geral de operadores de consulta padrão (C#)](./standard-query-operators-overview.md)
- [Tipos Anônimos](../../classes-and-structs/anonymous-types.md)
- [Formular junções e consultas entre produtos](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [Cláusula join](../../../language-reference/keywords/join-clause.md)
- [Join usando chaves compostas](../../../linq/join-by-using-composite-keys.md)
- [Como unir conteúdo de arquivos diferentes (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md)
- [Ordenar os resultados de uma cláusula join](../../../linq/order-the-results-of-a-join-clause.md)
- [Executar operações de junção personalizadas](../../../linq/perform-custom-join-operations.md)
- [Executar junções agrupadas](../../../linq/perform-grouped-joins.md)
- [Executar junções internas](../../../linq/perform-inner-joins.md)
- [Executar junções externas esquerdas](../../../linq/perform-left-outer-joins.md)
- [Como preencher coleções de objetos de várias fontes (LINQ) (C#)](./how-to-populate-object-collections-from-multiple-sources-linq.md)
