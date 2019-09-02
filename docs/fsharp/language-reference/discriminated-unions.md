---
title: Uniões discriminadas
description: Saiba como usar F# uniões discriminadas.
ms.date: 05/16/2016
ms.openlocfilehash: 3ed05fdb144d7266adc1718cdf015ab64680f3d8
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206163"
---
# <a name="discriminated-unions"></a><span data-ttu-id="ba52b-103">Uniões discriminadas</span><span class="sxs-lookup"><span data-stu-id="ba52b-103">Discriminated Unions</span></span>

<span data-ttu-id="ba52b-104">Uniões discriminadas fornecem suporte para valores que podem ser um de vários casos nomeados, possivelmente cada um com valores e tipos diferentes.</span><span class="sxs-lookup"><span data-stu-id="ba52b-104">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="ba52b-105">Uniões discriminadas são úteis para dados heterogêneos; dados que podem ter casos especiais, incluindo casos de erro e válidos; dados que variam em tipo de uma instância para outra; e como uma alternativa para hierarquias de objetos pequenos.</span><span class="sxs-lookup"><span data-stu-id="ba52b-105">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="ba52b-106">Além disso, as uniões discriminadas recursivas são usadas para representar estruturas de dados de árvore.</span><span class="sxs-lookup"><span data-stu-id="ba52b-106">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="ba52b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ba52b-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="ba52b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="ba52b-108">Remarks</span></span>

<span data-ttu-id="ba52b-109">Uniões discriminadas são semelhantes aos tipos Union em outras linguagens, mas há diferenças.</span><span class="sxs-lookup"><span data-stu-id="ba52b-109">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="ba52b-110">Como com um tipo de União C++ em ou um tipo variant no Visual Basic, os dados armazenados no valor não são fixos; pode ser uma das várias opções distintas.</span><span class="sxs-lookup"><span data-stu-id="ba52b-110">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="ba52b-111">No entanto, ao contrário das uniões nessas outras linguagens, cada uma das opções possíveis recebe um *identificador de caso*.</span><span class="sxs-lookup"><span data-stu-id="ba52b-111">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="ba52b-112">Os identificadores de caso são nomes para os vários tipos possíveis de valores que os objetos desse tipo podem ser; os valores são opcionais.</span><span class="sxs-lookup"><span data-stu-id="ba52b-112">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="ba52b-113">Se os valores não estiverem presentes, o caso será equivalente a um caso de enumeração.</span><span class="sxs-lookup"><span data-stu-id="ba52b-113">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="ba52b-114">Se os valores estiverem presentes, cada valor poderá ser um único valor de um tipo especificado ou uma tupla que agrega vários campos dos mesmos ou de tipos diferentes.</span><span class="sxs-lookup"><span data-stu-id="ba52b-114">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="ba52b-115">Você pode dar um nome a um campo individual, mas o nome é opcional, mesmo que outros campos no mesmo caso sejam nomeados.</span><span class="sxs-lookup"><span data-stu-id="ba52b-115">You can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="ba52b-116">A acessibilidade para uniões discriminadas usa como `public`padrão.</span><span class="sxs-lookup"><span data-stu-id="ba52b-116">Accessibility for discriminated unions defaults to `public`.</span></span>

