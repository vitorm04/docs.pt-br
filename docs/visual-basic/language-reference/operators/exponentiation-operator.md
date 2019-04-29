---
title: Operador ^ (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponentiation
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
ms.openlocfilehash: 54de9c91d4e166b8ca1733952dfa9c98ebf11ffe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778483"
---
# <a name="-operator-visual-basic"></a>Operador ^ (Visual Basic)

Eleva um número à potência de outro número.

## <a name="syntax"></a>Sintaxe

```
number ^ exponent
```

## <a name="parts"></a>Partes

`number`\
Necessário. Qualquer expressão numérica.

`exponent`\
Necessário. Qualquer expressão numérica.

## <a name="result"></a>Resultado

O resultado será `number` elevado à potência de `exponent`, sempre como um `Double` valor.

## <a name="supported-types"></a>Tipos com suporte

`Double`. Operandos de qualquer outro tipo são convertidos em `Double`.

## <a name="remarks"></a>Comentários

Visual Basic sempre executa exponenciação na [tipo de dados Double](../../../visual-basic/language-reference/data-types/double-data-type.md).

O valor de `exponent` pode ser fracionário, negativo, ou ambos.

Quando mais de um expoente é executada em uma única expressão, o `^` operador é avaliado como ele é encontrado da esquerda para a direita.

> [!NOTE]
> O `^` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).

## <a name="example"></a>Exemplo

O exemplo a seguir usa o `^` operador para elevar um número à potência de um expoente. O resultado é o primeiro operando elevado à potência do segundo.

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

O exemplo anterior produz os seguintes resultados:

`exp1` é definido como 4 (2 ao quadrado).

`exp2` é definido como 19683 (3 ao cubo, em seguida, esse valor ao cubo).

`exp3` é definido como -125 (-5 cúbico).

`exp4` é definido como 625 (-5 à quarta potência).

`exp5` é definido como 2 (raiz cúbica de 8).

`exp6` é definido como 0,5 (1.0 dividido pela raiz cúbica de 8).

Observe a importância dos parênteses nas expressões no exemplo anterior. Por causa da *precedência do operador*, Visual Basic normalmente executa o `^` operador antes de qualquer outro, até mesmo o operador unário `–` operador. Se `exp4` e `exp6` tinha sido calculada sem parênteses, deve ter produzido os seguintes resultados:

`exp4 = -5 ^ 4` será calculado como – (5 à quarta potência), que resultaria em-625.

`exp6 = 8 ^ -1.0 / 3.0` será calculado como (8 para a potência de-1 ou 0,125) dividido por 3.0, o que resultaria em 0.041666666666666666666666666666667.

## <a name="see-also"></a>Consulte também

- [Operador ^=](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
