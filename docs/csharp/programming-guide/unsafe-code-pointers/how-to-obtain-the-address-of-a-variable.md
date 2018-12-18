---
title: Como obter o endereço de uma variável – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
ms.openlocfilehash: 3e2eac468643b755c6db2d6055427baa7ce2b7a7
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241769"
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="44a41-102">Como obter o endereço de uma variável (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="44a41-102">How to: obtain the address of a variable (C# Programming Guide)</span></span>

<span data-ttu-id="44a41-103">Para obter o endereço de uma expressão unária, que é avaliada como uma variável fixa, use o operador address-of `&`:</span><span class="sxs-lookup"><span data-stu-id="44a41-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator `&`:</span></span>  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="44a41-104">O operador address-of pode ser aplicado somente a uma variável.</span><span class="sxs-lookup"><span data-stu-id="44a41-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="44a41-105">Se a variável for uma variável móvel, é possível usar a [instrução fixa](../../../csharp/language-reference/keywords/fixed-statement.md) para corrigir temporariamente a variável antes de obter seu endereço.</span><span class="sxs-lookup"><span data-stu-id="44a41-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span>  
  
 <span data-ttu-id="44a41-106">É sua responsabilidade assegurar que a variável seja inicializada.</span><span class="sxs-lookup"><span data-stu-id="44a41-106">It's your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="44a41-107">O compilador não emitirá uma mensagem de erro se a variável não for inicializada.</span><span class="sxs-lookup"><span data-stu-id="44a41-107">The compiler doesn't issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="44a41-108">Não é possível obter o endereço de uma constante nem de um valor.</span><span class="sxs-lookup"><span data-stu-id="44a41-108">You can't get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44a41-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44a41-109">Example</span></span>  
 <span data-ttu-id="44a41-110">Neste exemplo, um ponteiro para `int`, `p`, é declarado e atribuído ao endereço de uma variável de inteiro, `number`.</span><span class="sxs-lookup"><span data-stu-id="44a41-110">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="44a41-111">A variável `number` é inicializada como resultado da atribuição a `*p`.</span><span class="sxs-lookup"><span data-stu-id="44a41-111">The variable `number` is initialized as a result of the assignment to `*p`.</span></span> <span data-ttu-id="44a41-112">Se você comentar esta instrução de atribuição, a inicialização da variável `number` será removida, mas não será emitido nenhum erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="44a41-112">If you comment out this assignment statement, the initialization of the variable `number` is removed, but no compile-time error is issued.</span></span>  

> [!NOTE]
> <span data-ttu-id="44a41-113">Compile este exemplo com a opção do compilador [`-unsafe`](../../language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="44a41-113">Compile this example with the [`-unsafe`](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="44a41-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44a41-114">See Also</span></span>

- [<span data-ttu-id="44a41-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="44a41-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="44a41-116">Expressões de ponteiro</span><span class="sxs-lookup"><span data-stu-id="44a41-116">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="44a41-117">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="44a41-117">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="44a41-118">Tipos</span><span class="sxs-lookup"><span data-stu-id="44a41-118">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="44a41-119">unsafe</span><span class="sxs-lookup"><span data-stu-id="44a41-119">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="44a41-120">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="44a41-120">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="44a41-121">stackalloc</span><span class="sxs-lookup"><span data-stu-id="44a41-121">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