<span data-ttu-id="ba52b-117">Por exemplo, considere a declaração a seguir de um tipo de forma.</span><span class="sxs-lookup"><span data-stu-id="ba52b-117">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="ba52b-118">O código anterior declara uma forma de união discriminada, que pode ter valores de qualquer um dos três casos: Retângulo, círculo e prisma.</span><span class="sxs-lookup"><span data-stu-id="ba52b-118">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="ba52b-119">Cada caso tem um conjunto diferente de campos.</span><span class="sxs-lookup"><span data-stu-id="ba52b-119">Each case has a different set of fields.</span></span> <span data-ttu-id="ba52b-120">O caso de retângulo tem dois campos nomeados, ambos `float`os tipos, que têm a largura e o comprimento dos nomes.</span><span class="sxs-lookup"><span data-stu-id="ba52b-120">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="ba52b-121">O caso de círculo tem apenas um campo nomeado, raio.</span><span class="sxs-lookup"><span data-stu-id="ba52b-121">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="ba52b-122">O caso do prisma tem três campos, dois dos quais (largura e altura) são campos nomeados.</span><span class="sxs-lookup"><span data-stu-id="ba52b-122">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="ba52b-123">Os campos sem nome são referidos como campos anônimos.</span><span class="sxs-lookup"><span data-stu-id="ba52b-123">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="ba52b-124">Você constrói objetos fornecendo valores para os campos nomeados e anônimos de acordo com os exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="ba52b-124">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="ba52b-125">Esse código mostra que você pode usar os campos nomeados na inicialização ou pode contar com a ordenação dos campos na declaração e apenas fornecer os valores para cada campo por vez.</span><span class="sxs-lookup"><span data-stu-id="ba52b-125">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="ba52b-126">A chamada de construtor `rect` para no código anterior usa os campos nomeados, mas a chamada de `circ` Construtor para usa a ordenação.</span><span class="sxs-lookup"><span data-stu-id="ba52b-126">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="ba52b-127">Você pode misturar os campos ordenados e os campos nomeados, como na `prism`construção de.</span><span class="sxs-lookup"><span data-stu-id="ba52b-127">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="ba52b-128">O `option` tipo é uma união discriminada simples na biblioteca F# principal.</span><span class="sxs-lookup"><span data-stu-id="ba52b-128">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="ba52b-129">O `option` tipo é declarado da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="ba52b-129">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="ba52b-130">O código anterior especifica que o tipo `Option` é uma união discriminada que tem dois `Some` casos e `None`.</span><span class="sxs-lookup"><span data-stu-id="ba52b-130">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="ba52b-131">O `Some` caso tem um valor associado que consiste em um campo anônimo cujo tipo é representado pelo parâmetro `'a`de tipo.</span><span class="sxs-lookup"><span data-stu-id="ba52b-131">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="ba52b-132">O `None` caso não tem nenhum valor associado.</span><span class="sxs-lookup"><span data-stu-id="ba52b-132">The `None` case has no associated value.</span></span> <span data-ttu-id="ba52b-133">Portanto, `option` o tipo especifica um tipo genérico que tem um valor de algum tipo ou nenhum valor.</span><span class="sxs-lookup"><span data-stu-id="ba52b-133">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="ba52b-134">O tipo `Option` também tem um alias de tipo minúsculo, `option`, que é mais comumente usado.</span><span class="sxs-lookup"><span data-stu-id="ba52b-134">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="ba52b-135">Os identificadores de caso podem ser usados como construtores para o tipo de união discriminada.</span><span class="sxs-lookup"><span data-stu-id="ba52b-135">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="ba52b-136">Por exemplo, o código a seguir é usado para criar valores do `option` tipo.</span><span class="sxs-lookup"><span data-stu-id="ba52b-136">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="ba52b-137">Os identificadores de caso também são usados em expressões de correspondência de padrões.</span><span class="sxs-lookup"><span data-stu-id="ba52b-137">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="ba52b-138">Em uma expressão de correspondência de padrões, os identificadores são fornecidos para os valores associados aos casos individuais.</span><span class="sxs-lookup"><span data-stu-id="ba52b-138">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="ba52b-139">Por exemplo, no código a seguir, `x` é o identificador dado ao valor associado `Some` ao caso do `option` tipo.</span><span class="sxs-lookup"><span data-stu-id="ba52b-139">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="ba52b-140">Em expressões de correspondência de padrões, você pode usar campos nomeados para especificar correspondências de União discriminadas.</span><span class="sxs-lookup"><span data-stu-id="ba52b-140">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="ba52b-141">Para o tipo de forma que foi declarado anteriormente, você pode usar os campos nomeados como mostra o código a seguir para extrair os valores dos campos.</span><span class="sxs-lookup"><span data-stu-id="ba52b-141">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

