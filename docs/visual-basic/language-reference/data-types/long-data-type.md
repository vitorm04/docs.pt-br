---
title: Tipo de dados Long (Visual Basic)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b3970aad08f2be98d175b4175ef06711bcaf609
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43731755"
---
# <a name="long-data-type-visual-basic"></a>Tipo de dados Long (Visual Basic)

Armazena inteiros de 64 bits (8 bytes) cujo valor varia de -9.223.372.036.854.775.808 por meio de 9.223.372.036.854.775.807 (9.2... E + 18).  
  
## <a name="remarks"></a>Comentários

 Use o `Long` tipo de dados para conter os números inteiros que são muito grandes para caber `Integer` tipo de dados.  
  
 O valor padrão de `Long` é 0.

## <a name="literal-assignments"></a>Atribuições de literal 

Você pode declarar e inicializar um `Long` variável atribuindo a ela um literal decimal, um literal hexadecimal, um literal octal, ou (começando com o Visual Basic 2017) um literal binário. Se o literal inteiro estiver fora do intervalo de `Long` (ou seja, se for menor que <xref:System.Int64.MinValue?displayProperty=nameWithType> ou maior que <xref:System.Int64.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.

No exemplo a seguir, inteiros iguais a 4.294.967.296 representados como literais decimais, hexadecimais e binários são atribuídos a valores `Long`.
  
[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]  

> [!NOTE]
> Use o prefixo `&h` ou `&H` a fim de denotar um literal hexadecimal, o prefixo `&b` ou `&B` para indicar um literal binário e o prefixo `&o` ou `&O` para denotar um literal octal. Literais decimais não têm nenhum prefixo.

Começando com o Visual Basic 2017, você pode também usar o caractere de sublinhado, `_`, como um separador de dígitos para melhorar a legibilidade, como o exemplo a seguir mostra.

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Começando com o Visual Basic 15.5, você pode também usar o caractere de sublinhado (`_`) como um separador à esquerda entre o prefixo e os dígitos octais, hexadecimais ou binários. Por exemplo:

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literais numéricos também podem incluir o `L` [caractere de tipo](../../programming-guide\language-features\data-types/type-characters.md) para denotar o `Long` tipo de dados, como mostra o exemplo a seguir.

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>Dicas de programação

-   **Considerações de interoperabilidade.** Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos Automation ou COM, lembre-se de que `Long` tem uma largura de dados diferente (32 bits) em outros ambientes. Se você estiver passando um argumento de 32 bits para tal componente, declare-o como `Integer` em vez de `Long` no seu novo código do Visual Basic.  
  
-   **Ampliação.** O `Long` tipo de dados amplia a `Decimal`, `Single`, ou `Double`. Isso significa que você pode converter `Long` em qualquer um desses tipos sem a ocorrência de um erro <xref:System.OverflowException?displayProperty=nameWithType>.  
  
-   **Caracteres de tipo.** Acrescentar o caractere de tipo literal `L` a um literal o força ao tipo de dados `Long`. Acrescentar o caractere de tipo identificador `&` a qualquer identificador o força ao tipo `Long`.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.Int64?displayProperty=nameWithType>.  

## <a name="see-also"></a>Consulte também

<xref:System.Int64>
[Tipos de dados](../../../visual-basic/language-reference/data-types/index.md)   
[Tipo de dados inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
[Tipo de dados Short](../../../visual-basic/language-reference/data-types/short-data-type.md)   
[Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
[Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
[Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
