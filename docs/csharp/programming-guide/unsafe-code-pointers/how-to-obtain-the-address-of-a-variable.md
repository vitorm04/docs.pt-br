---
title: "Como obter o endereço de uma variável (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: 19
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
ms.openlocfilehash: 169f68cc80b7a27427a9987942e66e0ba9ed1a02
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="5fb8e-102">Como obter o endereço de uma variável (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="5fb8e-102">How to: Obtain the Address of a Variable (C# Programming Guide)</span></span>
<span data-ttu-id="5fb8e-103">Para obter o endereço de uma expressão unária, que é avaliada como uma variável fixa, use o operador address-of:</span><span class="sxs-lookup"><span data-stu-id="5fb8e-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator:</span></span>  
  
```  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="5fb8e-104">O operador address-of pode ser aplicado somente a uma variável.</span><span class="sxs-lookup"><span data-stu-id="5fb8e-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="5fb8e-105">Se a variável for uma variável móvel, é possível usar a [instrução fixa](../../../csharp/language-reference/keywords/fixed-statement.md) para corrigir temporariamente a variável antes de obter seu endereço.</span><span class="sxs-lookup"><span data-stu-id="5fb8e-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span>  
  
 <span data-ttu-id="5fb8e-106">É sua responsabilidade assegurar que a variável seja inicializada.</span><span class="sxs-lookup"><span data-stu-id="5fb8e-106">It is your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="5fb8e-107">O compilador não emitirá uma mensagem de erro se a variável não for inicializada.</span><span class="sxs-lookup"><span data-stu-id="5fb8e-107">The compiler will not issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="5fb8e-108">Não é possível obter o endereço de uma constante ou um valor.</span><span class="sxs-lookup"><span data-stu-id="5fb8e-108">You cannot get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fb8e-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5fb8e-109">Example</span></span>  
 <span data-ttu-id="5fb8e-110">Neste exemplo, um ponteiro para `int`, `p`, é declarado e atribuído ao endereço de uma variável de inteiro, `number`.</span><span class="sxs-lookup"><span data-stu-id="5fb8e-110">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="5fb8e-111">A variável `number` é inicializada como resultado da atribuição a *p.</span><span class="sxs-lookup"><span data-stu-id="5fb8e-111">The variable `number` is initialized as a result of the assignment to *p.</span></span> <span data-ttu-id="5fb8e-112">Se essa instrução de atribuição for transformada em um comentário, a inicialização da variável `number` será removida, mas nenhum erro em tempo de compilação será emitido.</span><span class="sxs-lookup"><span data-stu-id="5fb8e-112">If you make this assignment statement a comment, the initialization of the variable `number` will be removed, but no compile-time error is issued.</span></span> <span data-ttu-id="5fb8e-113">Observe o uso do operador [Acesso a Membro](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) `->` para obter e exibir o endereço armazenado no ponteiro.</span><span class="sxs-lookup"><span data-stu-id="5fb8e-113">Notice the use of the [Member Access](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) operator `->` to obtain and display the address stored in the pointer.</span></span>  
  
 <span data-ttu-id="5fb8e-114">[!code-cs[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="5fb8e-114">[!code-cs[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_1.cs)]</span></span>  
  
 <span data-ttu-id="5fb8e-115">[!code-cs[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="5fb8e-115">[!code-cs[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fb8e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5fb8e-116">See Also</span></span>  
 <span data-ttu-id="5fb8e-117">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="5fb8e-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="5fb8e-118">[Expressões de Ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="5fb8e-118">[Pointer Expressions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span></span>  
 <span data-ttu-id="5fb8e-119">[Tipos de Ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span><span class="sxs-lookup"><span data-stu-id="5fb8e-119">[Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span></span>  
 <span data-ttu-id="5fb8e-120">[Tipos](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="5fb8e-120">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="5fb8e-121">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="5fb8e-121">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 <span data-ttu-id="5fb8e-122">[Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5fb8e-122">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 [<span data-ttu-id="5fb8e-123">stackalloc</span><span class="sxs-lookup"><span data-stu-id="5fb8e-123">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)

