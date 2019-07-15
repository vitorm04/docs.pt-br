---
title: Tipos de ponteiro – Guia de Programação em C#
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 59846affb1eea5bd9d6a80c623eab5e3aa9db87c
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661077"
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="88a75-102">Tipos de ponteiro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="88a75-102">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="88a75-103">Em um contexto inseguro, um tipo pode ser de ponteiro, valor ou referência.</span><span class="sxs-lookup"><span data-stu-id="88a75-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="88a75-104">Uma declaração de tipo de ponteiro usa uma das seguintes formas:</span><span class="sxs-lookup"><span data-stu-id="88a75-104">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="88a75-105">O tipo especificado antes do `*` em um tipo de ponteiro é chamado de **tipo referent**.</span><span class="sxs-lookup"><span data-stu-id="88a75-105">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="88a75-106">Qualquer um dos tipos a seguir pode ser do tipo referent:</span><span class="sxs-lookup"><span data-stu-id="88a75-106">Any of the following types may be a referent type:</span></span>

- <span data-ttu-id="88a75-107">Qualquer tipo integral: [sbyte](../../language-reference/builtin-types/integral-numeric-types.md), [byte](../../language-reference/builtin-types/integral-numeric-types.md), [short](../../language-reference/builtin-types/integral-numeric-types.md), [ushort](../../language-reference/builtin-types/integral-numeric-types.md), [int](../../language-reference/builtin-types/integral-numeric-types.md), [uint](../../language-reference/builtin-types/integral-numeric-types.md), [long](../../language-reference/builtin-types/integral-numeric-types.md), [ulong](../../language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="88a75-107">Any integral type: [sbyte](../../language-reference/builtin-types/integral-numeric-types.md), [byte](../../language-reference/builtin-types/integral-numeric-types.md), [short](../../language-reference/builtin-types/integral-numeric-types.md), [ushort](../../language-reference/builtin-types/integral-numeric-types.md), [int](../../language-reference/builtin-types/integral-numeric-types.md), [uint](../../language-reference/builtin-types/integral-numeric-types.md), [long](../../language-reference/builtin-types/integral-numeric-types.md), [ulong](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>
- <span data-ttu-id="88a75-108">Qualquer tipo de ponto flutuante: [float](../../language-reference/builtin-types/floating-point-numeric-types.md), [double](../../language-reference/builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="88a75-108">Any floating-point type: [float](../../language-reference/builtin-types/floating-point-numeric-types.md), [double](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>
- <span data-ttu-id="88a75-109">[char](../../language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="88a75-109">[char](../../language-reference/keywords/char.md).</span></span>
- <span data-ttu-id="88a75-110">[bool](../../language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="88a75-110">[bool](../../language-reference/keywords/bool.md).</span></span>
- <span data-ttu-id="88a75-111">[decimal](../../language-reference/builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="88a75-111">[decimal](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>
- <span data-ttu-id="88a75-112">Qualquer tipo [enum](../../language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="88a75-112">Any [enum](../../language-reference/keywords/enum.md) type.</span></span>
- <span data-ttu-id="88a75-113">Qualquer tipo de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="88a75-113">Any pointer type.</span></span> <span data-ttu-id="88a75-114">Isso permite expressões como `void**`.</span><span class="sxs-lookup"><span data-stu-id="88a75-114">This allows expressions such as `void**`.</span></span>
- <span data-ttu-id="88a75-115">Qualquer struct definido pelo usuário que contenha somente campos de tipos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="88a75-115">Any user-defined struct type that contains fields of unmanaged types only.</span></span>

<span data-ttu-id="88a75-116">Os tipos de ponteiro não são herdados de [objeto](../../language-reference/keywords/object.md) e não há nenhuma conversão entre tipos de ponteiro e `object`.</span><span class="sxs-lookup"><span data-stu-id="88a75-116">Pointer types do not inherit from [object](../../language-reference/keywords/object.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="88a75-117">Além disso, as conversões boxing e unboxing não oferecem suporte a ponteiros.</span><span class="sxs-lookup"><span data-stu-id="88a75-117">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="88a75-118">No entanto, você pode converter entre diferentes tipos de ponteiro e tipos de ponteiro e tipos integrais.</span><span class="sxs-lookup"><span data-stu-id="88a75-118">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="88a75-119">Quando você designa vários ponteiros na mesma declaração, o asterisco (\*) é escrito junto apenas com o tipo subjacente; ele não é usado como um prefixo para cada nome de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="88a75-119">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="88a75-120">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="88a75-120">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="88a75-121">Um ponteiro não pode apontar para uma referência ou um [struct](../../language-reference/keywords/struct.md) que contenha referências, pois uma referência de objeto pode ser coletada como lixo mesmo se um ponteiro estiver apontando para ela.</span><span class="sxs-lookup"><span data-stu-id="88a75-121">A pointer cannot point to a reference or to a [struct](../../language-reference/keywords/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="88a75-122">O coletor de lixo não acompanha se um objeto está sendo apontado por qualquer tipo de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="88a75-122">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="88a75-123">O valor da variável de ponteiro do tipo `myType*` é o endereço de uma variável do tipo `myType`.</span><span class="sxs-lookup"><span data-stu-id="88a75-123">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="88a75-124">Estes são exemplos de declarações de tipos de ponteiro:</span><span class="sxs-lookup"><span data-stu-id="88a75-124">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="88a75-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="88a75-125">Example</span></span>|<span data-ttu-id="88a75-126">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="88a75-126">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="88a75-127">`p` é um ponteiro para um inteiro.</span><span class="sxs-lookup"><span data-stu-id="88a75-127">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="88a75-128">`p` é um ponteiro para um ponteiro para um inteiro.</span><span class="sxs-lookup"><span data-stu-id="88a75-128">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="88a75-129">`p` é uma matriz unidimensional de ponteiros para inteiros.</span><span class="sxs-lookup"><span data-stu-id="88a75-129">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="88a75-130">`p` é um ponteiro para um caractere.</span><span class="sxs-lookup"><span data-stu-id="88a75-130">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="88a75-131">`p` é um ponteiro para um tipo desconhecido.</span><span class="sxs-lookup"><span data-stu-id="88a75-131">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="88a75-132">O operador de indireção de ponteiro \* pode ser usado para acessar o conteúdo no local apontado pela variável de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="88a75-132">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="88a75-133">Por exemplo, considere a seguinte declaração:</span><span class="sxs-lookup"><span data-stu-id="88a75-133">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="88a75-134">A expressão `*myVariable` denota a variável `int` encontrada no endereço contido em `myVariable`.</span><span class="sxs-lookup"><span data-stu-id="88a75-134">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="88a75-135">Há vários exemplos de ponteiros nos tópicos [Instrução fixed](../../language-reference/keywords/fixed-statement.md) e [Conversões de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="88a75-135">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](../../programming-guide/unsafe-code-pointers/pointer-conversions.md).</span></span> <span data-ttu-id="88a75-136">O exemplo a seguir usa a palavra-chave `unsafe` e a instrução `fixed` e mostra como incrementar um ponteiro interior.</span><span class="sxs-lookup"><span data-stu-id="88a75-136">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="88a75-137">Você pode colar esse código na função principal de um aplicativo de console para executá-lo.</span><span class="sxs-lookup"><span data-stu-id="88a75-137">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="88a75-138">Estes exemplos precisam ser compilados com o conjunto de opções do compilador [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="88a75-138">These examples must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option set.</span></span>

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

<span data-ttu-id="88a75-139">Você não pode aplicar o operador de indireção para um ponteiro do tipo `void*`.</span><span class="sxs-lookup"><span data-stu-id="88a75-139">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="88a75-140">No entanto, você pode usar uma conversão para converter um ponteiro nulo em qualquer outro tipo de ponteiro e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="88a75-140">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="88a75-141">Um ponteiro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="88a75-141">A pointer can be `null`.</span></span> <span data-ttu-id="88a75-142">Aplicar o operador de indireção a um ponteiro nulo causa um comportamento definido por implementação.</span><span class="sxs-lookup"><span data-stu-id="88a75-142">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="88a75-143">Passar ponteiros entre métodos pode causar um comportamento indefinido.</span><span class="sxs-lookup"><span data-stu-id="88a75-143">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="88a75-144">Considere usar um método que retorne um ponteiro para uma variável local por meio de um parâmetro `in`, `out` ou `ref`, ou como o resultado da função.</span><span class="sxs-lookup"><span data-stu-id="88a75-144">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="88a75-145">Se o ponteiro foi definido em um bloco fixo, a variável à qual ele aponta não pode mais ser corrigida.</span><span class="sxs-lookup"><span data-stu-id="88a75-145">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="88a75-146">A tabela a seguir lista os operadores e as instruções que podem operar em ponteiros em um contexto inseguro:</span><span class="sxs-lookup"><span data-stu-id="88a75-146">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="88a75-147">Operador/Instrução</span><span class="sxs-lookup"><span data-stu-id="88a75-147">Operator/Statement</span></span>|<span data-ttu-id="88a75-148">Use</span><span class="sxs-lookup"><span data-stu-id="88a75-148">Use</span></span>|
|-------------------------|---------|
|`*`|<span data-ttu-id="88a75-149">Executa indireção de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="88a75-149">Performs pointer indirection.</span></span>|
|`->`|<span data-ttu-id="88a75-150">Acessa um membro de um struct através de um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="88a75-150">Accesses a member of a struct through a pointer.</span></span>|
|`[]`|<span data-ttu-id="88a75-151">Indexa um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="88a75-151">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="88a75-152">Obtém o endereço de uma variável.</span><span class="sxs-lookup"><span data-stu-id="88a75-152">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="88a75-153">`++` e `--`</span><span class="sxs-lookup"><span data-stu-id="88a75-153">`++` and `--`</span></span>|<span data-ttu-id="88a75-154">Incrementa e decrementa ponteiros.</span><span class="sxs-lookup"><span data-stu-id="88a75-154">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="88a75-155">`+` e `-`</span><span class="sxs-lookup"><span data-stu-id="88a75-155">`+` and `-`</span></span>|<span data-ttu-id="88a75-156">Executa aritmética de ponteiros.</span><span class="sxs-lookup"><span data-stu-id="88a75-156">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="88a75-157">`==`, `!=`, `<`, `>`, `<=` e `>=`</span><span class="sxs-lookup"><span data-stu-id="88a75-157">`==`, `!=`, `<`, `>`, `<=`, and `>=`</span></span>|<span data-ttu-id="88a75-158">Compara ponteiros.</span><span class="sxs-lookup"><span data-stu-id="88a75-158">Compares pointers.</span></span>|
|[<span data-ttu-id="88a75-159">Operador `stackalloc`</span><span class="sxs-lookup"><span data-stu-id="88a75-159">`stackalloc` operator</span></span>](../../language-reference/operators/stackalloc.md)|<span data-ttu-id="88a75-160">Aloca memória na pilha.</span><span class="sxs-lookup"><span data-stu-id="88a75-160">Allocates memory on the stack.</span></span>|
|[<span data-ttu-id="88a75-161">Instrução `fixed`</span><span class="sxs-lookup"><span data-stu-id="88a75-161">`fixed` statement</span></span>](../../language-reference/keywords/fixed-statement.md)|<span data-ttu-id="88a75-162">Corrige temporariamente uma variável para que seu endereço possa ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="88a75-162">Temporarily fixes a variable so that its address may be found.</span></span>|

<span data-ttu-id="88a75-163">Para obter mais informações sobre operadores relacionados a ponteiro, veja [Operadores relacionados a ponteiro](../../language-reference/operators/pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="88a75-163">For more information about pointer related operators, see [Pointer related operators](../../language-reference/operators/pointer-related-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="88a75-164">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="88a75-164">C# language specification</span></span>

<span data-ttu-id="88a75-165">Para saber mais, confira a seção [Tipos de ponteiro](~/_csharplang/spec/unsafe-code.md#pointer-types) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="88a75-165">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="88a75-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88a75-166">See also</span></span>

- [<span data-ttu-id="88a75-167">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="88a75-167">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="88a75-168">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="88a75-168">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="88a75-169">Conversões de ponteiro</span><span class="sxs-lookup"><span data-stu-id="88a75-169">Pointer Conversions</span></span>](pointer-conversions.md)
- [<span data-ttu-id="88a75-170">Tipos</span><span class="sxs-lookup"><span data-stu-id="88a75-170">Types</span></span>](../../language-reference/keywords/types.md)
- [<span data-ttu-id="88a75-171">unsafe</span><span class="sxs-lookup"><span data-stu-id="88a75-171">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
