---
title: 'Como: obter o valor de uma variável de ponteiro – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: b20642344b34b5426512ef64bde2ab33d55136b9
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236629"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a><span data-ttu-id="26210-102">Como: obter o valor de uma variável de ponteiro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="26210-102">How to: Obtain the Value of a Pointer Variable (C# Programming Guide)</span></span>
<span data-ttu-id="26210-103">Use o operador de indireção de ponteiro para obter a variável no local apontado por um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="26210-103">Use the pointer indirection operator to obtain the variable at the location pointed to by a pointer.</span></span> <span data-ttu-id="26210-104">A expressão usa o seguinte formato, em que `p` é um tipo de ponteiro:</span><span class="sxs-lookup"><span data-stu-id="26210-104">The expression takes the following form, where `p` is a pointer type:</span></span>  
  
```  
*p;  
```  
  
 <span data-ttu-id="26210-105">Não é possível utilizar o operador de indireção unário em uma expressão de qualquer tipo diferente do tipo de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="26210-105">You cannot use the unary indirection operator on an expression of any type other than the pointer type.</span></span> <span data-ttu-id="26210-106">Além disso, não é possível aplicá-lo a um ponteiro [void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="26210-106">Also, you cannot apply it to a [void](../../../csharp/language-reference/keywords/void.md) pointer.</span></span>  
  
 <span data-ttu-id="26210-107">Ao aplicar o operador de indireção a um ponteiro [nulo](../../../csharp/language-reference/keywords/null.md), o resultado dependerá da implementação.</span><span class="sxs-lookup"><span data-stu-id="26210-107">When you apply the indirection operator to a [null](../../../csharp/language-reference/keywords/null.md) pointer, the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26210-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="26210-108">Example</span></span>  
 <span data-ttu-id="26210-109">No exemplo a seguir, uma variável do tipo `char` é acessada usando ponteiros de tipos diferentes.</span><span class="sxs-lookup"><span data-stu-id="26210-109">In the following example, a variable of the type `char` is accessed by using pointers of different types.</span></span> <span data-ttu-id="26210-110">Observe que o endereço do `theChar` variará de execução em execução, pois o endereço físico alocado a uma variável pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="26210-110">Note that the address of `theChar` will vary from run to run, because the physical address allocated to a variable can change.</span></span>  
  
 [!code-csharp[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
<span data-ttu-id="26210-111">**Valor de theChar = Z**
**Endereço de theChar = 12F718**
**Valor de pChar = Z**
**Valor de pInt = 90**</span><span class="sxs-lookup"><span data-stu-id="26210-111">**Value of theChar = Z**
**Address of theChar = 12F718**
**Value of pChar = Z**
**Value of pInt = 90**</span></span>

## <a name="see-also"></a><span data-ttu-id="26210-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26210-112">See Also</span></span>

- [<span data-ttu-id="26210-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="26210-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="26210-114">Expressões de ponteiro</span><span class="sxs-lookup"><span data-stu-id="26210-114">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="26210-115">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="26210-115">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="26210-116">Tipos</span><span class="sxs-lookup"><span data-stu-id="26210-116">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="26210-117">unsafe</span><span class="sxs-lookup"><span data-stu-id="26210-117">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="26210-118">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="26210-118">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="26210-119">stackalloc</span><span class="sxs-lookup"><span data-stu-id="26210-119">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
