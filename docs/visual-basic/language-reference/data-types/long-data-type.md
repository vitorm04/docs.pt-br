---
title: Tipo de Dados Long
ms.date: 01/31/2018
f1_keywords:
- vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
ms.openlocfilehash: 16d7409c802e97b1f33474d810134db4d9f0ad6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400809"
---
# <a name="long-data-type-visual-basic"></a>Tipo de dados longos (Visual Basic)

Mantém-se assinado 64 bits (8 bytes) inteiros que variam em valor de -9.223.372.036.854.775.808 a 9.223.372.036.854.775.807 (9.2...E+18).

## <a name="remarks"></a>Comentários

Use `Long` o tipo de dados para conter números inteiros `Integer` que são muito grandes para se encaixar no tipo de dados.

O valor padrão de `Long` é 0.

## <a name="literal-assignments"></a>Atribuições literais

Você pode declarar e `Long` inicializar uma variável atribuindo-a um literal decimal, um literal hexadecimal, um literal octal, ou (começando com Visual Basic 2017) um literal binário. Se o literal inteiro estiver fora do intervalo de `Long` (ou seja, se for menor que <xref:System.Int64.MinValue?displayProperty=nameWithType> ou maior que <xref:System.Int64.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.

No exemplo a seguir, inteiros iguais a 4.294.967.296 representados como literais decimais, hexadecimais e binários são atribuídos a valores `Long`.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> Você usa `&h` o `&H` prefixo ou para denotar um literal `&b` `&B` hexadecimal, o prefixo ou para denotar um literal binário, e o prefixo `&o` ou `&O` para denotar um literal octal. Literais decimais não têm nenhum prefixo.

A partir do Visual Basic 2017, você `_`também pode usar o caractere sublinhado, como um separador de dígitos para melhorar a legibilidade, como mostra o exemplo a seguir.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Começando com visual basic 15.5, você também`_`pode usar o caractere sublinhado ( ) como um separador líder entre o prefixo e os dígitos hexadecimal, binário ou octal. Por exemplo: 

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literais numéricos `L` também podem incluir `Long` o caractere [tipo](../../programming-guide/language-features/data-types/type-characters.md) para denotar o tipo de dados, como mostra o exemplo a seguir.

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>Dicas de programação

- **Interop Considerações.** Se você estiver interagindo com componentes não gravados para o .NET `Long` Framework, por exemplo Automação ou objetos COM, lembre-se que tem uma largura de dados diferente (32 bits) em outros ambientes. Se você estiver passando um argumento de 32 bits para um componente, declare-o como `Integer` em vez de `Long` em seu novo código Visual Basic.

- **Alargamento.** O `Long` tipo de `Decimal`dados `Single`se `Double`expande para, ou . Isso significa que você pode converter `Long` em qualquer um desses tipos sem a ocorrência de um erro <xref:System.OverflowException?displayProperty=nameWithType>.

- **Digite caracteres.** Acrescentar o caractere de tipo literal `L` a um literal o força ao tipo de dados `Long`. Acrescentar o caractere de tipo identificador `&` a qualquer identificador o força ao tipo `Long`.

- **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.Int64?displayProperty=nameWithType>.

## <a name="see-also"></a>Confira também

- <xref:System.Int64>
- [Tipos de dados](../../../visual-basic/language-reference/data-types/index.md)
- [Tipo de dados inteiros](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Tipo de Dados Short](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
