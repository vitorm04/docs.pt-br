---
title: "Tipos de dados de resultados do operador (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "tipos de dados [Visual Basic], tipos de dados de resultado do Operador"
  - "tipos de dados [Visual Basic], intervalos"
  - "tipos de dados de resultado do Operador"
  - "operadores [Visual Basic], tipos de dados"
  - "operadores [Visual Basic], tipos de dados de resultado"
  - "tipos de dados de resultado"
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipos de dados de resultados do operador (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] determina o tipo de dado do resultado de uma operação baseada nos tipos de dado dos operandos.  Em alguns casos, ele deve ser de um tipo de dado com um intervalo maior do que o dos operandos.  
  
## Intervalos de Tipo de Dado  
 Os intervalos de tipos de dado relevantes, em ordem do menor para o menor, são os seguintes:  
  
-   [Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) \- dois valores possíveis  
  
-   [SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md),[Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md) \- 256 possíveis valores integrais  
  
-   [Short](../../../visual-basic/language-reference/data-types/short-data-type.md),[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) \- 65,536 \(6.5...E\+4\) valores integrais possíveis  
  
-   [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md),[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) \- 4,294,967,296 \(4.2...E\+9\) valores integrais possíveis  
  
-   [Long](../../../visual-basic/language-reference/data-types/long-data-type.md),[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md) \- 18,446,744,073,709,551,615 \(1.8...E\+19\) valores integrais possíveis  
  
-   [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) \- 1.5...E\+29 valores integrais possíveis, intervalo máximo de 7.9...E\+28 \(valor absoluto\)  
  
-   [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) \- máximo intervalo 3.4...E\+38 \(valor absoluto\)  
  
-   [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) \- máximo intervalo 1.7...E\+308 \(valor absoluto\)  
  
 Para obter mais informações, sobre tipos de dado [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], consulte [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
 Se um operando obtém [Nothing](../../../visual-basic/language-reference/nothing.md),  os operadores aritméticos [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tratam como zero.  
  
## Aritmética Decimal  
 Observe que o tipo de dado [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) não é de ponto flutuante nem inteiro.  
  
 If either operand of a `+`, `–`, `*`, `/`, or `Mod` operation is `Decimal` and the other is not `Single` or `Double`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] widens the other operand to `Decimal`.  Ele realiza a operação em `Decimal`, e o tipo de dado do resultado será `Decimal`.  
  
## Aritmética de Ponto\-Flutuante  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] realiza a maioria da aritmética de ponto flutuante em [Double](../../../visual-basic/language-reference/data-types/double-data-type.md), que é o tipo de dado mais eficiente para tais operações.  Entretanto, se um operando for [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) e o outro não for `Double`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] realiza a operação em `Single`.  Isso amplia cada operando conforme seja necessário para o tipo de dado apropriado antes da operação, e o resultado tem esse tipo de dado.  
  
### Operadores \/ e ^  
 O `/` operador está definido apenas para o  [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md),  [único](../../../visual-basic/language-reference/data-types/single-data-type.md), e  [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) tipos de dados.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]amplia a cada operando conforme necessário para o tipo de dados apropriado antes que a operação e o resultado tenha esse tipo de dados.  
  
 A tabela seguinte mostra tipos de dado de resultado para o operador `/`.  Observe que essa tabela é simétrica; para uma dada combinação de tipos de dado de operandos, o tipo de dado do resultado é o mesmo, independemente da ordem dos operandos.  
  
||||||  
|-|-|-|-|-|  
||`Decimal`|`Single`|`Double`|Qualquer tipo inteiro|  
|`Decimal`|Decimal|Simples|Double|Decimal|  
|`Single`|Simples|Simples|Double|Simples|  
|`Double`|Double|Double|Double|Double|  
|Qualquer tipo inteiro|Decimal|Simples|Double|Double|  
  
 O `^` o operador está definido somente para o `Double` tipo de dados.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]amplia a cada operando conforme necessário para `Double` antes da operação e o resultado é do tipo de dados sempre `Double`.  
  
