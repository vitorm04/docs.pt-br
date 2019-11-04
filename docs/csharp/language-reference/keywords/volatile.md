---
title: volatile – Referência de C#
ms.custom: seodec18
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: e72173ba1b91f03ccb1c15ca6451ac997666bc7f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422123"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="d37ed-102">volatile (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d37ed-102">volatile (C# Reference)</span></span>

<span data-ttu-id="d37ed-103">A palavra-chave `volatile` indica que um campo pode ser modificado por vários threads que estão em execução ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="d37ed-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="d37ed-104">O compilador, o sistema do tempo de execução e até mesmo o hardware podem reorganizar as leituras e gravações para locais de memória por motivos de desempenho.</span><span class="sxs-lookup"><span data-stu-id="d37ed-104">The compiler, the runtime system, and even hardware may rearrange reads and writes to memory locations for performance reasons.</span></span> <span data-ttu-id="d37ed-105">Os campos que são declarados `volatile` não estão sujeitos a essas otimizações.</span><span class="sxs-lookup"><span data-stu-id="d37ed-105">Fields that are declared `volatile` are not subject to these optimizations.</span></span> <span data-ttu-id="d37ed-106">A adição do modificador `volatile` garante que todos os threads observarão gravações voláteis executadas por qualquer outro thread na ordem em que elas foram executadas.</span><span class="sxs-lookup"><span data-stu-id="d37ed-106">Adding the `volatile` modifier ensures that all threads will observe volatile writes performed by any other thread in the order in which they were performed.</span></span> <span data-ttu-id="d37ed-107">Não há nenhuma garantia de uma única ordenação total de gravações voláteis como visto em todos os threads de execução.</span><span class="sxs-lookup"><span data-stu-id="d37ed-107">There is no guarantee of a single total ordering of volatile writes as seen from all threads of execution.</span></span>

<span data-ttu-id="d37ed-108">A palavra-chave `volatile` pode ser aplicada a campos desses tipos:</span><span class="sxs-lookup"><span data-stu-id="d37ed-108">The `volatile` keyword can be applied to fields of these types:</span></span>

- <span data-ttu-id="d37ed-109">Tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="d37ed-109">Reference types.</span></span>
- <span data-ttu-id="d37ed-110">Tipos de ponteiro (em um contexto sem segurança).</span><span class="sxs-lookup"><span data-stu-id="d37ed-110">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="d37ed-111">Observe que embora o ponteiro em si possa ser volátil, o objeto para o qual ele aponta não pode.</span><span class="sxs-lookup"><span data-stu-id="d37ed-111">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="d37ed-112">Em outras palavras, você não pode declarar um "ponteiro como volátil".</span><span class="sxs-lookup"><span data-stu-id="d37ed-112">In other words, you cannot declare a "pointer to volatile."</span></span>
- <span data-ttu-id="d37ed-113">Tipos simples, como `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float` e `bool`.</span><span class="sxs-lookup"><span data-stu-id="d37ed-113">Simple types such as `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`, and `bool`.</span></span>
- <span data-ttu-id="d37ed-114">Um tipo `enum` com um dos seguintes tipos base: `byte`, `sbyte`, `short`, `ushort`, `int` ou `uint`.</span><span class="sxs-lookup"><span data-stu-id="d37ed-114">An `enum` type with one of the following base types: `byte`, `sbyte`, `short`, `ushort`, `int`, or `uint`.</span></span>
- <span data-ttu-id="d37ed-115">Parâmetros de tipo genérico conhecidos por serem tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="d37ed-115">Generic type parameters known to be reference types.</span></span>
- <span data-ttu-id="d37ed-116"><xref:System.IntPtr> e <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="d37ed-116"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>

<span data-ttu-id="d37ed-117">Outros tipos, inclusive `double` e `long`, não podem ser marcados como `volatile`, pois as leituras e gravações nos campos desses tipos não podem ser garantidas como atômicas.</span><span class="sxs-lookup"><span data-stu-id="d37ed-117">Other types, including `double` and `long`, cannot be marked `volatile` because reads and writes to fields of those types cannot be guaranteed to be atomic.</span></span> <span data-ttu-id="d37ed-118">Para proteger o acesso multithreaded a esses tipos de campo, use os membros da classe <xref:System.Threading.Interlocked> ou proteja o acesso usando a instrução [`lock`](lock-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d37ed-118">To protect multi-threaded access to those types of fields, use the <xref:System.Threading.Interlocked> class members or protect access using the [`lock`](lock-statement.md) statement.</span></span>

<span data-ttu-id="d37ed-119">A palavra-chave `volatile` pode ser aplicada somente aos campos de uma `class` ou `struct`.</span><span class="sxs-lookup"><span data-stu-id="d37ed-119">The `volatile` keyword can only be applied to fields of a `class` or `struct`.</span></span> <span data-ttu-id="d37ed-120">As variáveis locais não podem ser declaradas como `volatile`.</span><span class="sxs-lookup"><span data-stu-id="d37ed-120">Local variables cannot be declared `volatile`.</span></span>

## <a name="example"></a><span data-ttu-id="d37ed-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d37ed-121">Example</span></span>

<span data-ttu-id="d37ed-122">O exemplo a seguir mostra como declarar uma variável de campo público como `volatile`.</span><span class="sxs-lookup"><span data-stu-id="d37ed-122">The following example shows how to declare a public field variable as `volatile`.</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

<span data-ttu-id="d37ed-123">O exemplo a seguir demonstra como um thread de trabalho ou auxiliar pode ser criado e usado para executar o processamento em paralelo com o do thread primário.</span><span class="sxs-lookup"><span data-stu-id="d37ed-123">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="d37ed-124">Para saber mais sobre multithreading, confira [Threading gerenciado](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="d37ed-124">For more information about multithreading, see [Managed Threading](../../../standard/threading/index.md).</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

<span data-ttu-id="d37ed-125">Com o modificador `volatile` adicionado à declaração de `_shouldStop` definida, você sempre obterá os mesmos resultados (semelhante ao trecho mostrado no código anterior).</span><span class="sxs-lookup"><span data-stu-id="d37ed-125">With the `volatile` modifier added to the declaration of `_shouldStop` in place, you'll always get the same results (similar to the excerpt shown in the preceding code).</span></span> <span data-ttu-id="d37ed-126">No entanto, sem esse modificador no membro `_shouldStop`, o comportamento é imprevisível.</span><span class="sxs-lookup"><span data-stu-id="d37ed-126">However, without that modifier on the `_shouldStop` member, the behavior is unpredictable.</span></span> <span data-ttu-id="d37ed-127">O método `DoWork` pode otimizar o acesso do membro, resultando na leitura de dados obsoletos.</span><span class="sxs-lookup"><span data-stu-id="d37ed-127">The `DoWork` method may optimize the member access, resulting in reading stale data.</span></span> <span data-ttu-id="d37ed-128">Devido à natureza da programação multithreaded, o número de leituras obsoletas é imprevisível.</span><span class="sxs-lookup"><span data-stu-id="d37ed-128">Because of the nature of multi-threaded programming, the number of stale reads is unpredictable.</span></span> <span data-ttu-id="d37ed-129">Diferentes execuções do programa produzirão resultados um pouco diferentes.</span><span class="sxs-lookup"><span data-stu-id="d37ed-129">Different runs of the program will produce somewhat different results.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d37ed-130">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d37ed-130">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d37ed-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d37ed-131">See also</span></span>

- [<span data-ttu-id="d37ed-132">Especificação da linguagem C#: palavra-chave volatile</span><span class="sxs-lookup"><span data-stu-id="d37ed-132">C# language specification: volatile keyword</span></span>](../../../../_csharplang/spec/classes.md#volatile-fields)
- [<span data-ttu-id="d37ed-133">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d37ed-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d37ed-134">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d37ed-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d37ed-135">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="d37ed-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d37ed-136">Modificadores</span><span class="sxs-lookup"><span data-stu-id="d37ed-136">Modifiers</span></span>](index.md)
- [<span data-ttu-id="d37ed-137">Instrução lock</span><span class="sxs-lookup"><span data-stu-id="d37ed-137">lock statement</span></span>](lock-statement.md)
- <xref:System.Threading.Interlocked>
