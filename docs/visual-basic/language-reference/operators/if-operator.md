---
title: Operador If (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.IfOperator
- IfOperator
helpviewer_keywords:
- ternary operators [Visual Basic]
- conditional execution
- If expressions [Visual Basic]
- conditional operator [Visual Basic]
- If Operator [Visual Basic]
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
ms.openlocfilehash: 192309a7ca728feb300e867bf2340e669e9da16c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="if-operator-visual-basic"></a>Operador If (Visual Basic)
Usos de curto-circuito avaliação para retornar um de dois valores condicionalmente. O `If` operador pode ser chamado com três argumentos ou com dois argumentos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
If( [argument1,] argument2, argument3 )  
```  
  
## <a name="if-operator-called-with-three-arguments"></a>Se o operador chamado com três argumentos  
 Quando `If` é chamado usando três argumentos, o primeiro argumento deve ser avaliada como um valor que pode ser convertido como um `Boolean`. Que `Boolean` valor determinará qual dos outros dois argumentos é avaliado e retornado. A lista a seguir se aplica somente quando o `If` operador é chamado por meio de três argumentos.  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`argument1`|Necessário. `Boolean`. Determina qual dos outros argumentos para avaliar e retornar.|  
|`argument2`|Necessário. `Object`. Avaliado e retornado se `argument1` é avaliada como `True`.|  
|`argument3`|Necessário. `Object`. Avaliado e retornado se `argument1` é avaliada como `False` ou se `argument1` é um [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variável que é avaliada como [nada](../../../visual-basic/language-reference/nothing.md).|  
  
 Um `If` operador que é chamado com três argumentos funciona como um `IIf` função exceto que ele usa curto-circuito avaliação. Um `IIf` função sempre avalia todas as três argumentos, enquanto um `If` operador que tem três argumentos é avaliada apenas duas delas. A primeira `If` argumento é avaliado e o resultado será convertido como uma `Boolean` valor, `True` ou `False`. Se o valor for `True`, `argument2` é avaliada e seu valor é retornado, mas `argument3` não será avaliada. Se o valor da `Boolean` expressão é `False`, `argument3` é avaliada e seu valor é retornado, mas `argument2` não será avaliada. Os exemplos a seguir ilustram o uso do `If` quando são usados os três argumentos:  
  
 [!code-vb[VbVbalrOperators#100](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_1.vb)]  
  
 O exemplo a seguir ilustra o valor de avaliação de curto-circuito. O exemplo mostra duas tentativas de dividir variável `number` pela variável `divisor` , exceto quando `divisor` é zero. Nesse caso, 0 deve ser retornado, e deve ser feita nenhuma tentativa de executar a divisão porque resultaria um erro de tempo de execução. Porque o `If` avaliação de curto-circuito do uso de expressões, ela avalia o segundo ou o terceiro argumento, dependendo do valor do primeiro argumento. Se o primeiro argumento for true, o divisor não for zero e é seguro avaliar o segundo argumento e executar a divisão. Se o primeiro argumento for false, apenas o terceiro argumento é avaliado e 0 é retornado. Portanto, quando o divisor for 0, nenhuma tentativa de executar a divisão e nenhum resultado de erro. No entanto, como `IIf` não usa avaliação de curto-circuito, o segundo argumento é avaliado, mesmo quando o primeiro argumento é false. Isso causa um erro de divisão por zero tempo de execução.  
  
 [!code-vb[VbVbalrOperators#101](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_2.vb)]  
  
## <a name="if-operator-called-with-two-arguments"></a>Se o operador chamado com dois argumentos  
 O primeiro argumento para `If` pode ser omitido. Isso permite que o operador a ser chamado usando apenas dois argumentos. A lista a seguir se aplica somente quando o `If` operador é chamado com dois argumentos.  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`argument2`|Necessário. `Object`. Deve ser uma referência ou um tipo anulável. Avaliado e retornado quando ele for avaliado como algo diferente de `Nothing`.|  
|`argument3`|Necessário. `Object`. Avaliado e retornado se `argument2` é avaliada como `Nothing`.|  
  
 Quando o `Boolean` argumento for omitido, o primeiro argumento deve ser uma referência ou um tipo anulável. Se o primeiro argumento for avaliado como `Nothing`, o valor do segundo argumento é retornado. Em todos os outros casos, o valor do primeiro argumento será retornado. O exemplo a seguir ilustra como esta avaliação funciona.  
  
 [!code-vb[VbVbalrOperators#102](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_3.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Interaction.IIf%2A>  
 [Tipos de Valor Anulável](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Nothing](../../../visual-basic/language-reference/nothing.md)
