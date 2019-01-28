---
title: Executar junções internas (LINQ em C#)
description: Saiba como executar junções internas usando o LINQ em C#.
ms.date: 12/01/2016
ms.assetid: 45bceed6-f549-4114-a9b1-b44feb497742
ms.openlocfilehash: a3e8e9bd97ec630797bc48a3302b27ed45d9103e
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857951"
---
# <a name="perform-inner-joins"></a>Executar junções internas

Em termos de banco de dados relacionais, uma *junção interna* produz um conjunto de resultados no qual cada elemento da primeira coleção aparece uma vez para todo elemento correspondente na segunda coleção. Se um elemento na primeira coleção não tiver nenhum elemento correspondente, ele não aparece no conjunto de resultados. O método <xref:System.Linq.Enumerable.Join%2A>, que é chamado pela cláusula `join` no C#, implementa uma junção interna.

Este artigo mostra como executar quatro variações de uma junção interna:

- Uma junção interna simples que correlaciona os elementos de duas fontes de dados com base em uma chave simples.

- Uma junção interna simples que correlaciona os elementos de duas fontes de dados com base em uma chave *composta*. Uma chave composta, que é uma chave que consiste em mais de um valor, permite que você correlacione os elementos com base em mais de uma propriedade.

- Uma *junção múltipla* na qual operações join sucessivas são acrescentadas umas às outras.

- Uma junção interna que é implementada por meio de uma junção de grupo.

## <a name="example---simple-key-join"></a>Exemplo – junção de chave simples

O exemplo a seguir cria duas coleções que contêm objetos de dois tipos definidos pelo usuário, `Person` e `Pet`. A consulta usa a cláusula `join` em C# para corresponder objetos `Person` com objetos `Pet` cujo `Owner` é `Person`. A cláusula `select` em C# define a aparência dos objetos resultantes. Neste exemplo, os objetos resultantes são tipos anônimos que consistem no nome do proprietário e no nome do animal de estimação.

[!code-csharp[CsLINQProgJoining#1](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_1.cs)]

Observe que o objeto `Person` cujo `LastName` é "Huff" não aparecerá no conjunto de resultados porque não há nenhum objeto `Pet` que tenha `Pet.Owner` igual a esse `Person`.

## <a name="example---composite-key-join"></a>Exemplo – junção de chave composta

Em vez de correlacionar os elementos com base em apenas uma propriedade, você pode usar uma chave composta para comparar elementos com base em várias propriedades. Para fazer isso, especifique a função de seletor de chave para cada coleção retornar um tipo anônimo que consiste nas propriedades que você deseja comparar. Se você rotular as propriedades, elas devem ter o mesmo rótulo no tipo anônimo cada chave. As propriedades também devem aparecer na mesma ordem.

O exemplo a seguir usa uma lista de objetos `Employee` e uma lista de objetos `Student` para determinar quais funcionários também são alunos. Ambos os tipos têm uma propriedade `FirstName` e uma `LastName` do tipo <xref:System.String>. As funções que criam as chaves de junção dos elementos de cada lista retornam um tipo anônimo que consiste nas propriedades `FirstName` e `LastName` de cada elemento. A operação join compara essas chaves compostas quanto à igualdade e retorna pares de objetos de cada lista em que o nome e o sobrenome correspondem.

[!code-csharp[CsLINQProgJoining#2](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_2.cs)]

## <a name="example---multiple-join"></a>Exemplo – junção múltipla

Qualquer número de operações join pode ser acrescentado entre si para realizar uma junção múltipla. Cada cláusula `join` em C# correlaciona uma fonte de dados especificada com os resultados da junção anterior.

O exemplo a seguir cria três coleções: uma lista de objetos `Person`, uma lista de objetos `Cat` e uma lista de objetos `Dog`.

A primeira cláusula `join` em C# corresponde a pessoas e gatos com base em um objeto `Person` correspondendo a `Cat.Owner`. Ela retorna uma sequência de tipos anônimos que contêm o objeto `Person` e `Cat.Name`.

A segunda cláusula `join` em C# correlaciona os tipos anônimos retornados pela primeira junção com objetos `Dog` na lista de cães fornecida, com base em uma chave composta que consiste na propriedade `Owner` do tipo `Person` e na primeira letra do nome do animal. Ela retorna uma sequência de tipos anônimos que contêm as propriedades `Cat.Name` e `Dog.Name` de cada par correspondente. Como esta é uma junção interna, apenas os objetos da primeira fonte de dados que têm uma correspondência na segunda fonte de dados são retornados.

[!code-csharp[CsLINQProgJoining#3](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_3.cs)]

## <a name="example---inner-join-by-using-grouped-join"></a>Exemplo – junção interna usando junção agrupada

O exemplo a seguir mostra como implementar uma junção interna usando uma junção de grupo.

Em `query1`, a lista de objetos `Person` é unida por grupo à lista de objetos `Pet` com base no `Person` correspondente à propriedade `Pet.Owner`. A junção de grupo cria uma coleção de grupos intermediários, em que cada grupo é composto por um objeto `Person` e uma sequência de objetos `Pet` correspondentes.

Ao adicionar uma segunda cláusula `from` à consulta, essa sequência de sequências é combinada (ou mesclada) na sequência mais longa. O tipo dos elementos da sequência de final é especificado pela cláusula `select`. Neste exemplo, o tipo é um tipo anônimo que consiste nas propriedades `Person.FirstName` e `Pet.Name` para cada par correspondente.

O resultado de `query1` é equivalente ao conjunto de resultados que seria obtido usando a cláusula `join` sem a cláusula `into` para realizar uma junção interna. A variável `query2` demonstra essa consulta equivalente.

[!code-csharp[CsLINQProgJoining#4](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_4.cs)]

## <a name="see-also"></a>Consulte também

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [Executar junções agrupadas](perform-grouped-joins.md)
- [Executar junções externas esquerdas](perform-left-outer-joins.md)
- [Tipos anônimos](../programming-guide/classes-and-structs/anonymous-types.md)
