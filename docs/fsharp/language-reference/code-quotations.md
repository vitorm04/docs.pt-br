---
title: Citações de código
description: 'Saiba mais sobre as cotações de código F #, um recurso de linguagem que permite gerar e trabalhar com expressões de código F # programaticamente.'
ms.date: 08/13/2020
ms.openlocfilehash: dc37fdbd6cd29e5ee94e5c0186dfe2bfeb666f32
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557188"
---
# <a name="code-quotations"></a><span data-ttu-id="c6693-103">Cotações de código</span><span class="sxs-lookup"><span data-stu-id="c6693-103">Code quotations</span></span>

<span data-ttu-id="c6693-104">Este artigo descreve as *Cotações de código* , um recurso de linguagem que permite gerar e trabalhar com expressões de código F # programaticamente.</span><span class="sxs-lookup"><span data-stu-id="c6693-104">This article describes *code quotations* , a language feature that enables you to generate and work with F# code expressions programmatically.</span></span> <span data-ttu-id="c6693-105">Esse recurso permite gerar uma árvore de sintaxe abstrata que representa o código F #.</span><span class="sxs-lookup"><span data-stu-id="c6693-105">This feature lets you generate an abstract syntax tree that represents F# code.</span></span> <span data-ttu-id="c6693-106">A árvore de sintaxe abstrata pode ser atravessada e processada de acordo com as necessidades do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c6693-106">The abstract syntax tree can then be traversed and processed according to the needs of your application.</span></span> <span data-ttu-id="c6693-107">Por exemplo, você pode usar a árvore para gerar código F # ou gerar código em alguma outra linguagem.</span><span class="sxs-lookup"><span data-stu-id="c6693-107">For example, you can use the tree to generate F# code or generate code in some other language.</span></span>

## <a name="quoted-expressions"></a><span data-ttu-id="c6693-108">Expressões entre aspas</span><span class="sxs-lookup"><span data-stu-id="c6693-108">Quoted Expressions</span></span>

<span data-ttu-id="c6693-109">Uma *expressão entre aspas* é uma expressão F # em seu código que é delimitada de tal forma que não é compilada como parte do seu programa, mas em vez disso é compilada em um objeto que representa uma expressão F #.</span><span class="sxs-lookup"><span data-stu-id="c6693-109">A *quoted expression* is an F# expression in your code that is delimited in such a way that it is not compiled as part of your program, but instead is compiled into an object that represents an F# expression.</span></span> <span data-ttu-id="c6693-110">Você pode marcar uma expressão entre aspas de uma das duas maneiras: com informações de tipo ou sem informações de tipo.</span><span class="sxs-lookup"><span data-stu-id="c6693-110">You can mark a quoted expression in one of two ways: either with type information or without type information.</span></span> <span data-ttu-id="c6693-111">Se você quiser incluir informações de tipo, use os símbolos `<@` e `@>` para delimitar a expressão entre aspas.</span><span class="sxs-lookup"><span data-stu-id="c6693-111">If you want to include type information, you use the symbols `<@` and `@>` to delimit the quoted expression.</span></span> <span data-ttu-id="c6693-112">Se você não precisar de informações de tipo, use os símbolos `<@@` e `@@>` .</span><span class="sxs-lookup"><span data-stu-id="c6693-112">If you do not need type information, you use the symbols `<@@` and `@@>`.</span></span> <span data-ttu-id="c6693-113">O código a seguir mostra as cotações digitadas e não tipadas.</span><span class="sxs-lookup"><span data-stu-id="c6693-113">The following code shows typed and untyped quotations.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

