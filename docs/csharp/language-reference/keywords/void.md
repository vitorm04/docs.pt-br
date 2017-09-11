---
title: "void (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- void_CSharpKeyword
- void
dev_langs:
- CSharp
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
caps.latest.revision: 15
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
ms.openlocfilehash: d1bd7ece5ce3b558c616a4eb3a4668c3c13eb1cb
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="void-c-reference"></a><span data-ttu-id="477be-102">void (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="477be-102">void (C# Reference)</span></span>
<span data-ttu-id="477be-103">Quando usado como o tipo de retorno para um método, `void` especifica que o método não retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="477be-103">When used as the return type for a method, `void` specifies that the method doesn't return a value.</span></span>

<span data-ttu-id="477be-104">`void` não é permitido na lista de parâmetros de um método.</span><span class="sxs-lookup"><span data-stu-id="477be-104">`void` isn't allowed in the parameter list of a method.</span></span> <span data-ttu-id="477be-105">Um método que não usa parâmetros e não retorna nenhum valor é declarado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="477be-105">A method that takes no parameters and returns no value is declared as follows:</span></span>

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

<span data-ttu-id="477be-106">`void` também é usado em um contexto desprotegido para declarar um ponteiro para um tipo desconhecido.</span><span class="sxs-lookup"><span data-stu-id="477be-106">`void` is also used in an unsafe context to declare a pointer to an unknown type.</span></span> <span data-ttu-id="477be-107">Para obter mais informações, consulte [Tipos de ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="477be-107">For more information, see [Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="477be-108">`void` é um alias para o tipo <xref:System.Void?displayProperty=fullName> do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="477be-108">`void` is an alias for the .NET Framework <xref:System.Void?displayProperty=fullName> type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="477be-109">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="477be-109">C# Language Specification</span></span>
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="477be-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="477be-110">See also</span></span>
 <span data-ttu-id="477be-111">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="477be-111">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="477be-112">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="477be-112">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="477be-113">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="477be-113">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="477be-114">[Tipos de Referência](../../../csharp/language-reference/keywords/reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="477be-114">[Reference Types](../../../csharp/language-reference/keywords/reference-types.md) </span></span>  
 <span data-ttu-id="477be-115">[Tipos de Valor](../../../csharp/language-reference/keywords/value-types.md) </span><span class="sxs-lookup"><span data-stu-id="477be-115">[Value Types](../../../csharp/language-reference/keywords/value-types.md) </span></span>  
 <span data-ttu-id="477be-116">[Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md) </span><span class="sxs-lookup"><span data-stu-id="477be-116">[Methods](../../../csharp/programming-guide/classes-and-structs/methods.md) </span></span>  
 [<span data-ttu-id="477be-117">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="477be-117">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)

