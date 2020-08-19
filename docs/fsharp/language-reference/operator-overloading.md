---
title: Sobrecarga de operador
description: 'Saiba como sobrecarregar operadores aritméticos em um tipo de classe ou de registro e no nível global em F #.'
ms.date: 08/15/2020
ms.openlocfilehash: fb86ceb95101fcc1f157ec9ba17a9d8145b11a91
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557575"
---
# <a name="operator-overloading"></a><span data-ttu-id="9e637-103">Sobrecarga de operador</span><span class="sxs-lookup"><span data-stu-id="9e637-103">Operator Overloading</span></span>

<span data-ttu-id="9e637-104">Este tópico descreve como sobrecarregar operadores aritméticos em um tipo de classe ou de registro e no nível global.</span><span class="sxs-lookup"><span data-stu-id="9e637-104">This topic describes how to overload arithmetic operators in a class or record type, and at the global level.</span></span>

## <a name="syntax"></a><span data-ttu-id="9e637-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e637-105">Syntax</span></span>

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a><span data-ttu-id="9e637-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="9e637-106">Remarks</span></span>

<span data-ttu-id="9e637-107">Na sintaxe anterior, o *operador-símbolo* é um de `+` , `-` ,,, `*` `/` `=` e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="9e637-107">In the previous syntax, the *operator-symbol* is one of `+`, `-`, `*`, `/`, `=`, and so on.</span></span> <span data-ttu-id="9e637-108">A *lista de parâmetros* especifica os operandos na ordem em que aparecem na sintaxe usual para esse operador.</span><span class="sxs-lookup"><span data-stu-id="9e637-108">The *parameter-list* specifies the operands in the order they appear in the usual syntax for that operator.</span></span> <span data-ttu-id="9e637-109">O *corpo do método* constrói o valor resultante.</span><span class="sxs-lookup"><span data-stu-id="9e637-109">The *method-body* constructs the resulting value.</span></span>

<span data-ttu-id="9e637-110">Sobrecargas de operador para operadores devem ser estáticas.</span><span class="sxs-lookup"><span data-stu-id="9e637-110">Operator overloads for operators must be static.</span></span> <span data-ttu-id="9e637-111">Sobrecargas de operador para operadores unários, como `+` e `-` , devem usar um til ( `~` ) no *símbolo de operador* para indicar que o operador é um operador unário e não um operador binário, como mostrado na declaração a seguir.</span><span class="sxs-lookup"><span data-stu-id="9e637-111">Operator overloads for unary operators, such as `+` and `-`, must use a tilde (`~`) in the *operator-symbol* to indicate that the operator is a unary operator and not a binary operator, as shown in the following declaration.</span></span>

```fsharp
static member (~-) (v : Vector)
```

<span data-ttu-id="9e637-112">O código a seguir ilustra uma classe vector que tem apenas dois operadores, um para menos unário e outro para multiplicação por um escalar.</span><span class="sxs-lookup"><span data-stu-id="9e637-112">The following code illustrates a vector class that has just two operators, one for unary minus and one for multiplication by a scalar.</span></span> <span data-ttu-id="9e637-113">No exemplo, são necessárias duas sobrecargas para a multiplicação escalar, pois o operador deve funcionar independentemente da ordem em que o vetor e o escalar são exibidos.</span><span class="sxs-lookup"><span data-stu-id="9e637-113">In the example, two overloads for scalar multiplication are needed because the operator must work regardless of the order in which the vector and scalar appear.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a><span data-ttu-id="9e637-114">Criando novos operadores</span><span class="sxs-lookup"><span data-stu-id="9e637-114">Creating New Operators</span></span>

