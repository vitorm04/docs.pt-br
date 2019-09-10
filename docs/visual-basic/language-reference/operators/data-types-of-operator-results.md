---
title: Tipos de dados de resultados do operador (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], operator result data types
- result data types [Visual Basic]
- operator result data types [Visual Basic]
- operators [Visual Basic], data types
- data types [Visual Basic], ranges
- operators [Visual Basic], result data types
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
ms.openlocfilehash: bc7f29ae0e29a4c2fbfdf2e40d2226e174a06d3a
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856051"
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
  
 Se um dos operandos `+`de `–`uma `*`operação `/`,, `Mod` ou for `Decimal` e o outro não `Single` for ou `Double`, Visual Basic ampliará o outro operando para `Decimal`. Ele executa a operação em `Decimal`e o tipo de dados de resultado `Decimal`é.  
  
## <a name="floating-point-arithmetic"></a>Aritmética de ponto flutuante  
 Visual Basic executa a maioria das aritméticas de ponto flutuante em [Double](../../../visual-basic/language-reference/data-types/double-data-type.md), que é o tipo de dados mais eficiente para essas operações. No entanto, se um operando for [único](../../../visual-basic/language-reference/data-types/single-data-type.md) e o outro `Double`não for, Visual Basic executará `Single`a operação no. Ele amplia cada operando conforme necessário para o tipo de dados apropriado antes da operação, e o resultado tem esse tipo de dados.  
  
