---
title: volatile (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: 64bd5ce7d7dfe3265c3c645467493ab7d8792172
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37936872"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="b5a5a-102">volatile (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b5a5a-102">volatile (C# Reference)</span></span>
<span data-ttu-id="b5a5a-103">A palavra-chave `volatile` indica que um campo pode ser modificado por vários threads que estão em execução ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="b5a5a-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="b5a5a-104">Os campos que são declarados `volatile` não estão sujeitos a otimizações do compilador que assumem o acesso por um único thread.</span><span class="sxs-lookup"><span data-stu-id="b5a5a-104">Fields that are declared `volatile` are not subject to compiler optimizations that assume access by a single thread.</span></span> <span data-ttu-id="b5a5a-105">Essas restrições garantem que todos os threads observem as gravações voláteis executadas por qualquer outro thread na ordem em que elas foram realizadas.</span><span class="sxs-lookup"><span data-stu-id="b5a5a-105">These restrictions ensure that all threads will observe volatile writes performed by any other thread in the order in which they were performed.</span></span> <span data-ttu-id="b5a5a-106">Não há nenhuma garantia de uma única ordenação total de gravações voláteis como visto em todos os threads de execução.</span><span class="sxs-lookup"><span data-stu-id="b5a5a-106">There is no guarantee of a single total ordering of volatile writes as seen from all threads of execution.</span></span>  
  
 <span data-ttu-id="b5a5a-107">O modificador `volatile` geralmente é usado para um campo que é acessado por vários threads sem usar a instrução [block](../../../csharp/language-reference/keywords/lock-statement.md) para serializar o acesso.</span><span class="sxs-lookup"><span data-stu-id="b5a5a-107">The `volatile` modifier is usually used for a field that is accessed by multiple threads without using the [lock](../../../csharp/language-reference/keywords/lock-statement.md) statement to serialize access.</span></span>  
  
 <span data-ttu-id="b5a5a-108">A palavra-chave `volatile` pode ser aplicada a campos desses tipos:</span><span class="sxs-lookup"><span data-stu-id="b5a5a-108">The `volatile` keyword can be applied to fields of these types:</span></span>  
  
-   <span data-ttu-id="b5a5a-109">Tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="b5a5a-109">Reference types.</span></span>  
  
-   <span data-ttu-id="b5a5a-110">Tipos de ponteiro (em um contexto sem segurança).</span><span class="sxs-lookup"><span data-stu-id="b5a5a-110">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="b5a5a-111">Observe que embora o ponteiro em si possa ser volátil, o objeto para o qual ele aponta não pode.</span><span class="sxs-lookup"><span data-stu-id="b5a5a-111">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="b5a5a-112">Em outras palavras, você não pode declarar um "ponteiro como volátil".</span><span class="sxs-lookup"><span data-stu-id="b5a5a-112">In other words, you cannot declare a "pointer to volatile."</span></span>  
  
-   <span data-ttu-id="b5a5a-113">Tipos como sbyte, byte, short, ushort, int, uint, char, float e bool.</span><span class="sxs-lookup"><span data-stu-id="b5a5a-113">Types such as sbyte, byte, short, ushort, int, uint, char, float, and bool.</span></span>  
  
-   <span data-ttu-id="b5a5a-114">Um tipo de enumeração com um dos seguintes tipos de base: byte, sbyte, short, ushort, int ou uint.</span><span class="sxs-lookup"><span data-stu-id="b5a5a-114">An enum type with one of the following base types: byte, sbyte, short, ushort, int, or uint.</span></span>  
  
-   <span data-ttu-id="b5a5a-115">Parâmetros de tipo genérico conhecidos por serem tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="b5a5a-115">Generic type parameters known to be reference types.</span></span>  
  
-   <span data-ttu-id="b5a5a-116"><xref:System.IntPtr> e <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="b5a5a-116"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>  
  
 <span data-ttu-id="b5a5a-117">A palavra-chave volatile pode ser aplicada apenas a campos de uma classe ou struct.</span><span class="sxs-lookup"><span data-stu-id="b5a5a-117">The volatile keyword can only be applied to fields of a class or struct.</span></span> <span data-ttu-id="b5a5a-118">As variáveis locais não podem ser declaradas como `volatile`.</span><span class="sxs-lookup"><span data-stu-id="b5a5a-118">Local variables cannot be declared `volatile`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5a5a-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b5a5a-119">Example</span></span>  
 <span data-ttu-id="b5a5a-120">O exemplo a seguir mostra como declarar uma variável de campo público como `volatile`.</span><span class="sxs-lookup"><span data-stu-id="b5a5a-120">The following example shows how to declare a public field variable as `volatile`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="b5a5a-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b5a5a-121">Example</span></span>  
 <span data-ttu-id="b5a5a-122">O exemplo a seguir demonstra como um thread de trabalho ou auxiliar pode ser criado e usado para executar o processamento em paralelo com o do thread primário.</span><span class="sxs-lookup"><span data-stu-id="b5a5a-122">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="b5a5a-123">Para obter informações detalhadas sobre multithreading, confira [Threading gerenciado](../../../standard/threading/index.md) e [Threading (C#)](../../programming-guide/concepts/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="b5a5a-123">For background information about multithreading, see [Managed Threading](../../../standard/threading/index.md) and [Threading (C#)](../../programming-guide/concepts/threading/index.md).</span></span>  
  
 [!code-csharp[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="b5a5a-124">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b5a5a-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b5a5a-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5a5a-125">See Also</span></span>  
 [<span data-ttu-id="b5a5a-126">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="b5a5a-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b5a5a-127">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b5a5a-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b5a5a-128">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="b5a5a-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="b5a5a-129">Modificadores</span><span class="sxs-lookup"><span data-stu-id="b5a5a-129">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
