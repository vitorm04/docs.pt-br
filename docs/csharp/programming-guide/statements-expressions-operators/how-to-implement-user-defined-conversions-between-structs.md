---
title: 'Como: implementar conversões definidas pelo usuário entre structs – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: 85345203982679c0ab8dc9a6ae899312204c3230
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241568"
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a><span data-ttu-id="aded7-102">Como: implementar conversões definidas pelo usuário entre structs (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="aded7-102">How to: Implement User-Defined Conversions Between Structs (C# Programming Guide)</span></span>
<span data-ttu-id="aded7-103">Este exemplo define dois structs, `RomanNumeral` e `BinaryNumeral`, e demonstra conversões entre eles.</span><span class="sxs-lookup"><span data-stu-id="aded7-103">This example defines two structs, `RomanNumeral` and `BinaryNumeral`, and demonstrates conversions between them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aded7-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aded7-104">Example</span></span>  
 [!code-csharp[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="aded7-105">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="aded7-105">Robust Programming</span></span>  
  
-   <span data-ttu-id="aded7-106">No exemplo anterior, a instrução:</span><span class="sxs-lookup"><span data-stu-id="aded7-106">In the previous example, the statement:</span></span>  
  
     [!code-csharp[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]  
  
     <span data-ttu-id="aded7-107">executa uma conversão de um `RomanNumeral` para um `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="aded7-107">performs a conversion from a `RomanNumeral` to a `BinaryNumeral`.</span></span> <span data-ttu-id="aded7-108">Como não há nenhuma conversão direta de `RomanNumeral` para `BinaryNumeral`, uma conversão é usada para converter de um `RomanNumeral` para um `int` e outra conversão para converter de um `int` para um `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="aded7-108">Because there is no direct conversion from `RomanNumeral` to `BinaryNumeral`, a cast is used to convert from a `RomanNumeral` to an `int`, and another cast to convert from an `int` to a `BinaryNumeral`.</span></span>  
  
-   <span data-ttu-id="aded7-109">Além disso, a instrução</span><span class="sxs-lookup"><span data-stu-id="aded7-109">Also the statement</span></span>  
  
     [!code-csharp[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]  
  
     <span data-ttu-id="aded7-110">executa uma conversão de um `BinaryNumeral` para um `RomanNumeral`.</span><span class="sxs-lookup"><span data-stu-id="aded7-110">performs a conversion from a `BinaryNumeral` to a `RomanNumeral`.</span></span> <span data-ttu-id="aded7-111">Como `RomanNumeral` define uma conversão implícita de `BinaryNumeral`, nenhuma conversão é necessária.</span><span class="sxs-lookup"><span data-stu-id="aded7-111">Because `RomanNumeral` defines an implicit conversion from `BinaryNumeral`, no cast is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aded7-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aded7-112">See Also</span></span>

- [<span data-ttu-id="aded7-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="aded7-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="aded7-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="aded7-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="aded7-115">Operadores de conversão</span><span class="sxs-lookup"><span data-stu-id="aded7-115">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