## Aritmética de Inteiros  
 O tipo de dados do resultado de uma operação com inteiro depende do tipo de dado dos operandos.  Em geral, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] usa as seguintes políticas para determinar o tipo de dado do resultado:  
  
-   Se ambos os operandos de um operador binário têm o mesmo tipo de dado, o resultado terá esse tipo de dado.  Uma exceção é `Boolean`, que é forçado a `Short`.  
  
-   Se um operador sem\-sinal participar em uma operação com sinal, o resultado será com sinal e com pelo menos o tamanho do intervalo de cada um dos operandos.  
  
-   Por outro lado, o resultado geralmente toma do maior dos tipos de dado dos operandos.  
  
 Observe que o tipo de dado do resultado pode não ser o mesmo de ambos os tipos de dado dos operandos.  
  
> [!NOTE]
>  O tipo de dado do resultado não é sempre grande o suficiente para armazenar todos os valores possíveis resultantes da operação.  Uma exceção <xref:System.OverflowException> pode ocorrer se o valor for muito grande para o tipo de dado do resultado.  
  
### Operadores unários \+ e \- .  
 A tabela a seguir mostra o resultado tipos de dados para os dois operadores unários, `+` e `–`.  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|Unário `+`|Short|SByte|Byte|Short|UShort|Integer|UInteger|Long|ULong|  
|Unário `–`|Short|SByte|Short|Short|Integer|Integer|Long|Long|Decimal|  
  
### Operadores \<\< e \>\>  
 A tabela a seguir mostra o resultado tipos de dados para os dois operadores bit shift, `<<` e `>>`.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]trata cada operador de deslocamento de bits como um operador unário em seu operando esquerdo \(o padrão de bits deslocamento\).  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Short|SByte|Byte|Short|UShort|Integer|UInteger|Long|ULong|  
  
 Se o operador esquerdo for `Decimal`,`Single`,`Double`, ou `String`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tenta convertê\-lo para `Long` antes da operação, e o tipo de dado do resultado será `Long`.  O operador direito \(o número de posições de bit a deslocar\) deve ser `Integer` ou um tipo que amplie para `Integer`.NUMBER  
  
### Operadores Binários \+,\-,\*, e Mod  
 A tabela a seguir mostra o resultado de tipos de dados para o binário `+` e `–` operadores e a `*` e `Mod` operadores.  Observe que essa tabela é simétrica; para uma dada combinação de tipos de dado de operandos, o tipo de dado do resultado é o mesmo, independemente da ordem dos operandos.  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Short|SByte|Short|Short|Integer|Integer|Long|Long|Decimal|  
|`SByte`|SByte|SByte|Short|Short|Integer|Integer|Long|Long|Decimal|  
|`Byte`|Short|Short|Byte|Short|UShort|Integer|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|Integer|Integer|Long|Long|Decimal|  
|`UShort`|Integer|Integer|UShort|Integer|UShort|Integer|UInteger|Long|ULong|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|Long|Long|Decimal|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Decimal|  
|`ULong`|Decimal|Decimal|ULong|Decimal|ULong|Decimal|ULong|Decimal|ULong|  
  
