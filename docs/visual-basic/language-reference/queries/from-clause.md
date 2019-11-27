---
title: Cláusula From
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: a63fb41fc2b0ad885acf76ad5d56e446922f5b90
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343773"
---
# <a name="from-clause-visual-basic"></a>Cláusula From (Visual Basic)
Especifica uma ou mais variáveis de intervalo e uma coleção a ser consultada.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`element`|Necessária. Uma *variável de intervalo* usada para iterar pelos elementos da coleção. Uma variável de intervalo é usada para fazer referência a cada membro da `collection` à medida que a consulta é iterada por meio do `collection`. Deve ser um tipo enumerável.|  
|`type`|Opcional. O tipo de `element`. Se nenhum `type` for especificado, o tipo de `element` será inferido de `collection`.|  
|`collection`|Necessária. Refere-se à coleção a ser consultada. Deve ser um tipo enumerável.|  
  
## <a name="remarks"></a>Comentários  
 A cláusula `From` é usada para identificar os dados de origem de uma consulta e as variáveis que são usadas para fazer referência a um elemento da coleção de origem. Essas variáveis são chamadas de *variáveis de intervalo*. A cláusula `From` é necessária para uma consulta, exceto quando a cláusula `Aggregate` é usada para identificar uma consulta que retorna apenas resultados agregados. Para obter mais informações, consulte [cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Você pode especificar várias cláusulas `From` em uma consulta para identificar várias coleções a serem unidas. Quando várias coleções são especificadas, elas são iteradas de forma independente ou você pode associá-las se estiverem relacionadas. Você pode unir coleções implicitamente usando a cláusula `Select` ou explicitamente usando as cláusulas `Join` ou `Group Join`. Como alternativa, você pode especificar várias variáveis de intervalo e coleções em uma única cláusula de `From`, com cada variável de intervalo relacionada e uma coleção separada das outras por uma vírgula. O exemplo de código a seguir mostra ambas as opções de sintaxe para a cláusula `From`.  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 A cláusula `From` define o escopo de uma consulta, que é semelhante ao escopo de um loop de `For`. Portanto, cada variável de intervalo `element` no escopo de uma consulta deve ter um nome exclusivo. Como você pode especificar várias cláusulas `From` para uma consulta, as cláusulas subseqüentes `From` podem se referir a variáveis de intervalo na cláusula `From`, ou podem se referir a variáveis de intervalo em uma cláusula `From` anterior. Por exemplo, o exemplo a seguir mostra uma cláusula aninhada `From` em que a coleção na segunda cláusula é baseada em uma propriedade da variável Range na primeira cláusula.  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 Cada cláusula de `From` pode ser seguida por qualquer combinação de cláusulas de consulta adicionais para refinar a consulta. Você pode refinar a consulta das seguintes maneiras:  
  
- Combine várias coleções implicitamente usando as cláusulas `From` e `Select` ou explicitamente usando as cláusulas `Join` ou `Group Join`.  
  
- Use a cláusula `Where` para filtrar o resultado da consulta.  
  
- Classifique o resultado usando a cláusula `Order By`.  
  
- Agrupe resultados semelhantes em conjunto usando a cláusula `Group By`.  
  
- Use a cláusula `Aggregate` para identificar as funções de agregação a serem avaliadas para todo o resultado da consulta.  
  
- Use a cláusula `Let` para introduzir uma variável de iteração cujo valor é determinado por uma expressão em vez de uma coleção.  
  
- Use a cláusula `Distinct` para ignorar os resultados de consulta duplicados.  
  
- Identifique partes do resultado a serem retornadas usando as cláusulas `Skip`, `Take`, `Skip While`e `Take While`.  
  
## <a name="example"></a>Exemplo  
 A expressão de consulta a seguir usa uma cláusula `From` para declarar uma variável de intervalo `cust` para cada objeto `Customer` na coleção de `customers`. A cláusula `Where` usa a variável Range para restringir a saída aos clientes da região especificada. O loop de `For Each` exibe o nome da empresa para cada cliente no resultado da consulta.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a>Consulte também

- [Consultas](../../../visual-basic/language-reference/queries/index.md)
- [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)
- [Cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Cláusula Distinct](../../../visual-basic/language-reference/queries/distinct-clause.md)
- [Cláusula Join](../../../visual-basic/language-reference/queries/join-clause.md)
- [Cláusula Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [Cláusula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Cláusula Let](../../../visual-basic/language-reference/queries/let-clause.md)
- [Cláusula Skip](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Cláusula Take](../../../visual-basic/language-reference/queries/take-clause.md)
- [Cláusula Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md)
