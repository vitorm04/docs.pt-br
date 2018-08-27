---
title: Caracteres de tipo (Visual Basic)
ms.date: 01/31/2018
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals [Visual Basic]
- F literal type character [Visual Basic]
- '& identifier type character'
- type characters [Visual Basic]
- octal literals [Visual Basic]
- literals [Visual Basic], hexadecimal
- '&O prefix for octal values'
- literals [Visual Basic], default types
- defaults, literal types
- C literal type character [Visual Basic]
- type characters [Visual Basic], literal
- $ identifier type character
- L literal type character [Visual Basic]
- UI literal type characters [Visual Basic]
- default literal types [Visual Basic]
- D literal type character [Visual Basic]
- literals [Visual Basic], octal
- S literal type character [Visual Basic]
- '! identifier type character'
- US literal type characters [Visual Basic]
- '% identifier type character'
- data types [Visual Basic], type characters
- characters [Visual Basic], identifier type
- type characters [Visual Basic], identifier
- '# identifier type character'
- identifier type characters [Visual Basic]
- literal type characters [Visual Basic]
- I literal type character [Visual Basic]
- R literal type character [Visual Basic]
- '@ identifier type character'
- UL literal type characters [Visual Basic]
- literal types [Visual Basic], default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31dc703598fa6d92b3f312b2b5f0bf5fadab9c04
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42911816"
---
# <a name="type-characters-visual-basic"></a>Digite os caracteres (Visual Basic)

Além de especificar um tipo de dados em uma instrução de declaração, você pode forçar o tipo de dados de alguns elementos de programação com uma *caractere de tipo*. O caractere de tipo deve vir logo após o elemento, com nenhum caractere intermediário de qualquer tipo.

O caractere de tipo não é parte do nome do elemento. Um elemento definido com um caractere de tipo pode ser referenciado sem o caractere de tipo.

## <a name="identifier-type-characters"></a>Caracteres de tipo

Visual Basic fornece um conjunto de *caracteres de tipo identificador* que você pode usar em uma declaração para especificar o tipo de dados de uma variável ou constante. A tabela a seguir mostra os caracteres de tipo identificador disponíveis com exemplos de uso.
  
|Caractere de tipo identificador|Tipo de dados|Exemplo|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 Nenhum caractere de tipo identificador existe para o `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, ou `UShort` tipos de dados, ou para qualquer tipos de dados compostos, como matrizes ou estruturas.

Em alguns casos, você pode acrescentar a `$` caracteres para uma função do Visual Basic, por exemplo `Left$` em vez de `Left`, para obter um valor retornado do tipo `String`.

Em todos os casos, o caractere de tipo identificador deve seguir imediatamente o nome do identificador.

## <a name="literal-type-characters"></a>Caracteres de tipo literal

Um *literal* é uma representação textual de um determinado valor de um tipo de dados.  

### <a name="default-literal-types"></a>Tipos de literal padrão

A forma de um literal como ele aparece no seu código normalmente determina seu tipo de dados. A tabela a seguir mostra esses tipos padrão.  
  
|Formato textual de literal|Tipo de dados padrão|Exemplo|  
|-----------------------------|-----------------------|-------------|  
|Numérico, sem parte fracionária|`Integer`|`2147483647`|  
|Numérico, sem parte fracionária, muito grande para `Integer`|`Long`|`2147483648`|  
|Numérico, parte fracionária|`Double`|`1.2`|  
|Entre aspas duplas|`String`|`"A"`|  
|Entre sinais numéricos|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a>Tipos literais forçados

Visual Basic fornece um conjunto de *caracteres de tipo literal*, indicando que você pode usar para forçar um literal a assumir um tipo de dados diferente do seu formulário. Você pode fazer isso por meio do acréscimo do caractere ao final do literal. A tabela a seguir mostra os caracteres de tipo literal disponíveis com exemplos de uso.
  
|Caractere de tipo literal|Tipo de dados|Exemplo|  
|----------------------------|---------------|-------------|  
|`S`|`Short`|`I = 347S`|
|`I`|`Integer`|`J = 347I`|
|`L`|`Long`|`K = 347L`|
|`D`|`Decimal`|`X = 347D`|
|`F`|`Single`|`Y = 347F`|
|`R`|`Double`|`Z = 347R`|
|`US`|`UShort`|`L = 347US`|
|`UI`|`UInteger`|`M = 347UI`|
|`UL`|`ULong`|`N = 347UL`|
|`C`|`Char`|`Q = "."C`|

Nenhum caractere de tipo literal existe para o `Boolean`, `Byte`, `Date`, `Object`, `SByte`, ou `String` tipos de dados, ou para quaisquer tipos de dados compostos, como matrizes ou estruturas.

Literais também podem usar caracteres de tipo (`%`, `&`, `@`, `!`, `#`, `$`), bem como variáveis, constantes e expressões. No entanto, o literal digitar caracteres (`S`, `I`, `L`, `D`, `F`, `R`, `C`) pode ser usado somente com literais.

Em todos os casos, o caractere de tipo literal deve seguir imediatamente o valor literal.

## <a name="hexadecimal-binary-and-octal-literals"></a>Literais octais hexadecimais e binários

Normalmente, o compilador interpreta um literal de inteiro para ser o sistema de número decimal (base 10). Você também pode definir um literal inteiro como um número hexadecimal (base 16) com o `&H` prefixo, como um número binário (base 2) com o `&B` prefixo e como um octal (base 8) número com o `&O` prefixo. Os dígitos que seguem o prefixo devem ser apropriados para o sistema de número. A tabela a seguir ilustra isso.  
  
|Número base|Prefixo|Valores de dígito válido|Exemplo|
|-----------------|------------|------------------------|-------------|
|Hexadecimal (base 16)|`&H`|0-9 e A-F|`&HFFFF`|
|Binário (base 2)|`&B`|0-1|`&B01111100`|
|Octal (base 8)|`&O`|0-7|`&O77`|

A partir do Visual Basic 2017, você pode usar o caractere de sublinhado (`_`) como um separador de grupo para melhorar a legibilidade de um literal integral. O exemplo a seguir usa o `_` caractere para agrupar um literal binário em grupos de 8 bits:

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

Você pode seguir um literal prefixado com um caractere de tipo literal. O exemplo a seguir mostra isso.

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

No exemplo anterior, `counter` tem o valor decimal de -32768, e `flags` tem o valor decimal de + 32768.

Começando com o Visual Basic 15.5, você pode também usar o caractere de sublinhado (`_`) como um separador à esquerda entre o prefixo e os dígitos octais, hexadecimais ou binários. Por exemplo:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a>Consulte também

 [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Tipos de Dados Elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Solução de problemas de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Declaração de Variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Tipos de Dados](../../../../visual-basic/language-reference/data-types/index.md)
