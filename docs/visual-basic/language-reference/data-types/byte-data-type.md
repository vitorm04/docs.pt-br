---
title: Tipo de dados Byte (Visual Basic)
ms.date: 01/31/2018
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02234afc0dc51a2c1338cdd16d1f97765f64b45e
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="byte-data-type-visual-basic"></a>Tipo de dados byte (Visual Basic)
Mantém inteiros sem sinal de 8 bits (1-bytes) que variam de 0 a 255.

## <a name="remarks"></a>Comentários

Use o `Byte` tipo de dados para conter dados binários.  
  
O valor padrão de `Byte` é 0.

## <a name="literal-assignments"></a>Atribuições de literal

Você pode declarar e inicializar uma `Byte` variável atribuindo a ele um literal decimal, hexadecimal literal, um literal octal, ou (começando com Visual Basic 2017) um literal binário. Se o literal de inteiro está fora do intervalo de um `Byte` (ou seja, se ele for menor que <xref:System.Byte.MinValue?displayProperty=nameWithType> ou maior que <xref:System.Byte.MaxValue?displayProperty=nameWithType>), ocorre um erro de compilação.

No exemplo a seguir, inteiros igual à 201 são representados como decimal, hexadecimal, e literais binárias são implicitamente convertidos do [inteiro](integer-data-type.md) para `byte` valores.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Use o prefixo `&h` ou `&H` para denotar um hexadecimal literal, o prefixo `&b` ou `&B` para denotar um literal binário e o prefixo `&o` ou `&O` para denotar um literal octal. Literais decimais não têm nenhum prefixo.

A partir do Visual Basic de 2017, você também pode usar o caractere de sublinhado, `_`, como um separador de dígito para melhorar a legibilidade, como o exemplo a seguir mostra.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

A partir do Visual Basic 15,5, você também pode usar o caractere de sublinhado (`_`) como um separador à esquerda entre o prefixo e os dígitos hexadecimais, binários ou octais. Por exemplo:

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>Dicas de programação

-   **Números negativos.** Porque `Byte` é um tipo sem sinal, ele não pode representar um número negativo. Se você usar o operador unário menos (`-`) ou uma expressão que é avaliada como tipo `Byte`, Visual Basic converte a expressão a ser `Short` primeiro.
  
-   **Conversões de formato.** Quando Visual Basic lê ou grava arquivos, ou quando ele chama DLLs, métodos e propriedades, ele pode converter entre formatos de dados automaticamente. Dados binários armazenados em `Byte` matrizes e variáveis são preservados durante essas conversões de formato. Você não deve usar um `String` variável para dados binários, porque seu conteúdo pode ser corrompido durante a conversão entre ANSI e Unicode formatos.

-   **Ampliação.** O `Byte` tipo de dados amplia a `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, ou `Double`. Isso significa que você pode converter `Byte` para qualquer um desses tipos sem encontrar um <xref:System.OverflowException?displayProperty=nameWithType> erro.
  
-   **Caracteres de tipo.** `Byte`não tem o caractere de tipo literal ou caractere de tipo identificador.

-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.Byte?displayProperty=nameWithType>.

## <a name="example"></a>Exemplo

 No exemplo a seguir, `b` é um `Byte` variável. As instruções demonstram o intervalo da variável e a aplicação de operadores bit shift para ele.

[!code-vb[VbVbalrDataTypes#16](../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/byte-data-type_1.vb)]  

## <a name="see-also"></a>Consulte também

 <xref:System.Byte?displayProperty=nameWithType>  
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
