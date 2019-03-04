---
title: Como acessar um elemento de matriz com um ponteiro – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: 7b2991776ca032aa53111187a061835725cfe223
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965599"
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a><span data-ttu-id="f2d93-102">Como acessar um elemento de matriz com um ponteiro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="f2d93-102">How to: access an array element with a pointer (C# Programming Guide)</span></span>

<span data-ttu-id="f2d93-103">Em um contexto não seguro, é possível acessar um elemento na memória por meio do acesso de elemento de ponteiro, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f2d93-103">In an unsafe context, you can access an element in memory by using pointer element access, as shown in the following example:</span></span>

```csharp
char* charPointer = stackalloc char[123];
for (int i = 65; i < 123; i++)
{
    charPointer[i] = (char)i; //access array elements
}
```

<span data-ttu-id="f2d93-104">A expressão entre colchetes deve ser implicitamente conversível para `int`, `uint`, `long` ou `ulong`.</span><span class="sxs-lookup"><span data-stu-id="f2d93-104">The expression in square brackets must be implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="f2d93-105">A operação `p[e]` é equivalente à `*(p+e)`.</span><span class="sxs-lookup"><span data-stu-id="f2d93-105">The operation `p[e]` is equivalent to `*(p+e)`.</span></span> <span data-ttu-id="f2d93-106">Assim como no C e no C++, o acesso de elemento de ponteiro não verifica erros fora dos limites.</span><span class="sxs-lookup"><span data-stu-id="f2d93-106">Like C and C++, the pointer element access does not check for out-of-bounds errors.</span></span>

## <a name="example"></a><span data-ttu-id="f2d93-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f2d93-107">Example</span></span>

<span data-ttu-id="f2d93-108">Neste exemplo, os locais de memória 123 são alocados para uma matriz de caracteres, `charPointer`.</span><span class="sxs-lookup"><span data-stu-id="f2d93-108">In this example, 123 memory locations are allocated to a character array, `charPointer`.</span></span> <span data-ttu-id="f2d93-109">A matriz é usada para exibir as letras minúsculas e maiúsculas em dois loops [for](../../../csharp/language-reference/keywords/for.md).</span><span class="sxs-lookup"><span data-stu-id="f2d93-109">The array is used to display the lowercase letters and the uppercase letters in two [for](../../../csharp/language-reference/keywords/for.md) loops.</span></span>

<span data-ttu-id="f2d93-110">Observe que a expressão `charPointer[i]` é equivalente à expressão `*(charPointer + i)` e é possível obter o mesmo resultado usando qualquer uma das duas expressões.</span><span class="sxs-lookup"><span data-stu-id="f2d93-110">Notice that the expression `charPointer[i]` is equivalent to the expression `*(charPointer + i)`, and you can obtain the same result by using either of the two expressions.</span></span>

 [!code-csharp[csProgGuidePointers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#11)]

 [!code-csharp[csProgGuidePointers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#12)]

<span data-ttu-id="f2d93-111">**Letras maiúsculas:**</span><span class="sxs-lookup"><span data-stu-id="f2d93-111">**Uppercase letters:**</span></span>  
<span data-ttu-id="f2d93-112">**ABCDEFGHIJKLMNOPQRSTUVWXYZ**</span><span class="sxs-lookup"><span data-stu-id="f2d93-112">**ABCDEFGHIJKLMNOPQRSTUVWXYZ**</span></span>  
<span data-ttu-id="f2d93-113">**Letras minúsculas:**</span><span class="sxs-lookup"><span data-stu-id="f2d93-113">**Lowercase letters:**</span></span>  
<span data-ttu-id="f2d93-114">**abcdefghijklmnopqrstuvwxyz**</span><span class="sxs-lookup"><span data-stu-id="f2d93-114">**abcdefghijklmnopqrstuvwxyz**</span></span>  

## <a name="see-also"></a><span data-ttu-id="f2d93-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2d93-115">See also</span></span>

- [<span data-ttu-id="f2d93-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="f2d93-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f2d93-117">Expressões de ponteiro</span><span class="sxs-lookup"><span data-stu-id="f2d93-117">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="f2d93-118">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="f2d93-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="f2d93-119">Tipos</span><span class="sxs-lookup"><span data-stu-id="f2d93-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="f2d93-120">unsafe</span><span class="sxs-lookup"><span data-stu-id="f2d93-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="f2d93-121">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="f2d93-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="f2d93-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="f2d93-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
