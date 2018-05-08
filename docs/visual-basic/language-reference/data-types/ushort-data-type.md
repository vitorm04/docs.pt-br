---
title: Tipo de dados UShort (Visual Basic)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 520c21d4df5c340b41a8b1e9055b3fadddfdf6e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ushort-data-type-visual-basic"></a>Tipo de dados UShort (Visual Basic)

Mantém inteiros sem sinal 16 bits (2 bytes) que variam de 0 a 65.535.  
  
## <a name="remarks"></a>Comentários

 Use o `UShort` tipo de dados para conter dados binários muito grandes para `Byte`.  
  
 O valor padrão de `UShort` é 0.  

# <a name="literal-assignments"></a>Atribuições de literal

Você pode declarar e inicializar uma `UShort` variável atribuindo a ele um literal decimal, hexadecimal literal, um literal octal, ou (começando com Visual Basic 2017) um literal binário. Se o literal inteiro estiver fora do intervalo de `UShort` (ou seja, se for menor que <xref:System.UInt16.MinValue?displayProperty=nameWithType> ou maior que <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.

No exemplo a seguir, inteiros igual à 65,034 que são representados como decimal, hexadecimal, e literais binárias são atribuídas a `UShort` valores.
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> Use o prefixo `&h` ou `&H` para denotar um hexadecimal literal, o prefixo `&b` ou `&B` para denotar um literal binário e o prefixo `&o` ou `&O` para denotar um literal octal. Literais decimais não têm nenhum prefixo.

A partir do Visual Basic de 2017, você também pode usar o caractere de sublinhado, `_`, como um separador de dígito para melhorar a legibilidade, como o exemplo a seguir mostra.

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

A partir do Visual Basic 15,5, você também pode usar o caractere de sublinhado (`_`) como um separador à esquerda entre o prefixo e os dígitos hexadecimais, binários ou octais. Por exemplo:

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literais numéricos também podem incluir o `US` ou `us` [caractere de tipo](../../programming-guide\language-features\data-types/type-characters.md) para denotar o `UShort` tipo de dados, como mostra o exemplo a seguir.

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>Dicas de programação
  
-   **Números negativos.** Porque `UShort` é um tipo sem sinal, ele não pode representar um número negativo. Se você usar o operador unário menos (`-`) ou uma expressão que é avaliada como tipo `UShort`, Visual Basic converte a expressão a ser `Integer` primeiro.  
  
-   **Compatibilidade com CLS.** O `UShort` tipo de dados não é parte do [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), então um código compatível com CLS não pode consumir um componente que usa.
  
-   **Ampliação.** O `UShort` tipo de dados amplia a `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, e `Double`. Isso significa que você pode converter `UShort` para qualquer um desses tipos sem encontrar um <xref:System.OverflowException?displayProperty=nameWithType> erro.  
  
-   **Caracteres de tipo.** Acrescentar os caracteres de tipo literal `US` para um literal força-o `UShort` tipo de dados. `UShort` não tem nenhum caractere de tipo identificador.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.UInt16?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.UInt16>  
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Como chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
