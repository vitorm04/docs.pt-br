---
title: "Como incrementar e diminuir ponteiros (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
caps.latest.revision: 20
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
ms.openlocfilehash: b474249ed9f7778e44981b292d51f29f46bc420d
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a><span data-ttu-id="f4bc1-102">Como incrementar e diminuir ponteiros (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="f4bc1-102">How to: Increment and Decrement Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="f4bc1-103">Utilize os operadores de decremento e incremento, `++` e `--`, para alterar o local do ponteiro por [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) para um ponteiro do tipo “tipo de ponteiro”*.</span><span class="sxs-lookup"><span data-stu-id="f4bc1-103">Use the increment and the decrement operators, `++` and `--`, to change the pointer location by [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) for a pointer of type pointer-type*.</span></span> <span data-ttu-id="f4bc1-104">As expressões de incremento e de decremento têm o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="f4bc1-104">The increment and decrement expressions take the following form:</span></span>  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 <span data-ttu-id="f4bc1-105">Os operadores de incremento e de decremento podem ser aplicados a ponteiros de qualquer tipo, exceto o tipo `void*`.</span><span class="sxs-lookup"><span data-stu-id="f4bc1-105">The increment and decrement operators can be applied to pointers of any type except the type `void*`.</span></span>  
  
 <span data-ttu-id="f4bc1-106">O efeito de aplicar o operador de incremento a um ponteiro do tipo `pointer-type` é a adição de [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) ao endereço que está contido na variável do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="f4bc1-106">The effect of applying the increment operator to a pointer of the type `pointer-type` is to add [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) to the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="f4bc1-107">O efeito de aplicar o operador de decremento a um ponteiro do tipo `pointer-type` é a subtração de `sizeof` (`pointer-type`) do endereço que está contido na variável do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="f4bc1-107">The effect of applying the decrement operator to a pointer of the type `pointer-type` is to subtract `sizeof` (`pointer-type`) from the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="f4bc1-108">Nenhuma exceção é gerada quando a operação estoura o domínio do ponteiro e o resultado depende da implementação.</span><span class="sxs-lookup"><span data-stu-id="f4bc1-108">No exceptions are generated when the operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4bc1-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f4bc1-109">Example</span></span>  
 <span data-ttu-id="f4bc1-110">Neste exemplo, você percorre cada etapa de uma matriz incrementando o ponteiro pelo tamanho de `int`.</span><span class="sxs-lookup"><span data-stu-id="f4bc1-110">In this example, you step through an array by incrementing the pointer by the size of `int`.</span></span> <span data-ttu-id="f4bc1-111">Em cada etapa, é possível exibir o endereço e o conteúdo do elemento da matriz.</span><span class="sxs-lookup"><span data-stu-id="f4bc1-111">With each step, you display the address and the content of the array element.</span></span>  
  
 <span data-ttu-id="f4bc1-112">[!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f4bc1-112">[!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]</span></span>  
  
 <span data-ttu-id="f4bc1-113">[!code-cs[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="f4bc1-113">[!code-cs[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]</span></span>  
  
 <span data-ttu-id="f4bc1-114">**Valor:0 @ Endereço:12860272**</span><span class="sxs-lookup"><span data-stu-id="f4bc1-114">**Value:0 @ Address:12860272**</span></span>  
<span data-ttu-id="f4bc1-115">**Valor:1 @ Endereço:12860276**</span><span class="sxs-lookup"><span data-stu-id="f4bc1-115">**Value:1 @ Address:12860276**</span></span>  
<span data-ttu-id="f4bc1-116">**Valor:2 @ Endereço:12860280**</span><span class="sxs-lookup"><span data-stu-id="f4bc1-116">**Value:2 @ Address:12860280**</span></span>  
<span data-ttu-id="f4bc1-117">**Valor:3 @ Endereço:12860284**</span><span class="sxs-lookup"><span data-stu-id="f4bc1-117">**Value:3 @ Address:12860284**</span></span>  
<span data-ttu-id="f4bc1-118">**Valor:4 @ Endereço:12860288**</span><span class="sxs-lookup"><span data-stu-id="f4bc1-118">**Value:4 @ Address:12860288**</span></span>   
## <a name="see-also"></a><span data-ttu-id="f4bc1-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4bc1-119">See Also</span></span>  
 <span data-ttu-id="f4bc1-120">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f4bc1-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f4bc1-121">[Expressões de Ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="f4bc1-121">[Pointer Expressions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span></span>  
 <span data-ttu-id="f4bc1-122">[Operadores do C#](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="f4bc1-122">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 <span data-ttu-id="f4bc1-123">[Manipulando Ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md) </span><span class="sxs-lookup"><span data-stu-id="f4bc1-123">[Manipulating Pointers](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md) </span></span>  
 <span data-ttu-id="f4bc1-124">[Tipos de Ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span><span class="sxs-lookup"><span data-stu-id="f4bc1-124">[Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span></span>  
 <span data-ttu-id="f4bc1-125">[Tipos](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="f4bc1-125">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="f4bc1-126">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="f4bc1-126">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 <span data-ttu-id="f4bc1-127">[Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="f4bc1-127">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 [<span data-ttu-id="f4bc1-128">stackalloc</span><span class="sxs-lookup"><span data-stu-id="f4bc1-128">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)

