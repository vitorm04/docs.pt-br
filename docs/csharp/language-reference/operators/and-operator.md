---
title: Operador &amp; (Referência de C#)
ms.date: 04/04/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: b257c7d41618464e26ab3b54bcfb1f1e2c2e420e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467368"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="25ce0-102">Operador &amp; (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="25ce0-102">&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="25ce0-103">O operador `&` pode funcionar como um operador unário ou binário.</span><span class="sxs-lookup"><span data-stu-id="25ce0-103">The `&` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25ce0-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="25ce0-104">Remarks</span></span>  
 <span data-ttu-id="25ce0-105">O operador unário `&` retorna o endereço de seu operando (requer um contexto [desprotegido](../../../csharp/language-reference/keywords/unsafe.md)).</span><span class="sxs-lookup"><span data-stu-id="25ce0-105">The unary `&` operator returns the address of its operand (requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context).</span></span>  
  
 <span data-ttu-id="25ce0-106">Os operadores binários `&` são predefinidos para os tipos integrais e `bool`.</span><span class="sxs-lookup"><span data-stu-id="25ce0-106">Binary `&` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="25ce0-107">Para os tipos integrais, o & computa o AND lógico bit a bit de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="25ce0-107">For integral types, & computes the logical bitwise AND of its operands.</span></span> <span data-ttu-id="25ce0-108">Para operandos `bool`, o & computa o AND lógico de seus operandos; ou seja, o resultado será `true` se e somente se ambos seus operandos forem `true`.</span><span class="sxs-lookup"><span data-stu-id="25ce0-108">For `bool` operands, & computes the logical AND of its operands; that is, the result is `true` if and only if both its operands are `true`.</span></span>  
  
 <span data-ttu-id="25ce0-109">O operador binário `&` avalia os dois operandos, independentemente do valor do primeiro, ao contrário do [operador AND condicional](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`.</span><span class="sxs-lookup"><span data-stu-id="25ce0-109">The binary `&` operator evaluates both operands regardless of the first one's value, in contrast to the [conditional AND operator](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`.</span></span> <span data-ttu-id="25ce0-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="25ce0-110">For example:</span></span>  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 <span data-ttu-id="25ce0-111">Tipos definidos pelo usuário podem sobrecarregar o operador binário `&` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="25ce0-111">User-defined types can overload the binary `&` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="25ce0-112">As operações em tipos integrais geralmente são permitidas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="25ce0-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="25ce0-113">Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="25ce0-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25ce0-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="25ce0-114">Example</span></span>  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="25ce0-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25ce0-115">See Also</span></span>

- [<span data-ttu-id="25ce0-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="25ce0-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="25ce0-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="25ce0-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="25ce0-118">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="25ce0-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
