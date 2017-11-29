---
title: Tipo de dados SByte (Visual Basic)
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.sbyte
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
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bcd00665ec5b8651089811a61212bfa302fe95d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="sbyte-data-type-visual-basic"></a>Tipo de dados SByte (Visual Basic)

Armazena inteiros de 8 bits (1-bytes) que variam em valor entre -128 a 127.  
  
## <a name="remarks"></a>Comentários

Use o `SByte` tipo de dados para conter valores inteiros que não requerem a largura total de dados de `Integer` ou até mesmo a metade dos bits de `Short`. Em alguns casos, o common language runtime poderá compactar seu `SByte` variáveis próximas uma da outra e economizar memória.

O valor padrão de `SByte` é 0.

## <a name="literal-assignments"></a>Atribuições de literal
  
Você pode declarar e inicializar uma `SByte` variável atribuindo a ele um literal decimal, hexadecimal literal, um literal octal, ou (começando com Visual Basic 2017) um literal binário.

No exemplo a seguir, inteiros igual à-102 que são representados como decimal, hexadecimal, e literais binárias são atribuídas a `SByte` valores. Este exemplo requer que você compile com o `/removeintchecks` opção de compilador.

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]  

> [!NOTE] 
> Use o prefixo `&h` ou `&H` para denotar um hexadecimal literal, o prefixo `&b` ou `&B` para denotar um literal binário e o prefixo `&o` ou `&O` para denotar um literal octal. Literais decimais não têm nenhum prefixo.

A partir do Visual Basic de 2017, você também pode usar o caractere de sublinhado, `_`, como um separador de dígito para melhorar a legibilidade, como o exemplo a seguir mostra.

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]  

Se o literal inteiro estiver fora do intervalo de `SByte` (ou seja, se for menor que <xref:System.SByte.MinValue?displayProperty=nameWithType> ou maior que <xref:System.SByte.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação. Quando um literal inteiro não tiver nenhum sufixo, um [inteiro](integer-data-type.md) é inferido. Se o literal de inteiro está fora do intervalo da `Integer` tipo, uma [longo](long-data-type.md) é inferido. Isso significa que, nos exemplos anteriores, os literais numéricos `0x9A` e `0b10011010` são interpretados como inteiros com sinal de 32 bits com um valor de 156, que excede <xref:System.SByte.MaxValue?displayProperty=nameWithType>. Para compilar código assim que atribui um inteiro decimal não para um `SByte`, você pode fazer o seguinte:

- Desabilitar verificações de limites de inteiro compilando com o `/removeintchecks` opção de compilador.

- Use um [caractere de tipo](../../programming-guide\language-features\data-types/type-characters.md) definir explicitamente o valor literal que você deseja atribuir ao `SByte`. O exemplo a seguir atribui um valor literal negativo `Short` valor para um `SByte`. Observe que, para números negativos, o bit de ordem alta da palavra de ordem alta do literal numérico deve ser definido. No caso do nosso exemplo, esse é o bit 15 do literal `Short` valor.

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>Dicas de programação
  
-   **Compatibilidade com CLS.** O `SByte` tipo de dados não é parte do [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), então um código compatível com CLS não pode consumir um componente que usa.

-   **Ampliação.** O `SByte` tipo de dados amplia a `Short`, `Integer`, `Long`, `Decimal`, `Single`, e `Double`. Isso significa que você pode converter `SByte` para qualquer um desses tipos sem encontrar um <xref:System.OverflowException?displayProperty=nameWithType> erro.
  
-   **Caracteres de tipo.** `SByte`não tem o caractere de tipo literal ou caractere de tipo identificador.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.SByte?displayProperty=nameWithType>.
  
## <a name="see-also"></a>Consulte também

 <xref:System.SByte?displayProperty=nameWithType>  
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Tipo de Dados Short](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [Tipo de Dados Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Tipo de Dados Long](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
