---
title: + Operador (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: d4a269c07e0d6dc2ac6a6a101f200653c6ea7a29
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244865"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="11187-102">Operador + (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="11187-102">+ Operator (C# Reference)</span></span>
<span data-ttu-id="11187-103">O operador `+` pode funcionar como um operador unário ou binário.</span><span class="sxs-lookup"><span data-stu-id="11187-103">The `+` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11187-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="11187-104">Remarks</span></span>  
 <span data-ttu-id="11187-105">Os operadores `+` unários são predefinidos para todos os tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="11187-105">Unary `+` operators are predefined for all numeric types.</span></span> <span data-ttu-id="11187-106">O resultado de uma operação `+` unária em um tipo numérico é apenas o valor do operando.</span><span class="sxs-lookup"><span data-stu-id="11187-106">The result of a unary `+` operation on a numeric type is just the value of the operand.</span></span>  
  
 <span data-ttu-id="11187-107">Operadores `+` binários são predefinidos para tipos numéricos e de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="11187-107">Binary `+` operators are predefined for numeric and string types.</span></span> <span data-ttu-id="11187-108">Para tipos numéricos, + calcula a soma de dois operandos.</span><span class="sxs-lookup"><span data-stu-id="11187-108">For numeric types, + computes the sum of its two operands.</span></span> <span data-ttu-id="11187-109">Quando um ou os dois operandos forem do tipo de cadeia de caracteres, + concatenará as representações de cadeia de caracteres dos operandos.</span><span class="sxs-lookup"><span data-stu-id="11187-109">When one or both operands are of type string, + concatenates the string representations of the operands.</span></span>  
  
 <span data-ttu-id="11187-110">Tipos de delegado também fornecem um operador `+` binário, que executa a concatenação de delegados.</span><span class="sxs-lookup"><span data-stu-id="11187-110">Delegate types also provide a binary `+` operator, which performs delegate concatenation.</span></span>  
  
 <span data-ttu-id="11187-111">Tipos definidos pelo usuário podem sobrecarregar os operadores `+` unários e `+` binários.</span><span class="sxs-lookup"><span data-stu-id="11187-111">User-defined types can overload the unary `+` and binary `+` operators.</span></span> <span data-ttu-id="11187-112">As operações em tipos integrais geralmente são permitidas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="11187-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="11187-113">Para obter mais informações, consulte [operador (Referência de C#)](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="11187-113">For more information, see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="11187-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="11187-114">Example</span></span>  
 [!code-csharp[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="11187-115">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="11187-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="11187-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11187-116">See Also</span></span>  
 [<span data-ttu-id="11187-117">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="11187-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="11187-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="11187-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="11187-119">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="11187-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="11187-120">operator (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="11187-120">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)
