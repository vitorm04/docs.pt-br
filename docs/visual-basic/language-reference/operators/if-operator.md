---
title: Operador If
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
ms.openlocfilehash: 3b45a5afe331bd00c2b92f8c305351b77bc319cf
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249481"
---
# <a name="if-operator-visual-basic"></a>Operador If (Visual Basic)

Usa avaliação de curto-circuito para retornar condicionalmente um dos dois valores. O `If` operador pode ser chamado com três argumentos ou com dois argumentos.

## <a name="syntax"></a>Sintaxe

```vb
If( [argument1,] argument2, argument3 )
```

## <a name="if-operator-called-with-three-arguments"></a>Se o operador ligou com três argumentos

Quando `If` é chamado usando três argumentos, o primeiro argumento deve avaliar `Boolean`um valor que pode ser lançado como um . Esse `Boolean` valor determinará qual dos outros dois argumentos é avaliado e devolvido. A lista a seguir `If` só se aplica quando o operador é chamado usando três argumentos.

### <a name="parts"></a>Partes

|Termo|Definição|
|---|---|
|`argument1`|Obrigatórios. `Boolean`. Determina qual dos outros argumentos avaliar e retornar.|
|`argument2`|Obrigatórios. `Object`. Avaliado e devolvido `argument1` se avaliado `True`em .|
|`argument3`|Obrigatórios. `Object`. Avaliado e devolvido `argument1` se avalia `False` ou `argument1` se [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) é uma`Boolean` variável anulada que avalia nada . [Nothing](../../../visual-basic/language-reference/nothing.md)|

Um `If` operador que é chamado com `IIf` três argumentos funciona como uma função, exceto que ele usa avaliação de curto-circuito. Uma `IIf` função sempre avalia todos os três argumentos, enquanto um `If` operador que tem três argumentos avalia apenas dois deles. O `If` primeiro argumento é avaliado e o `Boolean` resultado `True` `False`é lançado como um valor, ou . Se o `True`valor `argument2` for, é avaliado e seu `argument3` valor é devolvido, mas não é avaliado. Se o valor `Boolean` da `False` `argument3` expressão for, é avaliado e `argument2` seu valor é devolvido, mas não é avaliado. Os exemplos a seguir `If` ilustram o uso de quando três argumentos são usados:

[!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]

O exemplo a seguir ilustra o valor da avaliação de curto-circuito. O exemplo mostra duas `number` tentativas `divisor` de `divisor` dividir variável por variável, exceto quando é zero. Nesse caso, um 0 deve ser devolvido, e nenhuma tentativa deve ser feita para executar a divisão porque um erro de tempo de execução resultaria. Como `If` a expressão usa avaliação de curto-circuito, avalia o segundo ou o terceiro argumento, dependendo do valor do primeiro argumento. Se o primeiro argumento for verdadeiro, o divisor não é zero e é seguro avaliar o segundo argumento e realizar a divisão. Se o primeiro argumento for falso, apenas o terceiro argumento é avaliado e um 0 é devolvido. Portanto, quando o divisor é 0, nenhuma tentativa é feita para realizar a divisão e nenhum resultado de erro. No entanto, como `IIf` não se utiliza avaliação de curto-circuito, o segundo argumento é avaliado mesmo quando o primeiro argumento é falso. Isso causa um erro de divisão por zero no tempo de execução.

[!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]

## <a name="if-operator-called-with-two-arguments"></a>Se o operador ligou com dois argumentos

O primeiro `If` argumento pode ser omitido. Isso permite que o operador seja chamado usando apenas dois argumentos. A lista a seguir `If` só se aplica quando o operador é chamado com dois argumentos.

### <a name="parts"></a>Partes

|Termo|Definição|
|---|---|
|`argument2`|Obrigatórios. `Object`. Deve ser um tipo de valor de referência ou nulo. Avaliado e devolvido quando avalia qualquer coisa `Nothing`que não seja .|
|`argument3`|Obrigatórios. `Object`. Avaliado e devolvido `argument2` se avaliado `Nothing`em .|

Quando `Boolean` o argumento é omitido, o primeiro argumento deve ser um tipo de valor de referência ou nulo. Se o primeiro argumento `Nothing`avaliar , o valor do segundo argumento é devolvido. Em todos os outros casos, o valor do primeiro argumento é devolvido. O exemplo a seguir ilustra como essa avaliação funciona:

[!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [Tipos de valor anulados](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Nada](../nothing.md)
