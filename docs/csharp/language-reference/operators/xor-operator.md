---
title: Operador ^ (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: 5cc3cd2cfc932646e5b2dd6ec034555b07582379
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33271244"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d0488-102">Operador ^ (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d0488-102">^ Operator (C# Reference)</span></span>
<span data-ttu-id="d0488-103">Os operadores binários `^` são predefinidos para os tipos integrais e `bool`.</span><span class="sxs-lookup"><span data-stu-id="d0488-103">Binary `^` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="d0488-104">Para os tipos integrais, o `^` computa o OR exclusivo bit a bit de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="d0488-104">For integral types, `^` computes the bitwise exclusive-OR of its operands.</span></span> <span data-ttu-id="d0488-105">Para operandos `bool`, o `^` computa o OR exclusivo lógico de seus operandos; ou seja, o resultado será `true` se e somente se exatamente um dos operandos for `true`.</span><span class="sxs-lookup"><span data-stu-id="d0488-105">For `bool` operands, `^` computes the logical exclusive-or of its operands; that is, the result is `true` if and only if exactly one of its operands is `true`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0488-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0488-106">Remarks</span></span>  
 <span data-ttu-id="d0488-107">Os tipos definidos pelo usuário podem sobrecarregar o operador `^` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="d0488-107">User-defined types can overload the `^` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="d0488-108">As operações em tipos integrais geralmente são permitidas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="d0488-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0488-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0488-109">Example</span></span>  
 [!code-csharp[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 <span data-ttu-id="d0488-110">O cálculo de `0xf8 ^ 0x3f` no exemplo anterior executa um OR exclusivo bit a bit dos dois valores binários a seguir, que correspondem aos valores hexadecimais F8 e 3F:</span><span class="sxs-lookup"><span data-stu-id="d0488-110">The computation of `0xf8 ^ 0x3f` in the previous example performs a bitwise exclusive-OR of the following two binary values, which correspond to the hexadecimal values F8 and 3F:</span></span>  
  
 `1111 1000`  
  
 `0011 1111`  
  
 <span data-ttu-id="d0488-111">O resultado do OR exclusivo é `1100 0111`, que é igual a C7 em hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="d0488-111">The result of the exclusive-OR is `1100 0111`, which is C7 in hexadecimal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0488-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0488-112">See Also</span></span>  
 [<span data-ttu-id="d0488-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d0488-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d0488-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d0488-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d0488-115">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="d0488-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
