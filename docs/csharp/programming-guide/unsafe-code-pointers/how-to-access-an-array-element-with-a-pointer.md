---
title: Como acessar um elemento de matriz com um ponteiro (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: 0e76ebddd8b703e8d0de4aa6825cbd6d0221079b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861644"
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a><span data-ttu-id="067db-102">Como acessar um elemento de matriz com um ponteiro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="067db-102">How to access an array element with a pointer (C# Programming Guide)</span></span>

<span data-ttu-id="067db-103">Em um contexto não seguro, é possível acessar um elemento na memória por meio do acesso de elemento de ponteiro, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="067db-103">In an unsafe context, you can access an element in memory by using pointer element access, as shown in the following example:</span></span>

```csharp
char* charPointer = stackalloc char[123];
for (int i = 65; i < 123; i++)
{
    charPointer[i] = (char)i; //access array elements
}
```

<span data-ttu-id="067db-104">A expressão entre colchetes deve ser implicitamente conversível para `int`, `uint`, `long` ou `ulong`.</span><span class="sxs-lookup"><span data-stu-id="067db-104">The expression in square brackets must be implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="067db-105">A operação p[e] é equivalente a \*(p+e).</span><span class="sxs-lookup"><span data-stu-id="067db-105">The operation p[e] is equivalent to \*(p+e).</span></span> <span data-ttu-id="067db-106">Assim como no C e no C++, o acesso de elemento de ponteiro não verifica erros fora dos limites.</span><span class="sxs-lookup"><span data-stu-id="067db-106">Like C and C++, the pointer element access does not check for out-of-bounds errors.</span></span>

## <a name="example"></a><span data-ttu-id="067db-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="067db-107">Example</span></span>

<span data-ttu-id="067db-108">Neste exemplo, os locais de memória 123 são alocados para uma matriz de caracteres, `charPointer`.</span><span class="sxs-lookup"><span data-stu-id="067db-108">In this example, 123 memory locations are allocated to a character array, `charPointer`.</span></span> <span data-ttu-id="067db-109">A matriz é usada para exibir as letras minúsculas e maiúsculas em dois loops [for](../../../csharp/language-reference/keywords/for.md).</span><span class="sxs-lookup"><span data-stu-id="067db-109">The array is used to display the lowercase letters and the uppercase letters in two [for](../../../csharp/language-reference/keywords/for.md) loops.</span></span>

<span data-ttu-id="067db-110">Observe que a expressão `charPointer[i]` é equivalente à expressão `*(charPointer + i)` e é possível obter o mesmo resultado usando qualquer uma das duas expressões.</span><span class="sxs-lookup"><span data-stu-id="067db-110">Notice that the expression `charPointer[i]` is equivalent to the expression `*(charPointer + i)`, and you can obtain the same result by using either of the two expressions.</span></span>

[!code-csharp[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]

[!code-csharp[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]

<span data-ttu-id="067db-111">**Letras maiúsculas:**
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**
**Letras minúsculas:**
**abcdefghijklmnopqrstuvwxyz**</span><span class="sxs-lookup"><span data-stu-id="067db-111">**Uppercase letters:**
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**
**Lowercase letters:**
**abcdefghijklmnopqrstuvwxyz**</span></span>

## <a name="see-also"></a><span data-ttu-id="067db-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="067db-112">See also</span></span>

- [<span data-ttu-id="067db-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="067db-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="067db-114">Expressões de ponteiro</span><span class="sxs-lookup"><span data-stu-id="067db-114">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="067db-115">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="067db-115">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="067db-116">Tipos</span><span class="sxs-lookup"><span data-stu-id="067db-116">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="067db-117">unsafe</span><span class="sxs-lookup"><span data-stu-id="067db-117">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="067db-118">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="067db-118">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="067db-119">stackalloc</span><span class="sxs-lookup"><span data-stu-id="067db-119">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