<span data-ttu-id="9e637-115">Você pode sobrecarregar todos os operadores padrão, mas também pode criar novos operadores fora de sequências de determinados caracteres.</span><span class="sxs-lookup"><span data-stu-id="9e637-115">You can overload all the standard operators, but you can also create new operators out of sequences of certain characters.</span></span> <span data-ttu-id="9e637-116">Os caracteres de operador permitidos são,,,,,,, `!` `%` `&` `*` `+` `-` `.` `/` , `<` ,,,,,, `=` `>` `?` `@` `^` `|` e `~` .</span><span class="sxs-lookup"><span data-stu-id="9e637-116">Allowed operator characters are `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, and `~`.</span></span> <span data-ttu-id="9e637-117">O `~` caractere tem o significado especial de tornar um operador unário e não faz parte da sequência de caracteres do operador.</span><span class="sxs-lookup"><span data-stu-id="9e637-117">The `~` character has the special meaning of making an operator unary, and is not part of the operator character sequence.</span></span> <span data-ttu-id="9e637-118">Nem todos os operadores podem se tornar unários.</span><span class="sxs-lookup"><span data-stu-id="9e637-118">Not all operators can be made unary.</span></span>

<span data-ttu-id="9e637-119">Dependendo da sequência de caracteres exata que você usar, o operador terá uma certa precedência e associação.</span><span class="sxs-lookup"><span data-stu-id="9e637-119">Depending on the exact character sequence you use, your operator will have a certain precedence and associativity.</span></span> <span data-ttu-id="9e637-120">A associação pode ser da esquerda para a direita ou da direita para a esquerda e é usada sempre que os operadores do mesmo nível de precedência aparecem em sequência, sem parênteses.</span><span class="sxs-lookup"><span data-stu-id="9e637-120">Associativity can be either left to right or right to left and is used whenever operators of the same level of precedence appear in sequence without parentheses.</span></span>

<span data-ttu-id="9e637-121">O caractere operador não `.` afeta a precedência, de modo que, por exemplo, se você quiser definir sua própria versão de multiplicação que tenha a mesma precedência e associação como multiplicação comum, poderá criar operadores como `.*` .</span><span class="sxs-lookup"><span data-stu-id="9e637-121">The operator character `.` does not affect precedence, so that, for example, if you want to define your own version of multiplication that has the same precedence and associativity as ordinary multiplication, you could create operators such as `.*`.</span></span>

<span data-ttu-id="9e637-122">Somente os operadores `?` e `?<-` podem começar com `?` .</span><span class="sxs-lookup"><span data-stu-id="9e637-122">Only the operators `?` and `?<-` may start with `?`.</span></span>

<span data-ttu-id="9e637-123">Uma tabela que mostra a precedência de todos os operadores em F # pode ser encontrada em [referência de símbolo e operador](./symbol-and-operator-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="9e637-123">A table that shows the precedence of all operators in F# can be found in [Symbol and Operator Reference](./symbol-and-operator-reference/index.md).</span></span>

## <a name="overloaded-operator-names"></a><span data-ttu-id="9e637-124">Nomes de operador sobrecarregados</span><span class="sxs-lookup"><span data-stu-id="9e637-124">Overloaded Operator Names</span></span>

<span data-ttu-id="9e637-125">Quando o compilador F # compila uma expressão de operador, ele gera um método que tem um nome gerado pelo compilador para esse operador.</span><span class="sxs-lookup"><span data-stu-id="9e637-125">When the F# compiler compiles an operator expression, it generates a method that has a compiler-generated name for that operator.</span></span> <span data-ttu-id="9e637-126">Esse é o nome que aparece na MSIL (Microsoft Intermediate Language) para o método e também em reflexão e IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="9e637-126">This is the name that appears in the Microsoft intermediate language (MSIL) for the method, and also in reflection and IntelliSense.</span></span> <span data-ttu-id="9e637-127">Normalmente, você não precisa usar esses nomes no código F #.</span><span class="sxs-lookup"><span data-stu-id="9e637-127">You do not normally need to use these names in F# code.</span></span>

<span data-ttu-id="9e637-128">A tabela a seguir mostra os operadores padrão e seus nomes gerados correspondentes.</span><span class="sxs-lookup"><span data-stu-id="9e637-128">The following table shows the standard operators and their corresponding generated names.</span></span>

|<span data-ttu-id="9e637-129">Operador</span><span class="sxs-lookup"><span data-stu-id="9e637-129">Operator</span></span>|<span data-ttu-id="9e637-130">Nome gerado</span><span class="sxs-lookup"><span data-stu-id="9e637-130">Generated name</span></span>|
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

<span data-ttu-id="9e637-131">Observe que o `not` operador em F # não é emitido `op_Inequality` porque não é um operador simbólico.</span><span class="sxs-lookup"><span data-stu-id="9e637-131">Note that the `not` operator in F# does not emit `op_Inequality` because it is not a symbolic operator.</span></span> <span data-ttu-id="9e637-132">É uma função que emite IL que nega uma expressão booliana.</span><span class="sxs-lookup"><span data-stu-id="9e637-132">It is a function that emits IL that negates a boolean expression.</span></span>

<span data-ttu-id="9e637-133">Outras combinações de caracteres de operador que não estão listadas aqui podem ser usadas como operadores e têm nomes que são compostos por meio da concatenação de nomes para os caracteres individuais da tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="9e637-133">Other combinations of operator characters that are not listed here can be used as operators and have names that are made up by concatenating names for the individual characters from the following table.</span></span> <span data-ttu-id="9e637-134">Por exemplo, +!</span><span class="sxs-lookup"><span data-stu-id="9e637-134">For example, +!</span></span> <span data-ttu-id="9e637-135">se torna `op_PlusBang` .</span><span class="sxs-lookup"><span data-stu-id="9e637-135">becomes `op_PlusBang`.</span></span>

|<span data-ttu-id="9e637-136">Caractere de operador</span><span class="sxs-lookup"><span data-stu-id="9e637-136">Operator character</span></span>|<span data-ttu-id="9e637-137">Nome</span><span class="sxs-lookup"><span data-stu-id="9e637-137">Name</span></span>|
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

## <a name="prefix-and-infix-operators"></a><span data-ttu-id="9e637-138">Operadores de prefixo e infixo</span><span class="sxs-lookup"><span data-stu-id="9e637-138">Prefix and Infix Operators</span></span>

<span data-ttu-id="9e637-139">Espera-se que os operadores de *prefixo* sejam colocados na frente de um operando ou operandos, de forma muito semelhante a uma função.</span><span class="sxs-lookup"><span data-stu-id="9e637-139">*Prefix* operators are expected to be placed in front of an operand or operands, much like a function.</span></span> <span data-ttu-id="9e637-140">Espera-se que os operadores de *infixos* sejam colocados entre os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="9e637-140">*Infix* operators are expected to be placed between the two operands.</span></span>

<span data-ttu-id="9e637-141">Somente determinados operadores podem ser usados como operadores de prefixo.</span><span class="sxs-lookup"><span data-stu-id="9e637-141">Only certain operators can be used as prefix operators.</span></span> <span data-ttu-id="9e637-142">Alguns operadores são sempre operadores de prefixo, outros podem ser infixos ou prefixo e o restante são sempre operadores de infixos.</span><span class="sxs-lookup"><span data-stu-id="9e637-142">Some operators are always prefix operators, others can be infix or prefix, and the rest are always infix operators.</span></span> <span data-ttu-id="9e637-143">Os operadores que começam com `!` , exceto `!=` e o operador `~` , ou sequências repetidas de `~` , são sempre operadores de prefixo.</span><span class="sxs-lookup"><span data-stu-id="9e637-143">Operators that begin with `!`, except `!=`, and the operator `~`, or repeated sequences of`~`, are always prefix operators.</span></span> <span data-ttu-id="9e637-144">Os operadores,,,,,, `+` `-` `+.` `-.` `&` `&&` `%` e `%%` podem ser operadores de prefixo ou operadores de infixos.</span><span class="sxs-lookup"><span data-stu-id="9e637-144">The operators `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, and `%%` can be prefix operators or infix operators.</span></span> <span data-ttu-id="9e637-145">Você distingue a versão de prefixo desses operadores da versão de infixo adicionando um `~` no início de um operador de prefixo quando ele é definido.</span><span class="sxs-lookup"><span data-stu-id="9e637-145">You distinguish the prefix version of these operators from the infix version by adding a `~` at the beginning of a prefix operator when it is defined.</span></span> <span data-ttu-id="9e637-146">O `~` não é usado quando você usa o operador, somente quando ele é definido.</span><span class="sxs-lookup"><span data-stu-id="9e637-146">The `~` is not used when you use the operator, only when it is defined.</span></span>

