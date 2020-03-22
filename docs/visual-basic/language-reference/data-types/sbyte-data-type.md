---
title: Tipo de Dados SByte
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
ms.openlocfilehash: 01a0a4a261213d7e6e2016bf49128092e5b22308
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400788"
---
# <a name="sbyte-data-type-visual-basic"></a>Tipo de dados SByte (Visual Basic)

Mantém inteiros assinados de 8 bits (1 byte) que variam em valor de -128 a 127.

## <a name="remarks"></a>Comentários

Use `SByte` o tipo de dados para conter valores inteiros `Integer` que não requerem `Short`a largura total dos dados ou mesmo a largura de meio de dados de . Em alguns casos, o tempo de execução do idioma comum pode ser capaz de embalar suas `SByte` variáveis de perto e economizar o consumo de memória.

O valor padrão de `SByte` é 0.

## <a name="literal-assignments"></a>Atribuições literais

Você pode declarar e `SByte` inicializar uma variável atribuindo-a um literal decimal, um literal hexadecimal, um literal octal, ou (começando com Visual Basic 2017) um literal binário.

No exemplo a seguir, inteiros iguais a -102 que são representados como decimais, hexadecimais e literais binários são atribuídos aos `SByte` valores. Este exemplo requer que você `/removeintchecks` compile com o interruptor do compilador.

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> Você usa `&h` o `&H` prefixo ou para denotar um literal `&b` `&B` hexadecimal, o prefixo ou para denotar um literal binário, e o prefixo `&o` ou `&O` para denotar um literal octal. Literais decimais não têm nenhum prefixo.

A partir do Visual Basic 2017, você `_`também pode usar o caractere sublinhado, como um separador de dígitos para melhorar a legibilidade, como mostra o exemplo a seguir.

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

Começando com visual basic 15.5, você também`_`pode usar o caractere sublinhado ( ) como um separador líder entre o prefixo e os dígitos hexadecimal, binário ou octal. Por exemplo: 

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Se o literal inteiro estiver fora do intervalo de `SByte` (ou seja, se for menor que <xref:System.SByte.MinValue?displayProperty=nameWithType> ou maior que <xref:System.SByte.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação. Quando um inteiro literal não tem sufixo, um [inteiro](integer-data-type.md) é inferido. Se o inteiro literal estiver fora `Integer` do alcance do tipo, um [Long](long-data-type.md) é inferido. Isso significa que, nos exemplos anteriores, os `0x9A` `0b10011010` literais numéricos são interpretados como inteiros assinados de <xref:System.SByte.MaxValue?displayProperty=nameWithType>32 bits com um valor de 156, que excede . Para compilar com sucesso um código como este que atribui `SByte`um inteiro não decimal a um , você pode fazer qualquer um dos seguintes:

- Desativar as verificações dos limites inteiros `/removeintchecks` compilando com o interruptor do compilador.

- Use um [caractere de tipo](../../programming-guide/language-features/data-types/type-characters.md) para definir explicitamente o valor `SByte`literal que você deseja atribuir ao . O exemplo a seguir `Short` atribui um `SByte`valor literal negativo a um . Note que, para números negativos, a parte de alta ordem da palavra de alta ordem do literal numérico deve ser definida. No caso do nosso exemplo, este é `Short` um pouco 15 do valor literal.

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>Dicas de programação

- **Conformidade cls.** O `SByte` tipo de dados não faz parte da [Especificação de Linguagem Comum](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), portanto, o código compatível com CLS não pode consumir um componente que o use.

- **Alargamento.** O `SByte` tipo de `Short`dados `Integer` `Long`se `Decimal` `Single`expande `Double`para, , , , e . Isso significa que `SByte` você pode converter para <xref:System.OverflowException?displayProperty=nameWithType> qualquer um desses tipos sem encontrar um erro.

- **Digite caracteres.** `SByte`não tem caractere de tipo literal ou tipo identificador.

- **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.SByte?displayProperty=nameWithType>.

## <a name="see-also"></a>Confira também

- <xref:System.SByte?displayProperty=nameWithType>
- [Tipos de dados](../../../visual-basic/language-reference/data-types/index.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Tipo de Dados Short](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [Tipo de dados inteiros](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Tipo de Dados Long](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
