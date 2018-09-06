---
title: Sobrecarga de operador (F#)
description: 'Saiba como sobrecarregar operadores aritméticos em uma classe ou tipo de registro e no nível global em F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 6232ebf215289e6a22b9d77fbd5fa67b82460486
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43798733"
---
# <a name="operator-overloading"></a><span data-ttu-id="c663a-103">Sobrecarga de operador</span><span class="sxs-lookup"><span data-stu-id="c663a-103">Operator Overloading</span></span>

<span data-ttu-id="c663a-104">Este tópico descreve como sobrecarregar operadores aritméticos em uma classe ou tipo de registro e no nível global.</span><span class="sxs-lookup"><span data-stu-id="c663a-104">This topic describes how to overload arithmetic operators in a class or record type, and at the global level.</span></span>

## <a name="syntax"></a><span data-ttu-id="c663a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c663a-105">Syntax</span></span>

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a><span data-ttu-id="c663a-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="c663a-106">Remarks</span></span>

<span data-ttu-id="c663a-107">Na sintaxe anterior, o *símbolo do operador* é uma das `+`, `-`, `*`, `/`, `=`e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="c663a-107">In the previous syntax, the *operator-symbol* is one of `+`, `-`, `*`, `/`, `=`, and so on.</span></span> <span data-ttu-id="c663a-108">O *lista de parâmetros* Especifica os operandos na ordem em que aparecem na sintaxe comum para esse operador.</span><span class="sxs-lookup"><span data-stu-id="c663a-108">The *parameter-list* specifies the operands in the order they appear in the usual syntax for that operator.</span></span> <span data-ttu-id="c663a-109">O *corpo do método* constrói o valor resultante.</span><span class="sxs-lookup"><span data-stu-id="c663a-109">The *method-body* constructs the resulting value.</span></span>

<span data-ttu-id="c663a-110">Sobrecargas de operador para os operadores devem ser estáticas.</span><span class="sxs-lookup"><span data-stu-id="c663a-110">Operator overloads for operators must be static.</span></span> <span data-ttu-id="c663a-111">Sobrecargas de operador para operadores unários, tais como `+` e `-`, deve usar um til (`~`) na *símbolo do operador* para indicar que o operador é um operador unário e não é um operador binário, conforme mostrado no declaração a seguir.</span><span class="sxs-lookup"><span data-stu-id="c663a-111">Operator overloads for unary operators, such as `+` and `-`, must use a tilde (`~`) in the *operator-symbol* to indicate that the operator is a unary operator and not a binary operator, as shown in the following declaration.</span></span>

```fsharp
static member (~-) (v : Vector)
```

<span data-ttu-id="c663a-112">O código a seguir ilustra uma classe de vetor que tem apenas dois operadores, um para menos unário e outro para multiplicação por um escalar.</span><span class="sxs-lookup"><span data-stu-id="c663a-112">The following code illustrates a vector class that has just two operators, one for unary minus and one for multiplication by a scalar.</span></span> <span data-ttu-id="c663a-113">No exemplo, duas sobrecargas para multiplicação escalar são necessárias porque o operador deve trabalhar independentemente da ordem na qual o vetor e escalar aparecem.</span><span class="sxs-lookup"><span data-stu-id="c663a-113">In the example, two overloads for scalar multiplication are needed because the operator must work regardless of the order in which the vector and scalar appear.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a><span data-ttu-id="c663a-114">Criação de novos operadores</span><span class="sxs-lookup"><span data-stu-id="c663a-114">Creating New Operators</span></span>

<span data-ttu-id="c663a-115">Você pode sobrecarregar operadores padrão, mas você também pode criar novos operadores fora de sequências de determinados caracteres.</span><span class="sxs-lookup"><span data-stu-id="c663a-115">You can overload all the standard operators, but you can also create new operators out of sequences of certain characters.</span></span> <span data-ttu-id="c663a-116">Permitidos são caracteres de operador `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, e `~`.</span><span class="sxs-lookup"><span data-stu-id="c663a-116">Allowed operator characters are `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, and `~`.</span></span> <span data-ttu-id="c663a-117">O `~` caractere tem um significado especial de criação de um operador unário e não faz parte da sequência de caracteres de operador.</span><span class="sxs-lookup"><span data-stu-id="c663a-117">The `~` character has the special meaning of making an operator unary, and is not part of the operator character sequence.</span></span> <span data-ttu-id="c663a-118">Nem todos os operadores podem ser feitos unário.</span><span class="sxs-lookup"><span data-stu-id="c663a-118">Not all operators can be made unary.</span></span>

<span data-ttu-id="c663a-119">A sequência de caracteres exata que você usar, dependendo do seu operador terá um determinado precedência e associatividade.</span><span class="sxs-lookup"><span data-stu-id="c663a-119">Depending on the exact character sequence you use, your operator will have a certain precedence and associativity.</span></span> <span data-ttu-id="c663a-120">Associatividade ou pode ser deixada para a direita ou da direita para esquerda e é usada sempre que os operadores do mesmo nível de precedência aparecem em sequência, sem parênteses.</span><span class="sxs-lookup"><span data-stu-id="c663a-120">Associativity can be either left to right or right to left and is used whenever operators of the same level of precedence appear in sequence without parentheses.</span></span>

<span data-ttu-id="c663a-121">O caractere de operador `.` não afeta a precedência, para que, por exemplo, se você quiser definir sua própria versão de multiplicação que tem a mesma precedência e associatividade como multiplicação comum, você poderia criar operadores, como `.*`.</span><span class="sxs-lookup"><span data-stu-id="c663a-121">The operator character `.` does not affect precedence, so that, for example, if you want to define your own version of multiplication that has the same precedence and associativity as ordinary multiplication, you could create operators such as `.*`.</span></span>

<span data-ttu-id="c663a-122">Somente os operadores `?` e `?<-` pode começar com `?`.</span><span class="sxs-lookup"><span data-stu-id="c663a-122">Only the operators `?` and `?<-` may start with `?`.</span></span>

<span data-ttu-id="c663a-123">Uma tabela que mostra a precedência de todos os operadores em F # pode ser encontrada na [referência de símbolos e operador](symbol-and-operator-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="c663a-123">A table that shows the precedence of all operators in F# can be found in [Symbol and Operator Reference](symbol-and-operator-reference/index.md).</span></span>

## <a name="overloaded-operator-names"></a><span data-ttu-id="c663a-124">Nomes de operador sobrecarregado</span><span class="sxs-lookup"><span data-stu-id="c663a-124">Overloaded Operator Names</span></span>

<span data-ttu-id="c663a-125">Quando o compilador F # compila uma expressão de operador, ele gera um método que tem um nome gerado pelo compilador para esse operador.</span><span class="sxs-lookup"><span data-stu-id="c663a-125">When the F# compiler compiles an operator expression, it generates a method that has a compiler-generated name for that operator.</span></span> <span data-ttu-id="c663a-126">Esse é o nome que aparece no Microsoft intermediate language (MSIL) para o método e também na reflexão e IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c663a-126">This is the name that appears in the Microsoft intermediate language (MSIL) for the method, and also in reflection and IntelliSense.</span></span> <span data-ttu-id="c663a-127">Normalmente, não é necessário usar esses nomes no código F #.</span><span class="sxs-lookup"><span data-stu-id="c663a-127">You do not normally need to use these names in F# code.</span></span>

<span data-ttu-id="c663a-128">A tabela a seguir mostra os operadores padrão e suas respectivas nomes gerados.</span><span class="sxs-lookup"><span data-stu-id="c663a-128">The following table shows the standard operators and their corresponding generated names.</span></span>

|<span data-ttu-id="c663a-129">Operador</span><span class="sxs-lookup"><span data-stu-id="c663a-129">Operator</span></span>|<span data-ttu-id="c663a-130">Nome gerado</span><span class="sxs-lookup"><span data-stu-id="c663a-130">Generated name</span></span>|
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

<span data-ttu-id="c663a-131">Outras combinações de caracteres de operador que não estão listados aqui podem ser usadas como operadores e têm nomes que são compostos por meio da concatenação nomes para os caracteres individuais da tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="c663a-131">Other combinations of operator characters that are not listed here can be used as operators and have names that are made up by concatenating names for the individual characters from the following table.</span></span> <span data-ttu-id="c663a-132">Por exemplo, +!</span><span class="sxs-lookup"><span data-stu-id="c663a-132">For example, +!</span></span> <span data-ttu-id="c663a-133">se torna `op_PlusBang`.</span><span class="sxs-lookup"><span data-stu-id="c663a-133">becomes `op_PlusBang`.</span></span>

|<span data-ttu-id="c663a-134">Caractere de operador</span><span class="sxs-lookup"><span data-stu-id="c663a-134">Operator character</span></span>|<span data-ttu-id="c663a-135">Nome</span><span class="sxs-lookup"><span data-stu-id="c663a-135">Name</span></span>|
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

## <a name="prefix-and-infix-operators"></a><span data-ttu-id="c663a-136">Operadores Infixos e prefixo</span><span class="sxs-lookup"><span data-stu-id="c663a-136">Prefix and Infix Operators</span></span>

<span data-ttu-id="c663a-137">*Prefixo* operadores devem ser colocado na frente de um operando ou operandos, assim como uma função.</span><span class="sxs-lookup"><span data-stu-id="c663a-137">*Prefix* operators are expected to be placed in front of an operand or operands, much like a function.</span></span> <span data-ttu-id="c663a-138">*Infixo* operadores devem ser colocados entre os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="c663a-138">*Infix* operators are expected to be placed between the two operands.</span></span>

<span data-ttu-id="c663a-139">Apenas certos operadores podem ser usados como operadores de prefixo.</span><span class="sxs-lookup"><span data-stu-id="c663a-139">Only certain operators can be used as prefix operators.</span></span> <span data-ttu-id="c663a-140">Alguns operadores sempre são operadores de prefixo, outros podem ser fixos ou prefixo e o restante são sempre de infixo operadores.</span><span class="sxs-lookup"><span data-stu-id="c663a-140">Some operators are always prefix operators, others can be infix or prefix, and the rest are always infix operators.</span></span> <span data-ttu-id="c663a-141">Os operadores que começam com `!`, exceto `!=`e o operador `~`, ou repetidas de sequências de`~`, sempre são operadores de prefixo.</span><span class="sxs-lookup"><span data-stu-id="c663a-141">Operators that begin with `!`, except `!=`, and the operator `~`, or repeated sequences of`~`, are always prefix operators.</span></span> <span data-ttu-id="c663a-142">Os operadores `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, e `%%` podem ser operadores de prefixo ou operadores de infixo.</span><span class="sxs-lookup"><span data-stu-id="c663a-142">The operators `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, and `%%` can be prefix operators or infix operators.</span></span> <span data-ttu-id="c663a-143">Distinguir a versão de prefixo desses operadores da versão de infixo adicionando um `~` no início de um operador de prefixo quando ele está definido.</span><span class="sxs-lookup"><span data-stu-id="c663a-143">You distinguish the prefix version of these operators from the infix version by adding a `~` at the beginning of a prefix operator when it is defined.</span></span> <span data-ttu-id="c663a-144">O `~` não é usado quando você usa o operador, apenas quando ele está definido.</span><span class="sxs-lookup"><span data-stu-id="c663a-144">The `~` is not used when you use the operator, only when it is defined.</span></span>

## <a name="example"></a><span data-ttu-id="c663a-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c663a-145">Example</span></span>

<span data-ttu-id="c663a-146">O código a seguir ilustra o uso de sobrecarga de operador para implementar um tipo de fração.</span><span class="sxs-lookup"><span data-stu-id="c663a-146">The following code illustrates the use of operator overloading to implement a fraction type.</span></span> <span data-ttu-id="c663a-147">Uma fração é representada por um numerador e um denominador.</span><span class="sxs-lookup"><span data-stu-id="c663a-147">A fraction is represented by a numerator and a denominator.</span></span> <span data-ttu-id="c663a-148">A função `hcf` é usado para determinar o fator de comuns mais alto, que é usado para reduzir frações.</span><span class="sxs-lookup"><span data-stu-id="c663a-148">The function `hcf` is used to determine the highest common factor, which is used to reduce fractions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

<span data-ttu-id="c663a-149">**Saída:**</span><span class="sxs-lookup"><span data-stu-id="c663a-149">**Output:**</span></span>

```
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a><span data-ttu-id="c663a-150">Operadores no nível Global</span><span class="sxs-lookup"><span data-stu-id="c663a-150">Operators at the Global Level</span></span>

<span data-ttu-id="c663a-151">Você também pode definir operadores no nível global.</span><span class="sxs-lookup"><span data-stu-id="c663a-151">You can also define operators at the global level.</span></span> <span data-ttu-id="c663a-152">O código a seguir define um operador `+?`.</span><span class="sxs-lookup"><span data-stu-id="c663a-152">The following code defines an operator `+?`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

<span data-ttu-id="c663a-153">A saída do código acima é `12`.</span><span class="sxs-lookup"><span data-stu-id="c663a-153">The output of the above code is `12`.</span></span>

<span data-ttu-id="c663a-154">Você pode redefinir os operadores aritméticos regulares dessa maneira porque as regras de escopo para F # ditam que recém-definido operadores têm precedência sobre os operadores internos.</span><span class="sxs-lookup"><span data-stu-id="c663a-154">You can redefine the regular arithmetic operators in this manner because the scoping rules for F# dictate that newly defined operators take precedence over the built-in operators.</span></span>

<span data-ttu-id="c663a-155">A palavra-chave `inline` é frequentemente usado com operadores globais, que geralmente são pequenas funções que são mais bem integradas ao código de chamada.</span><span class="sxs-lookup"><span data-stu-id="c663a-155">The keyword `inline` is often used with global operators, which are often small functions that are best integrated into the calling code.</span></span> <span data-ttu-id="c663a-156">Tomada de operador funções embutidas também permite para trabalhar com parâmetros de tipo estaticamente resolvidos para produzir código genérico estaticamente resolvido.</span><span class="sxs-lookup"><span data-stu-id="c663a-156">Making operator functions inline also enables them to work with statically resolved type parameters to produce statically resolved generic code.</span></span> <span data-ttu-id="c663a-157">Para obter mais informações, consulte [funções embutidas](functions/inline-functions.md) e [estaticamente parâmetros de tipo resolvidos](generics/statically-resolved-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="c663a-157">For more information, see [Inline Functions](functions/inline-functions.md) and [Statically Resolved Type Parameters](generics/statically-resolved-type-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c663a-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c663a-158">See also</span></span>

- [<span data-ttu-id="c663a-159">Membros</span><span class="sxs-lookup"><span data-stu-id="c663a-159">Members</span></span>](members/index.md)
