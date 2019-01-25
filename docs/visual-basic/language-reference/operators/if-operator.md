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
ms.openlocfilehash: 82dc3e851f1f98ca689acc21f03cbbe68a4e974e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686667"
---
# <a name="if-operator-visual-basic"></a>Operador If (Visual Basic)
Usos de curto-circuito avaliação para retornar condicionalmente um dos dois valores. O `If` operador pode ser chamado com três argumentos ou com dois argumentos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
If( [argument1,] argument2, argument3 )  
```  
  
## <a name="if-operator-called-with-three-arguments"></a>Se o operador de chamada com três argumentos  
 Quando `If` é chamado usando três argumentos, o primeiro argumento deve ser avaliada como um valor que pode ser convertido como um `Boolean`. Que `Boolean` valor determinará qual dos outros dois argumentos é avaliado e retornado. A lista a seguir se aplica somente quando o `If` operador é chamado usando três argumentos.  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`argument1`|Necessário. `Boolean`. Determina qual dos outros argumentos para avaliar e retornar.|  
|`argument2`|Necessário. `Object`. Avaliado e retornado se `argument1` for avaliada como `True`.|  
|`argument3`|Necessário. `Object`. Avaliado e retornado se `argument1` for avaliada como `False` ou se `argument1` é uma [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variável que é avaliada como [nada](../../../visual-basic/language-reference/nothing.md).|  
  
 Uma `If` operador que é chamado com três argumentos funciona como um `IIf` função, exceto pelo fato de que ele usa avaliação curto-circuito. Uma `IIf` função sempre avalia todas as três de seus argumentos, enquanto um `If` operador que tem três argumentos avalia apenas dois deles. A primeira `If` argumento é avaliado e o resultado é convertido como um `Boolean` valor, `True` ou `False`. Se o valor for `True`, `argument2` é avaliada e seu valor é retornado, mas `argument3` não será avaliado. Se o valor da `Boolean` expressão é `False`, `argument3` é avaliada e seu valor é retornado, mas `argument2` não será avaliado. Os exemplos a seguir ilustram o uso do `If` quando três argumentos são usados:  
  
 [!code-vb[VbVbalrOperators#100](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_1.vb)]  
  
 O exemplo a seguir ilustra o valor de avaliação de curto-circuito. O exemplo mostra duas tentativas de dividir variável `number` pela variável `divisor` exceto quando `divisor` é zero. Nesse caso, um 0 deve ser retornado, e deve ser feita nenhuma tentativa de executar a divisão porque resultaria um erro de tempo de execução. Porque o `If` avaliação de curto-circuito do uso de expressões, ela avalia o segundo ou terceiro argumento, dependendo do valor do primeiro argumento. Se o primeiro argumento for true, o divisor não é zero e é seguro avaliar o segundo argumento e executar a divisão. Se o primeiro argumento for false, somente o terceiro argumento é avaliado e 0 é retornado. Portanto, quando o divisor for 0, nenhuma tentativa é feita para executar a divisão e nenhum resultado de erro. No entanto, porque `IIf` não usa avaliação curto-circuito, o segundo argumento é avaliado, mesmo quando o primeiro argumento for false. Isso causa um erro de divisão por zero tempo de execução.  
  
 [!code-vb[VbVbalrOperators#101](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_2.vb)]  
  
## <a name="if-operator-called-with-two-arguments"></a>Se o operador de chamada com dois argumentos  
 O primeiro argumento para `If` pode ser omitido. Isso permite que o operador a ser chamado usando apenas dois argumentos. A lista a seguir se aplica somente quando o `If` operador é chamado com dois argumentos.  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`argument2`|Necessário. `Object`. Deve ser uma referência ou um tipo anulável. Avaliado e retornado quando ele for avaliado como algo diferente de `Nothing`.|  
|`argument3`|Necessário. `Object`. Avaliado e retornado se `argument2` for avaliada como `Nothing`.|  
  
 Quando o `Boolean` argumento for omitido, o primeiro argumento deve ser uma referência ou um tipo anulável. Se o primeiro argumento é avaliado como `Nothing`, o valor do segundo argumento é retornado. Em todos os outros casos, o valor do primeiro argumento é retornado. O exemplo a seguir ilustra como funciona essa avaliação.  
  
 [!code-vb[VbVbalrOperators#102](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_3.vb)]  
  
## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [Tipos de Valor Anulável](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Nothing](../../../visual-basic/language-reference/nothing.md)
