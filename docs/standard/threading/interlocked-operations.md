---
title: "Operações interconectadas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Interlocked class, about Interlocked class
- threading [.NET Framework], Interlocked class
ms.assetid: cbda7114-c752-4f3e-ada1-b1e8dd262f2b
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 122058b7e826e27fe6c60c5b07610f7c63e64f78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="interlocked-operations"></a><span data-ttu-id="5be93-102">Operações interconectadas</span><span class="sxs-lookup"><span data-stu-id="5be93-102">Interlocked Operations</span></span>
<span data-ttu-id="5be93-103">O <xref:System.Threading.Interlocked> classe fornece métodos que sincronizam o acesso a uma variável que é compartilhada por vários threads.</span><span class="sxs-lookup"><span data-stu-id="5be93-103">The <xref:System.Threading.Interlocked> class provides methods that synchronize access to a variable that is shared by multiple threads.</span></span> <span data-ttu-id="5be93-104">Os threads de processos diferentes podem usar esse mecanismo se a variável estiver na memória compartilhada.</span><span class="sxs-lookup"><span data-stu-id="5be93-104">The threads of different processes can use this mechanism if the variable is in shared memory.</span></span> <span data-ttu-id="5be93-105">Operações interconectadas são atômicas — ou seja, toda a operação é uma unidade que não pode ser interrompida por outra operação sincronizada na mesma variável.</span><span class="sxs-lookup"><span data-stu-id="5be93-105">Interlocked operations are atomic — that is, the entire operation is a unit that cannot be interrupted by another interlocked operation on the same variable.</span></span> <span data-ttu-id="5be93-106">Isso é importante em sistemas de operacionais com preemptivo multithreading, onde um thread pode ser suspenso após o carregamento de um valor de um endereço de memória, mas antes de ter a chance de alterá-lo e armazená-lo.</span><span class="sxs-lookup"><span data-stu-id="5be93-106">This is important in operating systems with preemptive multithreading, where a thread can be suspended after loading a value from a memory address, but before having the chance to alter it and store it.</span></span>  
  
 <span data-ttu-id="5be93-107">O <xref:System.Threading.Interlocked> classe fornece as seguintes operações:</span><span class="sxs-lookup"><span data-stu-id="5be93-107">The <xref:System.Threading.Interlocked> class provides the following operations:</span></span>  
  
-   <span data-ttu-id="5be93-108">No .NET Framework versão 2.0, o <xref:System.Threading.Interlocked.Add%2A> método adiciona um valor inteiro para uma variável e retorna o novo valor da variável.</span><span class="sxs-lookup"><span data-stu-id="5be93-108">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.Add%2A> method adds an integer value to a variable and returns the new value of the variable.</span></span>  
  
-   <span data-ttu-id="5be93-109">No .NET Framework versão 2.0, o <xref:System.Threading.Interlocked.Read%2A> método lê um valor inteiro de 64 bits, como uma operação atômica.</span><span class="sxs-lookup"><span data-stu-id="5be93-109">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.Read%2A> method reads a 64-bit integer value as an atomic operation.</span></span> <span data-ttu-id="5be93-110">Isso é útil em sistemas operacionais de 32 bits, onde a leitura de um inteiro de 64 bits não é normalmente uma operação atômica.</span><span class="sxs-lookup"><span data-stu-id="5be93-110">This is useful on 32-bit operating systems, where reading a 64-bit integer is not ordinarily an atomic operation.</span></span>  
  
-   <span data-ttu-id="5be93-111">O <xref:System.Threading.Interlocked.Increment%2A> e <xref:System.Threading.Interlocked.Decrement%2A> métodos incrementar ou decrementar uma variável e retornar o valor resultante.</span><span class="sxs-lookup"><span data-stu-id="5be93-111">The <xref:System.Threading.Interlocked.Increment%2A> and <xref:System.Threading.Interlocked.Decrement%2A> methods increment or decrement a variable and return the resulting value.</span></span>  
  
-   <span data-ttu-id="5be93-112">O <xref:System.Threading.Interlocked.Exchange%2A> método executa uma troca atômica do valor em uma variável especificada, retornando o valor e substituí-lo com um novo valor.</span><span class="sxs-lookup"><span data-stu-id="5be93-112">The <xref:System.Threading.Interlocked.Exchange%2A> method performs an atomic exchange of the value in a specified variable, returning that value and replacing it with a new value.</span></span> <span data-ttu-id="5be93-113">No .NET Framework versão 2.0, uma sobrecarga desse método genérica pode ser usada para realizar essa troca em uma variável de qualquer tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="5be93-113">In the .NET Framework version 2.0, a generic overload of this method can be used to perform this exchange on a variable of any reference type.</span></span> <span data-ttu-id="5be93-114">Consulte <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>.</span><span class="sxs-lookup"><span data-stu-id="5be93-114">See <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>.</span></span>  
  