### <a name="-and--operators"></a>Operadores de ^/e  
 O `/` operador é definido somente para os tipos de dados [decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [único](../../../visual-basic/language-reference/data-types/single-data-type.md)e [duplo](../../../visual-basic/language-reference/data-types/double-data-type.md) . Visual Basic amplia cada operando conforme necessário para o tipo de dados apropriado antes da operação, e o resultado tem esse tipo de dados.  
  
 A tabela a seguir mostra os tipos de dados de `/` resultado para o operador. Observe que essa tabela é simétrica; para uma determinada combinação de tipos de dados de operando, o tipo de dados de resultado é o mesmo, independentemente da ordem dos operandos.  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|Qualquer tipo de inteiro|  
|`Decimal`|Decimal|Simples|Duplo|Decimal|  
|`Single`|Simples|Simples|Duplo|Simples|  
|`Double`|Duplo|Duplo|Duplo|Duplo|  
|Qualquer tipo de inteiro|Decimal|Simples|Duplo|Duplo|  
  
 O `^` operador é definido somente para o `Double` tipo de dados. Visual Basic amplia cada operando conforme necessário `Double` antes da operação, e o tipo de dados de resultado é sempre. `Double`  
  
## <a name="integer-arithmetic"></a>Aritmética de inteiro  
 O tipo de dados de resultado de uma operação de inteiro depende dos tipos de dados dos operandos. Em geral, Visual Basic usa as seguintes políticas para determinar o tipo de dados de resultado:  
  
- Se ambos os operandos de um operador binário tiverem o mesmo tipo de dados, o resultado terá esse tipo de dados. Uma exceção é `Boolean`, que é forçada `Short`para.  
  
- Se um operando não assinado participar de um operando assinado, o resultado terá um tipo assinado com pelo menos um intervalo grande como um dos operandos.  
  
- Caso contrário, o resultado geralmente tem o maior dos dois tipos de dados de operando.  
  
 Observe que o tipo de dados de resultado pode não ser o mesmo que o tipo de dados operando.  
  
> [!NOTE]
> O tipo de dados de resultado nem sempre é grande o suficiente para conter todos os valores possíveis resultantes da operação. Uma <xref:System.OverflowException> exceção pode ocorrer se o valor for muito grande para o tipo de dados de resultado.  
  
### <a name="unary--and--operators"></a>Operadores unários + e –  
 A tabela a seguir mostra os tipos de dados de resultado para os dois `+` operadores `–`unários e.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|Unário`+`|Abreviado|SByte|Byte|Abreviado|UShort|Inteiro|UInteger|Long|ULong|  
|Unário`–`|Abreviado|SByte|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Decimal|  
  
### <a name="-and--operators"></a><\<e > operadores de >  
 A tabela a seguir mostra os tipos de dados de resultado para os dois operadores `<<` de deslocamento de bits e. `>>` Visual Basic trata cada operador bit-Shift como um operador unário em seu operando esquerdo (o padrão de bit a ser deslocado).  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Abreviado|SByte|Byte|Abreviado|UShort|Inteiro|UInteger|Long|ULong|  
  
 Se o operando esquerdo for `Decimal`, `Single`, `Double` `String`ou,Visual Basic tentar convertê-lo `Long` antesdaoperaçãoeotipodedadosderesultadofor.`Long` O operando à direita (o número de posições de bit a ser deslocado) deve ser `Integer` ou um tipo que amplia para. `Integer`  
  
### <a name="binary----and-mod-operators"></a>Operadores +, –, \*e mod binários  
 A tabela a seguir mostra os tipos de dados de resultado `+` para `–` o binário e `*` os `Mod` operadores e os operadores e. Observe que essa tabela é simétrica; para uma determinada combinação de tipos de dados de operando, o tipo de dados de resultado é o mesmo, independentemente da ordem dos operandos.  
  
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
 A tabela a seguir mostra os tipos de dados de `\` resultado para o operador. Observe que essa tabela é simétrica; para uma determinada combinação de tipos de dados de operando, o tipo de dados de resultado é o mesmo, independentemente da ordem dos operandos.  
  
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
  
 Se qualquer operando do `\` operador for [decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [single](../../../visual-basic/language-reference/data-types/single-data-type.md)ou [Double](../../../visual-basic/language-reference/data-types/double-data-type.md), Visual Basic tentar convertê-lo para [Long](../../../visual-basic/language-reference/data-types/long-data-type.md) antes da operação e o tipo de dados de resultado for `Long`.  
  
## <a name="relational-and-bitwise-comparisons"></a>Comparações relacionais e de bits  
 O tipo de dados de resultado de uma operação relacional `<>`(, `>`, `<=` `<`, `>=`,,) `Boolean`é sempre`=` [tipo de dados booliano](../../../visual-basic/language-reference/data-types/boolean-data-type.md). O mesmo é verdadeiro para operações lógicas`And`( `AndAlso` `Not`, `Or` `OrElse`,,, `Xor`,) `Boolean` em operandos.  
  
 O tipo de dados de resultado de uma operação lógica bit a bit depende dos tipos de dados dos operandos. Observe que `AndAlso` e `OrElse` são definidos somente para `Boolean`, `Boolean` e Visual Basic converte cada operando conforme necessário antes de executar a operação.  
  
### <a name="-----and--operators"></a>=, < >, \<, >, \<= e > = Operators  
 Se ambos os operandos `Boolean`forem, Visual Basic `True` considerará ser menor `False`que. Se um tipo numérico for comparado com um `String`, Visual Basic tentará converter o `String` para `Double` antes da operação. Um `Char` operando `Date` or só pode ser comparado com outro operando do mesmo tipo de dados. O tipo de dados de resultado `Boolean`é sempre.  
  
### <a name="bitwise-not-operator"></a>Operador NOT bit a bit  
 A tabela a seguir mostra os tipos de dados de resultado `Not` para o operador bit a bit.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Boolean|SByte|Byte|Abreviado|UShort|Inteiro|UInteger|Long|ULong|  
  
 Se o operando for `Decimal`, `Single`, `Double` `String`ou,Visual Basic tentar convertê-lo `Long` antesdaoperaçãoeotipodedadosderesultadofor.`Long`  
  
### <a name="bitwise-and-or-and-xor-operators"></a>Operadores and, or e XOR  
 A tabela a seguir mostra os tipos de dados de resultado `And`para `Or`os operadores `Xor` bit a bit, e. Observe que essa tabela é simétrica; para uma determinada combinação de tipos de dados de operando, o tipo de dados de resultado é o mesmo, independentemente da ordem dos operandos.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Boolean|SByte|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Long|  
|`SByte`|SByte|SByte|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Long|  
|`Byte`|Abreviado|Abreviado|Byte|Abreviado|UShort|Inteiro|UInteger|Long|ULong|  
|`Short`|Abreviado|Abreviado|Abreviado|Abreviado|Inteiro|Inteiro|Long|Long|Long|  
|`UShort`|Inteiro|Inteiro|UShort|Inteiro|UShort|Inteiro|UInteger|Long|ULong|  
|`Integer`|Inteiro|Inteiro|Inteiro|Inteiro|Inteiro|Inteiro|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 Se um operando for `Decimal`, `Single`, `Double` `String`ou,Visual Basic tentar convertê-lo `Long` antesdaoperação,eotipodedadosderesultadoseráomesmoqueseesseoperandojátivessesido.`Long`  
  
## <a name="miscellaneous-operators"></a>Operadores diversos  
 O `&` operador é definido somente para concatenação de `String` operandos. Visual Basic converte cada operando conforme necessário `String` antes da operação, e o tipo de dados de resultado é sempre. `String` `&` Para os fins do operador, todas as conversões para `String` são consideradas como sendo ampliadas, mesmo se `Option Strict` for `On`.  
  
 Os `Is` operadores `IsNot` e exigem que ambos os operandos sejam de um tipo de referência. A `TypeOf`... `Is` a expressão requer que o primeiro operando seja de um tipo de referência e o segundo operando seja o nome de um tipo de dados. Em todos esses casos, o tipo de dados `Boolean`de resultado é.  
  
 O `Like` operador é definido somente para correspondência de padrões `String` de operandos. Visual Basic tenta converter cada operando conforme necessário `String` antes da operação. O tipo de dados de resultado `Boolean`é sempre.  
  
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