<span data-ttu-id="ba52b-142">Normalmente, os identificadores de caso podem ser usados sem qualificá-los com o nome da União.</span><span class="sxs-lookup"><span data-stu-id="ba52b-142">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="ba52b-143">Se desejar que o nome sempre seja qualificado com o nome da União, você poderá aplicar o atributo [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) à definição do tipo Union.</span><span class="sxs-lookup"><span data-stu-id="ba52b-143">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="ba52b-144">Desencapsular uniões discriminadas</span><span class="sxs-lookup"><span data-stu-id="ba52b-144">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="ba52b-145">Em F# uniões discriminadas geralmente são usadas em modelagem de domínio para encapsular um único tipo.</span><span class="sxs-lookup"><span data-stu-id="ba52b-145">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="ba52b-146">Também é fácil extrair o valor subjacente por meio de correspondência de padrões.</span><span class="sxs-lookup"><span data-stu-id="ba52b-146">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="ba52b-147">Você não precisa usar uma expressão de correspondência para um único caso:</span><span class="sxs-lookup"><span data-stu-id="ba52b-147">You don't need to use a match expression for a single case:</span></span>

```fsharp
let ([UnionCaseIdentifier] [values]) = [UnionValue]
```

<span data-ttu-id="ba52b-148">O exemplo a seguir demonstra este:</span><span class="sxs-lookup"><span data-stu-id="ba52b-148">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

<span data-ttu-id="ba52b-149">A correspondência de padrões também é permitida diretamente em parâmetros de função, para que você possa desencapsular um único caso:</span><span class="sxs-lookup"><span data-stu-id="ba52b-149">Pattern matching is also allowed directly in function parameters, so you can unwrap a single case there:</span></span>

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="ba52b-150">Uniões discriminadas de struct</span><span class="sxs-lookup"><span data-stu-id="ba52b-150">Struct Discriminated Unions</span></span>

<span data-ttu-id="ba52b-151">Você também pode representar uniões discriminadas como estruturas.</span><span class="sxs-lookup"><span data-stu-id="ba52b-151">You can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="ba52b-152">Isso é feito com o `[<Struct>]` atributo.</span><span class="sxs-lookup"><span data-stu-id="ba52b-152">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

<span data-ttu-id="ba52b-153">Como esses são tipos de valor e não tipos de referência, há considerações extras em comparação com as uniões discriminadas de referência:</span><span class="sxs-lookup"><span data-stu-id="ba52b-153">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="ba52b-154">Eles são copiados como tipos de valor e têm semântica de tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="ba52b-154">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="ba52b-155">Você não pode usar uma definição de tipo recursiva com uma união discriminada de struct com multicaixa.</span><span class="sxs-lookup"><span data-stu-id="ba52b-155">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="ba52b-156">Você deve fornecer nomes de caso exclusivos para uma união discriminada de struct com multicaixa.</span><span class="sxs-lookup"><span data-stu-id="ba52b-156">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="ba52b-157">Usando uniões discriminadas em vez de hierarquias de objeto</span><span class="sxs-lookup"><span data-stu-id="ba52b-157">Using Discriminated Unions Instead of Object Hierarchies</span></span>

<span data-ttu-id="ba52b-158">Geralmente, você pode usar uma união discriminada como uma alternativa mais simples a uma pequena hierarquia de objetos.</span><span class="sxs-lookup"><span data-stu-id="ba52b-158">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="ba52b-159">Por exemplo, a seguinte união discriminada pode ser usada em vez de `Shape` uma classe base que tenha tipos derivados para Circle, Square e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="ba52b-159">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="ba52b-160">Em vez de um método virtual para computar uma área ou um perímetro, como você usaria em uma implementação orientada a objeto, você pode usar a correspondência de padrões para ramificar para fórmulas apropriadas para computar essas quantidades.</span><span class="sxs-lookup"><span data-stu-id="ba52b-160">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="ba52b-161">No exemplo a seguir, fórmulas diferentes são usadas para calcular a área, dependendo da forma.</span><span class="sxs-lookup"><span data-stu-id="ba52b-161">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="ba52b-162">A saída é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="ba52b-162">The output is as follows:</span></span>

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="ba52b-163">Usando uniões discriminadas para estruturas de dados de árvore</span><span class="sxs-lookup"><span data-stu-id="ba52b-163">Using Discriminated Unions for Tree Data Structures</span></span>

