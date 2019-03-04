---
title: 'Como: implementar conversões definidas pelo usuário entre structs – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: bc792562b4849d402e03328e50dedac030520011
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201138"
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a><span data-ttu-id="ef961-102">Como: implementar conversões definidas pelo usuário entre structs (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="ef961-102">How to: Implement User-Defined Conversions Between Structs (C# Programming Guide)</span></span>
<span data-ttu-id="ef961-103">Este exemplo define dois structs, `RomanNumeral` e `BinaryNumeral`, e demonstra conversões entre eles.</span><span class="sxs-lookup"><span data-stu-id="ef961-103">This example defines two structs, `RomanNumeral` and `BinaryNumeral`, and demonstrates conversions between them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef961-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ef961-104">Example</span></span>  
 [!code-csharp[csProgGuideStatements#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#13)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ef961-105">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="ef961-105">Robust Programming</span></span>  
  
-   <span data-ttu-id="ef961-106">No exemplo anterior, a instrução:</span><span class="sxs-lookup"><span data-stu-id="ef961-106">In the previous example, the statement:</span></span>  
  
     [!code-csharp[csProgGuideStatements#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#14)]  
  
     <span data-ttu-id="ef961-107">executa uma conversão de um `RomanNumeral` para um `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="ef961-107">performs a conversion from a `RomanNumeral` to a `BinaryNumeral`.</span></span> <span data-ttu-id="ef961-108">Como não há nenhuma conversão direta de `RomanNumeral` para `BinaryNumeral`, uma conversão é usada para converter de um `RomanNumeral` para um `int` e outra conversão para converter de um `int` para um `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="ef961-108">Because there is no direct conversion from `RomanNumeral` to `BinaryNumeral`, a cast is used to convert from a `RomanNumeral` to an `int`, and another cast to convert from an `int` to a `BinaryNumeral`.</span></span>  
  
-   <span data-ttu-id="ef961-109">Além disso, a instrução</span><span class="sxs-lookup"><span data-stu-id="ef961-109">Also the statement</span></span>  
  
     [!code-csharp[csProgGuideStatements#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#15)]  
  
     <span data-ttu-id="ef961-110">executa uma conversão de um `BinaryNumeral` para um `RomanNumeral`.</span><span class="sxs-lookup"><span data-stu-id="ef961-110">performs a conversion from a `BinaryNumeral` to a `RomanNumeral`.</span></span> <span data-ttu-id="ef961-111">Como `RomanNumeral` define uma conversão implícita de `BinaryNumeral`, nenhuma conversão é necessária.</span><span class="sxs-lookup"><span data-stu-id="ef961-111">Because `RomanNumeral` defines an implicit conversion from `BinaryNumeral`, no cast is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef961-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef961-112">See also</span></span>

- [<span data-ttu-id="ef961-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="ef961-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="ef961-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="ef961-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ef961-115">Operadores de conversão</span><span class="sxs-lookup"><span data-stu-id="ef961-115">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
