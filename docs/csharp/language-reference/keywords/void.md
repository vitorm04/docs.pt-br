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
ms.openlocfilehash: ce52e4d19335db0e21637b87bbd1589c86c06ae1
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613122"
---
# <a name="void-c-reference"></a><span data-ttu-id="8d766-102">void (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="8d766-102">void (C# Reference)</span></span>

<span data-ttu-id="8d766-103">Quando usado como o tipo de retorno para um método, `void` especifica que o método não retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="8d766-103">When used as the return type for a method, `void` specifies that the method doesn't return a value.</span></span>

<span data-ttu-id="8d766-104">`void` não é permitido na lista de parâmetros de um método.</span><span class="sxs-lookup"><span data-stu-id="8d766-104">`void` isn't allowed in the parameter list of a method.</span></span> <span data-ttu-id="8d766-105">Um método que não usa parâmetros e não retorna nenhum valor é declarado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="8d766-105">A method that takes no parameters and returns no value is declared as follows:</span></span>

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

<span data-ttu-id="8d766-106">`void` também é usado em um contexto desprotegido para declarar um ponteiro para um tipo desconhecido.</span><span class="sxs-lookup"><span data-stu-id="8d766-106">`void` is also used in an unsafe context to declare a pointer to an unknown type.</span></span> <span data-ttu-id="8d766-107">Para obter mais informações, consulte [Tipos de ponteiros](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="8d766-107">For more information, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="8d766-108">`void` é um alias para o tipo <xref:System.Void?displayProperty=nameWithType> do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8d766-108">`void` is an alias for the .NET Framework <xref:System.Void?displayProperty=nameWithType> type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8d766-109">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="8d766-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="8d766-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d766-110">See also</span></span>

- [<span data-ttu-id="8d766-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="8d766-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8d766-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="8d766-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8d766-113">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="8d766-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8d766-114">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="8d766-114">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="8d766-115">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="8d766-115">Value Types</span></span>](value-types.md)
- [<span data-ttu-id="8d766-116">Métodos</span><span class="sxs-lookup"><span data-stu-id="8d766-116">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="8d766-117">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="8d766-117">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)