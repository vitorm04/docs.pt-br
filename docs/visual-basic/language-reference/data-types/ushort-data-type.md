---
title: Tipo de Dados UShort
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
ms.openlocfilehash: 7cdbd5fb192fd5cc1be6260dcdcdb1f30cf3f865
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400690"
---
# <a name="ushort-data-type-visual-basic"></a>UShort tipo de dados (Visual Basic)

Possui inteiros não assinados de 16 bits (2 bytes) variando em valor de 0 a 65.535.  
  
## <a name="remarks"></a>Comentários

 Use `UShort` o tipo de dados para conter `Byte`dados binários muito grandes para .  
  
 O valor padrão de `UShort` é 0.  

## <a name="literal-assignments"></a>Atribuições literais

Você pode declarar e `UShort` inicializar uma variável atribuindo-a um literal decimal, um literal hexadecimal, um literal octal, ou (começando com Visual Basic 2017) um literal binário. Se o literal inteiro estiver fora do intervalo de `UShort` (ou seja, se for menor que <xref:System.UInt16.MinValue?displayProperty=nameWithType> ou maior que <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.

No exemplo a seguir, inteiros iguais a 65.034 que são representados como decimais, hexadecimais e literais binários são atribuídos aos `UShort` valores.
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> Você usa `&h` o `&H` prefixo ou para denotar um literal `&b` `&B` hexadecimal, o prefixo ou para denotar um literal binário, e o prefixo `&o` ou `&O` para denotar um literal octal. Literais decimais não têm nenhum prefixo.

A partir do Visual Basic 2017, você `_`também pode usar o caractere sublinhado, como um separador de dígitos para melhorar a legibilidade, como mostra o exemplo a seguir.

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

Começando com visual basic 15.5, você também`_`pode usar o caractere sublinhado ( ) como um separador líder entre o prefixo e os dígitos hexadecimal, binário ou octal. Por exemplo: 

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literais numéricos `US` também `us` podem incluir o `UShort` caractere ou [tipo](../../programming-guide/language-features/data-types/type-characters.md) para denotar o tipo de dados, como mostra o exemplo a seguir.

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>Dicas de programação
  
- **Números Negativos.** Por `UShort` ser um tipo não assinado, ele não pode representar um número negativo. Se você usar o`-`operador unary minus ( ) `UShort`em uma expressão que `Integer` avalia para digitar, visual basic converte a expressão para primeiro.  
  
- **Conformidade cls.** O `UShort` tipo de dados não faz parte da [Especificação de Linguagem Comum](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), portanto, o código compatível com CLS não pode consumir um componente que o use.
  
- **Alargamento.** O `UShort` tipo de `Integer`dados `UInteger` `Long`se `ULong` `Decimal`expande para, , , , , `Single`, e `Double`. Isso significa que `UShort` você pode converter para <xref:System.OverflowException?displayProperty=nameWithType> qualquer um desses tipos sem encontrar um erro.  
  
- **Digite caracteres.** Anexar os caracteres `US` do tipo literal `UShort` a um literal força-o ao tipo de dados. `UShort`não tem nenhum tipo de caractere identificador.  
  
- **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.UInt16?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Confira também

- <xref:System.UInt16>
- [Tipos de dados](../../../visual-basic/language-reference/data-types/index.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Como chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
