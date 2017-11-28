---
title: "operator (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords: operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8fae5487d5daa5ada52d45919598d1abd217aee9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="operator-c-reference"></a><span data-ttu-id="95b57-102">operator (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="95b57-102">operator (C# Reference)</span></span>
<span data-ttu-id="95b57-103">Use a palavra-chave `operator` para sobrecarregar um operador interno ou para fornecer uma conversão definida pelo usuário em uma declaração de classe ou struct.</span><span class="sxs-lookup"><span data-stu-id="95b57-103">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95b57-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95b57-104">Example</span></span>  
 <span data-ttu-id="95b57-105">A seguir, temos uma classe bastante simplificada para números fracionários.</span><span class="sxs-lookup"><span data-stu-id="95b57-105">The following is a very simplified class for fractional numbers.</span></span> <span data-ttu-id="95b57-106">Ela sobrecarrega os operadores + e * para executar multiplicação e adição fracionária e também fornece um operador de conversão que converte um tipo de fração para um tipo double.</span><span class="sxs-lookup"><span data-stu-id="95b57-106">It overloads the + and * operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a Fraction type to a double type.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="95b57-107">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="95b57-107">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="95b57-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95b57-108">See Also</span></span>  
 [<span data-ttu-id="95b57-109">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="95b57-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="95b57-110">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="95b57-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="95b57-111">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="95b57-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="95b57-112">implicit</span><span class="sxs-lookup"><span data-stu-id="95b57-112">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
 [<span data-ttu-id="95b57-113">explicit</span><span class="sxs-lookup"><span data-stu-id="95b57-113">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="95b57-114">Como implementar conversões definidas pelo usuário entre structs</span><span class="sxs-lookup"><span data-stu-id="95b57-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
