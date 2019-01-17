---
title: acessar um elemento de matriz com um ponteiro – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: 4f5d82e0ccdffcb694e3030aabe58b8da687a5e1
ms.sourcegitcommit: d09c77414e9e4fc72c79b04deee7a756a120674e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54084791"
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a><span data-ttu-id="0458f-102">Como acessar um elemento de matriz com um ponteiro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="0458f-102">How to access an array element with a pointer (C# Programming Guide)</span></span>

<span data-ttu-id="0458f-103">Em um contexto não seguro, é possível acessar um elemento na memória por meio do acesso de elemento de ponteiro, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0458f-103">In an unsafe context, you can access an element in memory by using pointer element access, as shown in the following example:</span></span>

```csharp
char* charPointer = stackalloc char[123];
for (int i = 65; i < 123; i++)
{
    charPointer[i] = (char)i; //access array elements
}
```

<span data-ttu-id="0458f-104">A expressão entre colchetes deve ser implicitamente conversível para `int`, `uint`, `long` ou `ulong`.</span><span class="sxs-lookup"><span data-stu-id="0458f-104">The expression in square brackets must be implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="0458f-105">A operação `p[e]` é equivalente à `*(p+e)`.</span><span class="sxs-lookup"><span data-stu-id="0458f-105">The operation `p[e]` is equivalent to `*(p+e)`.</span></span> <span data-ttu-id="0458f-106">Assim como no C e no C++, o acesso de elemento de ponteiro não verifica erros fora dos limites.</span><span class="sxs-lookup"><span data-stu-id="0458f-106">Like C and C++, the pointer element access does not check for out-of-bounds errors.</span></span>

## <a name="example"></a><span data-ttu-id="0458f-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0458f-107">Example</span></span>

<span data-ttu-id="0458f-108">Neste exemplo, os locais de memória 123 são alocados para uma matriz de caracteres, `charPointer`.</span><span class="sxs-lookup"><span data-stu-id="0458f-108">In this example, 123 memory locations are allocated to a character array, `charPointer`.</span></span> <span data-ttu-id="0458f-109">A matriz é usada para exibir as letras minúsculas e maiúsculas em dois loops [for](../../../csharp/language-reference/keywords/for.md).</span><span class="sxs-lookup"><span data-stu-id="0458f-109">The array is used to display the lowercase letters and the uppercase letters in two [for](../../../csharp/language-reference/keywords/for.md) loops.</span></span>

<span data-ttu-id="0458f-110">Observe que a expressão `charPointer[i]` é equivalente à expressão `*(charPointer + i)` e é possível obter o mesmo resultado usando qualquer uma das duas expressões.</span><span class="sxs-lookup"><span data-stu-id="0458f-110">Notice that the expression `charPointer[i]` is equivalent to the expression `*(charPointer + i)`, and you can obtain the same result by using either of the two expressions.</span></span>

[!code-csharp[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]

[!code-csharp[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]

<span data-ttu-id="0458f-111">**Letras maiúsculas:**
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**
**Letras minúsculas:**
**abcdefghijklmnopqrstuvwxyz**</span><span class="sxs-lookup"><span data-stu-id="0458f-111">**Uppercase letters:**
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**
**Lowercase letters:**
**abcdefghijklmnopqrstuvwxyz**</span></span>

## <a name="see-also"></a><span data-ttu-id="0458f-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0458f-112">See also</span></span>

- [<span data-ttu-id="0458f-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="0458f-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="0458f-114">Expressões de ponteiro</span><span class="sxs-lookup"><span data-stu-id="0458f-114">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="0458f-115">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="0458f-115">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="0458f-116">Tipos</span><span class="sxs-lookup"><span data-stu-id="0458f-116">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="0458f-117">unsafe</span><span class="sxs-lookup"><span data-stu-id="0458f-117">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="0458f-118">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="0458f-118">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="0458f-119">stackalloc</span><span class="sxs-lookup"><span data-stu-id="0458f-119">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
