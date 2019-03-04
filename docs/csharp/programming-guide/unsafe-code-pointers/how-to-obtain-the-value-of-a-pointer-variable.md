---
title: Como obter o valor de uma variável de ponteiro – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: 288d8cb2d286f55cc9a162614d45ef7b298f79f1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974478"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a><span data-ttu-id="95677-102">Como obter o valor de uma variável de ponteiro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="95677-102">How to: obtain the value of a pointer variable (C# Programming Guide)</span></span>

<span data-ttu-id="95677-103">Use o operador de indireção de ponteiro para obter a variável no local apontado por um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="95677-103">Use the pointer indirection operator to obtain the variable at the location pointed to by a pointer.</span></span> <span data-ttu-id="95677-104">A expressão usa o seguinte formato, em que `p` é um tipo de ponteiro:</span><span class="sxs-lookup"><span data-stu-id="95677-104">The expression takes the following form, where `p` is a pointer type:</span></span>  

```csharp
*p;  
```

<span data-ttu-id="95677-105">Não é possível utilizar o operador de indireção unário em uma expressão de qualquer tipo diferente do tipo de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="95677-105">You cannot use the unary indirection operator on an expression of any type other than the pointer type.</span></span> <span data-ttu-id="95677-106">Além disso, não é possível aplicá-lo a um ponteiro [void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="95677-106">Also, you cannot apply it to a [void](../../../csharp/language-reference/keywords/void.md) pointer.</span></span>  

<span data-ttu-id="95677-107">Ao aplicar o operador de indireção a um ponteiro [nulo](../../../csharp/language-reference/keywords/null.md), o resultado dependerá da implementação.</span><span class="sxs-lookup"><span data-stu-id="95677-107">When you apply the indirection operator to a [null](../../../csharp/language-reference/keywords/null.md) pointer, the result depends on the implementation.</span></span>  

## <a name="example"></a><span data-ttu-id="95677-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95677-108">Example</span></span>

<span data-ttu-id="95677-109">No exemplo a seguir, uma variável do tipo `char` é acessada usando ponteiros de tipos diferentes.</span><span class="sxs-lookup"><span data-stu-id="95677-109">In the following example, a variable of the type `char` is accessed by using pointers of different types.</span></span> <span data-ttu-id="95677-110">Observe que o endereço do `theChar` variará de execução em execução, pois o endereço físico alocado a uma variável pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="95677-110">Note that the address of `theChar` will vary from run to run, because the physical address allocated to a variable can change.</span></span>  

 [!code-csharp[csProgGuidePointers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#5)]  

 [!code-csharp[csProgGuidePointers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#6)]  
  
<span data-ttu-id="95677-111">**Valor de theChar = Z**</span><span class="sxs-lookup"><span data-stu-id="95677-111">**Value of theChar = Z**</span></span>  
<span data-ttu-id="95677-112">**Endereço de theChar = 12F718**</span><span class="sxs-lookup"><span data-stu-id="95677-112">**Address of theChar = 12F718**</span></span>  
<span data-ttu-id="95677-113">**Valor de pChar = Z**</span><span class="sxs-lookup"><span data-stu-id="95677-113">**Value of pChar = Z**</span></span>  
<span data-ttu-id="95677-114">**Valor de pInt = 90**</span><span class="sxs-lookup"><span data-stu-id="95677-114">**Value of pInt = 90**</span></span>  

## <a name="see-also"></a><span data-ttu-id="95677-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95677-115">See also</span></span>

- [<span data-ttu-id="95677-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="95677-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="95677-117">Expressões de ponteiro</span><span class="sxs-lookup"><span data-stu-id="95677-117">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="95677-118">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="95677-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="95677-119">Tipos</span><span class="sxs-lookup"><span data-stu-id="95677-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="95677-120">unsafe</span><span class="sxs-lookup"><span data-stu-id="95677-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="95677-121">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="95677-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="95677-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="95677-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
