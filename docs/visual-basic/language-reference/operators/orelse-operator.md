---
title: Operador OrElse (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 1ee3c1a5b6089f44742281eb40e2a7e9cb3e2812
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="orelse-operator-visual-basic"></a>Operador OrElse (Visual Basic)
Executa uma disjunção lógica inclusiva em duas expressões do curto-circuito.  
  
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
 Uma operação lógica será considerada *curto-circuito* se o código compilado pode ignorar a avaliação de uma expressão, dependendo do resultado da outra expressão. Se o resultado da primeira expressão avaliada determina o resultado final da operação, não é necessário para avaliar a segunda expressão, porque ele não pode alterar o resultado final. Curto-circuito pode melhorar o desempenho se a expressão ignorada é complexa, ou se ela envolve chamadas de procedimento.  
  
 Se uma ou ambas as expressões são avaliadas como `True`, `result` é `True`. A tabela a seguir ilustra como `result` é determinado.  
  
|Se `expression1` é|E `expression2` é|O valor de `result` é|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(não avaliado)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>Tipos de Dados  
 O `OrElse` operador é definido somente para o [tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic converte cada operando conforme necessário para `Boolean` e executa a operação completamente em `Boolean`. Se você atribuir o resultado a um tipo numérico, Visual Basic converte do `Boolean` a esse tipo. Isso pode produzir um comportamento inesperado. Por exemplo, `5 OrElse 12` resulta em `–1` quando convertido em `Integer`.  
  
## <a name="overloading"></a>Sobrecarga  
 O [operador ou](../../../visual-basic/language-reference/operators/or-operator.md) e [Operador IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Sobrecarga de `Or` e `IsTrue` operadores afeta o comportamento do `OrElse` operador. Se seu código usa `OrElse` em uma classe ou estrutura que sobrecarrega `Or` e `IsTrue`, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `OrElse` operador para executar uma disjunção lógica em duas expressões. O resultado é um `Boolean` valor que representa se uma das duas expressões são verdadeiras. Se a primeira expressão é `True`, a segunda não será avaliada.  
  
 [!code-vb[VbVbalrOperators#37](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_1.vb)]  
  
 O exemplo anterior produz resultados de `True`, `True`, e `False` respectivamente. No cálculo de `firstCheck`, a segunda expressão é avaliada não porque a primeira já é `True`. No entanto, a segunda expressão é avaliada no cálculo de `secondCheck`.  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra um `If`... `Then` instrução que contém duas chamadas de procedimento. Se a primeira chamada retorna `True`, o segundo procedimento não é chamado. Isso pode produzir resultados inesperados se o segundo procedimento executa tarefas importantes que sempre devem ser executadas quando esta seção do código é executado.  
  
 [!code-vb[VbVbalrOperators#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Operadores lógicos/bit a bit (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operador Or](../../../visual-basic/language-reference/operators/or-operator.md)  
 [Operador IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
