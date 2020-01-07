---
title: Cláusula join – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- join
- join_CSharpKeyword
helpviewer_keywords:
- join clause [C#]
- join keyword [C#]
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
ms.openlocfilehash: 2e1304c9f38c82b43b0c6551d1b5e7aac523dfe4
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635958"
---
# <a name="join-clause-c-reference"></a>Cláusula join (Referência de C#)

A cláusula `join` é útil para associar elementos de sequências de origem diferentes que não têm nenhuma relação direta no modelo de objeto. O único requisito é que os elementos em cada fonte compartilhem algum valor que possa ser comparado pela igualdade. Por exemplo, um distribuidor de alimentos pode ter uma lista de fornecedores de um determinado produto e uma lista de compradores. Uma cláusula `join` pode ser usada, por exemplo, para criar uma lista de fornecedores e compradores daquele produto, que estejam na mesma região especificada.

Uma cláusula `join` recebe duas sequências de origem como entrada. Os elementos em cada sequência devem ser ou conter uma propriedade que possa ser comparada com uma propriedade correspondente na outra sequência. A cláusula `join` compara a igualdade das chaves especificadas, usando a palavra-chave especial `equals`. Todas as junções realizadas pela cláusula `join` são junções por igualdade. A forma da saída de uma cláusula `join` depende do tipo específico de junção que você está realizando. A seguir estão os três tipos de junção mais comuns:

- União interna

- Junção de grupo

- Junção externa esquerda

## <a name="inner-join"></a>União interna

O exemplo a seguir mostra uma junção por igualdade interna simples. Essa consulta produz uma sequência simples de pares "nome de produto / categoria". A mesma cadeia de caracteres de categoria aparecerá em vários elementos. Se um elemento de `categories` não tiver `products` correspondente, essa categoria não aparecerá nos resultados.

[!code-csharp[cscsrefQueryKeywords#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#24)]

Para obter mais informações, consulte [Executar junções internas](../../linq/perform-inner-joins.md).

## <a name="group-join"></a>Junção de grupo

Uma cláusula `join` com um expressão `into` é chamada de junção de grupo.

[!code-csharp[cscsrefQueryKeywords#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#25)]

Uma junção de grupo produz uma sequência de resultados hierárquicos, que associa os elementos na sequência de origem à esquerda com um ou mais elementos correspondentes na sequência de origem do lado direito. Uma junção de grupo não tem nenhum equivalente em termos relacionais. Ela é, essencialmente, uma sequência de matrizes de objetos.

Se nenhum elemento da sequência de origem à direita que corresponda a um elemento na origem à esquerda for encontrado, a cláusula `join` produzirá uma matriz vazia para aquele item. Portanto, a junção de grupo é, basicamente, uma junção por igualdade interna, exceto pelo fato de que a sequência de resultado é organizada em grupos.

É só selecionar os resultados de uma junção de grupo e você poderá acessar os itens, mas você não poderá identificar a chave na qual eles correspondem. Portanto, geralmente há maior utilidade em selecionar os resultados da junção de grupo em um novo tipo que também tenha o nome da chave, conforme mostrado no exemplo anterior.

Além disso, é claro que você pode usar o resultado de uma junção de grupo como o gerador de outra subconsulta:

[!code-csharp[cscsrefQueryKeywords#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#26)]

Para obter mais informações, consulte [Executar junções agrupadas](../../linq/perform-grouped-joins.md).

## <a name="left-outer-join"></a>Junção externa esquerda

Em uma junção externa esquerda, todos os elementos na sequência de origem à esquerda são retornados, mesmo que não haja elementos correspondentes na sequência à direita. Para executar uma junção externa esquerda no LINQ, use o método `DefaultIfEmpty` em combinação com uma junção de grupo para especificar um elemento padrão do lado direito para produzir se um elemento do lado esquerdo não tiver correspondências. Você pode usar `null` como o valor padrão para qualquer tipo de referência ou pode especificar um tipo padrão definido pelo usuário. No exemplo a seguir, é mostrado um tipo padrão definido pelo usuário:

[!code-csharp[cscsrefQueryKeywords#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#27)]

Para obter mais informações, consulte [Executar junções externas esquerdas](../../linq/perform-left-outer-joins.md).

## <a name="the-equals-operator"></a>O operador equals

Uma cláusula `join` realiza uma junção por igualdade. Em outras palavras, você só pode basear correspondências na igualdade de duas chaves. Não há suporte para outros tipos de comparações, como "maior que" ou "não é igual a". Para se certificar de que todas as junções são junções por igualdade, a cláusula `join` usa a palavra-chave `equals` em vez do operador `==`. A palavra-chave `equals` só pode ser usada em uma cláusula `join` e ela difere do operador `==` em um aspecto importante. Com `equals`, a chave esquerda consome a sequência de origem externa e a chave direita consome a origem interna. A origem externa somente está no escopo no lado esquerdo de `equals` e a sequência de origem interna somente está no escopo no lado direito.

## <a name="non-equijoins"></a>Junções por não igualdade

Você pode realizar junções por não igualdade, uniões cruzadas e outras operações de junção personalizadas, usando várias cláusulas `from` para introduzir novas sequências de maneira independente em uma consulta. Para obter mais informações, consulte [Executar operações de junção personalizadas](../../linq/perform-custom-join-operations.md).

## <a name="joins-on-object-collections-vs-relational-tables"></a>Junções em coleções de objetos versus tabelas relacionais

Em uma expressão de consulta LINQ, as operações de junção são executadas em coleções de objetos. As coleções de objetos não podem ser "unidas" exatamente da mesma forma que duas tabelas relacionais. No LINQ, as cláusulas `join` explícitas só são necessárias quando duas sequências de origem não são ligadas por nenhuma relação. Ao trabalhar com [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], as tabelas de chave estrangeira são representadas no modelo de objeto como propriedades da tabela primária. Por exemplo, no banco de dados Northwind, a tabela Cliente tem uma relação de chave estrangeira com a tabela Pedidos. Quando você mapear as tabelas para o modelo de objeto, a classe Cliente terá uma propriedade de Pedidos contendo a coleção de Pedidos associados a esse Cliente. Na verdade, a junção já foi feita para você.

Para obter mais informações sobre como fazer consultas entre tabelas relacionadas no contexto de [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], consulte [Como mapear relações de banco de dados](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md).

## <a name="composite-keys"></a>Chaves compostas

Você pode testar a igualdade de vários valores, usando uma chave de composição. Para obter mais informações, consulte [Unir usando chaves compostas](../../linq/join-by-using-composite-keys.md). As chaves compostas também podem ser usadas em uma cláusula `group`.

## <a name="example"></a>Exemplo

O exemplo a seguir compara os resultados de uma junção interna, uma junção de grupo e uma junção externa esquerda nas mesmas fontes de dados, usando as mesmas chaves correspondentes. Foi adicionado algum código extra nesses exemplos a fim de deixar os resultados na tela do console mais claros.

[!code-csharp[cscsrefQueryKeywords#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#23)]

## <a name="remarks"></a>Comentários

Uma cláusula `join` que não é seguida por `into` é convertida em uma chamada de método <xref:System.Linq.Enumerable.Join%2A>. Uma cláusula `join` que é seguida por `into` é convertida em uma chamada de método <xref:System.Linq.Enumerable.GroupJoin%2A>.

## <a name="see-also"></a>Veja também

- [Palavras-chave de Consulta (LINQ)](query-keywords.md)
- [LINQ (Consulta Integrada à Linguagem)](../../linq/index.md)
- [Operações join](../../programming-guide/concepts/linq/join-operations.md)
- [Cláusula group](group-clause.md)
- [Executar junções externas esquerdas](../../linq/perform-left-outer-joins.md)
- [Executar junções internas](../../linq/perform-inner-joins.md)
- [Executar junções agrupadas](../../linq/perform-grouped-joins.md)
- [Ordenar os resultados de uma cláusula join](../../linq/order-the-results-of-a-join-clause.md)
- [Unir usando chaves compostas](../../linq/join-by-using-composite-keys.md)
- [Sistemas de banco de dados compatíveis para Visual Studio](/visualstudio/data-tools/installing-database-systems-tools-and-samples)
