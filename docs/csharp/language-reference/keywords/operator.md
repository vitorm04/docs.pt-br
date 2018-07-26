---
title: operator (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: d633a46e21f913aa8c05289dccfb63e71efd697e
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37959534"
---
# <a name="operator-c-reference"></a><span data-ttu-id="a6874-102">operator (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a6874-102">operator (C# Reference)</span></span>
<span data-ttu-id="a6874-103">Use a palavra-chave `operator` para sobrecarregar um operador interno ou para fornecer uma conversão definida pelo usuário em uma declaração de classe ou struct.</span><span class="sxs-lookup"><span data-stu-id="a6874-103">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6874-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a6874-104">Example</span></span>  
 <span data-ttu-id="a6874-105">A seguir, temos uma classe bastante simplificada para números fracionários.</span><span class="sxs-lookup"><span data-stu-id="a6874-105">The following is a very simplified class for fractional numbers.</span></span> <span data-ttu-id="a6874-106">Ela sobrecarrega os operadores `+` e `*` para executar multiplicação e adição fracionária e também fornece um operador de conversão que converte um tipo `Fraction` em um tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="a6874-106">It overloads the `+` and `*` operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a `Fraction` type to a `double` type.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="a6874-107">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="a6874-107">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a6874-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6874-108">See Also</span></span>  
 [<span data-ttu-id="a6874-109">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a6874-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a6874-110">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a6874-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a6874-111">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="a6874-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="a6874-112">implicit</span><span class="sxs-lookup"><span data-stu-id="a6874-112">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
 [<span data-ttu-id="a6874-113">explicit</span><span class="sxs-lookup"><span data-stu-id="a6874-113">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="a6874-114">Como implementar conversões definidas pelo usuário entre structs</span><span class="sxs-lookup"><span data-stu-id="a6874-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
