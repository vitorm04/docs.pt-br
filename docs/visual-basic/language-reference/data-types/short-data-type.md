---
title: Tipo de dados curto
ms.date: 01/31/2018
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: 8dfdfb56de32e4b3a96729b09ccf46a6fee9a424
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343930"
---
# <a name="short-data-type-visual-basic"></a>Tipo de dados Short (Visual Basic)

Mantém números inteiros de 16 bits (2 bytes) assinados que variam em valor de-32.768 até 32.767.  
  
## <a name="remarks"></a>Comentários  

 Use o tipo de dados `Short` para conter valores inteiros que não exigem a largura total dos dados de `Integer`. Em alguns casos, o Common Language Runtime pode empacotar suas variáveis de `Short` em conjunto e economizar o consumo de memória.  
  
 O valor padrão de `Short` é 0.  
  
## <a name="literal-assignments"></a>Atribuições de literal

Você pode declarar e inicializar uma variável `Short` atribuindo-lhe um literal decimal, um literal hexadecimal, um literal octal ou (começando com Visual Basic 2017) um literal binário. Se o literal inteiro estiver fora do intervalo de `Short` (ou seja, se for menor que <xref:System.Int16.MinValue?displayProperty=nameWithType> ou maior que <xref:System.Int16.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.

No exemplo a seguir, números inteiros iguais a 1.034 que são representados como decimais, hexadecimais e literais binários são convertidos implicitamente de [inteiro](integer-data-type.md) para `Short` valores.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> Você usa o prefixo `&h` ou `&H` para indicar um literal hexadecimal, o prefixo `&b` ou `&B` para denotar um literal binário e o prefixo `&o` ou `&O` para indicar um literal octal. Literais decimais não têm nenhum prefixo.

A partir do Visual Basic 2017, você também pode usar o caractere de sublinhado, `_`, como um separador de dígitos para melhorar a legibilidade, como mostra o exemplo a seguir.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

A partir do Visual Basic 15,5, você também pode usar o caractere de sublinhado (`_`) como um separador à esquerda entre o prefixo e os dígitos hexadecimal, binário ou octal. Por exemplo:

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Os literais numéricos também podem incluir o [caractere de tipo](../../programming-guide/language-features/data-types/type-characters.md) `S` para denotar o tipo de dados `Short`, como mostra o exemplo a seguir.

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>Dicas de programação

- **Ampliação.** O tipo de dados `Short` amplia a `Integer`, `Long`, `Decimal`, `Single`ou `Double`. Isso significa que você pode converter `Short` em qualquer um desses tipos sem a ocorrência de um erro <xref:System.OverflowException?displayProperty=nameWithType>.  
  
- **Digite os caracteres.** Acrescentar o caractere de tipo literal `S` a um literal o força ao tipo de dados `Short`. `Short` não tem um caractere de tipo de identificador.  
  
- **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.Int16?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Int16?displayProperty=nameWithType>
- [Tipos de Dados](../../../visual-basic/language-reference/data-types/index.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Tipo de Dados Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Tipo de Dados Long](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
