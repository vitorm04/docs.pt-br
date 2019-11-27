---
title: Tipo de dados UInteger
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: ccff61608aed797734cb4f5ca0571d7ed73ba98b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343896"
---
# <a name="uinteger-data-type"></a>tipo de dados UInteger

Mantém inteiros de 32 bits (4 bytes) não assinados, variando no valor de 0 a 4.294.967.295.

## <a name="remarks"></a>Comentários

O tipo de dados `UInteger` fornece o maior valor não assinado na largura de dados mais eficiente.

O valor padrão de `UInteger` é 0.

## <a name="literal-assignments"></a>Atribuições de literal

Você pode declarar e inicializar uma variável `UInteger` atribuindo-lhe um literal decimal, um literal hexadecimal, um literal octal ou (começando com Visual Basic 2017) um literal binário. Se o literal inteiro estiver fora do intervalo de `UInteger` (ou seja, se for menor que <xref:System.UInt32.MinValue?displayProperty=nameWithType> ou maior que <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.

No exemplo a seguir, inteiros iguais a 3.000.000.000 representados como literais decimais, hexadecimais e binários são atribuídos a valores `UInteger`.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> Você usa o prefixo `&h` ou `&H` para indicar um literal hexadecimal, o prefixo `&b` ou `&B` para denotar um literal binário e o prefixo `&o` ou `&O` para indicar um literal octal. Literais decimais não têm nenhum prefixo.

A partir do Visual Basic 2017, você também pode usar o caractere de sublinhado, `_`, como um separador de dígitos para melhorar a legibilidade, como mostra o exemplo a seguir.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

A partir do Visual Basic 15,5, você também pode usar o caractere de sublinhado (`_`) como um separador à esquerda entre o prefixo e os dígitos hexadecimal, binário ou octal. Por exemplo:

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Os literais numéricos também podem incluir o `UI` ou `ui` [caractere de tipo](../../programming-guide/language-features/data-types/type-characters.md) para denotar o tipo de dados `UInteger`, como mostra o exemplo a seguir.

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>Dicas de programação

Os tipos de dados `UInteger` e `Integer` fornecem um desempenho ideal em um processador de 32 bits, porque os tipos de inteiro menores (`UShort`, `Short`, `Byte`e `SByte`), embora usem menos bits, levam mais tempo para carregar, armazenar e buscar.

- **Números negativos.** Como `UInteger` é um tipo não assinado, ele não pode representar um número negativo. Se você usar o operador menos unário (`-`) em uma expressão avaliada como tipo `UInteger`, Visual Basic converterá a expressão para `Long` primeiro.

- **Conformidade com CLS.** O tipo de dados `UInteger` não faz parte do [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), portanto o código em conformidade com CLS não pode consumir um componente que o utiliza.

- **Considerações sobre interoperabilidade.** Se você estiver fazendo a interface com componentes não escritos para o .NET Framework, por exemplo, automação ou objetos COM, tenha em mente que tipos como `uint` podem ter uma largura de dados diferente (16 bits) em outros ambientes. Se você estiver passando um argumento de 16 bits para esse componente, declare-o como `UShort` em vez de `UInteger` em seu código de Visual Basic gerenciado.

- **Ampliação.** O tipo de dados `UInteger` amplia a `Long`, `ULong`, `Decimal`, `Single`e `Double`. Isso significa que você pode converter `UInteger` em qualquer um desses tipos sem encontrar um erro de <xref:System.OverflowException?displayProperty=nameWithType>.

- **Digite os caracteres.** Acrescentar os caracteres do tipo literal `UI` a um literal o força ao tipo de dados `UInteger`. `UInteger` não tem um caractere de tipo de identificador.

- **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.UInt32?displayProperty=nameWithType>.

## <a name="see-also"></a>Consulte também

- <xref:System.UInt32>
- [Tipos de Dados](../../../visual-basic/language-reference/data-types/index.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Como chamar uma função do Windows que use tipos não assinados](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
