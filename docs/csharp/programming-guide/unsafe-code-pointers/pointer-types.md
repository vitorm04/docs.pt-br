---
title: Tipos de ponteiro – Guia de Programação em C#
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 1f394d3fe5a2cb03c39cb0416e4ae44d6e340a4e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345634"
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="8c49f-102">Tipos de ponteiro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="8c49f-102">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="8c49f-103">Em um contexto inseguro, um tipo pode ser de ponteiro, valor ou referência.</span><span class="sxs-lookup"><span data-stu-id="8c49f-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="8c49f-104">Uma declaração de tipo de ponteiro usa uma das seguintes formas:</span><span class="sxs-lookup"><span data-stu-id="8c49f-104">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="8c49f-105">O tipo especificado antes do `*` em um tipo de ponteiro é chamado de **tipo referent**.</span><span class="sxs-lookup"><span data-stu-id="8c49f-105">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="8c49f-106">Somente um [tipo não gerenciado](../../language-reference/builtin-types/unmanaged-types.md) pode ser um tipo referent.</span><span class="sxs-lookup"><span data-stu-id="8c49f-106">Only an [unmanaged type](../../language-reference/builtin-types/unmanaged-types.md) can be a referent type.</span></span>

<span data-ttu-id="8c49f-107">Os tipos de ponteiro não são herdados de [objeto](../../language-reference/builtin-types/reference-types.md) e não há nenhuma conversão entre tipos de ponteiro e `object`.</span><span class="sxs-lookup"><span data-stu-id="8c49f-107">Pointer types do not inherit from [object](../../language-reference/builtin-types/reference-types.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="8c49f-108">Além disso, as conversões boxing e unboxing não oferecem suporte a ponteiros.</span><span class="sxs-lookup"><span data-stu-id="8c49f-108">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="8c49f-109">No entanto, você pode converter entre diferentes tipos de ponteiro e tipos de ponteiro e tipos integrais.</span><span class="sxs-lookup"><span data-stu-id="8c49f-109">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="8c49f-110">Quando você designa vários ponteiros na mesma declaração, o asterisco (\*) é escrito junto apenas com o tipo subjacente; ele não é usado como um prefixo para cada nome de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="8c49f-110">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="8c49f-111">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="8c49f-111">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="8c49f-112">Um ponteiro não pode apontar para uma referência ou um [struct](../../language-reference/keywords/struct.md) que contenha referências, pois uma referência de objeto pode ser coletada como lixo mesmo se um ponteiro estiver apontando para ela.</span><span class="sxs-lookup"><span data-stu-id="8c49f-112">A pointer cannot point to a reference or to a [struct](../../language-reference/keywords/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="8c49f-113">O coletor de lixo não acompanha se um objeto está sendo apontado por qualquer tipo de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="8c49f-113">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="8c49f-114">O valor da variável de ponteiro do tipo `myType*` é o endereço de uma variável do tipo `myType`.</span><span class="sxs-lookup"><span data-stu-id="8c49f-114">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="8c49f-115">Estes são exemplos de declarações de tipos de ponteiro:</span><span class="sxs-lookup"><span data-stu-id="8c49f-115">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="8c49f-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8c49f-116">Example</span></span>|<span data-ttu-id="8c49f-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c49f-117">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="8c49f-118">`p` é um ponteiro para um inteiro.</span><span class="sxs-lookup"><span data-stu-id="8c49f-118">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="8c49f-119">`p` é um ponteiro para um ponteiro para um inteiro.</span><span class="sxs-lookup"><span data-stu-id="8c49f-119">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="8c49f-120">`p` é uma matriz unidimensional de ponteiros para inteiros.</span><span class="sxs-lookup"><span data-stu-id="8c49f-120">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="8c49f-121">`p` é um ponteiro para um caractere.</span><span class="sxs-lookup"><span data-stu-id="8c49f-121">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="8c49f-122">`p` é um ponteiro para um tipo desconhecido.</span><span class="sxs-lookup"><span data-stu-id="8c49f-122">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="8c49f-123">O operador de indireção de ponteiro \* pode ser usado para acessar o conteúdo no local apontado pela variável de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="8c49f-123">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="8c49f-124">Por exemplo, considere a seguinte declaração:</span><span class="sxs-lookup"><span data-stu-id="8c49f-124">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="8c49f-125">A expressão `*myVariable` denota a variável `int` encontrada no endereço contido em `myVariable`.</span><span class="sxs-lookup"><span data-stu-id="8c49f-125">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="8c49f-126">Há vários exemplos de ponteiros nos tópicos [Instrução fixed](../../language-reference/keywords/fixed-statement.md) e [Conversões de ponteiro](./pointer-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="8c49f-126">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](./pointer-conversions.md).</span></span> <span data-ttu-id="8c49f-127">O exemplo a seguir usa a palavra-chave `unsafe` e a instrução `fixed` e mostra como incrementar um ponteiro interior.</span><span class="sxs-lookup"><span data-stu-id="8c49f-127">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="8c49f-128">Você pode colar esse código na função principal de um aplicativo de console para executá-lo.</span><span class="sxs-lookup"><span data-stu-id="8c49f-128">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="8c49f-129">Estes exemplos precisam ser compilados com o conjunto de opções do compilador [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="8c49f-129">These examples must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option set.</span></span>

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

<span data-ttu-id="8c49f-130">Você não pode aplicar o operador de indireção para um ponteiro do tipo `void*`.</span><span class="sxs-lookup"><span data-stu-id="8c49f-130">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="8c49f-131">No entanto, você pode usar uma conversão para converter um ponteiro nulo em qualquer outro tipo de ponteiro e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="8c49f-131">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="8c49f-132">Um ponteiro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="8c49f-132">A pointer can be `null`.</span></span> <span data-ttu-id="8c49f-133">Aplicar o operador de indireção a um ponteiro nulo causa um comportamento definido por implementação.</span><span class="sxs-lookup"><span data-stu-id="8c49f-133">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="8c49f-134">Passar ponteiros entre métodos pode causar um comportamento indefinido.</span><span class="sxs-lookup"><span data-stu-id="8c49f-134">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="8c49f-135">Considere usar um método que retorne um ponteiro para uma variável local por meio de um parâmetro `in`, `out` ou `ref`, ou como o resultado da função.</span><span class="sxs-lookup"><span data-stu-id="8c49f-135">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="8c49f-136">Se o ponteiro foi definido em um bloco fixo, a variável à qual ele aponta não pode mais ser corrigida.</span><span class="sxs-lookup"><span data-stu-id="8c49f-136">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="8c49f-137">A tabela a seguir lista os operadores e as instruções que podem operar em ponteiros em um contexto inseguro:</span><span class="sxs-lookup"><span data-stu-id="8c49f-137">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="8c49f-138">Operador/Instrução</span><span class="sxs-lookup"><span data-stu-id="8c49f-138">Operator/Statement</span></span>|<span data-ttu-id="8c49f-139">Uso</span><span class="sxs-lookup"><span data-stu-id="8c49f-139">Use</span></span>|
|-------------------------|---------|
|`*`|<span data-ttu-id="8c49f-140">Executa indireção de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="8c49f-140">Performs pointer indirection.</span></span>|
|`->`|<span data-ttu-id="8c49f-141">Acessa um membro de um struct através de um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="8c49f-141">Accesses a member of a struct through a pointer.</span></span>|
|`[]`|<span data-ttu-id="8c49f-142">Indexa um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="8c49f-142">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="8c49f-143">Obtém o endereço de uma variável.</span><span class="sxs-lookup"><span data-stu-id="8c49f-143">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="8c49f-144">`++` e `--`</span><span class="sxs-lookup"><span data-stu-id="8c49f-144">`++` and `--`</span></span>|<span data-ttu-id="8c49f-145">Incrementa e decrementa ponteiros.</span><span class="sxs-lookup"><span data-stu-id="8c49f-145">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="8c49f-146">`+` e `-`</span><span class="sxs-lookup"><span data-stu-id="8c49f-146">`+` and `-`</span></span>|<span data-ttu-id="8c49f-147">Executa aritmética de ponteiros.</span><span class="sxs-lookup"><span data-stu-id="8c49f-147">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="8c49f-148">`==`, `!=`, `<`, `>`, `<=` e `>=`</span><span class="sxs-lookup"><span data-stu-id="8c49f-148">`==`, `!=`, `<`, `>`, `<=`, and `>=`</span></span>|<span data-ttu-id="8c49f-149">Compara ponteiros.</span><span class="sxs-lookup"><span data-stu-id="8c49f-149">Compares pointers.</span></span>|
|[<span data-ttu-id="8c49f-150">Operador `stackalloc`</span><span class="sxs-lookup"><span data-stu-id="8c49f-150">`stackalloc` operator</span></span>](../../language-reference/operators/stackalloc.md)|<span data-ttu-id="8c49f-151">Aloca memória na pilha.</span><span class="sxs-lookup"><span data-stu-id="8c49f-151">Allocates memory on the stack.</span></span>|
|[<span data-ttu-id="8c49f-152">Instrução `fixed`</span><span class="sxs-lookup"><span data-stu-id="8c49f-152">`fixed` statement</span></span>](../../language-reference/keywords/fixed-statement.md)|<span data-ttu-id="8c49f-153">Corrige temporariamente uma variável para que seu endereço possa ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="8c49f-153">Temporarily fixes a variable so that its address may be found.</span></span>|

<span data-ttu-id="8c49f-154">Para obter mais informações sobre operadores relacionados a ponteiro, veja [Operadores relacionados a ponteiro](../../language-reference/operators/pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="8c49f-154">For more information about pointer related operators, see [Pointer related operators](../../language-reference/operators/pointer-related-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8c49f-155">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="8c49f-155">C# language specification</span></span>

<span data-ttu-id="8c49f-156">Para saber mais, confira a seção [Tipos de ponteiro](~/_csharplang/spec/unsafe-code.md#pointer-types) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="8c49f-156">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8c49f-157">Veja também</span><span class="sxs-lookup"><span data-stu-id="8c49f-157">See also</span></span>

- [<span data-ttu-id="8c49f-158">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="8c49f-158">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8c49f-159">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="8c49f-159">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="8c49f-160">Conversões de ponteiro</span><span class="sxs-lookup"><span data-stu-id="8c49f-160">Pointer Conversions</span></span>](pointer-conversions.md)
- [<span data-ttu-id="8c49f-161">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="8c49f-161">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="8c49f-162">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="8c49f-162">Value types</span></span>](../../language-reference/keywords/value-types.md)
- [<span data-ttu-id="8c49f-163">unsafe</span><span class="sxs-lookup"><span data-stu-id="8c49f-163">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
