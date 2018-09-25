---
title: Como incrementar e diminuir ponteiros (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: 39cefc5dcebf1331a5e0ac0fadb8284e9041eb27
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44206465"
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a><span data-ttu-id="cbe43-102">Como incrementar e diminuir ponteiros (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="cbe43-102">How to: Increment and Decrement Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="cbe43-103">Utilize os operadores de decremento e incremento, `++` e `--`, para alterar o local do ponteiro por [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) para um ponteiro do tipo “tipo de ponteiro”\*.</span><span class="sxs-lookup"><span data-stu-id="cbe43-103">Use the increment and the decrement operators, `++` and `--`, to change the pointer location by [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) for a pointer of type pointer-type\*.</span></span> <span data-ttu-id="cbe43-104">As expressões de incremento e de decremento têm o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="cbe43-104">The increment and decrement expressions take the following form:</span></span>  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 <span data-ttu-id="cbe43-105">Os operadores de incremento e de decremento podem ser aplicados a ponteiros de qualquer tipo, exceto o tipo `void*`.</span><span class="sxs-lookup"><span data-stu-id="cbe43-105">The increment and decrement operators can be applied to pointers of any type except the type `void*`.</span></span>  
  
 <span data-ttu-id="cbe43-106">O efeito de aplicar o operador de incremento a um ponteiro do tipo `pointer-type` é a adição de [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) ao endereço que está contido na variável do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="cbe43-106">The effect of applying the increment operator to a pointer of the type `pointer-type` is to add [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) to the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="cbe43-107">O efeito de aplicar o operador de decremento a um ponteiro do tipo `pointer-type` é a subtração de `sizeof` (`pointer-type`) do endereço que está contido na variável do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="cbe43-107">The effect of applying the decrement operator to a pointer of the type `pointer-type` is to subtract `sizeof` (`pointer-type`) from the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="cbe43-108">Nenhuma exceção é gerada quando a operação estoura o domínio do ponteiro e o resultado depende da implementação.</span><span class="sxs-lookup"><span data-stu-id="cbe43-108">No exceptions are generated when the operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbe43-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cbe43-109">Example</span></span>  
 <span data-ttu-id="cbe43-110">Neste exemplo, você percorre cada etapa de uma matriz incrementando o ponteiro pelo tamanho de `int`.</span><span class="sxs-lookup"><span data-stu-id="cbe43-110">In this example, you step through an array by incrementing the pointer by the size of `int`.</span></span> <span data-ttu-id="cbe43-111">Em cada etapa, é possível exibir o endereço e o conteúdo do elemento da matriz.</span><span class="sxs-lookup"><span data-stu-id="cbe43-111">With each step, you display the address and the content of the array element.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
<span data-ttu-id="cbe43-112">**Value:0 @ Address:12860272**
**Value:1 @ Address:12860276**
**Value:2 @ Address:12860280**
**Value:3 @ Address:12860284**
**Value:4 @ Address:12860288**</span><span class="sxs-lookup"><span data-stu-id="cbe43-112">**Value:0 @ Address:12860272**
**Value:1 @ Address:12860276**
**Value:2 @ Address:12860280**
**Value:3 @ Address:12860284**
**Value:4 @ Address:12860288**</span></span>

## <a name="see-also"></a><span data-ttu-id="cbe43-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cbe43-113">See Also</span></span>

- [<span data-ttu-id="cbe43-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="cbe43-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="cbe43-115">Expressões de ponteiro</span><span class="sxs-lookup"><span data-stu-id="cbe43-115">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="cbe43-116">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="cbe43-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="cbe43-117">Manipulando ponteiros</span><span class="sxs-lookup"><span data-stu-id="cbe43-117">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [<span data-ttu-id="cbe43-118">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="cbe43-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="cbe43-119">Tipos</span><span class="sxs-lookup"><span data-stu-id="cbe43-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="cbe43-120">unsafe</span><span class="sxs-lookup"><span data-stu-id="cbe43-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="cbe43-121">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="cbe43-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="cbe43-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="cbe43-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
