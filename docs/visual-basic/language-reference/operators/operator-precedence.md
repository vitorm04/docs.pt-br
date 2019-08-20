---
title: Precedência do operador no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
ms.openlocfilehash: c420a34a18f9e8fb55411a062e6a47ab38e98978
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69611482"
---
# <a name="operator-precedence-in-visual-basic"></a>Precedência do operador no Visual Basic
Quando várias operações ocorrem em uma expressão, cada parte é avaliada e resolvida em uma ordem predeterminada chamada *prioridade do operador*.

## <a name="precedence-rules"></a>Regras de precedência
 Quando as expressões contêm operadores de mais de uma categoria, elas são avaliadas de acordo com as seguintes regras:

- Os operadores aritméticos e de concatenação têm a ordem de precedência descrita na seção a seguir, e todos têm maior precedência do que os operadores de comparação, lógico e bit-a.

- Todos os operadores de comparação têm precedência igual, e todos têm maior precedência do que os operadores lógicos e de bit-inteiro, mas precedência menor do que os operadores aritméticos e de concatenação.

- Os operadores lógicos e bits de bit têm a ordem de precedência descrita na seção a seguir, e todos têm precedência mais baixa do que os operadores aritméticos, de concatenação e de comparação.

- Os operadores com precedência igual são avaliados da esquerda para a direita na ordem em que aparecem na expressão.

## <a name="precedence-order"></a>Ordem de precedência
 Os operadores são avaliados na seguinte ordem de precedência:

### <a name="await-operator"></a>Operador Await
 Expressões

### <a name="arithmetic-and-concatenation-operators"></a>Operadores aritméticos e de concatenação
 Exponenciação`^`()

 Identidade e negação unários `–`(`+`,)

 Multiplicação e divisão de ponto flutuante (`*`, `/`)

 Divisão de inteiro`\`()

 Aritmética de módulo`Mod`()

 Adição e subtração (`+`, `–`)

 Concatenação de cadeia`&`de caracteres ()

 Deslocamento de bit aritmético`<<`( `>>`,)

### <a name="comparison-operators"></a>Operadores de comparação
 Todos os operadores de`=`comparação `<>`( `<`, `<=`, `>=` ,,,,`Is`, ,`IsNot` ,..`TypeOf`. `>` `Like` `Is`)

### <a name="logical-and-bitwise-operators"></a>Operadores lógicos e bit a bit
 Negação (`Not`)

 Conjunção`And`( `AndAlso`,)

 Disjunção inclusiva`Or`( `OrElse`,)

 Disjunção exclusiva (`Xor`)

### <a name="comments"></a>Comentários
 O `=` operador é apenas o operador de comparação de igualdade, não o operador de atribuição.

 O operador de concatenação de`&`cadeia de caracteres () não é um operador aritmético, mas, na precedência, ele é agrupado com os operadores aritméticos.

 Os `Is` operadores `IsNot` e são operadores de comparação de referência de objeto. Eles não comparam os valores de dois objetos; Eles só verificam se duas variáveis de objeto se referem à mesma instância de objeto.

## <a name="associativity"></a>Associatividade
 Quando os operadores de precedência igual aparecem juntos em uma expressão, por exemplo, multiplicação e divisão, o compilador avalia cada operação à medida que a encontra da esquerda para a direita. O exemplo a seguir ilustra essa situação.

```vb
Dim n1 As Integer = 96 / 8 / 4
Dim n2 As Integer = (96 / 8) / 4
Dim n3 As Integer = 96 / (8 / 4)
```

 A primeira expressão avalia a divisão 96/8 (que resulta em 12) e, em seguida, a divisão 12/4, que resulta em três. Como o compilador avalia as operações `n1` do da esquerda para a direita, a avaliação é a mesma quando essa ordem é indicada explicitamente para. `n2` Ambos `n1` e`n2` têm um resultado de três. Por outro lado `n3` , o tem um resultado de 48, porque os parênteses forçam o compilador a avaliar a 8/4 primeiro.

 Devido a esse comportamento, os operadores são considerados *associativos à esquerda* no Visual Basic.

## <a name="overriding-precedence-and-associativity"></a>Substituindo precedência e Associação
 Você pode usar parênteses para forçar algumas partes de uma expressão a serem avaliadas antes de outras. Isso pode substituir a ordem de precedência e a associação à esquerda. Visual Basic sempre executa operações que são colocadas entre parênteses antes das externas. No entanto, entre parênteses, ele mantém precedência comum e associação, a menos que você use parênteses dentro dos parênteses. O exemplo a seguir ilustra essa situação.

```vb
Dim a, b, c, d, e, f, g As Double
a = 8.0
b = 3.0
c = 4.0
d = 2.0
e = 1.0
f = a - b + c / d * e
' The preceding line sets f to 7.0. Because of natural operator
' precedence and associativity, it is exactly equivalent to the
' following line.
f = (a - b) + ((c / d) * e)
' The following line overrides the natural operator precedence
' and left associativity.
g = (a - (b + c)) / (d * e)
' The preceding line sets g to 0.5.
```

## <a name="see-also"></a>Consulte também

- [Operador =](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [Operador Is](../../../visual-basic/language-reference/operators/is-operator.md)
- [Operador IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Operador Like](../../../visual-basic/language-reference/operators/like-operator.md)
- [Operador TypeOf](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Operador Await](../../../visual-basic/language-reference/operators/await-operator.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