<span data-ttu-id="c6693-114">Percorrer uma árvore de expressão grande é mais rápido se você não incluir informações de tipo.</span><span class="sxs-lookup"><span data-stu-id="c6693-114">Traversing a large expression tree is faster if you do not include type information.</span></span> <span data-ttu-id="c6693-115">O tipo resultante de uma expressão citada com os símbolos tipados é `Expr<'T>` , em que o parâmetro de tipo tem o tipo da expressão, conforme determinado pelo algoritmo de inferência de tipo do compilador F #.</span><span class="sxs-lookup"><span data-stu-id="c6693-115">The resulting type of an expression quoted with the typed symbols is `Expr<'T>`, where the type parameter has the type of the expression as determined by the F# compiler's type inference algorithm.</span></span> <span data-ttu-id="c6693-116">Quando você usa Cotações de código sem informações de tipo, o tipo da expressão entre aspas é a [expr](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html)de tipo não genérico.</span><span class="sxs-lookup"><span data-stu-id="c6693-116">When you use code quotations without type information, the type of the quoted expression is the non-generic type [Expr](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html).</span></span> <span data-ttu-id="c6693-117">Você pode chamar a propriedade [RAW](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr-1.html#Raw) na classe tipada `Expr` para obter o objeto não tipado `Expr` .</span><span class="sxs-lookup"><span data-stu-id="c6693-117">You can call the [Raw](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr-1.html#Raw) property on the typed `Expr` class to obtain the untyped `Expr` object.</span></span>

<span data-ttu-id="c6693-118">Há uma variedade de métodos estáticos que permitem gerar objetos de expressão F # programaticamente na `Expr` classe sem usar expressões entre aspas.</span><span class="sxs-lookup"><span data-stu-id="c6693-118">There are a variety of static methods that allow you to generate F# expression objects programmatically in the `Expr` class without using quoted expressions.</span></span>

<span data-ttu-id="c6693-119">Observe que uma cotação de código deve incluir uma expressão completa.</span><span class="sxs-lookup"><span data-stu-id="c6693-119">Note that a code quotation must include a complete expression.</span></span> <span data-ttu-id="c6693-120">Para uma `let` associação, por exemplo, você precisa da definição do nome associado e de uma expressão adicional que usa a associação.</span><span class="sxs-lookup"><span data-stu-id="c6693-120">For a `let` binding, for example, you need both the definition of the bound name and an additional expression that uses the binding.</span></span> <span data-ttu-id="c6693-121">Na sintaxe detalhada, essa é uma expressão que segue a `in` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="c6693-121">In verbose syntax, this is an expression that follows the `in` keyword.</span></span> <span data-ttu-id="c6693-122">No nível superior de um módulo, essa é apenas a próxima expressão no módulo, mas em uma cotação, ela é explicitamente necessária.</span><span class="sxs-lookup"><span data-stu-id="c6693-122">At the top-level in a module, this is just the next expression in the module, but in a quotation, it is explicitly required.</span></span>

<span data-ttu-id="c6693-123">Portanto, a expressão a seguir não é válida.</span><span class="sxs-lookup"><span data-stu-id="c6693-123">Therefore, the following expression is not valid.</span></span>

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

<span data-ttu-id="c6693-124">Mas as expressões a seguir são válidas.</span><span class="sxs-lookup"><span data-stu-id="c6693-124">But the following expressions are valid.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

<span data-ttu-id="c6693-125">Para avaliar as cotações de F #, você deve usar o [avaliador de cotação f #](https://github.com/fsprojects/FSharp.Quotations.Evaluator).</span><span class="sxs-lookup"><span data-stu-id="c6693-125">To evaluate F# quotations, you must use the [F# Quotation Evaluator](https://github.com/fsprojects/FSharp.Quotations.Evaluator).</span></span> <span data-ttu-id="c6693-126">Ele fornece suporte para avaliar e executar objetos de expressão F #.</span><span class="sxs-lookup"><span data-stu-id="c6693-126">It provides support for evaluating and executing F# expression objects.</span></span>

<span data-ttu-id="c6693-127">As cotações de F # também mantêm informações de restrição de tipo.</span><span class="sxs-lookup"><span data-stu-id="c6693-127">F# quotations also retain type constraint information.</span></span> <span data-ttu-id="c6693-128">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="c6693-128">Consider the following example:</span></span>

```fsharp
open FSharp.Linq.RuntimeHelpers

let eval q = LeafExpressionConverter.EvaluateQuotation q

let inline negate x = -x
// val inline negate: x: ^a ->  ^a when  ^a : (static member ( ~- ) :  ^a ->  ^a)

<@ negate 1.0 @>  |> eval
```

