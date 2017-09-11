---
title: "volatile (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- volatile_CSharpKeyword
- volatile
dev_langs:
- CSharp
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
caps.latest.revision: 29
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c8f9fba15991197be885a973435089098a57db87
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="volatile-c-reference"></a><span data-ttu-id="013e5-102">volatile (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="013e5-102">volatile (C# Reference)</span></span>
<span data-ttu-id="013e5-103">A palavra-chave `volatile` indica que um campo pode ser modificado por vários threads que estão em execução ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="013e5-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="013e5-104">Os campos que são declarados `volatile` não estão sujeitos a otimizações do compilador que assumem o acesso por um único thread.</span><span class="sxs-lookup"><span data-stu-id="013e5-104">Fields that are declared `volatile` are not subject to compiler optimizations that assume access by a single thread.</span></span> <span data-ttu-id="013e5-105">Isso garante que o valor mais recente esteja presente no campo em todos os momentos.</span><span class="sxs-lookup"><span data-stu-id="013e5-105">This ensures that the most up-to-date value is present in the field at all times.</span></span>  
  
 <span data-ttu-id="013e5-106">O modificador `volatile` geralmente é usado para um campo que é acessado por vários threads sem usar a instrução [block](../../../csharp/language-reference/keywords/lock-statement.md) para serializar o acesso.</span><span class="sxs-lookup"><span data-stu-id="013e5-106">The `volatile` modifier is usually used for a field that is accessed by multiple threads without using the [lock](../../../csharp/language-reference/keywords/lock-statement.md) statement to serialize access.</span></span>  
  
 <span data-ttu-id="013e5-107">A palavra-chave `volatile` pode ser aplicada a campos desses tipos:</span><span class="sxs-lookup"><span data-stu-id="013e5-107">The `volatile` keyword can be applied to fields of these types:</span></span>  
  
-   <span data-ttu-id="013e5-108">Tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="013e5-108">Reference types.</span></span>  
  
-   <span data-ttu-id="013e5-109">Tipos de ponteiro (em um contexto sem segurança).</span><span class="sxs-lookup"><span data-stu-id="013e5-109">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="013e5-110">Observe que embora o ponteiro em si possa ser volátil, o objeto para o qual ele aponta não pode.</span><span class="sxs-lookup"><span data-stu-id="013e5-110">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="013e5-111">Em outras palavras, você não pode declarar um "ponteiro como volátil".</span><span class="sxs-lookup"><span data-stu-id="013e5-111">In other words, you cannot declare a "pointer to volatile."</span></span>  
  
-   <span data-ttu-id="013e5-112">Tipos como sbyte, byte, short, ushort, int, uint, char, float e bool.</span><span class="sxs-lookup"><span data-stu-id="013e5-112">Types such as sbyte, byte, short, ushort, int, uint, char, float, and bool.</span></span>  
  
-   <span data-ttu-id="013e5-113">Um tipo de enumeração com um dos seguintes tipos de base: byte, sbyte, short, ushort, int ou uint.</span><span class="sxs-lookup"><span data-stu-id="013e5-113">An enum type with one of the following base types: byte, sbyte, short, ushort, int, or uint.</span></span>  
  
-   <span data-ttu-id="013e5-114">Parâmetros de tipo genérico conhecidos por serem tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="013e5-114">Generic type parameters known to be reference types.</span></span>  
  
-   <span data-ttu-id="013e5-115"><xref:System.IntPtr> e <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="013e5-115"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>  
  
 <span data-ttu-id="013e5-116">A palavra-chave volatile pode ser aplicada apenas a campos de uma classe ou struct.</span><span class="sxs-lookup"><span data-stu-id="013e5-116">The volatile keyword can only be applied to fields of a class or struct.</span></span> <span data-ttu-id="013e5-117">As variáveis locais não podem ser declaradas como `volatile`.</span><span class="sxs-lookup"><span data-stu-id="013e5-117">Local variables cannot be declared `volatile`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="013e5-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="013e5-118">Example</span></span>  
 <span data-ttu-id="013e5-119">O exemplo a seguir mostra como declarar uma variável de campo público como `volatile`.</span><span class="sxs-lookup"><span data-stu-id="013e5-119">The following example shows how to declare a public field variable as `volatile`.</span></span>  
  
 <span data-ttu-id="013e5-120">[!code-cs[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="013e5-120">[!code-cs[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="013e5-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="013e5-121">Example</span></span>  
 <span data-ttu-id="013e5-122">O exemplo a seguir demonstra como um thread de trabalho ou auxiliar pode ser criado e usado para executar o processamento em paralelo com o do thread primário.</span><span class="sxs-lookup"><span data-stu-id="013e5-122">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="013e5-123">Para obter mais informações sobre multithreading, consulte [Threading](../../../standard/threading/index.md) e [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span><span class="sxs-lookup"><span data-stu-id="013e5-123">For background information about multithreading, see [Threading](../../../standard/threading/index.md) and [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span></span>  
  
 <span data-ttu-id="013e5-124">[!code-cs[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="013e5-124">[!code-cs[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="013e5-125">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="013e5-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="013e5-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="013e5-126">See Also</span></span>  
 <span data-ttu-id="013e5-127">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="013e5-127">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="013e5-128">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="013e5-128">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="013e5-129">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="013e5-129">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 [<span data-ttu-id="013e5-130">Modificadores</span><span class="sxs-lookup"><span data-stu-id="013e5-130">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)

