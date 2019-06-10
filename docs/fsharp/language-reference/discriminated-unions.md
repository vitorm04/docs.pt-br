---
title: Uniões discriminadas
description: Saiba como usar F# uniões discriminadas.
ms.date: 05/16/2016
ms.openlocfilehash: a3958a9ffb021c0c46c24216f17a1e7ee5605dd3
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816249"
---
# <a name="discriminated-unions"></a><span data-ttu-id="42acb-103">Uniões discriminadas</span><span class="sxs-lookup"><span data-stu-id="42acb-103">Discriminated Unions</span></span>

<span data-ttu-id="42acb-104">As uniões discriminadas fornecem suporte para valores que podem ser um dos vários casos nomeados, possivelmente cada um com tipos e valores diferentes.</span><span class="sxs-lookup"><span data-stu-id="42acb-104">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="42acb-105">As uniões discriminadas são úteis para dados heterogêneos; dados que podem ter casos especiais, incluindo válido e casos de erro. dados que variam em tipo de uma instância para outro; e como uma alternativa para hierarquias de objetos pequenos.</span><span class="sxs-lookup"><span data-stu-id="42acb-105">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="42acb-106">Além disso, discriminadas recursivas uniões são usadas para representar estruturas de dados de árvore.</span><span class="sxs-lookup"><span data-stu-id="42acb-106">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="42acb-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42acb-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="42acb-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="42acb-108">Remarks</span></span>

<span data-ttu-id="42acb-109">As uniões discriminadas são semelhantes aos tipos de união em outros idiomas, mas há diferenças.</span><span class="sxs-lookup"><span data-stu-id="42acb-109">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="42acb-110">Como com um tipo de união no C++ ou um tipo variante em Visual Basic, os dados armazenados no valor não é fixo; ele pode ser uma das várias opções diferentes.</span><span class="sxs-lookup"><span data-stu-id="42acb-110">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="42acb-111">Ao contrário de uniões em outras linguagens, no entanto, cada uma das opções possíveis recebe um *identificador de caso*.</span><span class="sxs-lookup"><span data-stu-id="42acb-111">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="42acb-112">Os identificadores de caso são nomes para os vários tipos possíveis de valores que podem ser objetos desse tipo; os valores são opcionais.</span><span class="sxs-lookup"><span data-stu-id="42acb-112">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="42acb-113">Se os valores não estiverem presentes, o caso é equivalente a um caso de enumeração.</span><span class="sxs-lookup"><span data-stu-id="42acb-113">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="42acb-114">Se valores estiverem presentes, cada valor pode ser um único valor de um tipo especificado ou um tuple que agregue vários campos dos tipos iguais ou diferentes.</span><span class="sxs-lookup"><span data-stu-id="42acb-114">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="42acb-115">Você pode dar a um campo individual um nome, mas o nome é opcional, mesmo se outros campos no mesmo caso forem nomeados.</span><span class="sxs-lookup"><span data-stu-id="42acb-115">You can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="42acb-116">Padrões de acessibilidade para uniões discriminadas para `public`.</span><span class="sxs-lookup"><span data-stu-id="42acb-116">Accessibility for discriminated unions defaults to `public`.</span></span>

