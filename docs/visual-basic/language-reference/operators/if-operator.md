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
ms.openlocfilehash: 483b58dd9c79c716fdc3d272cf699e33dec9c671
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799019"
---
# <a name="if-operator-visual-basic"></a>Operador If (Visual Basic)

Usa a avaliação de circuito curto para retornar condicionalmente um dos dois valores. O operador `If` pode ser chamado com três argumentos ou com dois argumentos.

## <a name="syntax"></a>Sintaxe

```vb
If( [argument1,] argument2, argument3 )
```

## <a name="if-operator-called-with-three-arguments"></a>Operador If chamado com três argumentos

Quando `If` é chamado usando três argumentos, o primeiro argumento deve ser avaliado como um valor que pode ser convertido como um `Boolean`. Esse valor `Boolean` determinará quais dos outros dois argumentos serão avaliados e retornados. A lista a seguir se aplica somente quando o operador de `If` é chamado usando três argumentos.

### <a name="parts"></a>Partes

|Termo|Definição|
|---|---|
|`argument1`|Necessário. `Boolean` Determina quais dos outros argumentos a serem avaliados e retornados.|
|`argument2`|Necessário. `Object` Avaliado e retornado se `argument1` for avaliada como `True`.|
|`argument3`|Necessário. `Object` Avaliado e retornado se `argument1` for avaliada como `False` ou se `argument1` for uma variável de`Boolean` [anulável](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) que é avaliada como [Nothing](../../../visual-basic/language-reference/nothing.md).|

Um operador de `If` que é chamado com três argumentos funciona como uma função `IIf`, exceto pelo fato de que ele usa a avaliação de circuito curto. Uma função `IIf` sempre avalia todos os três argumentos, enquanto um operador de `If` que tem três argumentos avalia apenas dois deles. O primeiro argumento `If` é avaliado e o resultado é convertido como um valor de `Boolean`, `True` ou `False`. Se o valor for `True`, `argument2` será avaliado e seu valor será retornado, mas `argument3` não será avaliado. Se o valor da expressão de `Boolean` for `False`, `argument3` será avaliado e seu valor será retornado, mas `argument2` não será avaliado. Os exemplos a seguir ilustram o uso de `If` quando três argumentos são usados:

[!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]

O exemplo a seguir ilustra o valor da avaliação de circuito curto. O exemplo mostra duas tentativas de dividir a variável `number` por variável `divisor`, exceto quando `divisor` é zero. Nesse caso, um 0 deve ser retornado e nenhuma tentativa deve ser feita para executar a divisão porque ocorreria um erro em tempo de execução. Como a expressão de `If` usa uma avaliação de curto-circuito, ela avalia o segundo ou o terceiro argumento, dependendo do valor do primeiro argumento. Se o primeiro argumento for true, o divisor não será zero e será seguro avaliar o segundo argumento e executar a divisão. Se o primeiro argumento for false, somente o terceiro argumento será avaliado e um 0 será retornado. Portanto, quando o divisor é 0, nenhuma tentativa é feita para executar a divisão e nenhum resultado de erro. No entanto, como `IIf` não usa a avaliação de curto-circuito, o segundo argumento é avaliado mesmo quando o primeiro argumento é falso. Isso causa um erro de divisão por zero em tempo de execução.

[!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]

## <a name="if-operator-called-with-two-arguments"></a>Operador If chamado com dois argumentos

O primeiro argumento para `If` pode ser omitido. Isso permite que o operador seja chamado usando apenas dois argumentos. A lista a seguir se aplica somente quando o operador de `If` é chamado com dois argumentos.

### <a name="parts"></a>Partes

|Termo|Definição|
|---|---|
|`argument2`|Necessário. `Object` Deve ser um tipo de referência ou anulável. Avaliado e retornado quando ele é avaliado como algo diferente de `Nothing`.|
|`argument3`|Necessário. `Object` Avaliado e retornado se `argument2` for avaliada como `Nothing`.|

Quando o argumento de `Boolean` é omitido, o primeiro argumento deve ser um tipo de referência ou anulável. Se o primeiro argumento for avaliado como `Nothing`, o valor do segundo argumento será retornado. Em todos os outros casos, o valor do primeiro argumento é retornado. O exemplo a seguir ilustra como essa avaliação funciona:

[!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [Tipos de Valor Anulável](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Nothing](../nothing.md)
