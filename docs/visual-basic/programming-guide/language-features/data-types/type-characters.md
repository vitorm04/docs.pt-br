---
title: Digite os caracteres (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals
- F literal type character
- '& identifier type character'
- type characters
- octal literals
- literals, hexadecimal
- '&O prefix for octal values'
- literals, default types
- defaults, literal types
- C literal type character
- type characters, literal
- $ identifier type character
- L literal type character
- UI literal type characters
- default literal types
- D literal type character
- literals, octal
- S literal type character
- '! identifier type character'
- US literal type characters
- '% identifier type character'
- data types [Visual Basic], type characters
- characters, identifier type
- type characters, identifier
- '# identifier type character'
- identifier type characters
- literal type characters
- I literal type character
- R literal type character
- '@ identifier type character'
- UL literal type characters
- literal types, default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6e112e7d221ef8e7a660094306bbb242c988e843
ms.lasthandoff: 03/13/2017

---
# <a name="type-characters-visual-basic"></a>Caracteres de tipo (Visual Basic)
Além de especificar um tipo de dados em uma instrução de declaração, você pode forçar o tipo de dados de alguns elementos de programação com um *caractere de tipo*. O caractere de tipo deve vir logo após o elemento, com nenhum caractere intermediário de qualquer tipo.  
  
 O caractere de tipo não é parte do nome do elemento. Um elemento definido com um caractere de tipo pode ser referenciado sem o caractere de tipo.  
  
## <a name="identifier-type-characters"></a>Caracteres de tipo identificador  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Fornece um conjunto de *caracteres de tipo identificador*, que você pode usar em uma declaração para especificar o tipo de dados de uma variável ou constante. A tabela a seguir mostra os caracteres de tipo identificador disponíveis com exemplos de uso.  
  
|Caractere de tipo identificador|Tipo de dados|Exemplo|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 Nenhum caractere de tipo identificador existe para o `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, ou `UShort` tipos de dados, ou para quaisquer tipos de dados compostos, como arrays ou estruturas.  
  
 Em alguns casos, você pode acrescentar o `$` caracteres para um [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] funcionar, por exemplo `Left$` em vez de `Left`, para obter um valor retornado do tipo `String`.  
  
 Em todos os casos, o caractere de tipo identificador deve seguir imediatamente o nome do identificador.  
  
## <a name="literal-type-characters"></a>Caracteres de tipo literal  
 A *literal* é uma representação textual de um determinado valor de um tipo de dados.  
  
### <a name="default-literal-types"></a>Tipos de Literal padrão  
 A forma de um literal como ele aparece no seu código normalmente determina seu tipo de dados. A tabela a seguir mostra esses tipos padrão.  
  
|Formato textual de literal|Tipo de dados padrão|Exemplo|  
|-----------------------------|-----------------------|-------------|  
|Numérico, sem parte fracionária|`Integer`|`2147483647`|  
|Numérico, sem parte fracionária, muito grande para`Integer`|`Long`|`2147483648`|  
|Numérico, parte fracionária|`Double`|`1.2`|  
|Entre aspas duplas|`String`|`"A"`|  
|Entre sinais numéricos|`Date`|`#5/17/1993 9:32 AM#`|  
  
### <a name="forced-literal-types"></a>Tipos literais forçados  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Fornece um conjunto de *caracteres de tipo literal*, indicando que você pode usar para forçar um literal a assumir um tipo de dados que não seja o seu formulário. Para fazer isso, acrescentando o caractere ao final do literal. A tabela a seguir mostra os caracteres de tipo literal disponíveis com exemplos de uso.  
  
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
  
 Nenhum caractere de tipo literal existe para o `Boolean`, `Byte`, `Date`, `Object`, `SByte`, ou `String` tipos de dados, ou para quaisquer tipos de dados compostos, como arrays ou estruturas.  
  
 Literais também podem usar os caracteres de tipo identificador (`%`, `&`, `@`, `!`, `#`, `$`), como variáveis, constantes e expressões. No entanto, o literal digitar caracteres (`S`, `I`, `L`, `D`, `F`, `R`, `C`) pode ser usado somente com literais.  
  
 Em todos os casos, o caractere de tipo literal deve vir logo após o valor literal.  
  
## <a name="hexadecimal-and-octal-literals"></a>Literais octais e hexadecimais  
 O compilador normalmente constrói um literal inteiro para ser do sistema de número decimal (base 10). Você pode forçar um literal inteiro para ser hexadecimal (base 16) com o `&H` prefixo e você pode forçá-lo para ser octal (base 8) com o `&O` prefixo. Os dígitos que seguem o prefixo devem ser apropriados para o sistema numérico. A tabela a seguir ilustra isso.  
  
|Número base|Prefixo|Valores válidos de dígitos|Exemplo|  
|-----------------|------------|------------------------|-------------|  
|Hexadecimal (base 16)|`&H`|0-9 e A-F|`&HFFFF`|  
|Octal (base 8)|`&O`|0-7|`&O77`|  
  
 Você pode seguir um literal prefixado com um caractere de tipo literal. O exemplo a seguir mostra isso.  
  
```  
Dim counter As Short = &H8000S  
Dim flags As UShort = &H8000US  
```  
  
 No exemplo anterior, `counter` tem o valor decimal de -32768, e `flags` possui o valor decimal de +&32768;.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Declaração de variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Tipos de Dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
