---
title: Tuplas
description: Saiba mais sobre F# a tupla, um agrupamento de valores sem nome, mas ordenados, possivelmente de tipos diferentes.
ms.date: 05/16/2016
ms.openlocfilehash: 7a15d7e0c6c9b42118dd75066f02cbb2e05335fc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630231"
---
# <a name="tuples"></a><span data-ttu-id="7c7a8-103">Tuplas</span><span class="sxs-lookup"><span data-stu-id="7c7a8-103">Tuples</span></span>

<span data-ttu-id="7c7a8-104">Uma *tupla* é um agrupamento de valores não nomeados, mas ordenados, possivelmente de tipos diferentes.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-104">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="7c7a8-105">As tuplas podem ser tipos de referência ou estruturas.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-105">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="7c7a8-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c7a8-106">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a><span data-ttu-id="7c7a8-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="7c7a8-107">Remarks</span></span>

<span data-ttu-id="7c7a8-108">Cada *elemento* na sintaxe anterior pode ser qualquer expressão válida F# .</span><span class="sxs-lookup"><span data-stu-id="7c7a8-108">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="7c7a8-109">Exemplos</span><span class="sxs-lookup"><span data-stu-id="7c7a8-109">Examples</span></span>

<span data-ttu-id="7c7a8-110">Exemplos de tuplas incluem pares, corridas e assim por diante, dos mesmos ou de tipos diferentes.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-110">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="7c7a8-111">Alguns exemplos são ilustrados no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-111">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a><span data-ttu-id="7c7a8-112">Obtendo valores individuais</span><span class="sxs-lookup"><span data-stu-id="7c7a8-112">Obtaining Individual Values</span></span>

<span data-ttu-id="7c7a8-113">Você pode usar a correspondência de padrões para acessar e atribuir nomes para elementos de tupla, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-113">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="7c7a8-114">Você também pode desconstruir uma tupla por meio de correspondência de padrões `match` fora de `let` uma expressão por meio de associação:</span><span class="sxs-lookup"><span data-stu-id="7c7a8-114">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="7c7a8-115">Ou você pode padronizar a correspondência em tuplas como entradas para funções:</span><span class="sxs-lookup"><span data-stu-id="7c7a8-115">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="7c7a8-116">Se você precisar de apenas um elemento da tupla, o caractere curinga (o sublinhado) poderá ser usado para evitar a criação de um novo nome para um valor que não seja necessário.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-116">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="7c7a8-117">A cópia de elementos de uma tupla de referência em uma tupla de struct também é simples:</span><span class="sxs-lookup"><span data-stu-id="7c7a8-117">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="7c7a8-118">As funções `fst` e `snd` (somente tuplas de referência) retornam o primeiro e o segundo elementos de uma tupla, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-118">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="7c7a8-119">Não há nenhuma função interna que retorne o terceiro elemento de um triplo, mas você pode facilmente escrever um da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-119">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="7c7a8-120">Em geral, é melhor usar a correspondência de padrões para acessar elementos individuais de tupla.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-120">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="7c7a8-121">Usando tuplas</span><span class="sxs-lookup"><span data-stu-id="7c7a8-121">Using Tuples</span></span>

<span data-ttu-id="7c7a8-122">As tuplas fornecem uma maneira conveniente de retornar vários valores de uma função, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-122">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="7c7a8-123">Este exemplo executa divisão de inteiros e retorna o resultado arredondado da operação como um primeiro membro de um par de tupla e o restante como um segundo membro do par.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-123">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="7c7a8-124">As tuplas também podem ser usadas como argumentos de função quando você deseja evitar o currying implícito de argumentos de função que é implícito pela sintaxe de função usual.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-124">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="7c7a8-125">A sintaxe comum para definir a função `let sum a b = a + b` permite que você defina uma função que é o aplicativo parcial do primeiro argumento da função, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-125">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="7c7a8-126">Usar uma tupla como o parâmetro desabilita currying.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-126">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="7c7a8-127">Para obter mais informações, consulte "aplicativo parcial de argumentos" em [funções](./functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="7c7a8-127">For more information, see "Partial Application of Arguments" in [Functions](./functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="7c7a8-128">Nomes de tipos de tupla</span><span class="sxs-lookup"><span data-stu-id="7c7a8-128">Names of Tuple Types</span></span>

<span data-ttu-id="7c7a8-129">Quando você escreve o nome de um tipo que é uma tupla, você usa o `*` símbolo para separar elementos.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-129">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="7c7a8-130">Para uma tupla que consiste em um `int`, um `float` `(10, 10.0, "ten")`e um `string`, como, o tipo seria escrito da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-130">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="7c7a8-131">Interoperação com C# tuplas</span><span class="sxs-lookup"><span data-stu-id="7c7a8-131">Interoperation with C# Tuples</span></span>