### \\ O operador  
 A tabela seguinte mostra tipos de dado de resultado para o operador `\`.  Observe que essa tabela é simétrica; para uma dada combinação de tipos de dado de operandos, o tipo de dado do resultado é o mesmo, independemente da ordem dos operandos.  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Short|SByte|Short|Short|Integer|Integer|Long|Long|Long|  
|`SByte`|SByte|SByte|Short|Short|Integer|Integer|Long|Long|Long|  
|`Byte`|Short|Short|Byte|Short|UShort|Integer|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|Integer|Integer|Long|Long|Long|  
|`UShort`|Integer|Integer|UShort|Integer|UShort|Integer|UInteger|Long|ULong|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 Se ambos os operandos de `\` forem [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md),[Single](../../../visual-basic/language-reference/data-types/single-data-type.md), ou [Double](../../../visual-basic/language-reference/data-types/double-data-type.md), [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tenta convertê\-los para [Long](../../../visual-basic/language-reference/data-types/long-data-type.md) antes de realizar a operação, e o tipo de dado do resultado será `Long`.  
  
## Comparações Relacionais e Bit a Bit  
 The result data type of a relational operation \(`=`, `<>`, `<`, `>`, `<=`, `>=`\) is always `Boolean`[Tipo de dados booliano](../../../visual-basic/language-reference/data-types/boolean-data-type.md).  O mesmo é válido para operações lógicas \(`And`,`AndAlso`,`Not`, `Or`,`OrElse`,`Xor`\) em operandos `Boolean`.  
  
 O tipo de dados do resultado de uma operação lógica bit a bit com inteiro depende do tipo de dado dos operandos.  Observe que `AndAlso` e `OrElse` são definidos somente para `Boolean`, e [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] converte cada operando conforme necessário para `Boolean` antes de realizar a operação.  
  
### \=, \< \>, \<\>,, \< \=, e \> \= operadores  
 Se ambos os operandos forem `Boolean`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] considera `True` como menos que `False`.  Se um tipo número é comparado com uma `String`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tenta converter a `String` para `Double` antes da operação.  Um operando `Char` ou `Date` pode ser comparado somente com outro operando do mesmo tipo.  O tipo de dado do resultado é sempre `Boolean`.  
  
### Operador Not bit a bit  
 A tabela seguinte mostra tipos de dado de resultado para o operador  bit a bit `Not`.  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Boolean|SByte|Byte|Short|UShort|Integer|UInteger|Long|ULong|  
  
 Se o operando `Decimal`,`Single`,`Double`, ou `String`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tenta convertê\-lo para `Long` antes da operação, e o tipo de dado do resultado será `Long`.  
  
### Operadores Bit a Bit, And, or e Xor  
 A tabela seguinte mostra tipos de dado de resultado para os operadores bit a bit `And` ,`Or`. e `Xor`.  Observe que essa tabela é simétrica; para uma dada combinação de tipos de dado de operandos, o tipo de dado do resultado é o mesmo, independemente da ordem dos operandos.  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Boolean|SByte|Short|Short|Integer|Integer|Long|Long|Long|  
|`SByte`|SByte|SByte|Short|Short|Integer|Integer|Long|Long|Long|  
|`Byte`|Short|Short|Byte|Short|UShort|Integer|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|Integer|Integer|Long|Long|Long|  
|`UShort`|Integer|Integer|UShort|Integer|UShort|Integer|UInteger|Long|ULong|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 Se um operando for `Decimal`,`Single`,`Double`, ou `String`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tenta convertê\-lo para `Long` antes da operação, e o tipo de dado do resultado será o mesmo, como se o operando já fosse  `Long`.  
  
## Operadores Mistos  
 O `&` operador está definido apenas para concatenação de `String` operandos.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Converte cada operando conforme necessário para `String` antes da operação e o resultado é do tipo de dados sempre `String`.  Para os propósitos do operador `&`, todas as conversões para `String` são considerandas abrangentes, mesmo se `Option Strict` for `On`.  
  
 Os operadores `Is` e `IsNot` necessitam que ambos os operandos sejam do tipo de referência.  A expressão `TypeOf`...`Is` necessita que o primeiro operando seja de tipo de referência e o segundo seja o nome de um tipo de dado.  Em todos esses casos, o tipo de dado do resultado será `Boolean`.  
  
 O `Like` operador está definido apenas para correspondência de padrões de `String` operandos.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]tenta converter cada operando conforme necessário para `String` antes da operação.  O tipo de dado do resultado é sempre `Boolean`.  
  
## Consulte também  
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Operadores e expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Operadores de comparação no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Operadores \(\)](../../../visual-basic/language-reference/operators/index.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores aritméticos](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Operadores de comparação](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)