---
title: Tipo de dados Byte (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b106005ff07f55e05ae66dba94041cd8b5c24bb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732138"
---
# <a name="byte-data-type-visual-basic"></a>Tipo de dados byte (Visual Basic)
Armazena inteiros sem sinal de 8 bits (1-bytes) que variam em valor de 0 a 255.

## <a name="remarks"></a>Comentários

Use o `Byte` tipo de dados para conter dados binários.  
  
O valor padrão de `Byte` é 0.

## <a name="literal-assignments"></a>Atribuições de literal

Você pode declarar e inicializar um `Byte` variável atribuindo a ela um literal decimal, um literal hexadecimal, um literal octal, ou (começando com o Visual Basic 2017) um literal binário. Se o literal inteiro estiver fora do intervalo de um `Byte` (ou seja, se ele for menor que <xref:System.Byte.MinValue?displayProperty=nameWithType> ou maior que <xref:System.Byte.MaxValue?displayProperty=nameWithType>), ocorrerá um erro de compilação.

No exemplo a seguir, inteiros iguais a 201 representados como decimais, hexadecimais e literais binários são implicitamente convertidos de [inteiro](integer-data-type.md) para `byte` valores.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Use o prefixo `&h` ou `&H` a fim de denotar um literal hexadecimal, o prefixo `&b` ou `&B` para indicar um literal binário e o prefixo `&o` ou `&O` para denotar um literal octal. Literais decimais não têm nenhum prefixo.

Começando com o Visual Basic 2017, você pode também usar o caractere de sublinhado, `_`, como um separador de dígitos para melhorar a legibilidade, como o exemplo a seguir mostra.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

Começando com o Visual Basic 15.5, você pode também usar o caractere de sublinhado (`_`) como um separador à esquerda entre o prefixo e os dígitos octais, hexadecimais ou binários. Por exemplo:

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>Dicas de programação

-   **Números negativos.** Porque `Byte` é um tipo sem sinal, ele não pode representar um número negativo. Se você usar o operador unário menos (`-`) ou uma expressão que é avaliada para o tipo `Byte`, Visual Basic converte a expressão para `Short` primeiro.
  
-   **Conversões de formato.** Quando o Visual Basic lê ou grava arquivos, ou quando ele chamar DLLs, métodos e propriedades, ele pode converter entre formatos de dados automaticamente. Dados binários armazenados em `Byte` matrizes e variáveis são preservados durante essas conversões de formato. Você não deve usar um `String` variável para dados binários, porque seu conteúdo pode estar corrompido durante a conversão entre os formatos ANSI e Unicode.

-   **Ampliação.** O `Byte` tipo de dados amplia a `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, ou `Double`. Isso significa que você pode converter `Byte` para qualquer um desses tipos sem encontrar uma <xref:System.OverflowException?displayProperty=nameWithType> erro.
  
-   **Caracteres de tipo.** `Byte` não tem nenhum caractere de tipo literal ou um caractere de tipo identificador.

-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.Byte?displayProperty=nameWithType>.

## <a name="example"></a>Exemplo

 No exemplo a seguir `b` é um `Byte` variável. As instruções demonstram o intervalo da variável e a aplicação de operadores bit shift a ele.

[!code-vb[VbVbalrDataTypes#16](../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/byte-data-type_1.vb)]  

## <a name="see-also"></a>Consulte também

 <xref:System.Byte?displayProperty=nameWithType>  
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/index.md)  
 [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
