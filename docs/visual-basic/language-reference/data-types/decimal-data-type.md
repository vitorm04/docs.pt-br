---
title: Tipo de Dados Decimal
ms.date: 07/20/2015
f1_keywords:
- vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
ms.openlocfilehash: d4d868ba7c05cf3c2d538de1217231df91d4f43d
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243317"
---
# <a name="decimal-data-type-visual-basic"></a>Tipo de dados decimal (Visual Basic)

Mantém valores de 128 bits (16 bytes) assinados que representam números inteiros de 96 bits (12 bytes) elevados a uma potência variável de 10. O fator de dimensionamento especifica o número de dígitos à direita do ponto decimal; varia de 0 a 28. Com uma escala de 0 (sem casas decimais), o maior valor possível é +/-79.228.162.514,264,337.593.543.950,335 (+/-7.922816251426437593543950335E+28). Com 28 casas decimais, o maior valor é +/-7,92281625142643337593543950335, e o menor valor não zero é +/-000000000000000000000000001 (+/-1E-28).

## <a name="remarks"></a>Comentários

O `Decimal` tipo de dados fornece o maior número de dígitos significativos para um número. Suporta até 29 dígitos significativos e pode representar valores superiores a 7,9228 x 10^28. É particularmente adequado para cálculos, como financeiros, que requerem um grande número de dígitos, mas não podem tolerar erros de arredondamento.

O valor padrão de `Decimal` é 0.

## <a name="programming-tips"></a>Dicas de programação

- **Precisão.** `Decimal`não é um tipo de dados de ponto flutuante. A `Decimal` estrutura possui um valor inteiro binário, juntamente com um bit de sinal e um fator de dimensionamento inteiro que especifica qual parte do valor é uma fração decimal. Por causa `Decimal` disso, os números têm uma representação`Single` mais `Double`precisa na memória do que os tipos de pontos flutuantes (e ).

- **Desempenho.** O `Decimal` tipo de dados é o mais lento de todos os tipos numéricos. Você deve pesar a importância da precisão contra o desempenho antes de escolher um tipo de dados.

- **Alargamento.** O `Decimal` tipo de `Single` dados `Double`se expande para ou . Isso significa que `Decimal` você pode converter para <xref:System.OverflowException?displayProperty=nameWithType> qualquer um desses tipos sem encontrar um erro.

- **Seguindo zeros.** Visual Basic não armazena zeros `Decimal` em um literal. No entanto, uma `Decimal` variável preserva quaisquer zeros de arrasto adquiridos computacionalmente. O exemplo a seguir ilustra isto.

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  A saída `MsgBox` do exemplo anterior é a seguinte:

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- **Digite caracteres.** Acrescentar o caractere de tipo literal `D` a um literal o força ao tipo de dados `Decimal`. Acrescentar o caractere de tipo identificador `@` a qualquer identificador o força ao tipo `Decimal`.

- **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.Decimal?displayProperty=nameWithType>.

## <a name="range"></a>Intervalo

 Você pode precisar `D` usar o caractere do tipo `Decimal` para atribuir um grande valor a uma variável ou constante. Este requisito é porque o compilador `Long` interpreta um literal como se um caractere de tipo literal seguisse o literal, como mostra o exemplo a seguir.

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

A declaração para `bigDec1` não produz um estouro porque o valor atribuído a `Long`ela está dentro do intervalo para . O `Long` valor pode ser `Decimal` atribuído à variável.

A declaração para `bigDec2` gera um erro de estouro porque o valor `Long`atribuído a ela é muito grande para . Como o literal numérico não pode `Long`ser interpretado como um, `Decimal` não pode ser atribuído à variável.

Para `bigDec3`, o `D` caractere tipo literal resolve o problema forçando o `Decimal` compilador a `Long`interpretar o literal como um em vez de como um .

## <a name="see-also"></a>Confira também

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [Tipos de dados](../../../visual-basic/language-reference/data-types/index.md)
- [Tipo de Dados Simples](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [Tipo de Dados Duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
