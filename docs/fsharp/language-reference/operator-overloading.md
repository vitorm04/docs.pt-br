---
title: Sobrecarga de operador (F#)
description: 'Saiba como sobrecarregar operadores aritméticos em uma classe ou tipo de registro e no nível global em F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 6232ebf215289e6a22b9d77fbd5fa67b82460486
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087293"
---
# <a name="operator-overloading"></a>Sobrecarga de operador

Este tópico descreve como sobrecarregar operadores aritméticos em uma classe ou tipo de registro e no nível global.

## <a name="syntax"></a>Sintaxe

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, o *símbolo do operador* é uma das `+`, `-`, `*`, `/`, `=`e assim por diante. O *lista de parâmetros* Especifica os operandos na ordem em que aparecem na sintaxe comum para esse operador. O *corpo do método* constrói o valor resultante.

Sobrecargas de operador para os operadores devem ser estáticas. Sobrecargas de operador para operadores unários, tais como `+` e `-`, deve usar um til (`~`) na *símbolo do operador* para indicar que o operador é um operador unário e não é um operador binário, conforme mostrado no declaração a seguir.

```fsharp
static member (~-) (v : Vector)
```

O código a seguir ilustra uma classe de vetor que tem apenas dois operadores, um para menos unário e outro para multiplicação por um escalar. No exemplo, duas sobrecargas para multiplicação escalar são necessárias porque o operador deve trabalhar independentemente da ordem na qual o vetor e escalar aparecem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a>Criação de novos operadores

Você pode sobrecarregar operadores padrão, mas você também pode criar novos operadores fora de sequências de determinados caracteres. Permitidos são caracteres de operador `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, e `~`. O `~` caractere tem um significado especial de criação de um operador unário e não faz parte da sequência de caracteres de operador. Nem todos os operadores podem ser feitos unário.

A sequência de caracteres exata que você usar, dependendo do seu operador terá um determinado precedência e associatividade. Associatividade ou pode ser deixada para a direita ou da direita para esquerda e é usada sempre que os operadores do mesmo nível de precedência aparecem em sequência, sem parênteses.

O caractere de operador `.` não afeta a precedência, para que, por exemplo, se você quiser definir sua própria versão de multiplicação que tem a mesma precedência e associatividade como multiplicação comum, você poderia criar operadores, como `.*`.

Somente os operadores `?` e `?<-` pode começar com `?`.

Uma tabela que mostra a precedência de todos os operadores em F # pode ser encontrada na [referência de símbolos e operador](symbol-and-operator-reference/index.md).

## <a name="overloaded-operator-names"></a>Nomes de operador sobrecarregado

Quando o compilador F # compila uma expressão de operador, ele gera um método que tem um nome gerado pelo compilador para esse operador. Esse é o nome que aparece no Microsoft intermediate language (MSIL) para o método e também na reflexão e IntelliSense. Normalmente, não é necessário usar esses nomes no código F #.

A tabela a seguir mostra os operadores padrão e suas respectivas nomes gerados.

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

Outras combinações de caracteres de operador que não estão listados aqui podem ser usadas como operadores e têm nomes que são compostos por meio da concatenação nomes para os caracteres individuais da tabela a seguir. Por exemplo, +! se torna `op_PlusBang`.

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

## <a name="prefix-and-infix-operators"></a>Operadores Infixos e prefixo

*Prefixo* operadores devem ser colocado na frente de um operando ou operandos, assim como uma função. *Infixo* operadores devem ser colocados entre os dois operandos.

Apenas certos operadores podem ser usados como operadores de prefixo. Alguns operadores sempre são operadores de prefixo, outros podem ser fixos ou prefixo e o restante são sempre de infixo operadores. Os operadores que começam com `!`, exceto `!=`e o operador `~`, ou repetidas de sequências de`~`, sempre são operadores de prefixo. Os operadores `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, e `%%` podem ser operadores de prefixo ou operadores de infixo. Distinguir a versão de prefixo desses operadores da versão de infixo adicionando um `~` no início de um operador de prefixo quando ele está definido. O `~` não é usado quando você usa o operador, apenas quando ele está definido.

## <a name="example"></a>Exemplo

O código a seguir ilustra o uso de sobrecarga de operador para implementar um tipo de fração. Uma fração é representada por um numerador e um denominador. A função `hcf` é usado para determinar o fator de comuns mais alto, que é usado para reduzir frações.

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

A palavra-chave `inline` é frequentemente usado com operadores globais, que geralmente são pequenas funções que são mais bem integradas ao código de chamada. Tomada de operador funções embutidas também permite para trabalhar com parâmetros de tipo estaticamente resolvidos para produzir código genérico estaticamente resolvido. Para obter mais informações, consulte [funções embutidas](functions/inline-functions.md) e [estaticamente parâmetros de tipo resolvidos](generics/statically-resolved-type-parameters.md).

## <a name="see-also"></a>Consulte também

- [Membros](members/index.md)
