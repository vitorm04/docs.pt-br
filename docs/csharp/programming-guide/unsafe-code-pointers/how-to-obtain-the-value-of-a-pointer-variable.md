---
title: "Como obter o valor de uma variável de ponteiro (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8065c10bec737789f13dcbafe147b50eedb9da36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a><span data-ttu-id="f0008-102">Como obter o valor de uma variável de ponteiro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="f0008-102">How to: Obtain the Value of a Pointer Variable (C# Programming Guide)</span></span>
<span data-ttu-id="f0008-103">Use o operador de indireção de ponteiro para obter a variável no local apontado por um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="f0008-103">Use the pointer indirection operator to obtain the variable at the location pointed to by a pointer.</span></span> <span data-ttu-id="f0008-104">A expressão usa o seguinte formato, em que `p` é um tipo de ponteiro:</span><span class="sxs-lookup"><span data-stu-id="f0008-104">The expression takes the following form, where `p` is a pointer type:</span></span>  
  
```  
*p;  
```  
  
 <span data-ttu-id="f0008-105">Não é possível utilizar o operador de indireção unário em uma expressão de qualquer tipo diferente do tipo de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="f0008-105">You cannot use the unary indirection operator on an expression of any type other than the pointer type.</span></span> <span data-ttu-id="f0008-106">Além disso, não é possível aplicá-lo a um ponteiro [void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="f0008-106">Also, you cannot apply it to a [void](../../../csharp/language-reference/keywords/void.md) pointer.</span></span>  
  
 <span data-ttu-id="f0008-107">Ao aplicar o operador de indireção a um ponteiro [nulo](../../../csharp/language-reference/keywords/null.md), o resultado dependerá da implementação.</span><span class="sxs-lookup"><span data-stu-id="f0008-107">When you apply the indirection operator to a [null](../../../csharp/language-reference/keywords/null.md) pointer, the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0008-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f0008-108">Example</span></span>  
 <span data-ttu-id="f0008-109">No exemplo a seguir, uma variável do tipo `char` é acessada usando ponteiros de tipos diferentes.</span><span class="sxs-lookup"><span data-stu-id="f0008-109">In the following example, a variable of the type `char` is accessed by using pointers of different types.</span></span> <span data-ttu-id="f0008-110">Observe que o endereço do `theChar` variará de execução em execução, pois o endereço físico alocado a uma variável pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="f0008-110">Note that the address of `theChar` will vary from run to run, because the physical address allocated to a variable can change.</span></span>  
  
 [!code-csharp[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
 <span data-ttu-id="f0008-111">**Valor de theChar = Z**</span><span class="sxs-lookup"><span data-stu-id="f0008-111">**Value of theChar = Z**</span></span>  
<span data-ttu-id="f0008-112">**Endereço de theChar = 12F718**</span><span class="sxs-lookup"><span data-stu-id="f0008-112">**Address of theChar = 12F718**</span></span>  
<span data-ttu-id="f0008-113">**Valor de pChar = Z** </span><span class="sxs-lookup"><span data-stu-id="f0008-113">**Value of pChar = Z** </span></span>  
<span data-ttu-id="f0008-114">**Valor de pInt = 90**</span><span class="sxs-lookup"><span data-stu-id="f0008-114">**Value of pInt = 90**</span></span>    
## <a name="see-also"></a><span data-ttu-id="f0008-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0008-115">See Also</span></span>  
 [<span data-ttu-id="f0008-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="f0008-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f0008-117">Expressões de ponteiro</span><span class="sxs-lookup"><span data-stu-id="f0008-117">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="f0008-118">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="f0008-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="f0008-119">Tipos</span><span class="sxs-lookup"><span data-stu-id="f0008-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="f0008-120">unsafe</span><span class="sxs-lookup"><span data-stu-id="f0008-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="f0008-121">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="f0008-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="f0008-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="f0008-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