<span data-ttu-id="7c7a8-132">C#7,0 introduziu tuplas para o idioma.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-132">C# 7.0 introduced tuples to the language.</span></span>  <span data-ttu-id="7c7a8-133">As tuplas C# no são structs e são equivalentes às tuplas struct F#no.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-133">Tuples in C# are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="7c7a8-134">Se você precisar interoperar com C#o, deverá usar tuplas struct.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-134">If you need to interoperate with C#, you must use struct tuples.</span></span>

<span data-ttu-id="7c7a8-135">Isso é fácil de fazer.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-135">This is easy to do.</span></span>  <span data-ttu-id="7c7a8-136">Por exemplo, imagine que você tenha que passar uma tupla para C# uma classe e, em seguida, consumir seu resultado, que também é uma tupla:</span><span class="sxs-lookup"><span data-stu-id="7c7a8-136">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

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

<span data-ttu-id="7c7a8-137">Em seu F# código, você pode passar uma tupla de struct como o parâmetro e consumir o resultado como uma tupla de struct.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-137">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="7c7a8-138">Convertendo entre tuplas de referência e tuplas de struct</span><span class="sxs-lookup"><span data-stu-id="7c7a8-138">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="7c7a8-139">Como tuplas de referência e tuplas de struct têm uma representação subjacente completamente diferente, elas não são implicitamente conversíveis.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-139">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="7c7a8-140">Ou seja, o código como o seguinte não será compilado:</span><span class="sxs-lookup"><span data-stu-id="7c7a8-140">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="7c7a8-141">Você deve fazer a correspondência de padrão em uma tupla e construir a outra com as partes constituintes.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-141">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="7c7a8-142">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="7c7a8-142">For example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="7c7a8-143">Formulário compilado de tuplas de referência</span><span class="sxs-lookup"><span data-stu-id="7c7a8-143">Compiled Form of Reference Tuples</span></span>

<span data-ttu-id="7c7a8-144">Esta seção explica a forma de tuplas quando elas são compiladas.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-144">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="7c7a8-145">As informações aqui não são necessárias para leitura, a menos que você esteja visando .NET Framework 3,5 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-145">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="7c7a8-146">As tuplas são compiladas em objetos de um dos vários tipos genéricos, `System.Tuple`todas nomeadas, que são sobrecarregadas na arity ou no número de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-146">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="7c7a8-147">Os tipos de tupla aparecem neste formulário quando você os exibe de outro idioma, como C# ou Visual Basic, ou quando você está usando uma ferramenta que não reconhece F# construções.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-147">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="7c7a8-148">Os `Tuple` tipos foram introduzidos no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-148">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="7c7a8-149">Se você estiver visando uma versão anterior do .NET Framework, o compilador usará versões do [System. tupla](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) da versão 2,0 da biblioteca F# principal.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-149">If you are targeting an earlier version of the .NET Framework, the compiler uses versions of [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="7c7a8-150">Os tipos nesta biblioteca são usados somente para aplicativos direcionados às versões 2,0, 3,0 e 3,5 do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-150">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of the .NET Framework.</span></span> <span data-ttu-id="7c7a8-151">O encaminhamento de tipo é usado para garantir a compatibilidade binária entre os componentes F# .NET Framework 2,0 e .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-151">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="7c7a8-152">Formulário compilado de tuplas de struct</span><span class="sxs-lookup"><span data-stu-id="7c7a8-152">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="7c7a8-153">As tuplas de struct (por `struct (x, y)`exemplo,) são fundamentalmente diferentes das tuplas de referência.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-153">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="7c7a8-154">Eles são compilados no <xref:System.ValueTuple> tipo, sobrecarregado por arity ou o número de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-154">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="7c7a8-155">Eles são equivalentes a [ C# 7,0 tuplas](../../csharp/tuples.md) e [Visual Basic 2017 tuplas](../../visual-basic/programming-guide/language-features/data-types/tuples.md)e interoperam bidirecionalmente.</span><span class="sxs-lookup"><span data-stu-id="7c7a8-155">They are equivalent to [C# 7.0 Tuples](../../csharp/tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c7a8-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c7a8-156">See also</span></span>

- [<span data-ttu-id="7c7a8-157">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="7c7a8-157">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="7c7a8-158">Tipos F#</span><span class="sxs-lookup"><span data-stu-id="7c7a8-158">F# Types</span></span>](fsharp-types.md)
