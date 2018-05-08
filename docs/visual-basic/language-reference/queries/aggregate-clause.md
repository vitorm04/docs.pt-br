---
title: Cláusula Aggregate (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: 1db4b7fdcf9c8a38c2c49eca9d874eccea90ab1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="aggregate-clause-visual-basic"></a>Cláusula Aggregate (Visual Basic)
Aplica um ou mais funções de agregação a uma coleção.  
  
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
|`element`|Necessário. Variável usada para percorrer os elementos da coleção.|  
|`type`|Opcional. O tipo de `element`. Se nenhum tipo for especificado, o tipo de `element` é inferido do `collection`.|  
|`collection`|Necessário. Refere-se à coleção para operar.|  
|`clause`|Opcional. Um ou mais cláusulas de consulta, como um `Where` cláusula para refinar o resultado da consulta para aplicar a cláusula aggregate ou cláusulas.|  
|`expressionList`|Necessário. Uma ou mais delimitada por vírgulas expressões que identificam uma função de agregação para aplicar à coleção. Você pode aplicar um alias para uma função de agregação para especificar um nome de membro para o resultado da consulta. Se nenhum alias for fornecido, o nome da função de agregação é usado. Para obter exemplos, consulte a seção sobre funções de agregação neste tópico.|  
  
## <a name="remarks"></a>Comentários  
 O `Aggregate` cláusula pode ser usada para incluir funções agregadas em suas consultas. Funções de agregação executam verificações e cálculos sobre um conjunto de valores e retornam um único valor. Você pode acessar o valor calculado usando um membro do tipo de resultado da consulta. As funções de agregação padrão que você pode usar são o `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, e `Sum` funções. Essas funções são familiares para desenvolvedores que estão familiarizados com agregados em SQL. Eles são descritos na seção a seguir deste tópico.  
  
 O resultado de uma função de agregação é incluído no resultado da consulta como um campo do tipo de resultado da consulta. Você pode fornecer um alias para o resultado da função de agregação especificar o nome do membro do tipo de resultado da consulta que conterá o valor de agregação. Se nenhum alias for fornecido, o nome da função de agregação é usado.  
  
 O `Aggregate` cláusula pode começar uma consulta, ou pode ser incluída como uma cláusula adicional em uma consulta. Se o `Aggregate` cláusula começa uma consulta, o resultado é um valor único que é o resultado da função de agregação especificada no `Into` cláusula. Se mais de uma função de agregação for especificada no `Into` cláusula, a consulta retorna um único tipo com uma propriedade separada para referenciar o resultado de cada função de agregação no `Into` cláusula. Se o `Aggregate` cláusula será incluída como uma cláusula adicional em uma consulta, o tipo retornado na coleção de consultas terá uma propriedade separada para referenciar o resultado de cada função de agregação no `Into` cláusula.  
  
## <a name="aggregate-functions"></a>Funções agregadas  
 A lista a seguir descreve as funções de agregação padrão que podem ser usadas com o `Aggregate` cláusula.  
  
|Função|Descrição|  
|---|---|  
|`All`|Retorna `true` se todos os elementos na coleção satisfazem uma condição especificada; caso contrário, retornará `false`. Veja um exemplo a seguir:<br /><br /> [!code-vb[VbSimpleQuerySamples#5](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_1.vb)]|  
|`Any`|Retorna `true` se qualquer elemento da coleção satisfazem uma condição especificada; caso contrário, retornará `false`. Veja um exemplo a seguir:<br /><br /> [!code-vb[VbSimpleQuerySamples#6](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_2.vb)]|  
|`Average`|Calcula a média de todos os elementos na coleção, ou calcula uma expressão fornecida para todos os elementos na coleção. Veja um exemplo a seguir:<br /><br /> [!code-vb[VbSimpleQuerySamples#7](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_3.vb)]|  
|`Count`|Conta o número de elementos na coleção. Você pode fornecer um recurso opcional `Boolean` expressão para contar somente o número de elementos na coleção que satisfazem uma condição. Veja um exemplo a seguir:<br /><br /> [!code-vb[VbSimpleQuerySamples#8](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_4.vb)]|  
|`Group`|Refere-se aos resultados da consulta que são agrupados como resultado de uma `Group By` ou `Group Join` cláusula. O `Group` função só é válida no `Into` cláusula de um `Group By` ou `Group Join` cláusula. Para obter mais informações e exemplos, consulte [grupo pela cláusula](../../../visual-basic/language-reference/queries/group-by-clause.md) e [cláusula Join do grupo](../../../visual-basic/language-reference/queries/group-join-clause.md).|  
|`LongCount`|Conta o número de elementos na coleção. Você pode fornecer um recurso opcional `Boolean` expressão para contar somente o número de elementos na coleção que satisfazem uma condição. Retorna o resultado como uma `Long`. Para obter um exemplo, consulte o `Count` função de agregação.|  
|`Max`|Calcula o valor máximo da coleção, ou calcula uma expressão fornecida para todos os elementos na coleção. Veja um exemplo a seguir:<br /><br /> [!code-vb[VbSimpleQuerySamples#9](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_5.vb)]|  
|`Min`|Calcula o valor mínimo da coleção, ou calcula uma expressão fornecida para todos os elementos na coleção. Veja um exemplo a seguir:<br /><br /> [!code-vb[VbSimpleQuerySamples#10](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_6.vb)]|  
|`Sum`|Calcula a soma de todos os elementos na coleção, ou calcula uma expressão fornecida para todos os elementos na coleção. Veja um exemplo a seguir:<br /><br /> [!code-vb[VbSimpleQuerySamples#15](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_7.vb)]|  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como usar o `Aggregate` cláusula para aplicar funções de agregação para um resultado de consulta.  
  
 [!code-vb[VbSimpleQuerySamples#4](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_8.vb)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>Criando funções de agregação definida pelo usuário  
 Você pode incluir suas próprias funções de agregação personalizadas em uma expressão de consulta adicionando métodos de extensão para o <xref:System.Collections.Generic.IEnumerable%601> tipo. O método personalizado pode executar um cálculo ou operação na coleção enumerável que referenciou sua função de agregação. Para obter mais informações sobre os métodos de extensão, consulte [Métodos de extensão](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
 Por exemplo, o exemplo de código a seguir mostra uma função de agregação personalizada que calcula o valor mediano de uma coleção de números. Há duas sobrecargas do `Median` método de extensão. A primeira sobrecarga aceita, como entrada, uma coleção do tipo `IEnumerable(Of Double)`. Se o `Median` função de agregação é chamada de um campo de consulta do tipo `Double`, esse método será chamado. A segunda sobrecarga do `Median` método pode ser passado a qualquer tipo genérico. A sobrecarga genérica do `Median` método usa um segundo parâmetro que faz referência a `Func(Of T, Double)` expressão lambda para projetar um valor para um tipo (de uma coleção) como o valor correspondente do tipo `Double`. Ele então delega o cálculo do valor mediano para a outra sobrecarga do `Median` método. Para obter mais informações sobre expressões lambda, consulte [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples#18](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_9.vb)]  
  
 O seguinte código de exemplo mostra exemplos de consultas que chamam o `Median` função em uma coleção do tipo de agregação `Integer`e uma coleção do tipo `Double`. A consulta que chama o `Median` função na coleção do tipo de agregação `Double` chama a sobrecarga do `Median` método que aceita como entrada, uma coleção do tipo `Double`. A consulta que chama o `Median` função na coleção do tipo de agregação `Integer` chama a sobrecarga genérica do `Median` método.  
  
 [!code-vb[VbSimpleQuerySamples#19](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_10.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)  
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Cláusula Group By](../../../visual-basic/language-reference/queries/group-by-clause.md)