<span data-ttu-id="42acb-117">Por exemplo, considere a seguinte declaração de um tipo de forma.</span><span class="sxs-lookup"><span data-stu-id="42acb-117">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="42acb-118">O código anterior declara uma união discriminada Shape, que pode ter valores de qualquer um dos três casos: Rectangle, Circle e Prism.</span><span class="sxs-lookup"><span data-stu-id="42acb-118">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="42acb-119">Cada caso tem um conjunto diferente de campos.</span><span class="sxs-lookup"><span data-stu-id="42acb-119">Each case has a different set of fields.</span></span> <span data-ttu-id="42acb-120">O caso Rectangle tem dois nomeados de campos, ambos do tipo `float`, que têm os nomes width e length.</span><span class="sxs-lookup"><span data-stu-id="42acb-120">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="42acb-121">O caso de círculo tem apenas um campo nomeado, raio.</span><span class="sxs-lookup"><span data-stu-id="42acb-121">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="42acb-122">O caso Prism têm três campos, duas das quais (largura e altura) são campos nomeadas.</span><span class="sxs-lookup"><span data-stu-id="42acb-122">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="42acb-123">Campos sem nome são chamados de campos anônimos.</span><span class="sxs-lookup"><span data-stu-id="42acb-123">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="42acb-124">Você constrói objetos fornecendo valores para os campos nomeados e anônimos de acordo com os exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="42acb-124">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="42acb-125">Este código mostra que você pode usar os campos nomeados na inicialização, ou você pode confiar na ordem dos campos na declaração e apenas por sua vez, fornecer os valores para cada campo.</span><span class="sxs-lookup"><span data-stu-id="42acb-125">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="42acb-126">A chamada de construtor para `rect` no código anterior usa os campos nomeados, mas a chamada de construtor para `circ` usa a ordenação.</span><span class="sxs-lookup"><span data-stu-id="42acb-126">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="42acb-127">Você pode combinar os campos ordenados e nomeados, como a construção de `prism`.</span><span class="sxs-lookup"><span data-stu-id="42acb-127">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="42acb-128">O `option` o tipo é uma união discriminada simples no F# biblioteca principal.</span><span class="sxs-lookup"><span data-stu-id="42acb-128">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="42acb-129">O `option` tipo é declarado da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="42acb-129">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="42acb-130">O código anterior Especifica que o tipo `Option` é uma união discriminada que tem dois casos, `Some` e `None`.</span><span class="sxs-lookup"><span data-stu-id="42acb-130">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="42acb-131">O `Some` caso tem um valor associado que consiste em um campo anônimo cujo tipo é representado pelo parâmetro de tipo `'a`.</span><span class="sxs-lookup"><span data-stu-id="42acb-131">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="42acb-132">O `None` caso não tem nenhum valor associado.</span><span class="sxs-lookup"><span data-stu-id="42acb-132">The `None` case has no associated value.</span></span> <span data-ttu-id="42acb-133">Portanto, o `option` tipo Especifica um tipo genérico que tem um valor de qualquer tipo ou nenhum valor.</span><span class="sxs-lookup"><span data-stu-id="42acb-133">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="42acb-134">O tipo `Option` também tem um alias de tipo em minúscula, `option`, que é mais comumente usadas.</span><span class="sxs-lookup"><span data-stu-id="42acb-134">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="42acb-135">Os identificadores de caso podem ser usados como construtores para o tipo de união discriminado.</span><span class="sxs-lookup"><span data-stu-id="42acb-135">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="42acb-136">Por exemplo, o código a seguir é usado para criar valores da `option` tipo.</span><span class="sxs-lookup"><span data-stu-id="42acb-136">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="42acb-137">Os identificadores de caso também são usados em expressões de correspondência.</span><span class="sxs-lookup"><span data-stu-id="42acb-137">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="42acb-138">Em um expressão de correspondência de padrão, os identificadores são fornecidos para os valores associados com os casos individuais.</span><span class="sxs-lookup"><span data-stu-id="42acb-138">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="42acb-139">Por exemplo, no código a seguir, `x` é o identificador dado o valor que está associado com o `Some` caso o `option` tipo.</span><span class="sxs-lookup"><span data-stu-id="42acb-139">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="42acb-140">Em expressões de correspondência, você pode usar campos nomeados para especificar correspondências de união discriminadas.</span><span class="sxs-lookup"><span data-stu-id="42acb-140">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="42acb-141">Para o tipo de forma que foi declarado anteriormente, você pode usar os campos nomeados como o código a seguir mostra para extrair os valores dos campos.</span><span class="sxs-lookup"><span data-stu-id="42acb-141">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

<span data-ttu-id="42acb-142">Normalmente, os identificadores de caso podem ser usados sem qualificá-los com o nome da união.</span><span class="sxs-lookup"><span data-stu-id="42acb-142">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="42acb-143">Se você quiser que o nome seja sempre qualificado com o nome da união, você pode aplicar a [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) de atributo para a definição de tipo de união.</span><span class="sxs-lookup"><span data-stu-id="42acb-143">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="42acb-144">Uniões discriminadas descompactação</span><span class="sxs-lookup"><span data-stu-id="42acb-144">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="42acb-145">No F# uniões discriminadas geralmente são usadas na modelagem de domínio para um único tipo de encapsulamento.</span><span class="sxs-lookup"><span data-stu-id="42acb-145">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="42acb-146">É fácil extrair o valor subjacente por meio de correspondência de padrões também.</span><span class="sxs-lookup"><span data-stu-id="42acb-146">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="42acb-147">Você não precisa usar uma expressão de correspondência para um único caso:</span><span class="sxs-lookup"><span data-stu-id="42acb-147">You don't need to use a match expression for a single case:</span></span>

