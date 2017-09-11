---
title: "Operador ^ (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ^_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
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
ms.openlocfilehash: f081dd2979930404639638179444adc05dd462e1
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="69585-102">Operador ^ (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="69585-102">^ Operator (C# Reference)</span></span>
<span data-ttu-id="69585-103">Os operadores binários `^` são predefinidos para os tipos integrais e `bool`.</span><span class="sxs-lookup"><span data-stu-id="69585-103">Binary `^` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="69585-104">Para os tipos integrais, o `^` computa o OR exclusivo bit a bit de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="69585-104">For integral types, `^` computes the bitwise exclusive-OR of its operands.</span></span> <span data-ttu-id="69585-105">Para operandos `bool`, o `^` computa o OR exclusivo lógico de seus operandos; ou seja, o resultado será `true` se e somente se exatamente um dos operandos for `true`.</span><span class="sxs-lookup"><span data-stu-id="69585-105">For `bool` operands, `^` computes the logical exclusive-or of its operands; that is, the result is `true` if and only if exactly one of its operands is `true`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69585-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="69585-106">Remarks</span></span>  
 <span data-ttu-id="69585-107">Os tipos definidos pelo usuário podem sobrecarregar o operador `^` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="69585-107">User-defined types can overload the `^` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="69585-108">As operações em tipos integrais geralmente são permitidas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="69585-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69585-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69585-109">Example</span></span>  
 <span data-ttu-id="69585-110">[!code-cs[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="69585-110">[!code-cs[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]</span></span>  
  
 <span data-ttu-id="69585-111">O cálculo de `0xf8 ^ 0x3f` no exemplo anterior executa um OR exclusivo bit a bit dos dois valores binários a seguir, que correspondem aos valores hexadecimais F8 e 3F:</span><span class="sxs-lookup"><span data-stu-id="69585-111">The computation of `0xf8 ^ 0x3f` in the previous example performs a bitwise exclusive-OR of the following two binary values, which correspond to the hexadecimal values F8 and 3F:</span></span>  
  
 `1111 1000`  
  
 `0011 1111`  
  
 <span data-ttu-id="69585-112">O resultado do OR exclusivo é `1100 0111`, que é igual a C7 em hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="69585-112">The result of the exclusive-OR is `1100 0111`, which is C7 in hexadecimal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69585-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69585-113">See Also</span></span>  
 <span data-ttu-id="69585-114">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="69585-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="69585-115">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="69585-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="69585-116">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="69585-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

