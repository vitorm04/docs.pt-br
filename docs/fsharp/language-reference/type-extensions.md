---
title: "Extensões de tipo (F#)"
description: "Saiba como extensões de tipo de F # permitem que você adiciona novos membros a um tipo de objeto definida anteriormente."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c9d7ce27-f5ad-4766-b9e9-34187da5bc24
ms.openlocfilehash: f78f8689e95fc1547f1a2b17c615592c00051f7c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="type-extensions"></a><span data-ttu-id="5fb78-104">Extensões de tipo</span><span class="sxs-lookup"><span data-stu-id="5fb78-104">Type Extensions</span></span>

<span data-ttu-id="5fb78-105">Extensões de tipo permitem que você adicionar novos membros a um tipo de objeto definida anteriormente.</span><span class="sxs-lookup"><span data-stu-id="5fb78-105">Type extensions let you add new members to a previously defined object type.</span></span>

## <a name="syntax"></a><span data-ttu-id="5fb78-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5fb78-106">Syntax</span></span>

```fsharp
// Intrinsic extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]

// Optional extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]
```

## <a name="remarks"></a><span data-ttu-id="5fb78-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="5fb78-107">Remarks</span></span>
<span data-ttu-id="5fb78-108">Há duas formas de extensões de tipo que tem o comportamento e sintaxe ligeiramente diferente.</span><span class="sxs-lookup"><span data-stu-id="5fb78-108">There are two forms of type extensions that have slightly different syntax and behavior.</span></span> <span data-ttu-id="5fb78-109">Um *extensões intrínsecas* é uma extensão que aparece no mesmo namespace ou módulo, no mesmo arquivo de origem e no mesmo assembly (DLL ou arquivo executável) como o tipo que está sendo estendido.</span><span class="sxs-lookup"><span data-stu-id="5fb78-109">An *intrinsic extension* is an extension that appears in the same namespace or module, in the same source file, and in the same assembly (DLL or executable file) as the type being extended.</span></span> <span data-ttu-id="5fb78-110">Um *extensão opcional* é uma extensão que aparece fora do módulo, namespace ou assembly do tipo que está sendo estendido original.</span><span class="sxs-lookup"><span data-stu-id="5fb78-110">An *optional extension* is an extension that appears outside the original module, namespace, or assembly of the type being extended.</span></span> <span data-ttu-id="5fb78-111">Extensões intrínsecas aparecem no tipo quando o tipo é examinado por reflexão, mas não extensões opcionais.</span><span class="sxs-lookup"><span data-stu-id="5fb78-111">Intrinsic extensions appear on the type when the type is examined by reflection, but optional extensions do not.</span></span> <span data-ttu-id="5fb78-112">Extensões opcionais devem estar em módulos e são somente no escopo quando o módulo que contém a extensão está aberto.</span><span class="sxs-lookup"><span data-stu-id="5fb78-112">Optional extensions must be in modules, and they are only in scope when the module that contains the extension is open.</span></span>

<span data-ttu-id="5fb78-113">Na sintaxe anterior, *typename* representa o tipo que está sendo estendido.</span><span class="sxs-lookup"><span data-stu-id="5fb78-113">In the previous syntax, *typename* represents the type that is being extended.</span></span> <span data-ttu-id="5fb78-114">Pode ser estendido a qualquer tipo que possa ser acessado, mas o nome do tipo deve ser um nome de tipo real, não é uma abreviação de tipo.</span><span class="sxs-lookup"><span data-stu-id="5fb78-114">Any type that can be accessed can be extended, but the type name must be an actual type name, not a type abbreviation.</span></span> <span data-ttu-id="5fb78-115">Você pode definir vários membros na extensão de um tipo.</span><span class="sxs-lookup"><span data-stu-id="5fb78-115">You can define multiple members in one type extension.</span></span> <span data-ttu-id="5fb78-116">O *identificador Self* representa a instância do objeto que está sendo invocado, assim como membros comuns.</span><span class="sxs-lookup"><span data-stu-id="5fb78-116">The *self-identifier* represents the instance of the object being invoked, just as in ordinary members.</span></span>

<span data-ttu-id="5fb78-117">O `end` palavra-chave é opcional em sintaxe leve.</span><span class="sxs-lookup"><span data-stu-id="5fb78-117">The `end` keyword is optional in lightweight syntax.</span></span>

