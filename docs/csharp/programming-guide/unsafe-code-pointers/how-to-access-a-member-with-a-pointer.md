---
title: Como acessar um membro com um ponteiro (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
ms.openlocfilehash: 20f0dd18bb5ca132d05335953958d8f747b6abc4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332196"
---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a><span data-ttu-id="5e986-102">Como acessar um membro com um ponteiro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="5e986-102">How to: Access a Member with a Pointer (C# Programming Guide)</span></span>
<span data-ttu-id="5e986-103">Para acessar um membro de um struct declarado em um contexto não seguro, é possível usar o operador de acesso de membro conforme mostrado no exemplo a seguir, no qual `p` é um ponteiro para um [struct](../../../csharp/language-reference/keywords/struct.md) que contém um membro `x`.</span><span class="sxs-lookup"><span data-stu-id="5e986-103">To access a member of a struct that is declared in an unsafe context, you can use the member access operator as shown in the following example in which `p` is a pointer to a [struct](../../../csharp/language-reference/keywords/struct.md) that contains a member `x`.</span></span>  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a><span data-ttu-id="5e986-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5e986-104">Example</span></span>  
 <span data-ttu-id="5e986-105">Nesse exemplo, um [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, que contém as duas coordenadas `x` e `y` é declarado e instanciado.</span><span class="sxs-lookup"><span data-stu-id="5e986-105">In this example, a [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, that contains the two coordinates `x` and `y` is declared and instantiated.</span></span> <span data-ttu-id="5e986-106">Usando o operador de acesso de membro `->` e um ponteiro para a instância `home`, `x` e `y` são valores atribuídos.</span><span class="sxs-lookup"><span data-stu-id="5e986-106">By using the member access operator `->` and a pointer to the instance `home`, `x` and `y` are assigned values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e986-107">Observe que a expressão `p->x` é equivalente à expressão `(*p).x` e é possível obter o mesmo resultado usando qualquer uma das duas expressões.</span><span class="sxs-lookup"><span data-stu-id="5e986-107">Notice that the expression `p->x` is equivalent to the expression `(*p).x`, and you can obtain the same result by using either of the two expressions.</span></span>  
  
 [!code-csharp[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5e986-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e986-108">See Also</span></span>  
 [<span data-ttu-id="5e986-109">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="5e986-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5e986-110">Expressões de ponteiro</span><span class="sxs-lookup"><span data-stu-id="5e986-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="5e986-111">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="5e986-111">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="5e986-112">Tipos</span><span class="sxs-lookup"><span data-stu-id="5e986-112">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="5e986-113">unsafe</span><span class="sxs-lookup"><span data-stu-id="5e986-113">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="5e986-114">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="5e986-114">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="5e986-115">stackalloc</span><span class="sxs-lookup"><span data-stu-id="5e986-115">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
