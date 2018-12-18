---
title: Tipos de ponteiro – Guia de Programação em C#
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 5474d179005742c610d29ccd9dac7bf1dc94c9d2
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239395"
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="f6f95-102">Tipos de ponteiro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="f6f95-102">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="f6f95-103">Em um contexto inseguro, um tipo pode ser de ponteiro, valor ou referência.</span><span class="sxs-lookup"><span data-stu-id="f6f95-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="f6f95-104">Uma declaração de tipo de ponteiro usa uma das seguintes formas:</span><span class="sxs-lookup"><span data-stu-id="f6f95-104">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="f6f95-105">O tipo especificado antes do `*` em um tipo de ponteiro é chamado de **tipo referent**.</span><span class="sxs-lookup"><span data-stu-id="f6f95-105">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="f6f95-106">Qualquer um dos tipos a seguir pode ser do tipo referent:</span><span class="sxs-lookup"><span data-stu-id="f6f95-106">Any of the following types may be a referent type:</span></span>

- <span data-ttu-id="f6f95-107">Qualquer tipo integral: [sbyte](../../language-reference/keywords/sbyte.md), [byte](../../language-reference/keywords/byte.md), [short](../../language-reference/keywords/short.md), [ushort](../../language-reference/keywords/ushort.md), [int](../../language-reference/keywords/int.md), [uint](../../language-reference/keywords/uint.md), [long](../../language-reference/keywords/long.md), [ulong](../../language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="f6f95-107">Any integral type: [sbyte](../../language-reference/keywords/sbyte.md), [byte](../../language-reference/keywords/byte.md), [short](../../language-reference/keywords/short.md), [ushort](../../language-reference/keywords/ushort.md), [int](../../language-reference/keywords/int.md), [uint](../../language-reference/keywords/uint.md), [long](../../language-reference/keywords/long.md), [ulong](../../language-reference/keywords/ulong.md).</span></span>
- <span data-ttu-id="f6f95-108">Qualquer tipo de ponto flutuante: [float](../../language-reference/keywords/float.md), [double](../../language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="f6f95-108">Any floating-point type: [float](../../language-reference/keywords/float.md), [double](../../language-reference/keywords/double.md).</span></span>
- <span data-ttu-id="f6f95-109">[char](../../language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="f6f95-109">[char](../../language-reference/keywords/char.md).</span></span>
- <span data-ttu-id="f6f95-110">[bool](../../language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="f6f95-110">[bool](../../language-reference/keywords/bool.md).</span></span>
- <span data-ttu-id="f6f95-111">[decimal](../../language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="f6f95-111">[decimal](../../language-reference/keywords/decimal.md).</span></span>
- <span data-ttu-id="f6f95-112">Qualquer tipo [enum](../../language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="f6f95-112">Any [enum](../../language-reference/keywords/enum.md) type.</span></span>
- <span data-ttu-id="f6f95-113">Qualquer tipo de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="f6f95-113">Any pointer type.</span></span> <span data-ttu-id="f6f95-114">Isso permite expressões como `void**`.</span><span class="sxs-lookup"><span data-stu-id="f6f95-114">This allows expressions such as `void**`.</span></span>
- <span data-ttu-id="f6f95-115">Qualquer struct definido pelo usuário que contenha somente campos de tipos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="f6f95-115">Any user-defined struct type that contains fields of unmanaged types only.</span></span>

<span data-ttu-id="f6f95-116">Os tipos de ponteiro não são herdados de [objeto](../../language-reference/keywords/object.md) e não há nenhuma conversão entre tipos de ponteiro e `object`.</span><span class="sxs-lookup"><span data-stu-id="f6f95-116">Pointer types do not inherit from [object](../../language-reference/keywords/object.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="f6f95-117">Além disso, as conversões boxing e unboxing não oferecem suporte a ponteiros.</span><span class="sxs-lookup"><span data-stu-id="f6f95-117">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="f6f95-118">No entanto, você pode converter entre diferentes tipos de ponteiro e tipos de ponteiro e tipos integrais.</span><span class="sxs-lookup"><span data-stu-id="f6f95-118">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="f6f95-119">Quando você designa vários ponteiros na mesma declaração, o asterisco (\*) é escrito junto apenas com o tipo subjacente; ele não é usado como um prefixo para cada nome de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="f6f95-119">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="f6f95-120">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f6f95-120">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="f6f95-121">Um ponteiro não pode apontar para uma referência ou um [struct](../../language-reference/keywords/struct.md) que contenha referências, pois uma referência de objeto pode ser coletada como lixo mesmo se um ponteiro estiver apontando para ela.</span><span class="sxs-lookup"><span data-stu-id="f6f95-121">A pointer cannot point to a reference or to a [struct](../../language-reference/keywords/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="f6f95-122">O coletor de lixo não acompanha se um objeto está sendo apontado por qualquer tipo de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="f6f95-122">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="f6f95-123">O valor da variável de ponteiro do tipo `myType*` é o endereço de uma variável do tipo `myType`.</span><span class="sxs-lookup"><span data-stu-id="f6f95-123">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="f6f95-124">Estes são exemplos de declarações de tipos de ponteiro:</span><span class="sxs-lookup"><span data-stu-id="f6f95-124">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="f6f95-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6f95-125">Example</span></span>|<span data-ttu-id="f6f95-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6f95-126">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="f6f95-127">`p` é um ponteiro para um inteiro.</span><span class="sxs-lookup"><span data-stu-id="f6f95-127">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="f6f95-128">`p` é um ponteiro para um ponteiro para um inteiro.</span><span class="sxs-lookup"><span data-stu-id="f6f95-128">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="f6f95-129">`p` é uma matriz unidimensional de ponteiros para inteiros.</span><span class="sxs-lookup"><span data-stu-id="f6f95-129">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="f6f95-130">`p` é um ponteiro para um caractere.</span><span class="sxs-lookup"><span data-stu-id="f6f95-130">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="f6f95-131">`p` é um ponteiro para um tipo desconhecido.</span><span class="sxs-lookup"><span data-stu-id="f6f95-131">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="f6f95-132">O operador de indireção de ponteiro \* pode ser usado para acessar o conteúdo no local apontado pela variável de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="f6f95-132">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="f6f95-133">Por exemplo, considere a seguinte declaração:</span><span class="sxs-lookup"><span data-stu-id="f6f95-133">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="f6f95-134">A expressão `*myVariable` denota a variável `int` encontrada no endereço contido em `myVariable`.</span><span class="sxs-lookup"><span data-stu-id="f6f95-134">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="f6f95-135">Há vários exemplos de ponteiros nos tópicos [Instrução fixed](../../language-reference/keywords/fixed-statement.md) e [Conversões de ponteiro](../../programming-guide/unsafe-code-pointers/pointer-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="f6f95-135">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](../../programming-guide/unsafe-code-pointers/pointer-conversions.md).</span></span> <span data-ttu-id="f6f95-136">O exemplo a seguir usa a palavra-chave `unsafe` e a instrução `fixed` e mostra como incrementar um ponteiro interior.</span><span class="sxs-lookup"><span data-stu-id="f6f95-136">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="f6f95-137">Você pode colar esse código na função principal de um aplicativo de console para executá-lo.</span><span class="sxs-lookup"><span data-stu-id="f6f95-137">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="f6f95-138">Estes exemplos precisam ser compilados com o conjunto de opções do compilador [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="f6f95-138">These examples must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option set.</span></span>

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

<span data-ttu-id="f6f95-139">Você não pode aplicar o operador de indireção para um ponteiro do tipo `void*`.</span><span class="sxs-lookup"><span data-stu-id="f6f95-139">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="f6f95-140">No entanto, você pode usar uma conversão para converter um ponteiro nulo em qualquer outro tipo de ponteiro e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="f6f95-140">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="f6f95-141">Um ponteiro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="f6f95-141">A pointer can be `null`.</span></span> <span data-ttu-id="f6f95-142">Aplicar o operador de indireção a um ponteiro nulo causa um comportamento definido por implementação.</span><span class="sxs-lookup"><span data-stu-id="f6f95-142">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="f6f95-143">Passar ponteiros entre métodos pode causar um comportamento indefinido.</span><span class="sxs-lookup"><span data-stu-id="f6f95-143">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="f6f95-144">Considere usar um método que retorne um ponteiro para uma variável local por meio de um parâmetro `in`, `out` ou `ref`, ou como o resultado da função.</span><span class="sxs-lookup"><span data-stu-id="f6f95-144">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="f6f95-145">Se o ponteiro foi definido em um bloco fixo, a variável à qual ele aponta não pode mais ser corrigida.</span><span class="sxs-lookup"><span data-stu-id="f6f95-145">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="f6f95-146">A tabela a seguir lista os operadores e as instruções que podem operar em ponteiros em um contexto inseguro:</span><span class="sxs-lookup"><span data-stu-id="f6f95-146">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="f6f95-147">Operador/Instrução</span><span class="sxs-lookup"><span data-stu-id="f6f95-147">Operator/Statement</span></span>|<span data-ttu-id="f6f95-148">Use</span><span class="sxs-lookup"><span data-stu-id="f6f95-148">Use</span></span>|
|-------------------------|---------|
|*|<span data-ttu-id="f6f95-149">Executa indireção de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="f6f95-149">Performs pointer indirection.</span></span>|
|->|<span data-ttu-id="f6f95-150">Acessa um membro de um struct através de um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="f6f95-150">Accesses a member of a struct through a pointer.</span></span>|
|<span data-ttu-id="f6f95-151">[]</span><span class="sxs-lookup"><span data-stu-id="f6f95-151">[]</span></span>|<span data-ttu-id="f6f95-152">Indexa um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="f6f95-152">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="f6f95-153">Obtém o endereço de uma variável.</span><span class="sxs-lookup"><span data-stu-id="f6f95-153">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="f6f95-154">++ e --</span><span class="sxs-lookup"><span data-stu-id="f6f95-154">++ and --</span></span>|<span data-ttu-id="f6f95-155">Incrementa e decrementa ponteiros.</span><span class="sxs-lookup"><span data-stu-id="f6f95-155">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="f6f95-156">+ e -</span><span class="sxs-lookup"><span data-stu-id="f6f95-156">+ and -</span></span>|<span data-ttu-id="f6f95-157">Executa aritmética de ponteiros.</span><span class="sxs-lookup"><span data-stu-id="f6f95-157">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="f6f95-158">==, !=, \<, >, \<= e >=</span><span class="sxs-lookup"><span data-stu-id="f6f95-158">==, !=, \<, >, \<=, and >=</span></span>|<span data-ttu-id="f6f95-159">Compara ponteiros.</span><span class="sxs-lookup"><span data-stu-id="f6f95-159">Compares pointers.</span></span>|
|`stackalloc`|<span data-ttu-id="f6f95-160">Aloca memória na pilha.</span><span class="sxs-lookup"><span data-stu-id="f6f95-160">Allocates memory on the stack.</span></span>|
|<span data-ttu-id="f6f95-161">Instrução `fixed`</span><span class="sxs-lookup"><span data-stu-id="f6f95-161">`fixed` statement</span></span>|<span data-ttu-id="f6f95-162">Corrige temporariamente uma variável para que seu endereço possa ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="f6f95-162">Temporarily fixes a variable so that its address may be found.</span></span>|

## <a name="c-language-specification"></a><span data-ttu-id="f6f95-163">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="f6f95-163">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f6f95-164">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6f95-164">See Also</span></span>

- [<span data-ttu-id="f6f95-165">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="f6f95-165">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="f6f95-166">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="f6f95-166">Unsafe Code and Pointers</span></span>](index.md)  
- [<span data-ttu-id="f6f95-167">Conversões de ponteiro</span><span class="sxs-lookup"><span data-stu-id="f6f95-167">Pointer Conversions</span></span>](pointer-conversions.md)  
- [<span data-ttu-id="f6f95-168">Expressões de ponteiro</span><span class="sxs-lookup"><span data-stu-id="f6f95-168">Pointer Expressions</span></span>](pointer-expressions.md)  
- [<span data-ttu-id="f6f95-169">Tipos</span><span class="sxs-lookup"><span data-stu-id="f6f95-169">Types</span></span>](../../language-reference/keywords/types.md)  
- [<span data-ttu-id="f6f95-170">unsafe</span><span class="sxs-lookup"><span data-stu-id="f6f95-170">unsafe</span></span>](../../language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="f6f95-171">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="f6f95-171">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="f6f95-172">stackalloc</span><span class="sxs-lookup"><span data-stu-id="f6f95-172">stackalloc</span></span>](../../language-reference/keywords/stackalloc.md)  
- [<span data-ttu-id="f6f95-173">Conversões boxing e unboxing</span><span class="sxs-lookup"><span data-stu-id="f6f95-173">Boxing and Unboxing</span></span>](../types/boxing-and-unboxing.md)
