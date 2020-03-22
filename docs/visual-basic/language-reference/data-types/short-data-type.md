---
title: Tipo de Dados Short
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400725"
---
# <a name="short-data-type-visual-basic"></a>Tipo de dados curtos (Visual Basic)

Mantém inteiros assinados de 16 bits (2 bytes) que variam em valor de -32.768 a 32.767.  
  
## <a name="remarks"></a>Comentários  

 Use `Short` o tipo de dados para conter valores inteiros `Integer`que não requerem a largura total dos dados de . Em alguns casos, o tempo `Short` de execução do idioma comum pode embalar suas variáveis de perto e economizar o consumo de memória.  
  
 O valor padrão de `Short` é 0.  
  
## <a name="literal-assignments"></a>Atribuições literais

Você pode declarar e `Short` inicializar uma variável atribuindo-a um literal decimal, um literal hexadecimal, um literal octal, ou (começando com Visual Basic 2017) um literal binário. Se o literal inteiro estiver fora do intervalo de `Short` (ou seja, se for menor que <xref:System.Int16.MinValue?displayProperty=nameWithType> ou maior que <xref:System.Int16.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.

No exemplo a seguir, inteiros iguais a 1.034 que são representados como decimais, hexadecimais e literais binários são implicitamente convertidos de [Inteiro](integer-data-type.md) para `Short` valores.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> Você usa `&h` o `&H` prefixo ou para denotar um literal `&b` `&B` hexadecimal, o prefixo ou para denotar um literal binário, e o prefixo `&o` ou `&O` para denotar um literal octal. Literais decimais não têm nenhum prefixo.

A partir do Visual Basic 2017, você `_`também pode usar o caractere sublinhado, como um separador de dígitos para melhorar a legibilidade, como mostra o exemplo a seguir.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

Começando com visual basic 15.5, você também`_`pode usar o caractere sublinhado ( ) como um separador líder entre o prefixo e os dígitos hexadecimal, binário ou octal. Por exemplo: 

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literais numéricos `S` também podem incluir `Short` o caractere [tipo](../../programming-guide/language-features/data-types/type-characters.md) para denotar o tipo de dados, como mostra o exemplo a seguir.

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>Dicas de programação

- **Alargamento.** O `Short` tipo de `Integer`dados `Long` `Decimal`se `Single`expande para, , , ou `Double`. Isso significa que você pode converter `Short` em qualquer um desses tipos sem a ocorrência de um erro <xref:System.OverflowException?displayProperty=nameWithType>.  
  
- **Digite caracteres.** Acrescentar o caractere de tipo literal `S` a um literal o força ao tipo de dados `Short`. `Short`não tem nenhum tipo de caractere identificador.  
  
- **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.Int16?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Int16?displayProperty=nameWithType>
- [Tipos de dados](../../../visual-basic/language-reference/data-types/index.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Tipo de dados inteiros](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Tipo de Dados Long](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
