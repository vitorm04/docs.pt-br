---
title: Cláusula Aggregate
ms.date: 08/28/2018
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: 5aa4b9afea4b6b26b853d4f4f6d4c8db08554e19
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350880"
---
# <a name="aggregate-clause-visual-basic"></a>Cláusula Aggregate (Visual Basic)
Aplica uma ou mais funções de agregação a uma coleção.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`element`|Necessária. Variável usada para iterar pelos elementos da coleção.|  
|`type`|Opcional. O tipo de `element`. Se nenhum tipo for especificado, o tipo de `element` será inferido de `collection`.|  
|`collection`|Necessária. Refere-se à coleção na qual operar.|  
|`clause`|Opcional. Uma ou mais cláusulas de consulta, como uma cláusula `Where`, para refinar o resultado da consulta para aplicar a cláusula ou cláusulas de agregação ao.|  
|`expressionList`|Necessária. Uma ou mais expressões delimitadas por vírgula que identificam uma função de agregação a ser aplicada à coleção. Você pode aplicar um alias a uma função de agregação para especificar um nome de membro para o resultado da consulta. Se nenhum alias for fornecido, o nome da função de agregação será usado. Para obter exemplos, consulte a seção sobre funções de agregação mais adiante neste tópico.|  
  
## <a name="remarks"></a>Comentários  
 A cláusula `Aggregate` pode ser usada para incluir funções de agregação em suas consultas. As funções de agregação executam verificações e computações em um conjunto de valores e retornam um único valor. Você pode acessar o valor computado usando um membro do tipo de resultado da consulta. As funções de agregação padrão que você pode usar são as funções `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`e `Sum`. Essas funções são familiares aos desenvolvedores que estão familiarizados com agregações no SQL. Eles são descritos na seção a seguir deste tópico.  
  
 O resultado de uma função de agregação é incluído no resultado da consulta como um campo do tipo de resultado da consulta. Você pode fornecer um alias para o resultado da função de agregação para especificar o nome do membro do tipo de resultado da consulta que conterá o valor de agregação. Se nenhum alias for fornecido, o nome da função de agregação será usado.  
  
 A cláusula `Aggregate` pode iniciar uma consulta ou pode ser incluída como uma cláusula adicional em uma consulta. Se a cláusula `Aggregate` iniciar uma consulta, o resultado será um valor único que é o resultado da função de agregação especificada na cláusula `Into`. Se mais de uma função de agregação for especificada na cláusula `Into`, a consulta retornará um único tipo com uma propriedade separada para referenciar o resultado de cada função de agregação na cláusula `Into`. Se a cláusula `Aggregate` for incluída como uma cláusula adicional em uma consulta, o tipo retornado na coleção de consulta terá uma propriedade separada para referenciar o resultado de cada função de agregação na cláusula `Into`.  
  
## <a name="aggregate-functions"></a>Funções agregadas

A seguir estão as funções de agregação padrão que podem ser usadas com a cláusula `Aggregate`.  
  
### <a name="all"></a>Tudo

Retorna `true` se todos os elementos na coleção atenderem a uma condição especificada; caso contrário, retorna `false`. Veja um exemplo a seguir:

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a>Qualquer

Retorna `true` se algum elemento da coleção satisfizer uma condição especificada; caso contrário, retorna `false`. Veja um exemplo a seguir:

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a>Média

Calcula a média de todos os elementos na coleção ou computa uma expressão fornecida para todos os elementos na coleção. Veja um exemplo a seguir:

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a>{1&gt;{2&gt;Contagem&lt;2}&lt;1}

Conta o número de elementos na coleção. Você pode fornecer uma expressão de `Boolean` opcional para contar apenas o número de elementos na coleção que atendem a uma condição. Veja um exemplo a seguir:

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a>Grupo

Refere-se aos resultados da consulta que são agrupados como resultado de uma cláusula `Group By` ou `Group Join`. A função `Group` é válida somente na cláusula `Into` de uma cláusula `Group By` ou `Group Join`. Para obter mais informações e exemplos, consulte cláusula [Group by](../../../visual-basic/language-reference/queries/group-by-clause.md) e Group [Join](../../../visual-basic/language-reference/queries/group-join-clause.md).

### <a name="longcount"></a>LongCount

Conta o número de elementos na coleção. Você pode fornecer uma expressão de `Boolean` opcional para contar apenas o número de elementos na coleção que atendem a uma condição. Retorna o resultado como um `Long`. Para obter um exemplo, consulte a função de agregação `Count`.

### <a name="max"></a>Max

Computa o valor máximo da coleção ou computa uma expressão fornecida para todos os elementos na coleção. Veja um exemplo a seguir:

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a>Min

Computa o valor mínimo da coleção ou computa uma expressão fornecida para todos os elementos na coleção. Veja um exemplo a seguir:

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a>Sum

Computa a soma de todos os elementos na coleção ou computa uma expressão fornecida para todos os elementos na coleção. Veja um exemplo a seguir:

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a>Exemplo  

O exemplo a seguir mostra como usar a cláusula `Aggregate` para aplicar funções de agregação a um resultado de consulta.  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>Criando funções de agregação definidas pelo usuário

 Você pode incluir suas próprias funções de agregação personalizadas em uma expressão de consulta adicionando métodos de extensão ao tipo de <xref:System.Collections.Generic.IEnumerable%601>. O método personalizado pode então executar um cálculo ou uma operação na coleção enumerável que referenciou sua função de agregação. Para obter mais informações sobre os métodos de extensão, consulte [Métodos de extensão](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
 Por exemplo, o exemplo a seguir mostra uma função de agregação personalizada que calcula o valor mediano de uma coleção de números. Há duas sobrecargas do método de extensão `Median`. A primeira sobrecarga aceita, como entrada, uma coleção do tipo `IEnumerable(Of Double)`. Se a função de agregação `Median` for chamada para um campo de consulta do tipo `Double`, esse método será chamado. A segunda sobrecarga do método `Median` pode ser passada qualquer tipo genérico. A sobrecarga genérica do método `Median` usa um segundo parâmetro que faz referência à expressão lambda `Func(Of T, Double)` para projetar um valor para um tipo (de uma coleção) como o valor correspondente do tipo `Double`. Em seguida, ele delega o cálculo do valor mediano para a outra sobrecarga do método `Median`. Para obter mais informações sobre expressões lambda, consulte [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 O exemplo a seguir mostra as consultas de exemplo que chamam a função de agregação `Median` em uma coleção do tipo `Integer`e uma coleção do tipo `Double`. A consulta que chama a função de agregação `Median` na coleção do tipo `Double` chama a sobrecarga do método `Median` que aceita, como entrada, uma coleção do tipo `Double`. A consulta que chama a função de agregação `Median` na coleção do tipo `Integer` chama a sobrecarga genérica do método `Median`.  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Consultas](../../../visual-basic/language-reference/queries/index.md)
- [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)
- [Cláusula Group By](../../../visual-basic/language-reference/queries/group-by-clause.md)