<span data-ttu-id="c6693-129">A restrição gerada pela `inline` função é mantida no código qutoation.</span><span class="sxs-lookup"><span data-stu-id="c6693-129">The constraint generated by the `inline` function is retained in the code qutoation.</span></span> <span data-ttu-id="c6693-130">O `negate` formulário quotated da função agora pode ser avaliado.</span><span class="sxs-lookup"><span data-stu-id="c6693-130">The `negate` function's quotated form can now be evaluated.</span></span>

## <a name="expr-type"></a><span data-ttu-id="c6693-131">Tipo de expr</span><span class="sxs-lookup"><span data-stu-id="c6693-131">Expr Type</span></span>

<span data-ttu-id="c6693-132">Uma instância do `Expr` tipo representa uma expressão F #.</span><span class="sxs-lookup"><span data-stu-id="c6693-132">An instance of the `Expr` type represents an F# expression.</span></span> <span data-ttu-id="c6693-133">Os tipos genérico e não genérico `Expr` são documentados na documentação da biblioteca F #.</span><span class="sxs-lookup"><span data-stu-id="c6693-133">Both the generic and the non-generic `Expr` types are documented in the F# library documentation.</span></span> <span data-ttu-id="c6693-134">Para obter mais informações, consulte o [namespace de FSharp. Cotações](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations.html) e a [classe requotas. expr](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html).</span><span class="sxs-lookup"><span data-stu-id="c6693-134">For more information, see [FSharp.Quotations Namespace](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations.html) and [Quotations.Expr Class](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html).</span></span>

## <a name="splicing-operators"></a><span data-ttu-id="c6693-135">Operadores da União</span><span class="sxs-lookup"><span data-stu-id="c6693-135">Splicing Operators</span></span>

<span data-ttu-id="c6693-136">O da União permite combinar Cotações de código literais com expressões que você criou programaticamente ou de outra cotação de código.</span><span class="sxs-lookup"><span data-stu-id="c6693-136">Splicing enables you to combine literal code quotations with expressions that you have created programmatically or from another code quotation.</span></span> <span data-ttu-id="c6693-137">Os `%` `%%` operadores e permitem que você adicione um objeto de expressão F # a uma cotação de código.</span><span class="sxs-lookup"><span data-stu-id="c6693-137">The `%` and `%%` operators enable you to add an F# expression object into a code quotation.</span></span> <span data-ttu-id="c6693-138">Você usa o `%` operador para inserir um objeto de expressão com tipo em uma cotação tipada; você usa o `%%` operador para inserir um objeto de expressão não tipado em uma cotação não tipada.</span><span class="sxs-lookup"><span data-stu-id="c6693-138">You use the `%` operator to insert a typed expression object into a typed quotation; you use the `%%` operator to insert an untyped expression object into an untyped quotation.</span></span> <span data-ttu-id="c6693-139">Ambos os operadores são operadores de prefixo unários.</span><span class="sxs-lookup"><span data-stu-id="c6693-139">Both operators are unary prefix operators.</span></span> <span data-ttu-id="c6693-140">Portanto `expr` , se for uma expressão não tipada do tipo `Expr` , o código a seguir será válido.</span><span class="sxs-lookup"><span data-stu-id="c6693-140">Thus if `expr` is an untyped expression of type `Expr`, the following code is valid.</span></span>

```fsharp
<@@ 1 + %%expr @@>
```

<span data-ttu-id="c6693-141">E se `expr` for uma citação tipada do tipo `Expr<int>` , o código a seguir será válido.</span><span class="sxs-lookup"><span data-stu-id="c6693-141">And if `expr` is a typed quotation of type `Expr<int>`, the following code is valid.</span></span>

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a><span data-ttu-id="c6693-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c6693-142">Example</span></span>

### <a name="description"></a><span data-ttu-id="c6693-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6693-143">Description</span></span>

