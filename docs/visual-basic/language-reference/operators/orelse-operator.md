---
title: Operador OrElse (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- OrElse
- vb.OrElse
dev_langs:
- VB
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
caps.latest.revision: 15
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: bd67ba46145fb20327f3a5f32dbd7d73c9117ff4
ms.lasthandoff: 03/13/2017

---
# <a name="orelse-operator-visual-basic"></a>Operador OrElse (Visual Basic)
Executa a disjunção lógica em duas expressões do curto-circuito.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Qualquer expressão de `Boolean` .  
  
 `expression1`  
 Necessário. Qualquer expressão de `Boolean` .  
  
 `expression2`  
 Necessário. Qualquer expressão de `Boolean` .  
  
## <a name="remarks"></a>Comentários  
 Uma operação lógica será considerada *Short-circuiting* se o código compilado pode ignorar a avaliação de uma expressão, dependendo do resultado da outra expressão. Se o resultado da primeira expressão avaliada determina o resultado final da operação, não é necessário para avaliar a segunda expressão, porque ele não pode alterar o resultado final. Short-circuiting pode melhorar o desempenho se a expressão ignorada é complexa, ou se ela envolve chamadas de procedimento.  
  
 Se uma ou ambas as expressões forem avaliados como `True`, `result` é `True`. A tabela a seguir ilustra como `result` é determinado.  
  
|If `expression1` is|E `expression2` é|O valor de `result` é|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(não avaliado)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>Tipos de Dados  
 O `OrElse` operador é definido somente para o [tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic converte cada operando conforme necessário para `Boolean` e executa a operação completamente em `Boolean`. Se você atribuir o resultado a um tipo numérico, Visual Basic converte do `Boolean` para esse tipo. Isso pode produzir um comportamento inesperado. Por exemplo, `5 OrElse 12` resulta em `–1` quando convertido em `Integer`.  
  
## <a name="overloading"></a>Sobrecarga  
 O [operador ou](../../../visual-basic/language-reference/operators/or-operator.md) e [Operador IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md) podem ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Sobrecarga de `Or` e `IsTrue` operadores afeta o comportamento do `OrElse` operador. Se seu código usa `OrElse` em uma classe ou estrutura que sobrecarrega `Or` e `IsTrue`, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `OrElse` operador para executar uma disjunção lógica em duas expressões. O resultado é um `Boolean` valor que representa se uma das duas expressões são verdadeiras. Se a primeira expressão for `True`, a segunda não será avaliada.  
  
 [!code-vb[VbVbalrOperators&#37;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_1.vb)]  
  
 O exemplo anterior produz resultados de `True`, `True`, e `False` respectivamente. No cálculo de `firstCheck`, a segunda expressão é avaliada não porque a primeira já é `True`. No entanto, a segunda expressão é avaliada no cálculo de `secondCheck`.  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra um `If`... `Then` instrução contendo duas chamadas de procedimento. Se a primeira chamada retornar `True`, o segundo procedimento não é chamado. Isso pode produzir resultados inesperados se o segundo procedimento executa tarefas importantes que sempre devem ser executadas quando esta seção do código é executado.  
  
 [!code-vb[VbVbalrOperators&38;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Operadores lógicos/bit a bit (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operador or](../../../visual-basic/language-reference/operators/or-operator.md)   
 [Operador IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md)   
 [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