```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

<span data-ttu-id="42acb-148">O exemplo a seguir demonstra este:</span><span class="sxs-lookup"><span data-stu-id="42acb-148">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

<span data-ttu-id="42acb-149">Correspondência de padrões também é permitida diretamente nos parâmetros de função, portanto, é possível desencapsular a um caso de único:</span><span class="sxs-lookup"><span data-stu-id="42acb-149">Pattern matching is also allowed directly in function parameters, so you can unwrap a single case there:</span></span>

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="42acb-150">Uniões discriminadas de struct</span><span class="sxs-lookup"><span data-stu-id="42acb-150">Struct Discriminated Unions</span></span>

<span data-ttu-id="42acb-151">Você também pode representar as uniões discriminadas como estruturas.</span><span class="sxs-lookup"><span data-stu-id="42acb-151">You can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="42acb-152">Isso é feito com o `[<Struct>]` atributo.</span><span class="sxs-lookup"><span data-stu-id="42acb-152">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

<span data-ttu-id="42acb-153">Como esses são tipos de valor e tipos de referência não, há extra uniões discriminadas de considerações em comparação com a referência:</span><span class="sxs-lookup"><span data-stu-id="42acb-153">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="42acb-154">Eles são copiados como tipos de valor e têm semântica de tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="42acb-154">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="42acb-155">Você não pode usar uma definição de tipo recursiva com um struct multicase Discriminated Union.</span><span class="sxs-lookup"><span data-stu-id="42acb-155">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="42acb-156">Você deve fornecer nomes exclusivos de casos para um struct multicase Discriminated Union.</span><span class="sxs-lookup"><span data-stu-id="42acb-156">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="42acb-157">Usando uniões discriminadas em vez de hierarquias de objeto</span><span class="sxs-lookup"><span data-stu-id="42acb-157">Using Discriminated Unions Instead of Object Hierarchies</span></span>

<span data-ttu-id="42acb-158">Você também pode usar uma união discriminada como uma alternativa mais simples para uma hierarquia de objetos pequenos.</span><span class="sxs-lookup"><span data-stu-id="42acb-158">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="42acb-159">Por exemplo, a seguinte união discriminada poderia ser usada em vez de um `Shape` classe base que tem tipos derivados para círculo, quadrado, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="42acb-159">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="42acb-160">Em vez disso, de um método virtual para calcular uma área ou o perímetro, como você usaria em uma implementação orientada a objeto, você pode usar a correspondência de padrões para ramificar para fórmulas apropriadas para calcular essas quantidades.</span><span class="sxs-lookup"><span data-stu-id="42acb-160">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="42acb-161">No exemplo a seguir, fórmulas diferentes são usadas para calcular a área, dependendo da forma.</span><span class="sxs-lookup"><span data-stu-id="42acb-161">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="42acb-162">A saída é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="42acb-162">The output is as follows:</span></span>

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="42acb-163">Usando uniões discriminadas para estruturas de dados de árvore</span><span class="sxs-lookup"><span data-stu-id="42acb-163">Using Discriminated Unions for Tree Data Structures</span></span>

<span data-ttu-id="42acb-164">As uniões discriminadas podem ser recursivas, que significa que a própria união pode ser incluída no tipo de um ou mais casos.</span><span class="sxs-lookup"><span data-stu-id="42acb-164">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="42acb-165">Recursiva uniões discriminadas podem ser usadas para criar estruturas de árvore, que são usados para modelar expressões nas linguagens de programação.</span><span class="sxs-lookup"><span data-stu-id="42acb-165">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="42acb-166">No código a seguir, uma recursivas discriminadas union é usado para criar uma estrutura de dados de árvore binária.</span><span class="sxs-lookup"><span data-stu-id="42acb-166">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="42acb-167">A união consiste em dois casos, `Node`, que é um nó com um valor inteiro e subárvores esquerdas e direita, e `Tip`, que finaliza a árvore.</span><span class="sxs-lookup"><span data-stu-id="42acb-167">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="42acb-168">No código anterior, `resultSumTree` tem o valor 10.</span><span class="sxs-lookup"><span data-stu-id="42acb-168">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="42acb-169">A ilustração a seguir mostra a estrutura de árvore para `myTree`.</span><span class="sxs-lookup"><span data-stu-id="42acb-169">The following illustration shows the tree structure for `myTree`.</span></span>

![Diagrama que mostra a estrutura de árvore para o myTree.](../media/discriminated-unions/tree-structure-mytree.png)

<span data-ttu-id="42acb-171">As uniões discriminadas funcionarão bem se os nós na árvore forem heterogêneos.</span><span class="sxs-lookup"><span data-stu-id="42acb-171">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="42acb-172">No código a seguir, o tipo `Expression` representa a árvore de sintaxe abstrata de uma expressão em uma linguagem de programação simples que dê suporte à adição e multiplicação de números e variáveis.</span><span class="sxs-lookup"><span data-stu-id="42acb-172">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="42acb-173">Alguns dos casos de união não são recursivos e representam números (`Number`) ou variáveis (`Variable`).</span><span class="sxs-lookup"><span data-stu-id="42acb-173">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="42acb-174">Outros casos são recursivos e representam operações (`Add` e `Multiply`), onde os operandos também são expressões.</span><span class="sxs-lookup"><span data-stu-id="42acb-174">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="42acb-175">O `Evaluate` função usa uma expressão de correspondência para processar recursivamente a árvore de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="42acb-175">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="42acb-176">Quando esse código é executado, o valor de `result` é 5.</span><span class="sxs-lookup"><span data-stu-id="42acb-176">When this code is executed, the value of `result` is 5.</span></span>

## <a name="members"></a><span data-ttu-id="42acb-177">Membros</span><span class="sxs-lookup"><span data-stu-id="42acb-177">Members</span></span>

<span data-ttu-id="42acb-178">É possível definir membros em uniões discriminadas.</span><span class="sxs-lookup"><span data-stu-id="42acb-178">It is possible to define members on discriminated unions.</span></span> <span data-ttu-id="42acb-179">O exemplo a seguir mostra como definir uma propriedade e implementar uma interface:</span><span class="sxs-lookup"><span data-stu-id="42acb-179">The following example shows how to define a property and implement an interface:</span></span>

```fsharp
open System