## <a name="example"></a><span data-ttu-id="9e637-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e637-147">Example</span></span>

<span data-ttu-id="9e637-148">O código a seguir ilustra o uso de sobrecarga de operador para implementar um tipo de fração.</span><span class="sxs-lookup"><span data-stu-id="9e637-148">The following code illustrates the use of operator overloading to implement a fraction type.</span></span> <span data-ttu-id="9e637-149">Uma fração é representada por um numerador e um denominador.</span><span class="sxs-lookup"><span data-stu-id="9e637-149">A fraction is represented by a numerator and a denominator.</span></span> <span data-ttu-id="9e637-150">A função `hcf` é usada para determinar o fator comum mais alto, que é usado para reduzir frações.</span><span class="sxs-lookup"><span data-stu-id="9e637-150">The function `hcf` is used to determine the highest common factor, which is used to reduce fractions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

<span data-ttu-id="9e637-151">**Saída:**</span><span class="sxs-lookup"><span data-stu-id="9e637-151">**Output:**</span></span>

```console
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a><span data-ttu-id="9e637-152">Operadores no nível global</span><span class="sxs-lookup"><span data-stu-id="9e637-152">Operators at the Global Level</span></span>

<span data-ttu-id="9e637-153">Você também pode definir operadores no nível global.</span><span class="sxs-lookup"><span data-stu-id="9e637-153">You can also define operators at the global level.</span></span> <span data-ttu-id="9e637-154">O código a seguir define um operador `+?` .</span><span class="sxs-lookup"><span data-stu-id="9e637-154">The following code defines an operator `+?`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

<span data-ttu-id="9e637-155">A saída do código acima é `12` .</span><span class="sxs-lookup"><span data-stu-id="9e637-155">The output of the above code is `12`.</span></span>

<span data-ttu-id="9e637-156">Você pode redefinir os operadores aritméticos regulares dessa maneira porque as regras de escopo para F # ditam que os operadores recentemente definidos têm precedência sobre os operadores internos.</span><span class="sxs-lookup"><span data-stu-id="9e637-156">You can redefine the regular arithmetic operators in this manner because the scoping rules for F# dictate that newly defined operators take precedence over the built-in operators.</span></span>

<span data-ttu-id="9e637-157">A palavra-chave `inline` é frequentemente usada com operadores globais, que geralmente são funções pequenas que são mais bem integradas ao código de chamada.</span><span class="sxs-lookup"><span data-stu-id="9e637-157">The keyword `inline` is often used with global operators, which are often small functions that are best integrated into the calling code.</span></span> <span data-ttu-id="9e637-158">A criação de funções de operador embutidas também permite que elas trabalhem com parâmetros de tipo resolvidos estaticamente para produzir código genérico resolvido estaticamente.</span><span class="sxs-lookup"><span data-stu-id="9e637-158">Making operator functions inline also enables them to work with statically resolved type parameters to produce statically resolved generic code.</span></span> <span data-ttu-id="9e637-159">Para obter mais informações, consulte [funções embutidas](./functions/inline-functions.md) e [parâmetros de tipo estaticamente resolvidos](./generics/statically-resolved-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="9e637-159">For more information, see [Inline Functions](./functions/inline-functions.md) and [Statically Resolved Type Parameters](./generics/statically-resolved-type-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9e637-160">Confira também</span><span class="sxs-lookup"><span data-stu-id="9e637-160">See also</span></span>

- [<span data-ttu-id="9e637-161">Membros</span><span class="sxs-lookup"><span data-stu-id="9e637-161">Members</span></span>](./members/index.md)
