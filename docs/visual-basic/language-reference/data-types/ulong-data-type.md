---
title: Tipo de Dados ULong
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
ms.openlocfilehash: 3c6cd4086e08b808c158948756b4806f098196b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400697"
---
# <a name="ulong-data-type-visual-basic"></a>ULong data type (Visual Basic)

Possui inteiros não assinados de 64 bits (8 bytes) variando em valor de 0 a 18.446.744.073.709.551.615 (mais de 1,84 vezes 10 ^ 19).

## <a name="remarks"></a>Comentários

Use `ULong` o tipo de dados para conter `UInteger`dados binários muito grandes para , ou os maiores valores inteiros não assinados possíveis.

O valor padrão de `ULong` é 0.

## <a name="literal-assignments"></a>Atribuições literais

Você pode declarar e `ULong` inicializar uma variável atribuindo-a um literal decimal, um literal hexadecimal, um literal octal, ou (começando com Visual Basic 2017) um literal binário. Se o literal inteiro estiver fora do intervalo de `ULong` (ou seja, se for menor que <xref:System.UInt64.MinValue?displayProperty=nameWithType> ou maior que <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.

No exemplo a seguir, inteiros iguais a 7.934.076.125 representados como literais decimais, hexadecimais e binários são atribuídos a valores `ULong`.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> Você usa `&h` o `&H` prefixo ou para denotar um literal `&b` `&B` hexadecimal, o prefixo ou para denotar um literal binário, e o prefixo `&o` ou `&O` para denotar um literal octal. Literais decimais não têm nenhum prefixo.

A partir do Visual Basic 2017, você `_`também pode usar o caractere sublinhado, como um separador de dígitos para melhorar a legibilidade, como mostra o exemplo a seguir.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Começando com visual basic 15.5, você também`_`pode usar o caractere sublinhado ( ) como um separador líder entre o prefixo e os dígitos hexadecimal, binário ou octal. Por exemplo: 

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literais numéricos `UL` também `ul` podem incluir o `ULong` caractere ou [tipo](../../programming-guide/language-features/data-types/type-characters.md) para denotar o tipo de dados, como mostra o exemplo a seguir.

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>Dicas de programação

- **Números Negativos.** Por `ULong` ser um tipo não assinado, ele não pode representar um número negativo. Se você usar o`-`operador unary minus ( ) `ULong`em uma expressão que `Decimal` avalia para digitar, visual basic converte a expressão para primeiro.

- **Conformidade cls.** O `ULong` tipo de dados não faz parte da [Especificação de Linguagem Comum](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), portanto, o código compatível com CLS não pode consumir um componente que o use.

- **Interop Considerações.** Se você estiver interagindo com componentes não gravados para o .NET Framework, por `ulong` exemplo, automação ou objetos COM, tenha em mente que tipos como podem ter uma largura de dados diferente (32 bits) em outros ambientes. Se você estiver passando um argumento de 32 bits para um componente, declare-o como `UInteger` em vez de `ULong` em seu código Visual Basic gerenciado.

  Além disso, a Automação não suporta inteiros de 64 bits no Windows 95, Windows 98, Windows ME ou Windows 2000. Não é possível `ULong` passar um argumento Visual Basic para um componente de Automação nessas plataformas.

- **Alargamento.** O `ULong` tipo de `Decimal`dados `Single`se `Double`expande para, e . Isso significa que `ULong` você pode converter para <xref:System.OverflowException?displayProperty=nameWithType> qualquer um desses tipos sem encontrar um erro.

- **Digite caracteres.** Anexar os caracteres `UL` do tipo literal `ULong` a um literal força-o ao tipo de dados. `ULong`não tem nenhum tipo de caractere identificador.

- **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.UInt64?displayProperty=nameWithType>.

## <a name="see-also"></a>Confira também

- <xref:System.UInt64>
- [Tipos de dados](../../../visual-basic/language-reference/data-types/index.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Como chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
