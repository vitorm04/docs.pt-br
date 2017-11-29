---
title: "Como obter o endereço de uma variável (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d0969f7e62864c682660f08cd4198aa4032e0e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="56974-102">Como obter o endereço de uma variável (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="56974-102">How to: Obtain the Address of a Variable (C# Programming Guide)</span></span>
<span data-ttu-id="56974-103">Para obter o endereço de uma expressão unária, que é avaliada como uma variável fixa, use o operador address-of:</span><span class="sxs-lookup"><span data-stu-id="56974-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator:</span></span>  
  
```  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="56974-104">O operador address-of pode ser aplicado somente a uma variável.</span><span class="sxs-lookup"><span data-stu-id="56974-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="56974-105">Se a variável for uma variável móvel, é possível usar a [instrução fixa](../../../csharp/language-reference/keywords/fixed-statement.md) para corrigir temporariamente a variável antes de obter seu endereço.</span><span class="sxs-lookup"><span data-stu-id="56974-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span>  
  
 <span data-ttu-id="56974-106">É sua responsabilidade assegurar que a variável seja inicializada.</span><span class="sxs-lookup"><span data-stu-id="56974-106">It is your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="56974-107">O compilador não emitirá uma mensagem de erro se a variável não for inicializada.</span><span class="sxs-lookup"><span data-stu-id="56974-107">The compiler will not issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="56974-108">Não é possível obter o endereço de uma constante ou um valor.</span><span class="sxs-lookup"><span data-stu-id="56974-108">You cannot get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56974-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="56974-109">Example</span></span>  
 <span data-ttu-id="56974-110">Neste exemplo, um ponteiro para `int`, `p`, é declarado e atribuído ao endereço de uma variável de inteiro, `number`.</span><span class="sxs-lookup"><span data-stu-id="56974-110">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="56974-111">A variável `number` é inicializada como resultado da atribuição a *p.</span><span class="sxs-lookup"><span data-stu-id="56974-111">The variable `number` is initialized as a result of the assignment to *p.</span></span> <span data-ttu-id="56974-112">Se essa instrução de atribuição for transformada em um comentário, a inicialização da variável `number` será removida, mas nenhum erro em tempo de compilação será emitido.</span><span class="sxs-lookup"><span data-stu-id="56974-112">If you make this assignment statement a comment, the initialization of the variable `number` will be removed, but no compile-time error is issued.</span></span> <span data-ttu-id="56974-113">Observe o uso do operador [Acesso a Membro](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) `->` para obter e exibir o endereço armazenado no ponteiro.</span><span class="sxs-lookup"><span data-stu-id="56974-113">Notice the use of the [Member Access](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) operator `->` to obtain and display the address stored in the pointer.</span></span>  
  
 [!code-csharp[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="56974-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56974-114">See Also</span></span>  
 [<span data-ttu-id="56974-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="56974-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="56974-116">Expressões de ponteiro</span><span class="sxs-lookup"><span data-stu-id="56974-116">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="56974-117">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="56974-117">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="56974-118">Tipos</span><span class="sxs-lookup"><span data-stu-id="56974-118">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="56974-119">unsafe</span><span class="sxs-lookup"><span data-stu-id="56974-119">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="56974-120">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="56974-120">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="56974-121">stackalloc</span><span class="sxs-lookup"><span data-stu-id="56974-121">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
