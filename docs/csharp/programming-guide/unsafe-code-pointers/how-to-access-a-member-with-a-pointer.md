---
title: Como acessar um membro com um ponteiro (Guia de programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
ms.openlocfilehash: b51239be8da8c45aa2d7f1ff0700884c43c07299
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130833"
---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a><span data-ttu-id="51e5c-102">Como acessar um membro com um ponteiro (Guia de programação em C#)</span><span class="sxs-lookup"><span data-stu-id="51e5c-102">How to: access a member with a pointer (C# Programming Guide)</span></span>
<span data-ttu-id="51e5c-103">Para acessar um membro de um struct declarado em um contexto não seguro, é possível usar o operador de acesso de membro conforme mostrado no exemplo a seguir, no qual `p` é um ponteiro para um [struct](../../../csharp/language-reference/keywords/struct.md) que contém um membro `x`.</span><span class="sxs-lookup"><span data-stu-id="51e5c-103">To access a member of a struct that is declared in an unsafe context, you can use the member access operator as shown in the following example in which `p` is a pointer to a [struct](../../../csharp/language-reference/keywords/struct.md) that contains a member `x`.</span></span>  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a><span data-ttu-id="51e5c-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="51e5c-104">Example</span></span>  
 <span data-ttu-id="51e5c-105">Nesse exemplo, um [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, que contém as duas coordenadas `x` e `y` é declarado e instanciado.</span><span class="sxs-lookup"><span data-stu-id="51e5c-105">In this example, a [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, that contains the two coordinates `x` and `y` is declared and instantiated.</span></span> <span data-ttu-id="51e5c-106">Usando o operador de acesso de membro `->` e um ponteiro para a instância `home`, `x` e `y` são valores atribuídos.</span><span class="sxs-lookup"><span data-stu-id="51e5c-106">By using the member access operator `->` and a pointer to the instance `home`, `x` and `y` are assigned values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51e5c-107">Observe que a expressão `p->x` é equivalente à expressão `(*p).x` e é possível obter o mesmo resultado usando qualquer uma das duas expressões.</span><span class="sxs-lookup"><span data-stu-id="51e5c-107">Notice that the expression `p->x` is equivalent to the expression `(*p).x`, and you can obtain the same result by using either of the two expressions.</span></span>  
  
 [!code-csharp[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="51e5c-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51e5c-108">See Also</span></span>

- [<span data-ttu-id="51e5c-109">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="51e5c-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="51e5c-110">Expressões de ponteiro</span><span class="sxs-lookup"><span data-stu-id="51e5c-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="51e5c-111">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="51e5c-111">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="51e5c-112">Tipos</span><span class="sxs-lookup"><span data-stu-id="51e5c-112">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="51e5c-113">unsafe</span><span class="sxs-lookup"><span data-stu-id="51e5c-113">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="51e5c-114">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="51e5c-114">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="51e5c-115">stackalloc</span><span class="sxs-lookup"><span data-stu-id="51e5c-115">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
