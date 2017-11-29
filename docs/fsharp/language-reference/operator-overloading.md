---
title: Sobrecarga de operador (F#)
description: "Aprenda a sobrecarga de operadores aritméticos em uma classe ou um tipo de registro e no nível global em F #."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 019277ed-f649-4fa5-ad43-097865f449d9
ms.openlocfilehash: 76ddab5339e11d71bb326b60d727017eb838ccf4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="operator-overloading"></a><span data-ttu-id="8b8f2-104">Sobrecarga de operador</span><span class="sxs-lookup"><span data-stu-id="8b8f2-104">Operator Overloading</span></span>

<span data-ttu-id="8b8f2-105">Este tópico descreve como a sobrecarga de operadores aritméticos em uma classe ou um tipo de registro e no nível global.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-105">This topic describes how to overload arithmetic operators in a class or record type, and at the global level.</span></span>


## <a name="syntax"></a><span data-ttu-id="8b8f2-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b8f2-106">Syntax</span></span>

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a><span data-ttu-id="8b8f2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b8f2-107">Remarks</span></span>
<span data-ttu-id="8b8f2-108">Na sintaxe anterior, o *símbolo do operador* é um dos `+`, `-`, `*`, `/`, `=`e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-108">In the previous syntax, the *operator-symbol* is one of `+`, `-`, `*`, `/`, `=`, and so on.</span></span> <span data-ttu-id="8b8f2-109">O *a lista de parâmetros* Especifica os operandos na ordem em que aparecem na sintaxe comum para esse operador.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-109">The *parameter-list* specifies the operands in the order they appear in the usual syntax for that operator.</span></span> <span data-ttu-id="8b8f2-110">O *corpo de método* constrói o valor resultante.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-110">The *method-body* constructs the resulting value.</span></span>

<span data-ttu-id="8b8f2-111">Sobrecargas de operador para operadores devem ser estáticas.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-111">Operator overloads for operators must be static.</span></span> <span data-ttu-id="8b8f2-112">Sobrecargas de operador para operadores unários, tais como `+` e `-`, deve usar um til (`~`) no *símbolo do operador* para indicar que o operador é um operador unário e não é um operador binário, conforme mostrado do declaração a seguir.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-112">Operator overloads for unary operators, such as `+` and `-`, must use a tilde (`~`) in the *operator-symbol* to indicate that the operator is a unary operator and not a binary operator, as shown in the following declaration.</span></span>

```fsharp
static member (~-) (v : Vector)
```

<span data-ttu-id="8b8f2-113">O código a seguir ilustra uma classe de vetor que tem apenas dois operadores, uma para unária de subtração e outra para multiplicação por um valor escalar.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-113">The following code illustrates a vector class that has just two operators, one for unary minus and one for multiplication by a scalar.</span></span> <span data-ttu-id="8b8f2-114">No exemplo, duas sobrecargas para multiplicação escalar são necessárias porque o operador deve funcionar independentemente da ordem na qual o vetor e escalar aparecem.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-114">In the example, two overloads for scalar multiplication are needed because the operator must work regardless of the order in which the vector and scalar appear.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a><span data-ttu-id="8b8f2-115">Criando novos operadores</span><span class="sxs-lookup"><span data-stu-id="8b8f2-115">Creating New Operators</span></span>
<span data-ttu-id="8b8f2-116">Você pode sobrecarregar os operadores padrão, mas você também pode criar novos operadores fora de sequências de determinados caracteres.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-116">You can overload all the standard operators, but you can also create new operators out of sequences of certain characters.</span></span> <span data-ttu-id="8b8f2-117">Permitidos são caracteres de operador `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, e `~`.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-117">Allowed operator characters are `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, and `~`.</span></span> <span data-ttu-id="8b8f2-118">O `~` caracteres tem um significado especial de criação de um operador unário e não faz parte da sequência de caracteres de operador.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-118">The `~` character has the special meaning of making an operator unary, and is not part of the operator character sequence.</span></span> <span data-ttu-id="8b8f2-119">Nem todos os operadores podem ser feitos unário.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-119">Not all operators can be made unary.</span></span>

<span data-ttu-id="8b8f2-120">Dependendo da sequência de caracteres exata que você usar, seu operador terá um determinado precedência e associação.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-120">Depending on the exact character sequence you use, your operator will have a certain precedence and associativity.</span></span> <span data-ttu-id="8b8f2-121">Capacidade de associação pode ser deixada ou para a direita ou da direita para esquerda e é usada sempre que os operadores do mesmo nível de precedência aparecem em sequência, sem parênteses.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-121">Associativity can be either left to right or right to left and is used whenever operators of the same level of precedence appear in sequence without parentheses.</span></span>

<span data-ttu-id="8b8f2-122">O caractere de operador `.` não afeta a precedência, para que, por exemplo, se você quiser definir sua própria versão da multiplicação que tem a mesma precedência e associatividade como multiplicação comum, pode criar operadores como `.*`.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-122">The operator character `.` does not affect precedence, so that, for example, if you want to define your own version of multiplication that has the same precedence and associativity as ordinary multiplication, you could create operators such as `.*`.</span></span>

<span data-ttu-id="8b8f2-123">Somente os operadores `?` e `?<-` pode começar com `?`.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-123">Only the operators `?` and `?<-` may start with `?`.</span></span>

<span data-ttu-id="8b8f2-124">Uma tabela que mostra a precedência de todos os operadores em F # pode ser encontrada em [símbolo e referência de operador](symbol-and-operator-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="8b8f2-124">A table that shows the precedence of all operators in F# can be found in [Symbol and Operator Reference](symbol-and-operator-reference/index.md).</span></span>


## <a name="overloaded-operator-names"></a><span data-ttu-id="8b8f2-125">Nomes de operador sobrecarregado</span><span class="sxs-lookup"><span data-stu-id="8b8f2-125">Overloaded Operator Names</span></span>
<span data-ttu-id="8b8f2-126">Quando o compilador F # compila uma expressão de operador, ele gera um método que tem um nome gerado pelo compilador para esse operador.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-126">When the F# compiler compiles an operator expression, it generates a method that has a compiler-generated name for that operator.</span></span> <span data-ttu-id="8b8f2-127">Esse é o nome que aparece no Microsoft intermediate language (MSIL) para o método e também em reflexão e IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-127">This is the name that appears in the Microsoft intermediate language (MSIL) for the method, and also in reflection and IntelliSense.</span></span> <span data-ttu-id="8b8f2-128">Normalmente, não é necessário usar esses nomes no código F #.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-128">You do not normally need to use these names in F# code.</span></span>

<span data-ttu-id="8b8f2-129">A tabela a seguir mostra os operadores padrão e seus correspondente nomes gerados.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-129">The following table shows the standard operators and their corresponding generated names.</span></span>



|<span data-ttu-id="8b8f2-130">Operador</span><span class="sxs-lookup"><span data-stu-id="8b8f2-130">Operator</span></span>|<span data-ttu-id="8b8f2-131">Nome gerado</span><span class="sxs-lookup"><span data-stu-id="8b8f2-131">Generated name</span></span>|
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
<span data-ttu-id="8b8f2-132">Outras combinações de caracteres de operador que não estão listados aqui podem ser usadas como operadores e têm nomes que são compostos concatenando os nomes para os caracteres individuais da tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-132">Other combinations of operator characters that are not listed here can be used as operators and have names that are made up by concatenating names for the individual characters from the following table.</span></span> <span data-ttu-id="8b8f2-133">Por exemplo, +!</span><span class="sxs-lookup"><span data-stu-id="8b8f2-133">For example, +!</span></span> <span data-ttu-id="8b8f2-134">torna-se `op_PlusBang`.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-134">becomes `op_PlusBang`.</span></span>



|<span data-ttu-id="8b8f2-135">Caractere de operador</span><span class="sxs-lookup"><span data-stu-id="8b8f2-135">Operator character</span></span>|<span data-ttu-id="8b8f2-136">Nome</span><span class="sxs-lookup"><span data-stu-id="8b8f2-136">Name</span></span>|
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

## <a name="prefix-and-infix-operators"></a><span data-ttu-id="8b8f2-137">Prefixo e operadores fixos</span><span class="sxs-lookup"><span data-stu-id="8b8f2-137">Prefix and Infix Operators</span></span>
<span data-ttu-id="8b8f2-138">*Prefixo* operadores devem ser colocado na frente de um operando ou operandos, semelhante a uma função.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-138">*Prefix* operators are expected to be placed in front of an operand or operands, much like a function.</span></span> <span data-ttu-id="8b8f2-139">*Infixo* operadores devem ser colocados entre os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-139">*Infix* operators are expected to be placed between the two operands.</span></span>

<span data-ttu-id="8b8f2-140">Apenas certos operadores podem ser usados como operadores de prefixo.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-140">Only certain operators can be used as prefix operators.</span></span> <span data-ttu-id="8b8f2-141">Alguns operadores sempre são operadores de prefixo, outros podem ser fixos ou prefixo e o restante são sempre infixo operadores.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-141">Some operators are always prefix operators, others can be infix or prefix, and the rest are always infix operators.</span></span> <span data-ttu-id="8b8f2-142">Operadores que começam com `!`, exceto `!=`e o operador `~`, ou repetido sequências de`~`, sempre são operadores de prefixo.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-142">Operators that begin with `!`, except `!=`, and the operator `~`, or repeated sequences of`~`, are always prefix operators.</span></span> <span data-ttu-id="8b8f2-143">Os operadores `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, e `%%` pode ser operadores de prefixo ou infixo operadores.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-143">The operators `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, and `%%` can be prefix operators or infix operators.</span></span> <span data-ttu-id="8b8f2-144">Distinguir a versão de prefixo desses operadores da versão infixo adicionando um `~` no início de um operador de prefixo quando ele está definido.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-144">You distinguish the prefix version of these operators from the infix version by adding a `~` at the beginning of a prefix operator when it is defined.</span></span> <span data-ttu-id="8b8f2-145">O `~` não é usado quando você usa o operador, apenas quando ele está definido.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-145">The `~` is not used when you use the operator, only when it is defined.</span></span>

## <a name="example"></a><span data-ttu-id="8b8f2-146">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8b8f2-146">Example</span></span>

<span data-ttu-id="8b8f2-147">O código a seguir ilustra o uso de sobrecarga de operador para implementar um tipo de fração.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-147">The following code illustrates the use of operator overloading to implement a fraction type.</span></span> <span data-ttu-id="8b8f2-148">Uma fração é representada por um numerador e um denominador.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-148">A fraction is represented by a numerator and a denominator.</span></span> <span data-ttu-id="8b8f2-149">A função `hcf` é usada para determinar o fator de comum mais alta, que é usado para reduzir frações.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-149">The function `hcf` is used to determine the highest common factor, which is used to reduce fractions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

<span data-ttu-id="8b8f2-150">**Saída:**</span><span class="sxs-lookup"><span data-stu-id="8b8f2-150">**Output:**</span></span>

```
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a><span data-ttu-id="8b8f2-151">Operadores no nível Global</span><span class="sxs-lookup"><span data-stu-id="8b8f2-151">Operators at the Global Level</span></span>
<span data-ttu-id="8b8f2-152">Você também pode definir operadores no nível global.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-152">You can also define operators at the global level.</span></span> <span data-ttu-id="8b8f2-153">O código a seguir define um operador `+?`.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-153">The following code defines an operator `+?`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

<span data-ttu-id="8b8f2-154">A saída do código acima é `12`.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-154">The output of the above code is `12`.</span></span>

<span data-ttu-id="8b8f2-155">Você pode redefinir os operadores aritméticos regulares dessa maneira porque as regras de escopo para F # ditam que recém-definido operadores têm precedência sobre os operadores internos.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-155">You can redefine the regular arithmetic operators in this manner because the scoping rules for F# dictate that newly defined operators take precedence over the built-in operators.</span></span>

<span data-ttu-id="8b8f2-156">A palavra-chave `inline` é frequentemente usada com operadores globais, que geralmente são pequenas funções que estão integradas melhor o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-156">The keyword `inline` is often used with global operators, which are often small functions that are best integrated into the calling code.</span></span> <span data-ttu-id="8b8f2-157">Fazer operador funções embutidas também permite trabalhar com parâmetros de tipo resolvidos estaticamente para gerar o código genérico resolvido estaticamente.</span><span class="sxs-lookup"><span data-stu-id="8b8f2-157">Making operator functions inline also enables them to work with statically resolved type parameters to produce statically resolved generic code.</span></span> <span data-ttu-id="8b8f2-158">Para obter mais informações, consulte [funções embutidas](functions/inline-functions.md) e [resolvidos estaticamente parâmetros de tipo](generics/statically-resolved-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="8b8f2-158">For more information, see [Inline Functions](functions/inline-functions.md) and [Statically Resolved Type Parameters](generics/statically-resolved-type-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8b8f2-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b8f2-159">See Also</span></span>
[<span data-ttu-id="8b8f2-160">Membros</span><span class="sxs-lookup"><span data-stu-id="8b8f2-160">Members</span></span>](members/index.md)