<span data-ttu-id="c6693-144">O exemplo a seguir ilustra o uso de aspas de código para colocar o código F # em um objeto de expressão e, em seguida, imprimir o código F # que representa a expressão.</span><span class="sxs-lookup"><span data-stu-id="c6693-144">The following example illustrates the use of code quotations to put F# code into an expression object and then print the F# code that represents the expression.</span></span> <span data-ttu-id="c6693-145">Uma função `println` é definida que contém uma função recursiva `print` que exibe um objeto de expressão F # (do tipo `Expr` ) em um formato amigável.</span><span class="sxs-lookup"><span data-stu-id="c6693-145">A function `println` is defined that contains a recursive function `print` that displays an F# expression object (of type `Expr`) in a friendly format.</span></span> <span data-ttu-id="c6693-146">Há vários padrões ativos nos módulos [FSharp. Enquotas. Patterns](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-patternsmodule.html) e [FSharp. requotas. DerivedPatterns](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-derivedpatternsmodule.html) que podem ser usados para analisar objetos de expressão.</span><span class="sxs-lookup"><span data-stu-id="c6693-146">There are several active patterns in the [FSharp.Quotations.Patterns](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-patternsmodule.html) and [FSharp.Quotations.DerivedPatterns](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-derivedpatternsmodule.html) modules that can be used to analyze expression objects.</span></span> <span data-ttu-id="c6693-147">Este exemplo não inclui todos os padrões possíveis que podem aparecer em uma expressão F #.</span><span class="sxs-lookup"><span data-stu-id="c6693-147">This example does not include all the possible patterns that might appear in an F# expression.</span></span> <span data-ttu-id="c6693-148">Qualquer padrão não reconhecido dispara uma correspondência ao padrão curinga ( `_` ) e é renderizado usando o `ToString` método, que, no `Expr` tipo, permite que você saiba o padrão ativo a ser adicionado à expressão de correspondência.</span><span class="sxs-lookup"><span data-stu-id="c6693-148">Any unrecognized pattern triggers a match to the wildcard pattern (`_`) and is rendered by using the `ToString` method, which, on the `Expr` type, lets you know the active pattern to add to your match expression.</span></span>

### <a name="code"></a><span data-ttu-id="c6693-149">Código</span><span class="sxs-lookup"><span data-stu-id="c6693-149">Code</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet601.fs)]

### <a name="output"></a><span data-ttu-id="c6693-150">Saída</span><span class="sxs-lookup"><span data-stu-id="c6693-150">Output</span></span>

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a><span data-ttu-id="c6693-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c6693-151">Example</span></span>

### <a name="description"></a><span data-ttu-id="c6693-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6693-152">Description</span></span>

<span data-ttu-id="c6693-153">Você também pode usar os três padrões ativos no [módulo ExprShape](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-exprshapemodule.html) para atravessar árvores de expressão com menos padrões ativos.</span><span class="sxs-lookup"><span data-stu-id="c6693-153">You can also use the three active patterns in the [ExprShape module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-exprshapemodule.html) to traverse expression trees with fewer active patterns.</span></span> <span data-ttu-id="c6693-154">Esses padrões ativos podem ser úteis quando você deseja percorrer uma árvore, mas não precisa de todas as informações na maioria dos nós.</span><span class="sxs-lookup"><span data-stu-id="c6693-154">These active patterns can be useful when you want to traverse a tree but you do not need all the information in most of the nodes.</span></span> <span data-ttu-id="c6693-155">Quando você usa esses padrões, qualquer expressão F # corresponde a um dos três padrões a seguir: `ShapeVar` se a expressão for uma variável, `ShapeLambda` se a expressão for uma expressão lambda ou `ShapeCombination` se a expressão for outra coisa.</span><span class="sxs-lookup"><span data-stu-id="c6693-155">When you use these patterns, any F# expression matches one of the following three patterns: `ShapeVar` if the expression is a variable, `ShapeLambda` if the expression is a lambda expression, or `ShapeCombination` if the expression is anything else.</span></span> <span data-ttu-id="c6693-156">Se você percorrer uma árvore de expressão usando os padrões ativos como no exemplo de código anterior, precisará usar muitos outros padrões para lidar com todos os tipos de expressão F # possíveis e seu código será mais complexo.</span><span class="sxs-lookup"><span data-stu-id="c6693-156">If you traverse an expression tree by using the active patterns as in the previous code example, you have to use many more patterns to handle all possible F# expression types, and your code will be more complex.</span></span> <span data-ttu-id="c6693-157">Para obter mais informações, consulte [ExprShape. ShapeVar&#124;ShapeLambda&#124;ShapeCombination active Pattern](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-exprshapemodule.html#(%20|ShapeVar|ShapeLambda|ShapeCombination|%20)).</span><span class="sxs-lookup"><span data-stu-id="c6693-157">For more information, see [ExprShape.ShapeVar&#124;ShapeLambda&#124;ShapeCombination Active Pattern](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-exprshapemodule.html#(%20|ShapeVar|ShapeLambda|ShapeCombination|%20)).</span></span>

