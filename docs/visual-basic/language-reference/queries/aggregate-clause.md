---
title: "Agregar cláusula (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
dev_langs:
- VB
helpviewer_keywords:
- Aggregate clause
- Aggregate statement
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2029a0cc032d3713063006a7c0818c16c4bdcae9
ms.lasthandoff: 03/13/2017

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
|`element`|Necessário. Variável usada para percorrer os elementos da coleção.|  
|`type`|Opcional. O tipo de `element`. Se nenhum tipo for especificado, o tipo de `element` é inferido do `collection`.|  
|`collection`|Necessário. Refere-se a coleção para operar.|  
|`clause`|Opcional. Um ou mais cláusulas de consulta, como um `Where` cláusula para refinar o resultado da consulta para aplicar a cláusula aggregate ou cláusulas.|  
|`expressionList`|Necessário. Uma ou mais delimitada por vírgulas expressões que identificam uma função agregada para aplicar à coleção. Você pode aplicar um alias para uma função agregada para especificar um nome de membro para o resultado da consulta. Se nenhum alias for fornecido, o nome da função de agregação é usado. Para obter exemplos, consulte a seção sobre funções agregadas neste tópico.|  
  
## <a name="remarks"></a>Comentários  
 O `Aggregate` cláusula pode ser usada para incluir funções agregadas em suas consultas. Funções agregadas executam verificações e cálculos sobre um conjunto de valores e retornam um único valor. Você pode acessar o valor calculado usando um membro do tipo do resultado da consulta. As funções agregadas padrão que você pode usar são o `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, e `Sum` funções. Essas funções são familiares aos desenvolvedores que estão familiarizados com agregados em SQL. Eles são descritos na seção a seguir deste tópico.  
  
 O resultado de uma função agregada é incluído no resultado da consulta como um campo do tipo de resultado da consulta. Você pode fornecer um alias para o resultado da função de agregação especificar o nome do membro do tipo do resultado da consulta que conterá o valor agregado. Se nenhum alias for fornecido, o nome da função de agregação é usado.  
  
 O `Aggregate` cláusula pode começar uma consulta, ou pode ser incluída como uma cláusula adicional em uma consulta. Se o `Aggregate` cláusula começa uma consulta, o resultado é um valor único que é o resultado da função de agregação especificada no `Into` cláusula. Se mais de uma função agregada for especificada no `Into` cláusula, a consulta retorna um único tipo com uma propriedade separada para referenciar o resultado de cada função de agregação no `Into` cláusula. Se o `Aggregate` cláusula é incluída como uma cláusula adicional em uma consulta, o tipo retornado na coleção de consultas terá uma propriedade separada para referenciar o resultado de cada função de agregação no `Into` cláusula.  
  
## <a name="aggregate-functions"></a>Funções agregadas  
 A lista a seguir descreve as funções de agregação padrão que podem ser usadas com o `Aggregate` cláusula.  
  
|Função|Descrição|  
|---|---|  
|`All`|Retorna `true` se todos os elementos na coleção satisfazem uma condição especificada; caso contrário, retornará `false`. Veja um exemplo a seguir:<br /><br /> [!code-vb[VbSimpleQuerySamples n º&5;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_1.vb)]|  
|`Any`|Retorna `true` se qualquer elemento da coleção satisfazem uma condição especificada; caso contrário, retornará `false`. Veja um exemplo a seguir:<br /><br /> [!code-vb[VbSimpleQuerySamples n º&6;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_2.vb)]|  
|`Average`|Calcula a média de todos os elementos na coleção, ou calcula uma expressão fornecida para todos os elementos na coleção. Veja um exemplo a seguir:<br /><br /> [!code-vb[VbSimpleQuerySamples&#7;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_3.vb)]|  
|`Count`|Conta o número de elementos na coleção. Você pode fornecer um recurso opcional `Boolean` expressão para contar somente o número de elementos da coleção que satisfazem a uma condição. Veja um exemplo a seguir:<br /><br /> [!code-vb[VbSimpleQuerySamples n º&8;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_4.vb)]|  
|`Group`|Refere-se aos resultados da consulta que são agrupados como resultado de uma `Group By` ou `Group Join` cláusula. O `Group` função é válida somente no `Into` cláusula de um `Group By` ou `Group Join` cláusula. Para obter mais informações e exemplos, consulte [grupo pela cláusula](../../../visual-basic/language-reference/queries/group-by-clause.md) e [cláusula Join do grupo](../../../visual-basic/language-reference/queries/group-join-clause.md).|  
|`LongCount`|Conta o número de elementos na coleção. Você pode fornecer um recurso opcional `Boolean` expressão para contar somente o número de elementos da coleção que satisfazem a uma condição. Retorna o resultado como um `Long`. Para obter um exemplo, consulte o `Count` função de agregação.|  
|`Max`|Calcula o valor máximo da coleção, ou calcula uma expressão fornecida para todos os elementos na coleção. Veja um exemplo a seguir:<br /><br /> [!code-vb[VbSimpleQuerySamples n º&9;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_5.vb)]|  
|`Min`|Calcula o valor mínimo da coleção, ou calcula uma expressão fornecida para todos os elementos na coleção. Veja um exemplo a seguir:<br /><br /> [!code-vb[VbSimpleQuerySamples n º&10;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_6.vb)]|  
|`Sum`|Calcula a soma de todos os elementos na coleção, ou calcula uma expressão fornecida para todos os elementos na coleção. Veja um exemplo a seguir:<br /><br /> [!code-vb[VbSimpleQuerySamples&#15;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_7.vb)]|  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como usar o `Aggregate` cláusula para aplicar funções de agregação a um resultado de consulta.  
  
 [!code-vb[VbSimpleQuerySamples n º&4;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_8.vb)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>Criando funções agregadas definidas pelo usuário  
 Você pode incluir suas próprias funções agregadas personalizadas em uma expressão de consulta adicionando métodos de extensão para o <xref:System.Collections.Generic.IEnumerable%601>tipo.</xref:System.Collections.Generic.IEnumerable%601> O método personalizado pode realizar um cálculo ou operação na coleção enumerável que referenciou sua função de agregação. Para obter mais informações sobre métodos de extensão, consulte [métodos de extensão](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
 Por exemplo, o exemplo de código a seguir mostra uma função de agregação personalizada que calcula o valor mediano de uma coleção de números. Há duas sobrecargas de `Median` método de extensão. A primeira sobrecarga aceita, como entrada, uma coleção do tipo `IEnumerable(Of Double)`. Se o `Median` função agregada é chamada para um campo de consulta do tipo `Double`, esse método será chamado. A segunda sobrecarga do `Median` método pode ser passado a qualquer tipo genérico. A sobrecarga genérica do `Median` método leva um segundo parâmetro que faz referência a `Func(Of T, Double)` expressão lambda para projetar um valor para um tipo (de uma coleção) como o valor correspondente do tipo `Double`. Ele então delega o cálculo do valor mediano para a outra sobrecarga do `Median` método. Para obter mais informações sobre expressões lambda, consulte [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples n º&18;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_9.vb)]  
  
 O seguinte código de exemplo mostra exemplos de consultas que chamam o `Median` função em uma coleção do tipo de agregação `Integer`e uma coleção do tipo `Double`. A consulta que chama o `Median` função na coleção do tipo de agregação `Double` chama a sobrecarga do `Median` método que aceita, como entrada, uma coleção do tipo `Double`. A consulta que chama o `Median` função na coleção do tipo de agregação `Integer` chama a sobrecarga genérica do `Median` método.  
  
 [!code-vb[19 VbSimpleQuerySamples](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_10.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Consultas](../../../visual-basic/language-reference/queries/queries.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Cláusula FROM](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Onde cláusula](../../../visual-basic/language-reference/queries/where-clause.md)   
 [Cláusula Group By](../../../visual-basic/language-reference/queries/group-by-clause.md)
