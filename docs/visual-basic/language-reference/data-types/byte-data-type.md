---
title: Tipo de dados Byte
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 347d7e7d0f09e089886bc81bd0be659deaca9b46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344072"
---
# <a name="byte-data-type-visual-basic"></a>Tipo de dados byte (Visual Basic)

Mantém inteiros de 8 bits (1 byte) não assinados que variam em valor de 0 a 255.

## <a name="remarks"></a>Comentários

Use o tipo de dados `Byte` para conter dados binários.  
  
O valor padrão de `Byte` é 0.

## <a name="literal-assignments"></a>Atribuições de literal

Você pode declarar e inicializar uma variável `Byte` atribuindo-lhe um literal decimal, um literal hexadecimal, um literal octal ou (começando com Visual Basic 2017) um literal binário. Se o literal integral estiver fora do intervalo de um `Byte` (ou seja, se for menor que <xref:System.Byte.MinValue?displayProperty=nameWithType> ou maior que <xref:System.Byte.MaxValue?displayProperty=nameWithType>), ocorrerá um erro de compilação.

No exemplo a seguir, números inteiros iguais a 201 que são representados como decimais, hexadecimais e literais binários são convertidos implicitamente de [inteiro](integer-data-type.md) para `byte` valores.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Você usa o prefixo `&h` ou `&H` para indicar um literal hexadecimal, o prefixo `&b` ou `&B` para denotar um literal binário e o prefixo `&o` ou `&O` para indicar um literal octal. Literais decimais não têm nenhum prefixo.

A partir do Visual Basic 2017, você também pode usar o caractere de sublinhado, `_`, como um separador de dígitos para melhorar a legibilidade, como mostra o exemplo a seguir.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

A partir do Visual Basic 15,5, você também pode usar o caractere de sublinhado (`_`) como um separador à esquerda entre o prefixo e os dígitos hexadecimal, binário ou octal. Por exemplo:

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>Dicas de programação

- **Números negativos.** Como `Byte` é um tipo não assinado, ele não pode representar um número negativo. Se você usar o operador menos unário (`-`) em uma expressão avaliada como tipo `Byte`, Visual Basic converterá a expressão para `Short` primeiro.
  
- **Conversões de formato.** Quando Visual Basic lê ou grava arquivos, ou quando chama DLLs, métodos e propriedades, ele pode converter automaticamente entre os formatos de dados. Os dados binários armazenados em `Byte` variáveis e matrizes são preservados durante as conversões de formato. Você não deve usar uma variável `String` para dados binários, porque seu conteúdo pode ser corrompido durante a conversão entre os formatos ANSI e Unicode.

- **Ampliação.** O tipo de dados `Byte` amplia a `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`ou `Double`. Isso significa que você pode converter `Byte` em qualquer um desses tipos sem encontrar um erro de <xref:System.OverflowException?displayProperty=nameWithType>.
  
- **Digite os caracteres.** `Byte` não tem nenhum caractere de tipo literal ou caractere de tipo de identificador.

- **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.Byte?displayProperty=nameWithType>.

## <a name="example"></a>Exemplo

 No exemplo a seguir, `b` é uma variável `Byte`. As instruções demonstram o intervalo da variável e o aplicativo de operadores de deslocamento de bits a ela.

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a>Consulte também

- <xref:System.Byte?displayProperty=nameWithType>
- [Tipos de Dados](../../../visual-basic/language-reference/data-types/index.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
