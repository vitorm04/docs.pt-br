---
title: Cláusula Aggregate (Visual Basic)
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
ms.openlocfilehash: 21781db637c71abbbe9366bc95b6ee4c89ac2246
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61712624"
---
# <a name="aggregate-clause-visual-basic"></a>Cláusula Aggregate (Visual Basic)
Aplica uma ou mais funções de agregação a uma coleção.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`element`|Necessário. Variável usada para iterar por meio dos elementos da coleção.|  
|`type`|Opcional. O tipo de `element`. Se nenhum tipo for especificado, o tipo de `element` é inferido do `collection`.|  
|`collection`|Necessário. Refere-se à coleção no qual operar.|  
|`clause`|Opcional. Um ou mais cláusulas de consulta, como um `Where` cláusula para refinar os resultados da consulta para aplicar a cláusula aggregate ou cláusulas.|  
|`expressionList`|Necessário. Uma ou mais delimitado por vírgula expressões que identificam uma função de agregação a ser aplicado à coleção. Você pode aplicar um alias para uma função de agregação para especificar um nome de membro para o resultado da consulta. Se nenhum alias for fornecido, o nome da função de agregação é usado. Para obter exemplos, consulte a seção sobre funções de agregação neste tópico.|  
  
## <a name="remarks"></a>Comentários  
 O `Aggregate` cláusula pode ser usada para incluir funções agregadas em suas consultas. Funções agregadas executam verificações e cálculos em um conjunto de valores e retornam um único valor. Você pode acessar o valor calculado usando um membro do tipo de resultado da consulta. São as funções de agregação padrão que você pode usar o `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, e `Sum` funções. Essas funções são familiares para desenvolvedores que estão familiarizados com agregações no SQL. Elas são descritas na seção a seguir deste tópico.  
  
 O resultado de uma função de agregação está incluído no resultado da consulta como um campo do tipo de resultado da consulta. Você pode fornecer um alias para o resultado da função de agregação especificar o nome do membro do tipo de resultado da consulta que conterá o valor de agregação. Se nenhum alias for fornecido, o nome da função de agregação é usado.  
  
 O `Aggregate` cláusula pode começar uma consulta, ou pode ser incluída como uma cláusula adicional em uma consulta. Se o `Aggregate` cláusula começa uma consulta, o resultado é um valor único que é o resultado da função de agregação especificada no `Into` cláusula. Se mais de uma função de agregação for especificada na `Into` cláusula, a consulta retorna um único tipo com uma propriedade separada para referenciar o resultado de cada função de agregação no `Into` cláusula. Se o `Aggregate` cláusula será incluída como uma cláusula adicional em uma consulta, o tipo retornado na coleção de consultas terá uma propriedade separada para referenciar o resultado de cada função de agregação no `Into` cláusula.  
  
## <a name="aggregate-functions"></a>Funções agregadas

A seguir estão as funções de agregação padrão que podem ser usadas com o `Aggregate` cláusula.  
  
### <a name="all"></a>Todos

Retorna `true` se todos os elementos na coleção satisfazem uma condição especificada; caso contrário, retornará `false`. A seguir está um exemplo:

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a>Qualquer

Retorna `true` se qualquer elemento na coleção satisfazem uma condição especificada; caso contrário, retornará `false`. A seguir está um exemplo:

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a>Média

Calcula a média de todos os elementos na coleção, ou calcula uma expressão fornecida para todos os elementos na coleção. A seguir está um exemplo:

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a>Contagem

Conta o número de elementos na coleção. Você pode fornecer um recurso opcional `Boolean` expressão para contar somente o número de elementos na coleção que satisfazem uma condição. A seguir está um exemplo:

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a>Grupo

Refere-se aos resultados da consulta que são agrupados como resultado de uma `Group By` ou `Group Join` cláusula. O `Group` função só é válida em de `Into` cláusula de uma `Group By` ou `Group Join` cláusula. Para obter mais informações e exemplos, consulte [por cláusula Group](../../../visual-basic/language-reference/queries/group-by-clause.md) e [cláusula de junção de grupo](../../../visual-basic/language-reference/queries/group-join-clause.md).

### <a name="longcount"></a>LongCount

Conta o número de elementos na coleção. Você pode fornecer um recurso opcional `Boolean` expressão para contar somente o número de elementos na coleção que satisfazem uma condição. Retorna o resultado como um `Long`. Por exemplo, consulte o `Count` função de agregação.

### <a name="max"></a>Máx.

Calcula o valor máximo da coleção, ou calcula uma expressão fornecida para todos os elementos na coleção. A seguir está um exemplo:

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a>Mín.

Calcula o valor mínimo da coleção, ou calcula uma expressão fornecida para todos os elementos na coleção. A seguir está um exemplo:

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a>Sum

Calcula a soma de todos os elementos na coleção, ou calcula uma expressão fornecida para todos os elementos na coleção. A seguir está um exemplo:

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a>Exemplo  

O exemplo a seguir mostra como usar o `Aggregate` cláusula para aplicar funções de agregação para um resultado de consulta.  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>Criando funções de agregação definida pelo usuário

 Você pode incluir suas próprias funções de agregação personalizadas em uma expressão de consulta adicionando métodos de extensão para o <xref:System.Collections.Generic.IEnumerable%601> tipo. O método personalizado, em seguida, pode executar um cálculo ou uma operação na coleção enumerável que referenciou sua função de agregação. Para obter mais informações sobre os métodos de extensão, consulte [Métodos de extensão](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
 Por exemplo, o exemplo a seguir mostra uma função de agregação personalizada que calcula o valor mediano de uma coleção de números. Há duas sobrecargas do `Median` método de extensão. A primeira sobrecarga aceita, como entrada, uma coleção do tipo `IEnumerable(Of Double)`. Se o `Median` função de agregação é chamada para um campo de consulta do tipo `Double`, esse método será chamado. A segunda sobrecarga da `Median` método pode ser passado qualquer tipo genérico. A sobrecarga genérica do `Median` método leva um segundo parâmetro que faz referência a `Func(Of T, Double)` expressão lambda para projetar um valor para um tipo (de uma coleção) como o valor correspondente do tipo `Double`. Ela então delega o cálculo do valor mediano para a outra sobrecarga da `Median` método. Para obter mais informações sobre expressões lambda, consulte [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 O exemplo a seguir mostra exemplos de consultas que chamam a `Median` função em uma coleção do tipo de agregação `Integer`e uma coleção do tipo `Double`. A consulta que chama o `Median` função na coleção do tipo de agregação `Double` chama a sobrecarga da `Median` método que aceita, como entrada, uma coleção do tipo `Double`. A consulta que chama o `Median` função na coleção do tipo de agregação `Integer` chama a sobrecarga genérica do `Median` método.  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Consultas](../../../visual-basic/language-reference/queries/index.md)
- [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)
- [Cláusula Group By](../../../visual-basic/language-reference/queries/group-by-clause.md)
