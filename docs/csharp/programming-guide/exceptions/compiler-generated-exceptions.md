---
title: Exceções geradas pelo compilador – Guia de Programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 2a6b2c3fa053f1c555856df8098975340e78e2b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705308"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a><span data-ttu-id="b8f62-102">Exceções geradas pelo compilador (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="b8f62-102">Compiler-Generated Exceptions (C# Programming Guide)</span></span>
<span data-ttu-id="b8f62-103">Algumas exceções são geradas automaticamente pelo CLR (Common Language Runtime) do .NET Framework quando as operações básicas falham.</span><span class="sxs-lookup"><span data-stu-id="b8f62-103">Some exceptions are thrown automatically by the .NET Framework's common language runtime (CLR) when basic operations fail.</span></span> <span data-ttu-id="b8f62-104">Essas exceções e suas condições de erro são listadas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="b8f62-104">These exceptions and their error conditions are listed in the following table.</span></span>  
  
|<span data-ttu-id="b8f62-105">Exceção</span><span class="sxs-lookup"><span data-stu-id="b8f62-105">Exception</span></span>|<span data-ttu-id="b8f62-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8f62-106">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|<span data-ttu-id="b8f62-107">Uma classe base para exceções que ocorrem durante operações aritméticas, tais como <xref:System.DivideByZeroException> e <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="b8f62-107">A base class for exceptions that occur during arithmetic operations, such as <xref:System.DivideByZeroException> and <xref:System.OverflowException>.</span></span>|  
|<xref:System.ArrayTypeMismatchException>|<span data-ttu-id="b8f62-108">Gerada quando uma matriz não pode armazenar um determinado elemento porque o tipo real do elemento é incompatível com o tipo real da matriz.</span><span class="sxs-lookup"><span data-stu-id="b8f62-108">Thrown when an array cannot store a given element because the actual type of the element is incompatible with the actual type of the array.</span></span>|  
|<xref:System.DivideByZeroException>|<span data-ttu-id="b8f62-109">Lançada quando é feita uma tentativa de dividir um valor inteiro por zero.</span><span class="sxs-lookup"><span data-stu-id="b8f62-109">Thrown when an attempt is made to divide an integral value by zero.</span></span>|  
|<xref:System.IndexOutOfRangeException>|<span data-ttu-id="b8f62-110">Lançada quando é feita uma tentativa de indexar uma matriz quando o índice é menor que zero ou fora dos limites da matriz.</span><span class="sxs-lookup"><span data-stu-id="b8f62-110">Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.</span></span>|  
|<xref:System.InvalidCastException>|<span data-ttu-id="b8f62-111">Gerada quando uma conversão explícita de um tipo base para uma interface ou um tipo derivado falha em runtime.</span><span class="sxs-lookup"><span data-stu-id="b8f62-111">Thrown when an explicit conversion from a base type to an interface or to a derived type fails at runtime.</span></span>|  
|<xref:System.NullReferenceException>|<span data-ttu-id="b8f62-112">Jogado quando uma tentativa é feita para referenciar um objeto cujo valor é [nulo](../../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="b8f62-112">Thrown when an attempt is made to reference an object whose value is [null](../../language-reference/keywords/null.md).</span></span>|  
|<xref:System.OutOfMemoryException>|<span data-ttu-id="b8f62-113">Lançada quando uma tentativa de alocar memória usando o operador [new](../../language-reference/operators/new-operator.md) falha.</span><span class="sxs-lookup"><span data-stu-id="b8f62-113">Thrown when an attempt to allocate memory using the [new](../../language-reference/operators/new-operator.md) operator fails.</span></span> <span data-ttu-id="b8f62-114">Isso indica que a memória disponível para o Common Language Runtime está esgotada.</span><span class="sxs-lookup"><span data-stu-id="b8f62-114">This indicates that the memory available to the common language runtime has been exhausted.</span></span>|  
|<xref:System.OverflowException>|<span data-ttu-id="b8f62-115">Lançada quando uma operação aritmética em um contexto `checked` estoura.</span><span class="sxs-lookup"><span data-stu-id="b8f62-115">Thrown when an arithmetic operation in a `checked` context overflows.</span></span>|  
|<xref:System.StackOverflowException>|<span data-ttu-id="b8f62-116">Lançada quando a pilha de execução acaba tendo muitas chamadas de método pendentes, normalmente indica uma recursão muito profunda ou infinita.</span><span class="sxs-lookup"><span data-stu-id="b8f62-116">Thrown when the execution stack is exhausted by having too many pending method calls; usually indicates a very deep or infinite recursion.</span></span>|  
|<xref:System.TypeInitializationException>|<span data-ttu-id="b8f62-117">Lançada quando um construtor estático lança uma exceção e não há nenhuma cláusula `catch` compatível para capturá-la.</span><span class="sxs-lookup"><span data-stu-id="b8f62-117">Thrown when a static constructor throws an exception and no compatible `catch` clause exists to catch it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b8f62-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="b8f62-118">See also</span></span>

- [<span data-ttu-id="b8f62-119">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="b8f62-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b8f62-120">Exceções e tratamento de exceções</span><span class="sxs-lookup"><span data-stu-id="b8f62-120">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="b8f62-121">Tratamento de exceção</span><span class="sxs-lookup"><span data-stu-id="b8f62-121">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="b8f62-122">tentar pegar</span><span class="sxs-lookup"><span data-stu-id="b8f62-122">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="b8f62-123">try-finally</span><span class="sxs-lookup"><span data-stu-id="b8f62-123">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="b8f62-124">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="b8f62-124">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