<span data-ttu-id="5fb78-118">Membros definidos em extensões de tipo podem ser usados exatamente como outros membros em um tipo de classe.</span><span class="sxs-lookup"><span data-stu-id="5fb78-118">Members defined in type extensions can be used just like other members on a class type.</span></span> <span data-ttu-id="5fb78-119">Como outros membros, podem ser estáticos ou membros de instância.</span><span class="sxs-lookup"><span data-stu-id="5fb78-119">Like other members, they can be static or instance members.</span></span> <span data-ttu-id="5fb78-120">Esses métodos também são conhecidos como *métodos de extensão*; propriedades são conhecidas como *propriedades de extensão*, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="5fb78-120">These methods are also known as *extension methods*; properties are known as *extension properties*, and so on.</span></span> <span data-ttu-id="5fb78-121">Membros de extensão opcional são compilados para membros estáticos para o qual a instância do objeto é passada implicitamente como o primeiro parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5fb78-121">Optional extension members are compiled to static members for which the object instance is passed implicitly as the first parameter.</span></span> <span data-ttu-id="5fb78-122">No entanto, eles atuam como se fossem membros de instância ou membros estáticos de acordo com como elas são declaradas.</span><span class="sxs-lookup"><span data-stu-id="5fb78-122">However, they act as if they were instance members or static members according to how they are declared.</span></span> <span data-ttu-id="5fb78-123">Membros de extensão implícitas são incluídos como membros do tipo e podem ser usados sem restrição.</span><span class="sxs-lookup"><span data-stu-id="5fb78-123">Implicit extension members are included as members of the type and can be used without restriction.</span></span>

<span data-ttu-id="5fb78-124">Métodos de extensão não podem ser métodos virtuais ou abstratos.</span><span class="sxs-lookup"><span data-stu-id="5fb78-124">Extension methods cannot be virtual or abstract methods.</span></span> <span data-ttu-id="5fb78-125">Ele podem sobrecarregar outros métodos de mesmo nome, mas o compilador dá preferência a métodos de extensão não no caso de uma chamada ambígua.</span><span class="sxs-lookup"><span data-stu-id="5fb78-125">They can overload other methods of the same name, but the compiler gives preference to non-extension methods in the case of an ambiguous call.</span></span>

<span data-ttu-id="5fb78-126">Se várias extensões de tipo intrínseco existirem para um tipo, todos os membros devem ser exclusivos.</span><span class="sxs-lookup"><span data-stu-id="5fb78-126">If multiple intrinsic type extensions exist for one type, all members must be unique.</span></span> <span data-ttu-id="5fb78-127">Para as extensões de tipo opcionais, membros de extensões de tipo diferente para o mesmo tipo podem ter os mesmos nomes.</span><span class="sxs-lookup"><span data-stu-id="5fb78-127">For optional type extensions, members in different type extensions to the same type can have the same names.</span></span> <span data-ttu-id="5fb78-128">Erros de ambiguidade ocorrer somente se o código de cliente abre dois escopos diferentes que definem os mesmos nomes de membro.</span><span class="sxs-lookup"><span data-stu-id="5fb78-128">Ambiguity errors occur only if client code opens two different scopes that define the same member names.</span></span>

<span data-ttu-id="5fb78-129">No exemplo a seguir, um tipo em um módulo tem uma extensão de tipo intrínseco.</span><span class="sxs-lookup"><span data-stu-id="5fb78-129">In the following example, a type in a module has an intrinsic type extension.</span></span> <span data-ttu-id="5fb78-130">Para o código do cliente fora do módulo, a extensão do tipo aparece como um membro regular do tipo em todos os aspectos.</span><span class="sxs-lookup"><span data-stu-id="5fb78-130">To client code outside the module, the type extension appears as a regular member of the type in all respects.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3701.fs)]

<span data-ttu-id="5fb78-131">Você pode usar extensões de tipo intrínseco para separar a definição de um tipo em seções.</span><span class="sxs-lookup"><span data-stu-id="5fb78-131">You can use intrinsic type extensions to separate the definition of a type into sections.</span></span> <span data-ttu-id="5fb78-132">Isso pode ser útil no gerenciamento de definições de tipo grande, por exemplo, para manter o código gerado pelo compilador e o código criado separada ou agrupar código criado por pessoas diferentes ou associado a uma funcionalidade diferente.</span><span class="sxs-lookup"><span data-stu-id="5fb78-132">This can be useful in managing large type definitions, for example, to keep compiler-generated code and authored code separate or to group together code created by different people or associated with different functionality.</span></span>

<span data-ttu-id="5fb78-133">No exemplo a seguir, uma extensão de tipo opcionais estende o `System.Int32` tipo com um método de extensão `FromString` que chama o membro estático `Parse`.</span><span class="sxs-lookup"><span data-stu-id="5fb78-133">In the following example, an optional type extension extends the `System.Int32` type with an extension method `FromString` that calls the static member `Parse`.</span></span> <span data-ttu-id="5fb78-134">O `testFromString` método demonstra que o novo membro é chamado, assim como qualquer membro de instância.</span><span class="sxs-lookup"><span data-stu-id="5fb78-134">The `testFromString` method demonstrates that the new member is called just like any instance member.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3702.fs)]

