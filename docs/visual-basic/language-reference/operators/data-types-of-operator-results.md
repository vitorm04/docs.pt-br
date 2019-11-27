---
title: Tipos de dados de resultados do operador
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], operator result data types
- result data types [Visual Basic]
- operator result data types [Visual Basic]
- operators [Visual Basic], data types
- data types [Visual Basic], ranges
- operators [Visual Basic], result data types
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
ms.openlocfilehash: 3867d433ea5f9a6effe70db0ff4162390fb50b5c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331463"
---
# <a name="data-types-of-operator-results-visual-basic"></a>Tipos de dados de resultados do operador (Visual Basic)
Visual Basic determina o tipo de dados de resultado de uma operação com base nos tipos de dados dos operandos. Em alguns casos, isso pode ser um tipo de dados com um intervalo maior do que o de um dos operandos.  
  
## <a name="data-type-ranges"></a>Intervalos de tipos de dados  
 Os intervalos dos tipos de dados relevantes, na ordem do menor para o maior, são os seguintes:  
  
- [Booliano](../../../visual-basic/language-reference/data-types/boolean-data-type.md) — dois valores possíveis  
  
- [SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [byte](../../../visual-basic/language-reference/data-types/byte-data-type.md) — 256 possíveis valores integrais  
  
- [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) — 65.536 (6.5... E + 4) valores integrais possíveis  
  
- [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) — 4.294.967.296 (4.2... E + 9) valores integrais possíveis  
  
- [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULONG](../../../visual-basic/language-reference/data-types/ulong-data-type.md) — 18446744073709551615 (1.8... E + 19) valores integrais possíveis  
  
- [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) – 1,5... e + 29 valores integrais possíveis, intervalo máximo de 7.9... e + 28 (valor absoluto)  
  
- [Único](../../../visual-basic/language-reference/data-types/single-data-type.md) – intervalo máximo de 3.4... E + 38 (valor absoluto)  
  
- [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) — intervalo máximo 1.7... E + 308 (valor absoluto)  
  
 Para obter mais informações sobre tipos de dados Visual Basic, consulte [tipos de dados](../../../visual-basic/language-reference/data-types/index.md).  
  
 Se um operando for avaliado como [Nothing](../../../visual-basic/language-reference/nothing.md), o Visual Basic operadores aritméticos o tratará como zero.  
  
## <a name="decimal-arithmetic"></a>Aritmética decimal  
 Observe que o tipo de dados [decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) não é ponto flutuante nem inteiro.  
  
 Se um dos operandos de uma `+`, `–`, `*`, `/`ou `Mod` operação for `Decimal` e o outro não for `Single` ou `Double`, Visual Basic ampliará o outro operando para `Decimal`. Ele executa a operação em `Decimal`e o tipo de dados de resultado é `Decimal`.  
  
## <a name="floating-point-arithmetic"></a>Aritmética de ponto flutuante  
 Visual Basic executa a maioria das aritméticas de ponto flutuante em [Double](../../../visual-basic/language-reference/data-types/double-data-type.md), que é o tipo de dados mais eficiente para essas operações. No entanto, se um operando for [único](../../../visual-basic/language-reference/data-types/single-data-type.md) e o outro não for `Double`, Visual Basic executará a operação no `Single`. Ele amplia cada operando conforme necessário para o tipo de dados apropriado antes da operação, e o resultado tem esse tipo de dados.  
  
### <a name="-and--operators"></a>Operadores de ^/e  
 O operador `/` é definido somente para os tipos de dados [decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [único](../../../visual-basic/language-reference/data-types/single-data-type.md)e [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md) . Visual Basic amplia cada operando conforme necessário para o tipo de dados apropriado antes da operação, e o resultado tem esse tipo de dados.  
  
 A tabela a seguir mostra os tipos de dados de resultado para o operador de `/`. Observe que essa tabela é simétrica; para uma determinada combinação de tipos de dados de operando, o tipo de dados de resultado é o mesmo, independentemente da ordem dos operandos.  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|Qualquer tipo de inteiro|  
|`Decimal`|Decimal|Simples|Duplo|Decimal|  
|`Single`|Simples|Simples|Duplo|Simples|  
|`Double`|Duplo|Duplo|Duplo|Duplo|  
|Qualquer tipo de inteiro|Decimal|Simples|Duplo|Duplo|  
  
 O operador `^` é definido somente para o tipo de dados `Double`. Visual Basic amplia cada operando conforme necessário para `Double` antes da operação, e o tipo de dados de resultado é sempre `Double`.  
  
## <a name="integer-arithmetic"></a>Aritmética de inteiro  
 O tipo de dados de resultado de uma operação de inteiro depende dos tipos de dados dos operandos. Em geral, Visual Basic usa as seguintes políticas para determinar o tipo de dados de resultado:  
  
- Se ambos os operandos de um operador binário tiverem o mesmo tipo de dados, o resultado terá esse tipo de dados. Uma exceção é `Boolean`, que é forçada a `Short`.  
  
- Se um operando não assinado participar de um operando assinado, o resultado terá um tipo assinado com pelo menos um intervalo grande como um dos operandos.  
  
- Caso contrário, o resultado geralmente tem o maior dos dois tipos de dados de operando.  
  
 Observe que o tipo de dados de resultado pode não ser o mesmo que o tipo de dados operando.  
  
> [!NOTE]
> O tipo de dados de resultado nem sempre é grande o suficiente para conter todos os valores possíveis resultantes da operação. Uma exceção <xref:System.OverflowException> pode ocorrer se o valor for muito grande para o tipo de dados de resultado.  
  
### <a name="unary--and--operators"></a>Operadores unários + e –  
 A tabela a seguir mostra os tipos de dados de resultado para os dois operadores unários, `+` e `–`.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`+` unário|Abreviado|SByte|Byte|Abreviado|UShort|Inteiro|UInteger|Long|ULong|  
|`–` unário|Abreviado|SByte|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Decimal|  
  
### <a name="-and--operators"></a><\< e > operadores de >  
 A tabela a seguir mostra os tipos de dados de resultado para os dois operadores de deslocamento de bits, `<<` e `>>`. Visual Basic trata cada operador bit-Shift como um operador unário em seu operando esquerdo (o padrão de bit a ser deslocado).  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Abreviado|SByte|Byte|Abreviado|UShort|Inteiro|UInteger|Long|ULong|  
  
 Se o operando esquerdo for `Decimal`, `Single`, `Double`ou `String`, o Visual Basic tentará convertê-lo em `Long` antes da operação e o tipo de dados de resultado será `Long`. O operando à direita (o número de posições de bit a serem deslocadas) deve ser `Integer` ou um tipo que se amplie para `Integer`.  
  
### <a name="binary----and-mod-operators"></a>Operadores binários +, –, \*e mod  
 A tabela a seguir mostra os tipos de dados de resultado para os operadores binários `+` e `–` e os operadores `*` e `Mod`. Observe que essa tabela é simétrica; para uma determinada combinação de tipos de dados de operando, o tipo de dados de resultado é o mesmo, independentemente da ordem dos operandos.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Abreviado|SByte|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Decimal|  
|`SByte`|SByte|SByte|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Decimal|  
|`Byte`|Abreviado|Abreviado|Byte|Abreviado|UShort|Inteiro|UInteger|Long|ULong|  
|`Short`|Abreviado|Abreviado|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Decimal|  
|`UShort`|Inteiro|Inteiro|UShort|Inteiro|UShort|Inteiro|UInteger|Long|ULong|  
|`Integer`|Inteiro|Inteiro|Inteiro|Inteiro|Inteiro|Inteiro|Long|Long|Decimal|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Decimal|  
|`ULong`|Decimal|Decimal|ULong|Decimal|ULong|Decimal|ULong|Decimal|ULong|  
  
### <a name="-operator"></a>Operador \\  
 A tabela a seguir mostra os tipos de dados de resultado para o operador de `\`. Observe que essa tabela é simétrica; para uma determinada combinação de tipos de dados de operando, o tipo de dados de resultado é o mesmo, independentemente da ordem dos operandos.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Abreviado|SByte|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Long|  
|`SByte`|SByte|SByte|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Long|  
|`Byte`|Abreviado|Abreviado|Byte|Abreviado|UShort|Inteiro|UInteger|Long|ULong|  
|`Short`|Abreviado|Abreviado|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Long|  
|`UShort`|Inteiro|Inteiro|UShort|Inteiro|UShort|Inteiro|UInteger|Long|ULong|  
|`Integer`|Inteiro|Inteiro|Inteiro|Inteiro|Inteiro|Inteiro|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 Se qualquer operando do operador de `\` for [decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [single](../../../visual-basic/language-reference/data-types/single-data-type.md)ou [Double](../../../visual-basic/language-reference/data-types/double-data-type.md), Visual Basic tentar convertê-lo para [Long](../../../visual-basic/language-reference/data-types/long-data-type.md) antes da operação, e o tipo de dados de resultado será `Long`.  
  
## <a name="relational-and-bitwise-comparisons"></a>Comparações relacionais e de bits  
 O tipo de dados de resultado de uma operação relacional (`=`, `<>`, `<`, `>`, `<=`, `>=`) é sempre `Boolean`[tipo de dados booliano](../../../visual-basic/language-reference/data-types/boolean-data-type.md). O mesmo é verdadeiro para operações lógicas (`And`, `AndAlso`, `Not`, `Or`, `OrElse`, `Xor`) em operandos `Boolean`.  
  
 O tipo de dados de resultado de uma operação lógica bit a bit depende dos tipos de dados dos operandos. Observe que `AndAlso` e `OrElse` são definidos somente para `Boolean`e Visual Basic converte cada operando conforme necessário para `Boolean` antes de executar a operação.  
  
### <a name="-----and--operators"></a>=, < >, \<, >, \<= e > = Operators  
 Se ambos os operandos forem `Boolean`, Visual Basic considerará `True` ser menor que `False`. Se um tipo numérico for comparado com um `String`, Visual Basic tentará converter o `String` para `Double` antes da operação. Um operando `Char` ou `Date` pode ser comparado apenas com outro operando do mesmo tipo de dados. O tipo de dados de resultado é sempre `Boolean`.  
  
### <a name="bitwise-not-operator"></a>Operador NOT bit a bit  
 A tabela a seguir mostra os tipos de dados de resultado para o operador de `Not` bits.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Booleano|SByte|Byte|Abreviado|UShort|Inteiro|UInteger|Long|ULong|  
  
 Se o operando for `Decimal`, `Single`, `Double`ou `String`, o Visual Basic tentará convertê-lo em `Long` antes da operação e o tipo de dados de resultado será `Long`.  
  
### <a name="bitwise-and-or-and-xor-operators"></a>Operadores and, or e XOR  
 A tabela a seguir mostra os tipos de dados de resultado para os operadores `And`, `Or`e `Xor` bits Observe que essa tabela é simétrica; para uma determinada combinação de tipos de dados de operando, o tipo de dados de resultado é o mesmo, independentemente da ordem dos operandos.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Booleano|SByte|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Long|  
|`SByte`|SByte|SByte|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Long|  
|`Byte`|Abreviado|Abreviado|Byte|Abreviado|UShort|Inteiro|UInteger|Long|ULong|  
|`Short`|Abreviado|Abreviado|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Long|  
|`UShort`|Inteiro|Inteiro|UShort|Inteiro|UShort|Inteiro|UInteger|Long|ULong|  
|`Integer`|Inteiro|Inteiro|Inteiro|Inteiro|Inteiro|Inteiro|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 Se um operando for `Decimal`, `Single`, `Double`ou `String`, o Visual Basic tentará convertê-lo em `Long` antes da operação, e o tipo de dados de resultado será o mesmo que se esse operando já tiver sido `Long`do.  
  
## <a name="miscellaneous-operators"></a>Operadores diversos  
 O operador `&` é definido somente para concatenação de `String` operandos. Visual Basic converte cada operando conforme necessário para `String` antes da operação, e o tipo de dados de resultado é sempre `String`. Para os fins do operador de `&`, todas as conversões para `String` são consideradas como sendo ampliadas, mesmo se `Option Strict` for `On`.  
  
 Os operadores `Is` e `IsNot` exigem que ambos os operandos sejam de um tipo de referência. A expressão `TypeOf`...`Is` requer que o primeiro operando seja de um tipo de referência e o segundo operando seja o nome de um tipo de dados. Em todos esses casos, o tipo de dados de resultado é `Boolean`.  
  
 O operador `Like` é definido apenas para correspondência de padrões de `String` operandos. Visual Basic tenta converter cada operando conforme necessário para `String` antes da operação. O tipo de dados de resultado é sempre `Boolean`.  
  
## <a name="see-also"></a>Consulte também

- [Tipos de Dados](../../../visual-basic/language-reference/data-types/index.md)
- [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Operadores aritméticos no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operadores de comparação no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operadores](../../../visual-basic/language-reference/operators/index.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operadores de Comparação](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
