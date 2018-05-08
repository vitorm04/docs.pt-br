---
title: Sobrecarga de operador (F#)
description: 'Aprenda a sobrecarga de operadores aritméticos em uma classe ou um tipo de registro e no nível global em F #.'
ms.date: 05/16/2016
ms.openlocfilehash: fc9b7311aa746fd758930365972a187ffdfff0d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="operator-overloading"></a>Sobrecarga de operador

Este tópico descreve como a sobrecarga de operadores aritméticos em uma classe ou um tipo de registro e no nível global.


## <a name="syntax"></a>Sintaxe

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a>Comentários
Na sintaxe anterior, o *símbolo do operador* é um dos `+`, `-`, `*`, `/`, `=`e assim por diante. O *a lista de parâmetros* Especifica os operandos na ordem em que aparecem na sintaxe comum para esse operador. O *corpo de método* constrói o valor resultante.

Sobrecargas de operador para operadores devem ser estáticas. Sobrecargas de operador para operadores unários, tais como `+` e `-`, deve usar um til (`~`) no *símbolo do operador* para indicar que o operador é um operador unário e não é um operador binário, conforme mostrado do declaração a seguir.

```fsharp
static member (~-) (v : Vector)
```

O código a seguir ilustra uma classe de vetor que tem apenas dois operadores, uma para unária de subtração e outra para multiplicação por um valor escalar. No exemplo, duas sobrecargas para multiplicação escalar são necessárias porque o operador deve funcionar independentemente da ordem na qual o vetor e escalar aparecem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a>Criando novos operadores
Você pode sobrecarregar os operadores padrão, mas você também pode criar novos operadores fora de sequências de determinados caracteres. Permitidos são caracteres de operador `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, e `~`. O `~` caracteres tem um significado especial de criação de um operador unário e não faz parte da sequência de caracteres de operador. Nem todos os operadores podem ser feitos unário.

Dependendo da sequência de caracteres exata que você usar, seu operador terá um determinado precedência e associação. Capacidade de associação pode ser deixada ou para a direita ou da direita para esquerda e é usada sempre que os operadores do mesmo nível de precedência aparecem em sequência, sem parênteses.

O caractere de operador `.` não afeta a precedência, para que, por exemplo, se você quiser definir sua própria versão da multiplicação que tem a mesma precedência e associatividade como multiplicação comum, pode criar operadores como `.*`.

Somente os operadores `?` e `?<-` pode começar com `?`.

Uma tabela que mostra a precedência de todos os operadores em F # pode ser encontrada em [símbolo e referência de operador](symbol-and-operator-reference/index.md).


## <a name="overloaded-operator-names"></a>Nomes de operador sobrecarregado
Quando o compilador F # compila uma expressão de operador, ele gera um método que tem um nome gerado pelo compilador para esse operador. Esse é o nome que aparece no Microsoft intermediate language (MSIL) para o método e também em reflexão e IntelliSense. Normalmente, não é necessário usar esses nomes no código F #.

A tabela a seguir mostra os operadores padrão e seus correspondente nomes gerados.



|Operador|Nome gerado|
|--------|--------------|
|`[]`|`op_Nil`|
|`::`|`op_Cons`|
|`+`|`op_Addition`|
|`-`|`op_Subtraction`|
|`*`|`op_Multiply`|
|`/`|`op_Division`|
|`@`|`op_Append`|
|`^`|`op_Concatenate`|
|`%`|`op_Modulus`|
|`&&&`|`op_BitwiseAnd`|
|<code>&#124;&#124;&#124;</code>|`op_BitwiseOr`|
|`^^^`|`op_ExclusiveOr`|
|`<<<`|`op_LeftShift`|
|`~~~`|`op_LogicalNot`|
|`>>>`|`op_RightShift`|
|`~+`|`op_UnaryPlus`|
|`~-`|`op_UnaryNegation`|
|`=`|`op_Equality`|
|`<=`|`op_LessThanOrEqual`|
|`>=`|`op_GreaterThanOrEqual`|
|`<`|`op_LessThan`|
|`>`|`op_GreaterThan`|
|`?`|`op_Dynamic`|
|`?<-`|`op_DynamicAssignment`|
|<code>&#124;></code>|`op_PipeRight`|
|<code><&#124;</code>|`op_PipeLeft`|
|`!`|`op_Dereference`|
|`>>`|`op_ComposeRight`|
|`<<`|`op_ComposeLeft`|
|`<@ @>`|`op_Quotation`|
|`<@@ @@>`|`op_QuotationUntyped`|
|`+=`|`op_AdditionAssignment`|
|`-=`|`op_SubtractionAssignment`|
|`*=`|`op_MultiplyAssignment`|
|`/=`|`op_DivisionAssignment`|
|`..`|`op_Range`|
|`.. ..`|`op_RangeStep`|
Outras combinações de caracteres de operador que não estão listados aqui podem ser usadas como operadores e têm nomes que são compostos concatenando os nomes para os caracteres individuais da tabela a seguir. Por exemplo, +! torna-se `op_PlusBang`.



|Caractere de operador|Nome|
|------------------|----|
|`>`|`Greater`|
|`<`|`Less`|
|`+`|`Plus`|
|`-`|`Minus`|
|`*`|`Multiply`|
|`/`|`Divide`|
|`=`|`Equals`|
|`~`|`Twiddle`|
|`%`|`Percent`|
|`.`|`Dot`|
|`&`|`Amp`|
|<code>&#124;</code>|`Bar`|
|`@`|`At`|
|`^`|`Hat`|
|`!`|`Bang`|
|`?`|`Qmark`|
|`(`|`LParen`|
|`,`|`Comma`|
|`)`|`RParen`|
|`[`|`LBrack`|
|`]`|`RBrack`|

## <a name="prefix-and-infix-operators"></a>Prefixo e operadores fixos
*Prefixo* operadores devem ser colocado na frente de um operando ou operandos, semelhante a uma função. *Infixo* operadores devem ser colocados entre os dois operandos.

Apenas certos operadores podem ser usados como operadores de prefixo. Alguns operadores sempre são operadores de prefixo, outros podem ser fixos ou prefixo e o restante são sempre infixo operadores. Operadores que começam com `!`, exceto `!=`e o operador `~`, ou repetido sequências de`~`, sempre são operadores de prefixo. Os operadores `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, e `%%` pode ser operadores de prefixo ou infixo operadores. Distinguir a versão de prefixo desses operadores da versão infixo adicionando um `~` no início de um operador de prefixo quando ele está definido. O `~` não é usado quando você usa o operador, apenas quando ele está definido.

## <a name="example"></a>Exemplo

O código a seguir ilustra o uso de sobrecarga de operador para implementar um tipo de fração. Uma fração é representada por um numerador e um denominador. A função `hcf` é usada para determinar o fator de comum mais alta, que é usado para reduzir frações.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

**Saída:**

```
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a>Operadores no nível Global
Você também pode definir operadores no nível global. O código a seguir define um operador `+?`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

A saída do código acima é `12`.

Você pode redefinir os operadores aritméticos regulares dessa maneira porque as regras de escopo para F # ditam que recém-definido operadores têm precedência sobre os operadores internos.

A palavra-chave `inline` é frequentemente usada com operadores globais, que geralmente são pequenas funções que estão integradas melhor o código de chamada. Fazer operador funções embutidas também permite trabalhar com parâmetros de tipo resolvidos estaticamente para gerar o código genérico resolvido estaticamente. Para obter mais informações, consulte [funções embutidas](functions/inline-functions.md) e [resolvidos estaticamente parâmetros de tipo](generics/statically-resolved-type-parameters.md).

## <a name="see-also"></a>Consulte também
[Membros](members/index.md)
