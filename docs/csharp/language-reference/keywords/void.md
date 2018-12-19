---
title: void – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 87ccc3a18f0956ffe800ae97598e621e5ca72480
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238371"
---
# <a name="void-c-reference"></a><span data-ttu-id="9f5b3-102">void (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="9f5b3-102">void (C# Reference)</span></span>
<span data-ttu-id="9f5b3-103">Quando usado como o tipo de retorno para um método, `void` especifica que o método não retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="9f5b3-103">When used as the return type for a method, `void` specifies that the method doesn't return a value.</span></span>

<span data-ttu-id="9f5b3-104">`void` não é permitido na lista de parâmetros de um método.</span><span class="sxs-lookup"><span data-stu-id="9f5b3-104">`void` isn't allowed in the parameter list of a method.</span></span> <span data-ttu-id="9f5b3-105">Um método que não usa parâmetros e não retorna nenhum valor é declarado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9f5b3-105">A method that takes no parameters and returns no value is declared as follows:</span></span>

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

<span data-ttu-id="9f5b3-106">`void` também é usado em um contexto desprotegido para declarar um ponteiro para um tipo desconhecido.</span><span class="sxs-lookup"><span data-stu-id="9f5b3-106">`void` is also used in an unsafe context to declare a pointer to an unknown type.</span></span> <span data-ttu-id="9f5b3-107">Para obter mais informações, consulte [Tipos de ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="9f5b3-107">For more information, see [Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="9f5b3-108">`void` é um alias para o tipo <xref:System.Void?displayProperty=nameWithType> do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f5b3-108">`void` is an alias for the .NET Framework <xref:System.Void?displayProperty=nameWithType> type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9f5b3-109">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="9f5b3-109">C# Language Specification</span></span>
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9f5b3-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f5b3-110">See also</span></span>

- [<span data-ttu-id="9f5b3-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="9f5b3-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="9f5b3-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="9f5b3-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="9f5b3-113">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="9f5b3-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="9f5b3-114">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="9f5b3-114">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
- [<span data-ttu-id="9f5b3-115">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="9f5b3-115">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
- [<span data-ttu-id="9f5b3-116">Métodos</span><span class="sxs-lookup"><span data-stu-id="9f5b3-116">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [<span data-ttu-id="9f5b3-117">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="9f5b3-117">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