type IPrintable =
    abstract Print: unit -> unit

type Shape =
    | Circle of float
    | EquilateralTriangle of float
    | Square of float
    | Rectangle of float * float

    member this.Area =
        match this with
        | Circle r -> 2.0 * Math.PI * r
        | EquilateralTriangle s -> s * s * sqrt 3.0 / 4.0
        | Square s -> s * s
        | Rectangle(l, w) -> l * w

    interface IPrintable with
        member this.Print () =
            match this with
            | Circle r -> printfn "Circle with radius %f" r
            | EquilateralTriangle s -> printfn "Equilateral Triangle of side %f" s
            | Square s -> printfn "Square with side %f" s
            | Rectangle(l, w) -> printfn "Rectangle with length %f and width %f" l w
```

## <a name="common-attributes"></a><span data-ttu-id="42acb-180">Atributos comuns</span><span class="sxs-lookup"><span data-stu-id="42acb-180">Common attributes</span></span>

<span data-ttu-id="42acb-181">Os seguintes atributos são geralmente vistos em uniões discriminadas:</span><span class="sxs-lookup"><span data-stu-id="42acb-181">The following attributes are commonly seen in discriminated unions:</span></span>

* `[<RequireQualifiedAccess>]`
* `[<NoEquality>]`
* `[<NoComparison>]`
* `[<Struct>]`

## <a name="see-also"></a><span data-ttu-id="42acb-182">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42acb-182">See also</span></span>

- [<span data-ttu-id="42acb-183">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="42acb-183">F# Language Reference</span></span>](index.md)