-   <span data-ttu-id="5be93-115">O <xref:System.Threading.Interlocked.CompareExchange%2A> método também troca dois valores, mas contingente no resultado de uma comparação.</span><span class="sxs-lookup"><span data-stu-id="5be93-115">The <xref:System.Threading.Interlocked.CompareExchange%2A> method also exchanges two values, but contingent on the result of a comparison.</span></span> <span data-ttu-id="5be93-116">No .NET Framework versão 2.0, uma sobrecarga desse método genérica pode ser usada para realizar essa troca em uma variável de qualquer tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="5be93-116">In the .NET Framework version 2.0, a generic overload of this method can be used to perform this exchange on a variable of any reference type.</span></span> <span data-ttu-id="5be93-117">Consulte <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>.</span><span class="sxs-lookup"><span data-stu-id="5be93-117">See <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>.</span></span>  
  
 <span data-ttu-id="5be93-118">Processadores modernos, os métodos do <xref:System.Threading.Interlocked> classe geralmente pode ser implementada por uma única instrução.</span><span class="sxs-lookup"><span data-stu-id="5be93-118">On modern processors, the methods of the <xref:System.Threading.Interlocked> class can often be implemented by a single instruction.</span></span> <span data-ttu-id="5be93-119">Portanto, eles fornecem sincronização de alto desempenho e pode ser usados para criar mecanismos de sincronização de nível superior, como bloqueios de rotação.</span><span class="sxs-lookup"><span data-stu-id="5be93-119">Thus, they provide very high-performance synchronization and can be used to build higher-level synchronization mechanisms, like spin locks.</span></span>  
  
 <span data-ttu-id="5be93-120">Para obter um exemplo que usa o <xref:System.Threading.Monitor> e <xref:System.Threading.Interlocked> classes de combinação, consulte [monitores](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span><span class="sxs-lookup"><span data-stu-id="5be93-120">For an example that uses the <xref:System.Threading.Monitor> and <xref:System.Threading.Interlocked> classes in combination, see [Monitors](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span></span>  
  
## <a name="compareexchange-example"></a><span data-ttu-id="5be93-121">Exemplo de CompareExchange</span><span class="sxs-lookup"><span data-stu-id="5be93-121">CompareExchange Example</span></span>  
 <span data-ttu-id="5be93-122">O <xref:System.Threading.Interlocked.CompareExchange%2A> método pode ser usado para proteger os cálculos que são mais complicados do que simples incremento e decremento.</span><span class="sxs-lookup"><span data-stu-id="5be93-122">The <xref:System.Threading.Interlocked.CompareExchange%2A> method can be used to protect computations that are more complicated than simple increment and decrement.</span></span> <span data-ttu-id="5be93-123">O exemplo a seguir demonstra um método de thread-safe que adiciona a um total de execução armazenado como um flutuante número de ponto.</span><span class="sxs-lookup"><span data-stu-id="5be93-123">The following example demonstrates a thread-safe method that adds to a running total stored as a floating point number.</span></span> <span data-ttu-id="5be93-124">(Para inteiros, o <xref:System.Threading.Interlocked.Add%2A> método é uma solução mais simples.) Para obter exemplos de código completo, consulte as sobrecargas de <xref:System.Threading.Interlocked.CompareExchange%2A> que recebem argumentos de ponto flutuantes de precisão simples e precisão dupla (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> e <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).</span><span class="sxs-lookup"><span data-stu-id="5be93-124">(For integers, the <xref:System.Threading.Interlocked.Add%2A> method is a simpler solution.) For complete code examples, see the overloads of <xref:System.Threading.Interlocked.CompareExchange%2A> that take single-precision and double-precision floating-point arguments (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> and <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).</span></span>  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## <a name="untyped-overloads-of-exchange-and-compareexchange"></a><span data-ttu-id="5be93-125">Sem tipo sobrecargas do Exchange e CompareExchange</span><span class="sxs-lookup"><span data-stu-id="5be93-125">Untyped Overloads of Exchange and CompareExchange</span></span>  
 <span data-ttu-id="5be93-126">O <xref:System.Threading.Interlocked.Exchange%2A> e <xref:System.Threading.Interlocked.CompareExchange%2A> métodos têm sobrecargas que usam argumentos de tipo <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="5be93-126">The <xref:System.Threading.Interlocked.Exchange%2A> and <xref:System.Threading.Interlocked.CompareExchange%2A> methods have overloads that take arguments of type <xref:System.Object>.</span></span> <span data-ttu-id="5be93-127">É o primeiro argumento de cada essas sobrecargas `ref Object` (`ByRef … As Object` no Visual Basic), e segurança de tipo requer que a variável passada para este argumento para ser digitado estritamente como <xref:System.Object>; você simplesmente não é possível converter o primeiro argumento para o tipo <xref:System.Object> ao chamar esses métodos.</span><span class="sxs-lookup"><span data-stu-id="5be93-127">The first argument of each of these overloads is `ref Object` (`ByRef … As Object` in Visual Basic), and type safety requires the variable passed to this argument to be typed strictly as <xref:System.Object>; you cannot simply cast the first argument to type <xref:System.Object> when calling these methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5be93-128">No .NET Framework versão 2.0, use as sobrecargas genéricas do <xref:System.Threading.Interlocked.Exchange%2A> e <xref:System.Threading.Interlocked.CompareExchange%2A> métodos para trocar fortemente tipados variáveis.</span><span class="sxs-lookup"><span data-stu-id="5be93-128">In the .NET Framework version 2.0, use the generic overloads of the <xref:System.Threading.Interlocked.Exchange%2A> and <xref:System.Threading.Interlocked.CompareExchange%2A> methods to exchange strongly typed variables.</span></span>  
  
 <span data-ttu-id="5be93-129">O exemplo de código a seguir mostra uma propriedade do tipo `ClassA` que pode ser definida apenas uma vez, como ele pode ser implementado no .NET Framework versão 1.0 ou 1.1.</span><span class="sxs-lookup"><span data-stu-id="5be93-129">The following code example shows a property of type `ClassA` that can be set only once, as it might be implemented in the .NET Framework version 1.0 or 1.1.</span></span>  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5be93-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5be93-130">See Also</span></span>  
 <xref:System.Threading.Interlocked>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="5be93-131">Threading</span><span class="sxs-lookup"><span data-stu-id="5be93-131">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="5be93-132">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="5be93-132">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
