---
title: "+ Operador (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- +_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
caps.latest.revision: 19
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
ms.openlocfilehash: 5455375148f1924c7fe1cdb10e7924abb83a1565
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="a282f-102">Operador + (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a282f-102">+ Operator (C# Reference)</span></span>
<span data-ttu-id="a282f-103">O operador `+` pode funcionar como um operador unário ou binário.</span><span class="sxs-lookup"><span data-stu-id="a282f-103">The `+` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a282f-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="a282f-104">Remarks</span></span>  
 <span data-ttu-id="a282f-105">Os operadores `+` unários são predefinidos para todos os tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="a282f-105">Unary `+` operators are predefined for all numeric types.</span></span> <span data-ttu-id="a282f-106">O resultado de uma operação `+` unária em um tipo numérico é apenas o valor do operando.</span><span class="sxs-lookup"><span data-stu-id="a282f-106">The result of a unary `+` operation on a numeric type is just the value of the operand.</span></span>  
  
 <span data-ttu-id="a282f-107">Operadores `+` binários são predefinidos para tipos numéricos e de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a282f-107">Binary `+` operators are predefined for numeric and string types.</span></span> <span data-ttu-id="a282f-108">Para tipos numéricos, + calcula a soma de dois operandos.</span><span class="sxs-lookup"><span data-stu-id="a282f-108">For numeric types, + computes the sum of its two operands.</span></span> <span data-ttu-id="a282f-109">Quando um ou os dois operandos forem do tipo de cadeia de caracteres, + concatenará as representações de cadeia de caracteres dos operandos.</span><span class="sxs-lookup"><span data-stu-id="a282f-109">When one or both operands are of type string, + concatenates the string representations of the operands.</span></span>  
  
 <span data-ttu-id="a282f-110">Tipos de delegado também fornecem um operador `+` binário, que executa a concatenação de delegados.</span><span class="sxs-lookup"><span data-stu-id="a282f-110">Delegate types also provide a binary `+` operator, which performs delegate concatenation.</span></span>  
  
 <span data-ttu-id="a282f-111">Tipos definidos pelo usuário podem sobrecarregar os operadores `+` unários e `+` binários.</span><span class="sxs-lookup"><span data-stu-id="a282f-111">User-defined types can overload the unary `+` and binary `+` operators.</span></span> <span data-ttu-id="a282f-112">As operações em tipos integrais geralmente são permitidas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="a282f-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="a282f-113">Para obter mais informações, consulte [operador (Referência de C#)](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="a282f-113">For more information, see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a282f-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a282f-114">Example</span></span>  
 <span data-ttu-id="a282f-115">[!code-cs[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="a282f-115">[!code-cs[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="a282f-116">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="a282f-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a282f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a282f-117">See Also</span></span>  
 <span data-ttu-id="a282f-118">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="a282f-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="a282f-119">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="a282f-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="a282f-120">[Operadores do C#](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="a282f-120">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 [<span data-ttu-id="a282f-121">operator (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a282f-121">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)

