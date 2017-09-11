---
title: "Operador &amp; (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d92a860df6fcc9acf14aab4ec558556735ac8aac
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="28d83-102">Operador &amp; (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="28d83-102">&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="28d83-103">O operador & pode funcionar como um operador unário ou binário.</span><span class="sxs-lookup"><span data-stu-id="28d83-103">The & operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28d83-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="28d83-104">Remarks</span></span>  
 <span data-ttu-id="28d83-105">O operador unário & retorna o endereço de seu operando (requer um contexto [unsafe](../../../csharp/language-reference/keywords/unsafe.md)).</span><span class="sxs-lookup"><span data-stu-id="28d83-105">The unary & operator returns the address of its operand (requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context).</span></span>  
  
 <span data-ttu-id="28d83-106">Os operadores binários & são predefinidos para os tipos integrais e `bool`.</span><span class="sxs-lookup"><span data-stu-id="28d83-106">Binary & operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="28d83-107">Para os tipos integrais, o & computa o AND lógico bit a bit de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="28d83-107">For integral types, & computes the logical bitwise AND of its operands.</span></span> <span data-ttu-id="28d83-108">Para operandos `bool`, o & computa o AND lógico de seus operandos; ou seja, o resultado será `true` se e somente se ambos seus operandos forem `true`.</span><span class="sxs-lookup"><span data-stu-id="28d83-108">For `bool` operands, & computes the logical AND of its operands; that is, the result is `true` if and only if both its operands are `true`.</span></span>  
  
 <span data-ttu-id="28d83-109">O operador `&` avalia os dois operadores independentemente do valor do primeiro.</span><span class="sxs-lookup"><span data-stu-id="28d83-109">The `&` operator evaluates both operators regardless of the first one's value.</span></span> <span data-ttu-id="28d83-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="28d83-110">For example:</span></span>  
  
 <span data-ttu-id="28d83-111">[!code-cs[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="28d83-111">[!code-cs[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]</span></span>  
  
 <span data-ttu-id="28d83-112">Tipos definidos pelo usuário podem sobrecarregar o operador binário `&` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="28d83-112">User-defined types can overload the binary `&` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="28d83-113">As operações em tipos integrais geralmente são permitidas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="28d83-113">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="28d83-114">Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="28d83-114">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28d83-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="28d83-115">Example</span></span>  
 <span data-ttu-id="28d83-116">[!code-cs[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="28d83-116">[!code-cs[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28d83-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28d83-117">See Also</span></span>  
 <span data-ttu-id="28d83-118">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="28d83-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="28d83-119">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="28d83-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="28d83-120">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="28d83-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