<span data-ttu-id="c6693-158">O exemplo de código a seguir pode ser usado como base para passagens mais complexas.</span><span class="sxs-lookup"><span data-stu-id="c6693-158">The following code example can be used as a basis for more complex traversals.</span></span> <span data-ttu-id="c6693-159">Nesse código, uma árvore de expressão é criada para uma expressão que envolve uma chamada de função, `add` .</span><span class="sxs-lookup"><span data-stu-id="c6693-159">In this code, an expression tree is created for an expression that involves a function call, `add`.</span></span> <span data-ttu-id="c6693-160">O padrão [SpecificCall](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-derivedpatternsmodule.html#(%20|SpecificCall|_|%20)) ativo é usado para detectar qualquer chamada para `add` na árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="c6693-160">The [SpecificCall](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-derivedpatternsmodule.html#(%20|SpecificCall|_|%20)) active pattern is used to detect any call to `add` in the expression tree.</span></span> <span data-ttu-id="c6693-161">Esse padrão ativo atribui os argumentos da chamada ao `exprList` valor.</span><span class="sxs-lookup"><span data-stu-id="c6693-161">This active pattern assigns the arguments of the call to the `exprList` value.</span></span> <span data-ttu-id="c6693-162">Nesse caso, há apenas dois, portanto, eles são retirados e a função é chamada recursivamente nos argumentos.</span><span class="sxs-lookup"><span data-stu-id="c6693-162">In this case, there are only two, so these are pulled out and the function is called recursively on the arguments.</span></span> <span data-ttu-id="c6693-163">Os resultados são inseridos em uma cotação de código que representa uma chamada para `mul` usando o operador de União ( `%%` ).</span><span class="sxs-lookup"><span data-stu-id="c6693-163">The results are inserted into a code quotation that represents a call to `mul` by using the splice operator (`%%`).</span></span> <span data-ttu-id="c6693-164">A `println` função do exemplo anterior é usada para exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="c6693-164">The `println` function from the previous example is used to display the results.</span></span>

<span data-ttu-id="c6693-165">O código em outras ramificações de padrão ativo apenas gera a mesma árvore de expressão, portanto, a única alteração na expressão resultante é a alteração de `add` para `mul` .</span><span class="sxs-lookup"><span data-stu-id="c6693-165">The code in the other active pattern branches just regenerates the same expression tree, so the only change in the resulting expression is the change from `add` to `mul`.</span></span>

### <a name="code"></a><span data-ttu-id="c6693-166">Código</span><span class="sxs-lookup"><span data-stu-id="c6693-166">Code</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet701.fs)]

### <a name="output"></a><span data-ttu-id="c6693-167">Saída</span><span class="sxs-lookup"><span data-stu-id="c6693-167">Output</span></span>

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a><span data-ttu-id="c6693-168">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6693-168">See also</span></span>

- [<span data-ttu-id="c6693-169">Referência de linguagem F #</span><span class="sxs-lookup"><span data-stu-id="c6693-169">F# Language Reference</span></span>](index.md)