<span data-ttu-id="5fb78-135">O novo membro de instância será exibida como qualquer outro método do `Int32` tipo do IntelliSense, mas somente quando o módulo que contém a extensão está aberto ou não no escopo.</span><span class="sxs-lookup"><span data-stu-id="5fb78-135">The new instance member will appear like any other method of the `Int32` type in IntelliSense, but only when the module that contains the extension is open or otherwise in scope.</span></span>

## <a name="generic-extension-methods"></a><span data-ttu-id="5fb78-136">Métodos de extensão genérico</span><span class="sxs-lookup"><span data-stu-id="5fb78-136">Generic Extension Methods</span></span>
<span data-ttu-id="5fb78-137">Antes de F # 3.1, o compilador F # não suporta o uso de c#-estilo de métodos de extensão com um tipo de função do F # como o parâmetro "this", tipo de matriz, tipo de tupla ou uma variável de tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="5fb78-137">Before F# 3.1, the F# compiler didn't support the use of C#-style extension methods with a generic type variable, array type, tuple type, or an F# function type as the "this" parameter.</span></span> <span data-ttu-id="5fb78-138">3.1 F # suporta o uso desses membros de extensão.</span><span class="sxs-lookup"><span data-stu-id="5fb78-138">F# 3.1 supports the use of these extension members.</span></span>

<span data-ttu-id="5fb78-139">Por exemplo, no código F # 3.1, você pode usar métodos de extensão com assinaturas que são semelhantes à seguinte sintaxe no c#:</span><span class="sxs-lookup"><span data-stu-id="5fb78-139">For example, in F# 3.1 code, you can use extension methods with signatures that resemble the following syntax in C#:</span></span>

```csharp
static member Method<T>(this T input, T other)
```

<span data-ttu-id="5fb78-140">Essa abordagem é particularmente útil quando o parâmetro de tipo genérico é restrito.</span><span class="sxs-lookup"><span data-stu-id="5fb78-140">This approach is particularly useful when the generic type parameter is constrained.</span></span> <span data-ttu-id="5fb78-141">Além disso, você pode declarar membros de extensão como esta no código F # e definir um conjunto de métodos de extensão adicional, semanticamente avançado.</span><span class="sxs-lookup"><span data-stu-id="5fb78-141">Further, you can now declare extension members like this in F# code and define an additional, semantically rich set of extension methods.</span></span> <span data-ttu-id="5fb78-142">Em F #, você geralmente definir membros de extensão como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="5fb78-142">In F#, you usually define extension members as the following example shows:</span></span>

```fsharp
open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq { for x in xs do for i in 1 .. n do yield x }
```

<span data-ttu-id="5fb78-143">No entanto, para um tipo genérico, a variável de tipo pode não ser restritos.</span><span class="sxs-lookup"><span data-stu-id="5fb78-143">However, for a generic type, the type variable may not be constrained.</span></span> <span data-ttu-id="5fb78-144">Agora você pode declarar um c#-membro de extensão de estilo em F # para contornar essa limitação.</span><span class="sxs-lookup"><span data-stu-id="5fb78-144">You can now declare a C#-style extension member in F# to work around this limitation.</span></span> <span data-ttu-id="5fb78-145">Quando você combinar esse tipo de declaração com o recurso de linha de F #, você pode apresentar algoritmos genéricos como membros de extensão.</span><span class="sxs-lookup"><span data-stu-id="5fb78-145">When you combine this kind of declaration with the inline feature of F#, you can present generic algorithms as extension members.</span></span>

<span data-ttu-id="5fb78-146">Considere a declaração a seguir:</span><span class="sxs-lookup"><span data-stu-id="5fb78-146">Consider the following declaration:</span></span>

```fsharp
[<Extension>]
type ExtraCSharpStyleExtensionMethodsInFSharp () =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

<span data-ttu-id="5fb78-147">Usando esta declaração, você pode escrever código que se parece com o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5fb78-147">By using this declaration, you can write code that resembles the following sample.</span></span>

```fsharp
let listOfIntegers = [ 1 .. 100 ]
let listOfBigIntegers = [ 1I to 100I ]
let sum1 = listOfIntegers.Sum()
let sum2 = listOfBigIntegers.Sum()
```

<span data-ttu-id="5fb78-148">Nesse código, o mesmo código de aritmético genérico é aplicado às listas de dois tipos sem sobrecarga, definindo um membro único de extensão.</span><span class="sxs-lookup"><span data-stu-id="5fb78-148">In this code, the same generic arithmetic code is applied to lists of two types without overloading, by defining a single extension member.</span></span>


## <a name="see-also"></a><span data-ttu-id="5fb78-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5fb78-149">See Also</span></span>
[<span data-ttu-id="5fb78-150">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="5fb78-150">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="5fb78-151">Membros</span><span class="sxs-lookup"><span data-stu-id="5fb78-151">Members</span></span>](members/index.md)
