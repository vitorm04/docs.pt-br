---
title: Tipo de dados UShort
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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343860"
---
# <a name="ushort-data-type-visual-basic"></a>Tipo de dados UShort (Visual Basic)

Mantém inteiros de 16 bits (2 bytes) não assinados, variando no valor de 0 a 65.535.  
  
## <a name="remarks"></a>Comentários

 Use o tipo de dados `UShort` para conter dados binários muito grandes para `Byte`.  
  
 O valor padrão de `UShort` é 0.  

## <a name="literal-assignments"></a>Atribuições de literal

Você pode declarar e inicializar uma variável `UShort` atribuindo-lhe um literal decimal, um literal hexadecimal, um literal octal ou (começando com Visual Basic 2017) um literal binário. Se o literal inteiro estiver fora do intervalo de `UShort` (ou seja, se for menor que <xref:System.UInt16.MinValue?displayProperty=nameWithType> ou maior que <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.

No exemplo a seguir, números inteiros iguais a 65.034 que são representados como decimais, hexadecimais e literais binários são atribuídos a `UShort` valores.
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> Você usa o prefixo `&h` ou `&H` para indicar um literal hexadecimal, o prefixo `&b` ou `&B` para denotar um literal binário e o prefixo `&o` ou `&O` para indicar um literal octal. Literais decimais não têm nenhum prefixo.

A partir do Visual Basic 2017, você também pode usar o caractere de sublinhado, `_`, como um separador de dígitos para melhorar a legibilidade, como mostra o exemplo a seguir.

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

A partir do Visual Basic 15,5, você também pode usar o caractere de sublinhado (`_`) como um separador à esquerda entre o prefixo e os dígitos hexadecimal, binário ou octal. Por exemplo:

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Os literais numéricos também podem incluir o `US` ou `us` [caractere de tipo](../../programming-guide/language-features/data-types/type-characters.md) para denotar o tipo de dados `UShort`, como mostra o exemplo a seguir.

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>Dicas de programação
  
- **Números negativos.** Como `UShort` é um tipo não assinado, ele não pode representar um número negativo. Se você usar o operador menos unário (`-`) em uma expressão avaliada como tipo `UShort`, Visual Basic converterá a expressão para `Integer` primeiro.  
  
- **Conformidade com CLS.** O tipo de dados `UShort` não faz parte do [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), portanto o código em conformidade com CLS não pode consumir um componente que o utiliza.
  
- **Ampliação.** O tipo de dados `UShort` amplia a `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`e `Double`. Isso significa que você pode converter `UShort` em qualquer um desses tipos sem encontrar um erro de <xref:System.OverflowException?displayProperty=nameWithType>.  
  
- **Digite os caracteres.** Acrescentar os caracteres do tipo literal `US` a um literal o força ao tipo de dados `UShort`. `UShort` não tem um caractere de tipo de identificador.  
  
- **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.UInt16?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.UInt16>
- [Tipos de Dados](../../../visual-basic/language-reference/data-types/index.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Como chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
