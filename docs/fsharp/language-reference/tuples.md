---
title: Tuplas (F#)
description: 'Saiba mais sobre F # tupla, um agrupamento de valores sem nome mas ordenados, possivelmente de tipos diferentes.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 9710f4996a952fdeaab07a30916215f27969e1a3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="tuples"></a><span data-ttu-id="371b2-103">Tuplas</span><span class="sxs-lookup"><span data-stu-id="371b2-103">Tuples</span></span>

<span data-ttu-id="371b2-104">Um *tupla* é um agrupamento de valores sem nome mas ordenados, possivelmente de tipos diferentes.</span><span class="sxs-lookup"><span data-stu-id="371b2-104">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="371b2-105">Tuplas podem ser tipos de referência ou estruturas.</span><span class="sxs-lookup"><span data-stu-id="371b2-105">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="371b2-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="371b2-106">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```
## <a name="remarks"></a><span data-ttu-id="371b2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="371b2-107">Remarks</span></span>
<span data-ttu-id="371b2-108">Cada *elemento* na sintaxe anterior pode ser qualquer expressão válida do F #.</span><span class="sxs-lookup"><span data-stu-id="371b2-108">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="371b2-109">Exemplos</span><span class="sxs-lookup"><span data-stu-id="371b2-109">Examples</span></span>
<span data-ttu-id="371b2-110">Exemplos de tuplas incluem pares, triplos e assim por diante, dos tipos iguais ou diferentes.</span><span class="sxs-lookup"><span data-stu-id="371b2-110">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="371b2-111">Alguns exemplos estão ilustrados no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="371b2-111">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]
    
