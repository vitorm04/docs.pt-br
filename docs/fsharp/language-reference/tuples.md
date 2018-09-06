---
title: Tuplas (F#)
description: 'Saiba mais sobre a tupla F #, um agrupamento de valores sem nomeados, mas ordenadas, possivelmente de diferentes tipos.'
ms.date: 05/16/2016
ms.openlocfilehash: e7628e4c4b538c2fe52fca25d2597b10fec28d1c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43749217"
---
# <a name="tuples"></a><span data-ttu-id="33773-103">Tuplas</span><span class="sxs-lookup"><span data-stu-id="33773-103">Tuples</span></span>

<span data-ttu-id="33773-104">Um *tupla* é um agrupamento de valores sem nomeados, mas ordenadas, possivelmente de diferentes tipos.</span><span class="sxs-lookup"><span data-stu-id="33773-104">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="33773-105">As tuplas podem ser tipos de referência ou structs.</span><span class="sxs-lookup"><span data-stu-id="33773-105">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="33773-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="33773-106">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a><span data-ttu-id="33773-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="33773-107">Remarks</span></span>

<span data-ttu-id="33773-108">Cada *elemento* na sintaxe anterior pode ser qualquer expressão válida do F #.</span><span class="sxs-lookup"><span data-stu-id="33773-108">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="33773-109">Exemplos</span><span class="sxs-lookup"><span data-stu-id="33773-109">Examples</span></span>

<span data-ttu-id="33773-110">Pares de triplos e assim por diante, dos tipos iguais ou diferentes são exemplos de tuplas.</span><span class="sxs-lookup"><span data-stu-id="33773-110">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="33773-111">Alguns exemplos são ilustrados no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="33773-111">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a><span data-ttu-id="33773-112">Obtendo valores individuais</span><span class="sxs-lookup"><span data-stu-id="33773-112">Obtaining Individual Values</span></span>

<span data-ttu-id="33773-113">Você pode usar a correspondência de padrões para acessar e atribuir nomes de elementos de tupla, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="33773-113">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="33773-114">Você também pode desconstruir uma tupla por meio de correspondência de fora de um `match` expressão por meio de `let` associação:</span><span class="sxs-lookup"><span data-stu-id="33773-114">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="33773-115">Você pode padrão or corresponder na tuplas como entradas para funções:</span><span class="sxs-lookup"><span data-stu-id="33773-115">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="33773-116">Se você precisar apenas um elemento da tupla, o caractere curinga (sublinhado) pode ser usado para evitar a criação de um novo nome para um valor que não é necessário.</span><span class="sxs-lookup"><span data-stu-id="33773-116">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="33773-117">Copiando elementos de uma tupla de referência em uma tupla de struct também é simple:</span><span class="sxs-lookup"><span data-stu-id="33773-117">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="33773-118">As funções `fst` e `snd` (referenciar apenas tuplas) retornar o primeiro e segundo os elementos de uma tupla, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="33773-118">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="33773-119">Não há nenhuma função interna que retorna o terceiro elemento de um triplo, mas você pode facilmente escrever um da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="33773-119">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="33773-120">Em geral, é melhor usar a correspondência de padrões para acessar os elementos de tupla individuais.</span><span class="sxs-lookup"><span data-stu-id="33773-120">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="33773-121">Uso de tuplas</span><span class="sxs-lookup"><span data-stu-id="33773-121">Using Tuples</span></span>

<span data-ttu-id="33773-122">As tuplas fornecem uma maneira conveniente para retornar vários valores de uma função, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="33773-122">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="33773-123">Este exemplo executa a divisão de inteiro e retorna o resultado arredondado da operação como membro de um par de tupla primeiro e o restante como um segundo membro do par.</span><span class="sxs-lookup"><span data-stu-id="33773-123">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="33773-124">As tuplas também podem ser usadas como argumentos de função quando você quer evitar currying implícita dos argumentos de função implícita a sintaxe da função normal.</span><span class="sxs-lookup"><span data-stu-id="33773-124">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="33773-125">A sintaxe normal para definir a função `let sum a b = a + b` permite que você defina uma função que é o aplicativo parcial do primeiro argumento da função, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="33773-125">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="33773-126">Usar uma tupla, como o parâmetro desabilita currying.</span><span class="sxs-lookup"><span data-stu-id="33773-126">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="33773-127">Para obter mais informações, consulte "Parcial dos argumentos de aplicativo" na [funções](functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="33773-127">For more information, see "Partial Application of Arguments" in [Functions](functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="33773-128">Nomes de tipos de tupla</span><span class="sxs-lookup"><span data-stu-id="33773-128">Names of Tuple Types</span></span>

<span data-ttu-id="33773-129">Quando você escreve o nome de um tipo que é uma tupla, você usar o `*` símbolo para separar os elementos.</span><span class="sxs-lookup"><span data-stu-id="33773-129">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="33773-130">Para uma tupla que consiste em uma `int`, um `float`e um `string`, tais como `(10, 10.0, "ten")`, o tipo deve ser escrito da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="33773-130">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="33773-131">Interoperação com tuplas do c#</span><span class="sxs-lookup"><span data-stu-id="33773-131">Interoperation with C# Tuples</span></span>

<span data-ttu-id="33773-132">C# 7.0 introduziu tuplas para o idioma.</span><span class="sxs-lookup"><span data-stu-id="33773-132">C# 7.0 introduced tuples to the language.</span></span>  <span data-ttu-id="33773-133">As tuplas em c# são structs e são equivalentes a tuplas de struct em F #.</span><span class="sxs-lookup"><span data-stu-id="33773-133">Tuples in C# are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="33773-134">Se você precisar interoperar com c#, você deve usar tuplas de struct.</span><span class="sxs-lookup"><span data-stu-id="33773-134">If you need to interoperate with C#, you must use struct tuples.</span></span>

<span data-ttu-id="33773-135">Isso é fácil de fazer.</span><span class="sxs-lookup"><span data-stu-id="33773-135">This is easy to do.</span></span>  <span data-ttu-id="33773-136">Por exemplo, imagine que você precisa passar uma tupla a uma classe c# e, em seguida, consumir seu resultado, que também é uma tupla:</span><span class="sxs-lookup"><span data-stu-id="33773-136">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

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

<span data-ttu-id="33773-137">No código do F #, você pode passar uma tupla de struct como parâmetro e consumir o resultado como uma tupla de struct.</span><span class="sxs-lookup"><span data-stu-id="33773-137">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="33773-138">Convertendo entre tuplas de referência e tuplas de Struct</span><span class="sxs-lookup"><span data-stu-id="33773-138">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="33773-139">Como as tuplas de referência e Tuples de Struct têm uma representação subjacente completamente diferente, eles não são implicitamente conversíveis.</span><span class="sxs-lookup"><span data-stu-id="33773-139">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="33773-140">Ou seja, não será compilado código como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="33773-140">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="33773-141">Você deve padrão correspondem em uma tupla e construir o outro com as partes constituintes.</span><span class="sxs-lookup"><span data-stu-id="33773-141">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="33773-142">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="33773-142">For example:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="33773-143">Forma compilada de tuplas de referência</span><span class="sxs-lookup"><span data-stu-id="33773-143">Compiled Form of Reference Tuples</span></span>

<span data-ttu-id="33773-144">Esta seção explica a forma de tuplas quando eles serão compilados.</span><span class="sxs-lookup"><span data-stu-id="33773-144">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="33773-145">As informações fornecidas aqui não não necessária para ler a menos que você tiver como alvo o .NET Framework 3.5 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="33773-145">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="33773-146">As tuplas são compiladas em objetos de um dos vários tipos genéricos, todas nomeados `System.Tuple`, que são sobrecarregados na arity ou número de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="33773-146">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="33773-147">Tipos de tupla aparecem neste formulário quando você exibi-los de outra linguagem, como c# ou Visual Basic, ou quando você estiver usando uma ferramenta que não está ciente das construções no F #.</span><span class="sxs-lookup"><span data-stu-id="33773-147">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="33773-148">O `Tuple` tipos foram introduzidos no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="33773-148">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="33773-149">Se você estiver selecionando uma versão anterior do .NET Framework, o compilador usa as versões do [System. Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) da versão 2.0 da biblioteca principal F #.</span><span class="sxs-lookup"><span data-stu-id="33773-149">If you are targeting an earlier version of the .NET Framework, the compiler uses versions of [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="33773-150">Os tipos na biblioteca são usados apenas para aplicativos que direcionam o 2.0, 3.0 e 3.5 versões do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="33773-150">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of the .NET Framework.</span></span> <span data-ttu-id="33773-151">Encaminhamento de tipo é usado para garantir a compatibilidade binária entre os componentes do .NET Framework 2.0 e o .NET Framework 4 F #.</span><span class="sxs-lookup"><span data-stu-id="33773-151">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="33773-152">Forma compilada de tuplas de Struct</span><span class="sxs-lookup"><span data-stu-id="33773-152">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="33773-153">Tuplas de struct (por exemplo, `struct (x, y)`), são fundamentalmente diferente das tuplas de referência.</span><span class="sxs-lookup"><span data-stu-id="33773-153">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="33773-154">Eles são compilados no <xref:System.ValueTuple> tipo, sobrecarregado por arity ou o número de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="33773-154">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="33773-155">Elas são equivalentes às [tuplas do c# 7.0](../../csharp/tuples.md) e [tuplas do Visual Basic 2017](../../visual-basic/programming-guide/language-features/data-types/tuples.md)e interoperar bidirecionalmente.</span><span class="sxs-lookup"><span data-stu-id="33773-155">They are equivalent to [C# 7.0 Tuples](../../csharp/tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="33773-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33773-156">See also</span></span>

- [<span data-ttu-id="33773-157">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="33773-157">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="33773-158">Tipos F#</span><span class="sxs-lookup"><span data-stu-id="33773-158">F# Types</span></span>](fsharp-types.md)
