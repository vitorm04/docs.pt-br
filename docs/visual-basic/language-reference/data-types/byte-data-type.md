---
title: Tipo de Dados Byte
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 347d7e7d0f09e089886bc81bd0be659deaca9b46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400739"
---
# <a name="byte-data-type-visual-basic"></a>Tipo de dados byte (Visual Basic)

Mantém inteiros não assinados de 8 bits (1 byte) que variam em valor de 0 a 255.

## <a name="remarks"></a>Comentários

Use `Byte` o tipo de dados para conter dados binários.  
  
O valor padrão de `Byte` é 0.

## <a name="literal-assignments"></a>Atribuições literais

Você pode declarar e `Byte` inicializar uma variável atribuindo-a um literal decimal, um literal hexadecimal, um literal octal, ou (começando com Visual Basic 2017) um literal binário. Se o literal integral estiver `Byte` fora do intervalo de a <xref:System.Byte.MinValue?displayProperty=nameWithType> (isto é, se for menor ou maior que), ocorre um erro de <xref:System.Byte.MaxValue?displayProperty=nameWithType>compilação.

No exemplo a seguir, inteiros iguais a 201 que são representados como decimais, hexadecimais e literais binários são implicitamente convertidos de [Inteiro](integer-data-type.md) para `byte` valores.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Você usa `&h` o `&H` prefixo ou para denotar um literal `&b` `&B` hexadecimal, o prefixo ou para denotar um literal binário, e o prefixo `&o` ou `&O` para denotar um literal octal. Literais decimais não têm nenhum prefixo.

A partir do Visual Basic 2017, você `_`também pode usar o caractere sublinhado, como um separador de dígitos para melhorar a legibilidade, como mostra o exemplo a seguir.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

Começando com visual basic 15.5, você também`_`pode usar o caractere sublinhado ( ) como um separador líder entre o prefixo e os dígitos hexadecimal, binário ou octal. Por exemplo: 

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>Dicas de programação

- **Números Negativos.** Por `Byte` ser um tipo não assinado, ele não pode representar um número negativo. Se você usar o`-`operador unary minus ( ) `Byte`em uma expressão que `Short` avalia para digitar, visual basic converte a expressão para primeiro.
  
- **Conversões de formato.** Quando o Visual Basic lê ou grava arquivos, ou quando ele chama DLLs, métodos e propriedades, ele pode converter automaticamente entre formatos de dados. Os dados binários armazenados em `Byte` variáveis e matrizes são preservados durante tais conversões de formato. Você não deve `String` usar uma variável para dados binários, pois seu conteúdo pode ser corrompido durante a conversão entre formatos ANSI e Unicode.

- **Alargamento.** O `Byte` tipo de `Short`dados `UShort` `Integer`se `UInteger` `Long`expande para, , , `ULong`, , , `Decimal`, `Single`ou `Double`. Isso significa que `Byte` você pode converter para <xref:System.OverflowException?displayProperty=nameWithType> qualquer um desses tipos sem encontrar um erro.
  
- **Digite caracteres.** `Byte`não tem caractere de tipo literal ou tipo identificador.

- **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.Byte?displayProperty=nameWithType>.

## <a name="example"></a>Exemplo

 No exemplo a `b` seguir, está uma `Byte` variável. As declarações demonstram o alcance da variável e a aplicação de operadores de bit-shift para ela.

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a>Confira também

- <xref:System.Byte?displayProperty=nameWithType>
- [Tipos de dados](../../../visual-basic/language-reference/data-types/index.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