## <a name="obtaining-individual-values"></a><span data-ttu-id="371b2-112">Obtendo valores individuais</span><span class="sxs-lookup"><span data-stu-id="371b2-112">Obtaining Individual Values</span></span>
<span data-ttu-id="371b2-113">Você pode usar a correspondência de padrões para acessar e atribuir nomes de elementos de tupla, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="371b2-113">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="371b2-114">Você também pode decompor uma tupla por meio de correspondência de padrões fora de um `match` expressão via `let` associação:</span><span class="sxs-lookup"><span data-stu-id="371b2-114">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="371b2-115">Ou você pode padrão corresponder tuplas como entradas para funções:</span><span class="sxs-lookup"><span data-stu-id="371b2-115">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="371b2-116">Se você precisar de apenas um elemento de tupla, o caractere curinga (sublinhado) pode ser usado para evitar a criação de um novo nome para um valor que não é necessário.</span><span class="sxs-lookup"><span data-stu-id="371b2-116">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="371b2-117">Copiando elementos de uma tupla de referência em uma tupla de struct é simple:</span><span class="sxs-lookup"><span data-stu-id="371b2-117">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="371b2-118">As funções `fst` e `snd` (referência apenas tuplas) retorna o primeiro e segundo elementos de uma tupla, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="371b2-118">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="371b2-119">Não há nenhuma função interna que retorna o terceiro elemento de um triplo, mas você pode facilmente escrever um da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="371b2-119">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="371b2-120">Geralmente, é melhor usar a correspondência de padrão para acessar elementos de coleção de itens individuais.</span><span class="sxs-lookup"><span data-stu-id="371b2-120">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="371b2-121">Usando tuplas</span><span class="sxs-lookup"><span data-stu-id="371b2-121">Using Tuples</span></span>
<span data-ttu-id="371b2-122">Tuplas fornecem uma maneira conveniente para retornar vários valores de uma função, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="371b2-122">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="371b2-123">Este exemplo executa a divisão de inteiro e retorna o resultado arredondado da operação como membro de um par de tupla primeiro e o restante como um segundo membro do par.</span><span class="sxs-lookup"><span data-stu-id="371b2-123">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="371b2-124">Tuplas também podem ser usadas como argumentos de função quando desejar evitar currying implícitos dos argumentos da função implícita a sintaxe de função normal.</span><span class="sxs-lookup"><span data-stu-id="371b2-124">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="371b2-125">A sintaxe normal para definir a função `let sum a b = a + b` permite que você defina uma função que é o aplicativo parcial do primeiro argumento da função, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="371b2-125">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="371b2-126">Usando uma coleção de itens como o parâmetro desabilita currying.</span><span class="sxs-lookup"><span data-stu-id="371b2-126">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="371b2-127">Para obter mais informações, consulte o "Aplicativo parcial de argumentos" [funções](functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="371b2-127">For more information, see "Partial Application of Arguments" in [Functions](functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="371b2-128">Nomes de tipos de coleção de itens</span><span class="sxs-lookup"><span data-stu-id="371b2-128">Names of Tuple Types</span></span>
<span data-ttu-id="371b2-129">Quando você escreve o nome de um tipo que é uma coleção de itens, você usar o `*` símbolo para separar elementos.</span><span class="sxs-lookup"><span data-stu-id="371b2-129">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="371b2-130">Para uma tupla que consiste em uma `int`, um `float`e um `string`, como `(10, 10.0, "ten")`, o tipo deve ser escrito da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="371b2-130">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="371b2-131">Interoperação com c# tuplas</span><span class="sxs-lookup"><span data-stu-id="371b2-131">Interoperation with C# Tuples</span></span>

<span data-ttu-id="371b2-132">C# 7.0 introduzidos tuplas para o idioma.</span><span class="sxs-lookup"><span data-stu-id="371b2-132">C# 7.0 introduced tuples to the language.</span></span>  <span data-ttu-id="371b2-133">Tuplas em c# são estruturas e são equivalentes a struct tuplas em F #.</span><span class="sxs-lookup"><span data-stu-id="371b2-133">Tuples in C# are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="371b2-134">Se você precisa interoperar com c#, você deve usar struct tuplas.</span><span class="sxs-lookup"><span data-stu-id="371b2-134">If you need to interoperate with C#, you must use struct tuples.</span></span>

<span data-ttu-id="371b2-135">Isso é fácil.</span><span class="sxs-lookup"><span data-stu-id="371b2-135">This is easy to do.</span></span>  <span data-ttu-id="371b2-136">Por exemplo, imagine que você precisa passar uma tupla a uma classe do c# e, em seguida, consumam seu resultado, o que também é uma coleção de itens:</span><span class="sxs-lookup"><span data-stu-id="371b2-136">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

```csharp
namespace CSharpTupleInterop
{
    public static class Example
    {
        public static (int, int) AddOneToXAndY((int x, int y) a) =>
            (a.x + 1, a.y + 1);
    }
}
```

<span data-ttu-id="371b2-137">No código F #, você pode passar uma tupla de estrutura como o parâmetro e consumir o resultado como uma tupla de struct.</span><span class="sxs-lookup"><span data-stu-id="371b2-137">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="371b2-138">Convertendo entre tuplas de referência e Struct tuplas</span><span class="sxs-lookup"><span data-stu-id="371b2-138">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="371b2-139">Como referência tuplas e Struct Tuples têm uma representação subjacente completamente diferente, eles não são implicitamente conversíveis.</span><span class="sxs-lookup"><span data-stu-id="371b2-139">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="371b2-140">Ou seja, não será compilado código como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="371b2-140">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="371b2-141">Você deve padrão correspondem em uma tupla e construir o outro com as partes constituintes.</span><span class="sxs-lookup"><span data-stu-id="371b2-141">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="371b2-142">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="371b2-142">For example:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="371b2-143">Forma compilada de tuplas de referência</span><span class="sxs-lookup"><span data-stu-id="371b2-143">Compiled Form of Reference Tuples</span></span>
<span data-ttu-id="371b2-144">Esta seção explica a forma de tuplas quando eles são compilados.</span><span class="sxs-lookup"><span data-stu-id="371b2-144">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="371b2-145">As informações aqui não são necessárias para ler a menos que o destino do .NET Framework 3.5 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="371b2-145">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="371b2-146">Tuplas são compiladas em objetos de um dos vários tipos genéricos, todos os `System.Tuple`, que estão sobrecarregados no arity, ou o número de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="371b2-146">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="371b2-147">Tipos de coleção de itens aparecem neste formulário quando você exibi-las de outra linguagem, como c# ou Visual Basic, ou quando você estiver usando uma ferramenta que não está ciente das construções de linguagem F #.</span><span class="sxs-lookup"><span data-stu-id="371b2-147">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="371b2-148">O `Tuple` tipos foram introduzidos no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="371b2-148">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="371b2-149">Se tiver como alvo uma versão anterior do .NET Framework, o compilador usa versões do [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) da versão 2.0 da biblioteca principal F #.</span><span class="sxs-lookup"><span data-stu-id="371b2-149">If you are targeting an earlier version of the .NET Framework, the compiler uses versions of [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="371b2-150">Os tipos na biblioteca são usados apenas para aplicativos voltados para o 2.0, 3.0 e 3.5 versões do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="371b2-150">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of the .NET Framework.</span></span> <span data-ttu-id="371b2-151">Encaminhamento de tipo é usado para garantir a compatibilidade binária entre os componentes do .NET Framework 2.0 e o .NET Framework 4 F #.</span><span class="sxs-lookup"><span data-stu-id="371b2-151">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="371b2-152">Forma compilada do Struct tuplas</span><span class="sxs-lookup"><span data-stu-id="371b2-152">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="371b2-153">Struct tuplas (por exemplo, `struct (x, y)`), são fundamentalmente diferente da referência tuplas.</span><span class="sxs-lookup"><span data-stu-id="371b2-153">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="371b2-154">Eles são compilados no <xref:System.ValueTuple> tipo, sobrecarregado por arity ou o número de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="371b2-154">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="371b2-155">Elas são equivalentes a [c# 7.0 tuplas](../../csharp/tuples.md) e [Visual Basic 2017 tuplas](../../visual-basic/programming-guide/language-features/data-types/tuples.md)e interoperem bidirecionalmente.</span><span class="sxs-lookup"><span data-stu-id="371b2-155">They are equivalent to [C# 7.0 Tuples](../../csharp/tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="371b2-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="371b2-156">See Also</span></span>
[<span data-ttu-id="371b2-157">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="371b2-157">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="371b2-158">Tipos F#</span><span class="sxs-lookup"><span data-stu-id="371b2-158">F# Types</span></span>](fsharp-types.md)
