---
title: volatile (Referência de C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
caps.latest.revision: 29
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1cefa39313c3c551e8d05fbc31e528b86c6888d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="volatile-c-reference"></a><span data-ttu-id="92367-102">volatile (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="92367-102">volatile (C# Reference)</span></span>
<span data-ttu-id="92367-103">A palavra-chave `volatile` indica que um campo pode ser modificado por vários threads que estão em execução ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="92367-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="92367-104">Os campos que são declarados `volatile` não estão sujeitos a otimizações do compilador que assumem o acesso por um único thread.</span><span class="sxs-lookup"><span data-stu-id="92367-104">Fields that are declared `volatile` are not subject to compiler optimizations that assume access by a single thread.</span></span> <span data-ttu-id="92367-105">Isso garante que o valor mais recente esteja presente no campo em todos os momentos.</span><span class="sxs-lookup"><span data-stu-id="92367-105">This ensures that the most up-to-date value is present in the field at all times.</span></span>  
  
 <span data-ttu-id="92367-106">O modificador `volatile` geralmente é usado para um campo que é acessado por vários threads sem usar a instrução [block](../../../csharp/language-reference/keywords/lock-statement.md) para serializar o acesso.</span><span class="sxs-lookup"><span data-stu-id="92367-106">The `volatile` modifier is usually used for a field that is accessed by multiple threads without using the [lock](../../../csharp/language-reference/keywords/lock-statement.md) statement to serialize access.</span></span>  
  
 <span data-ttu-id="92367-107">A palavra-chave `volatile` pode ser aplicada a campos desses tipos:</span><span class="sxs-lookup"><span data-stu-id="92367-107">The `volatile` keyword can be applied to fields of these types:</span></span>  
  
-   <span data-ttu-id="92367-108">Tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="92367-108">Reference types.</span></span>  
  
-   <span data-ttu-id="92367-109">Tipos de ponteiro (em um contexto sem segurança).</span><span class="sxs-lookup"><span data-stu-id="92367-109">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="92367-110">Observe que embora o ponteiro em si possa ser volátil, o objeto para o qual ele aponta não pode.</span><span class="sxs-lookup"><span data-stu-id="92367-110">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="92367-111">Em outras palavras, você não pode declarar um "ponteiro como volátil".</span><span class="sxs-lookup"><span data-stu-id="92367-111">In other words, you cannot declare a "pointer to volatile."</span></span>  
  
-   <span data-ttu-id="92367-112">Tipos como sbyte, byte, short, ushort, int, uint, char, float e bool.</span><span class="sxs-lookup"><span data-stu-id="92367-112">Types such as sbyte, byte, short, ushort, int, uint, char, float, and bool.</span></span>  
  
-   <span data-ttu-id="92367-113">Um tipo de enumeração com um dos seguintes tipos de base: byte, sbyte, short, ushort, int ou uint.</span><span class="sxs-lookup"><span data-stu-id="92367-113">An enum type with one of the following base types: byte, sbyte, short, ushort, int, or uint.</span></span>  
  
-   <span data-ttu-id="92367-114">Parâmetros de tipo genérico conhecidos por serem tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="92367-114">Generic type parameters known to be reference types.</span></span>  
  
-   <span data-ttu-id="92367-115"><xref:System.IntPtr> e <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="92367-115"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>  
  
 <span data-ttu-id="92367-116">A palavra-chave volatile pode ser aplicada apenas a campos de uma classe ou struct.</span><span class="sxs-lookup"><span data-stu-id="92367-116">The volatile keyword can only be applied to fields of a class or struct.</span></span> <span data-ttu-id="92367-117">As variáveis locais não podem ser declaradas como `volatile`.</span><span class="sxs-lookup"><span data-stu-id="92367-117">Local variables cannot be declared `volatile`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92367-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="92367-118">Example</span></span>  
 <span data-ttu-id="92367-119">O exemplo a seguir mostra como declarar uma variável de campo público como `volatile`.</span><span class="sxs-lookup"><span data-stu-id="92367-119">The following example shows how to declare a public field variable as `volatile`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="92367-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="92367-120">Example</span></span>  
 <span data-ttu-id="92367-121">O exemplo a seguir demonstra como um thread de trabalho ou auxiliar pode ser criado e usado para executar o processamento em paralelo com o do thread primário.</span><span class="sxs-lookup"><span data-stu-id="92367-121">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="92367-122">Para obter mais informações sobre multithreading, consulte [Threading](../../../standard/threading/index.md) e [Threading](../../programming-guide/concepts/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="92367-122">For background information about multithreading, see [Threading](../../../standard/threading/index.md) and [Threading](../../programming-guide/concepts/threading/index.md).</span></span>  
  
 [!code-csharp[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="92367-123">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="92367-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="92367-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92367-124">See Also</span></span>  
 [<span data-ttu-id="92367-125">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="92367-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="92367-126">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="92367-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="92367-127">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="92367-127">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="92367-128">Modificadores</span><span class="sxs-lookup"><span data-stu-id="92367-128">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