<span data-ttu-id="ba52b-164">Uniões discriminadas podem ser recursivas, o que significa que a União em si pode ser incluída no tipo de um ou mais casos.</span><span class="sxs-lookup"><span data-stu-id="ba52b-164">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="ba52b-165">As uniões discriminadas recursivas podem ser usadas para criar estruturas de árvore, que são usadas para modelar expressões em linguagens de programação.</span><span class="sxs-lookup"><span data-stu-id="ba52b-165">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="ba52b-166">No código a seguir, uma união discriminada recursiva é usada para criar uma estrutura de dados de árvore binária.</span><span class="sxs-lookup"><span data-stu-id="ba52b-166">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="ba52b-167">A União consiste em dois casos, `Node`, que é um nó com um valor inteiro e subárvores esquerda e direita, e `Tip`que encerra a árvore.</span><span class="sxs-lookup"><span data-stu-id="ba52b-167">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="ba52b-168">No código anterior, `resultSumTree` tem o valor 10.</span><span class="sxs-lookup"><span data-stu-id="ba52b-168">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="ba52b-169">A ilustração a seguir mostra a estrutura de `myTree`árvore do.</span><span class="sxs-lookup"><span data-stu-id="ba52b-169">The following illustration shows the tree structure for `myTree`.</span></span>

![Diagrama que mostra a estrutura de árvore para myTree.](../media/discriminated-unions/tree-structure-mytree.png)

<span data-ttu-id="ba52b-171">Uniões discriminadas funcionam bem se os nós na árvore forem heterogêneos.</span><span class="sxs-lookup"><span data-stu-id="ba52b-171">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="ba52b-172">No código a seguir, o tipo `Expression` representa a árvore de sintaxe abstrata de uma expressão em uma linguagem de programação simples que dá suporte à adição e à multiplicação de números e variáveis.</span><span class="sxs-lookup"><span data-stu-id="ba52b-172">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="ba52b-173">Alguns dos casos de União não são recursivos e representam números (`Number`) ou variáveis (`Variable`).</span><span class="sxs-lookup"><span data-stu-id="ba52b-173">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="ba52b-174">Outros casos são recursivos e representam operações (`Add` e `Multiply`), em que os operandos também são expressões.</span><span class="sxs-lookup"><span data-stu-id="ba52b-174">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="ba52b-175">A `Evaluate` função usa uma expressão de correspondência para processar recursivamente a árvore de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="ba52b-175">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="ba52b-176">Quando esse código é executado, o valor de `result` é 5.</span><span class="sxs-lookup"><span data-stu-id="ba52b-176">When this code is executed, the value of `result` is 5.</span></span>

## <a name="members"></a><span data-ttu-id="ba52b-177">Membros</span><span class="sxs-lookup"><span data-stu-id="ba52b-177">Members</span></span>

<span data-ttu-id="ba52b-178">É possível definir membros em uniões discriminadas.</span><span class="sxs-lookup"><span data-stu-id="ba52b-178">It is possible to define members on discriminated unions.</span></span> <span data-ttu-id="ba52b-179">O exemplo a seguir mostra como definir uma propriedade e implementar uma interface:</span><span class="sxs-lookup"><span data-stu-id="ba52b-179">The following example shows how to define a property and implement an interface:</span></span>

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

## <a name="common-attributes"></a><span data-ttu-id="ba52b-180">Atributos comuns</span><span class="sxs-lookup"><span data-stu-id="ba52b-180">Common attributes</span></span>

<span data-ttu-id="ba52b-181">Os seguintes atributos são normalmente vistos em uniões discriminadas:</span><span class="sxs-lookup"><span data-stu-id="ba52b-181">The following attributes are commonly seen in discriminated unions:</span></span>

- `[<RequireQualifiedAccess>]`
- `[<NoEquality>]`
- `[<NoComparison>]`
- `[<Struct>]`

## <a name="see-also"></a><span data-ttu-id="ba52b-182">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba52b-182">See also</span></span>

- [<span data-ttu-id="ba52b-183">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="ba52b-183">F# Language Reference</span></span>](index.md)
