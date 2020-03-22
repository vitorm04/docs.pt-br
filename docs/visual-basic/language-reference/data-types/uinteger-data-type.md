---
title: Tipo de Dados UInteger
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: ccff61608aed797734cb4f5ca0571d7ed73ba98b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400781"
---
# <a name="uinteger-data-type"></a>tipo de dados UInteger

Possui inteiros não assinados de 32 bits (4 bytes) variando em valor de 0 a 4.294.967.295.

## <a name="remarks"></a>Comentários

O `UInteger` tipo de dados fornece o maior valor não assinado na largura de dados mais eficiente.

O valor padrão de `UInteger` é 0.

## <a name="literal-assignments"></a>Atribuições literais

Você pode declarar e `UInteger` inicializar uma variável atribuindo-a um literal decimal, um literal hexadecimal, um literal octal, ou (começando com Visual Basic 2017) um literal binário. Se o literal inteiro estiver fora do intervalo de `UInteger` (ou seja, se for menor que <xref:System.UInt32.MinValue?displayProperty=nameWithType> ou maior que <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.

No exemplo a seguir, inteiros iguais a 3.000.000.000 representados como literais decimais, hexadecimais e binários são atribuídos a valores `UInteger`.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> Você usa `&h` o `&H` prefixo ou para denotar um literal `&b` `&B` hexadecimal, o prefixo ou para denotar um literal binário, e o prefixo `&o` ou `&O` para denotar um literal octal. Literais decimais não têm nenhum prefixo.

A partir do Visual Basic 2017, você `_`também pode usar o caractere sublinhado, como um separador de dígitos para melhorar a legibilidade, como mostra o exemplo a seguir.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

Começando com visual basic 15.5, você também`_`pode usar o caractere sublinhado ( ) como um separador líder entre o prefixo e os dígitos hexadecimal, binário ou octal. Por exemplo: 

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literais numéricos `UI` também `ui` podem incluir o `UInteger` caractere ou [tipo](../../programming-guide/language-features/data-types/type-characters.md) para denotar o tipo de dados, como mostra o exemplo a seguir.

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>Dicas de programação

Os `UInteger` `Integer` tipos de dados fornecem um desempenho ótimo em um processador de`UShort`32 bits, porque os tipos inteiros menores ( , `Short`e `Byte` `SByte`), mesmo que eles usam menos bits, levam mais tempo para carregar, armazenar e buscar.

- **Números Negativos.** Por `UInteger` ser um tipo não assinado, ele não pode representar um número negativo. Se você usar o`-`operador unary minus ( ) `UInteger`em uma expressão que `Long` avalia para digitar, visual basic converte a expressão para primeiro.

- **Conformidade cls.** O `UInteger` tipo de dados não faz parte da [Especificação de Linguagem Comum](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), portanto, o código compatível com CLS não pode consumir um componente que o use.

- **Interop Considerações.** Se você estiver interagindo com componentes não gravados para o .NET Framework, por `uint` exemplo, automação ou objetos COM, tenha em mente que tipos como podem ter uma largura de dados diferente (16 bits) em outros ambientes. Se você estiver passando um argumento de 16 bits para um componente, declare-o como `UShort` em vez de `UInteger` em seu código Visual Basic gerenciado.

- **Alargamento.** O `UInteger` tipo de `Long`dados `ULong` `Decimal`se `Single`expande para, , , e `Double`. Isso significa que `UInteger` você pode converter para <xref:System.OverflowException?displayProperty=nameWithType> qualquer um desses tipos sem encontrar um erro.

- **Digite caracteres.** Anexar os caracteres `UI` do tipo literal `UInteger` a um literal força-o ao tipo de dados. `UInteger`não tem nenhum tipo de caractere identificador.

- **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.UInt32?displayProperty=nameWithType>.

## <a name="see-also"></a>Confira também

- <xref:System.UInt32>
- [Tipos de dados](../../../visual-basic/language-reference/data-types/index.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Como chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
