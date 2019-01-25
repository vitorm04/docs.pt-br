---
title: Tipo de dados ULong (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
ms.openlocfilehash: 82a2badc1bb22a55f753c9075562db3a5ee0d234
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522954"
---
# <a name="ulong-data-type-visual-basic"></a>Tipo de dados ULong (Visual Basic)

Armazena inteiros sem sinal de 64 bits (8 bytes) variando de 0 a 18.446.744.073.709.551.615 (mais de 1,84 vezes 10 ^ 19).  
  
## <a name="remarks"></a>Comentários

Use o `ULong` tipo de dados para conter dados binários muito grandes para `UInteger`, ou valores inteiros sem sinal de maior possível.  
  
O valor padrão de `ULong` é 0.

## <a name="literal-assignments"></a>Atribuições de literal

Você pode declarar e inicializar um `ULong` variável atribuindo a ela um literal decimal, um literal hexadecimal, um literal octal, ou (começando com o Visual Basic 2017) um literal binário. Se o literal inteiro estiver fora do intervalo de `ULong` (ou seja, se for menor que <xref:System.UInt64.MinValue?displayProperty=nameWithType> ou maior que <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.

No exemplo a seguir, inteiros iguais a 7.934.076.125 representados como literais decimais, hexadecimais e binários são atribuídos a valores `ULong`.
  
[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE] 
> Use o prefixo `&h` ou `&H` a fim de denotar um literal hexadecimal, o prefixo `&b` ou `&B` para indicar um literal binário e o prefixo `&o` ou `&O` para denotar um literal octal. Literais decimais não têm nenhum prefixo.

Começando com o Visual Basic 2017, você pode também usar o caractere de sublinhado, `_`, como um separador de dígitos para melhorar a legibilidade, como o exemplo a seguir mostra.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Começando com o Visual Basic 15.5, você pode também usar o caractere de sublinhado (`_`) como um separador à esquerda entre o prefixo e os dígitos octais, hexadecimais ou binários. Por exemplo:

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literais numéricos também podem incluir o `UL` ou `ul` [caractere de tipo](../../programming-guide/language-features/data-types/type-characters.md) para denotar o `ULong` tipo de dados, como mostra o exemplo a seguir.

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>Dicas de programação
  
-   **Números negativos.** Porque `ULong` é um tipo sem sinal, ele não pode representar um número negativo. Se você usar o operador unário menos (`-`) ou uma expressão que é avaliada para o tipo `ULong`, Visual Basic converte a expressão para `Decimal` primeiro.  
  
-   **Conformidade com CLS.** O `ULong` tipo de dados não é parte do [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), então um código compatível com CLS não pode consumir um componente que usa-o.  
  
-   **Considerações de interoperabilidade.** Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos Automation ou COM, tenha em mente que tipos como `ulong` pode ter uma largura de dados diferente (32 bits) em outros ambientes. Se você estiver passando um argumento de 32 bits para tal componente, declare-o como `UInteger` em vez de `ULong` no seu código gerenciado do Visual Basic.  
  
     Além disso, automação não dá suporte a inteiros de 64 bits no Windows 95, Windows 98, Windows ME ou Windows 2000. Você não pode passar um Visual Basic `ULong` argumento para um componente de automação nessas plataformas.  
  
-   **Ampliação.** O `ULong` tipo de dados amplia a `Decimal`, `Single`, e `Double`. Isso significa que você pode converter `ULong` para qualquer um desses tipos sem encontrar uma <xref:System.OverflowException?displayProperty=nameWithType> erro.  
  
-   **Caracteres de tipo.** Acrescentar os caracteres de tipo literal `UL` a um literal o força ao `ULong` tipo de dados. `ULong` não tem nenhum caractere de tipo de identificador.
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.UInt64?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.UInt64>
- [Tipos de Dados](../../../visual-basic/language-reference/data-types/index.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Como: chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
