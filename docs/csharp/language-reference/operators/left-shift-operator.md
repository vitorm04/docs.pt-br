---
title: Operador &lt;&lt; (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: 036acd6159bcf5ca1677ee6383c9db357625cd67
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677377"
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="10e7e-102">Operador &lt;&lt; (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="10e7e-102">&lt;&lt; Operator (C# Reference)</span></span>
<span data-ttu-id="10e7e-103">O operador de deslocamento para a esquerda (`<<`) desloca o primeiro operando à esquerda pelo número de bits especificado pelo segundo operando.</span><span class="sxs-lookup"><span data-stu-id="10e7e-103">The left-shift operator (`<<`) shifts its first operand left by the number of bits specified by its second operand.</span></span> <span data-ttu-id="10e7e-104">O tipo do segundo operando deve ser um [int](../../../csharp/language-reference/keywords/int.md) ou um tipo que tem uma conversão numérica implícita predefinida para `int`.</span><span class="sxs-lookup"><span data-stu-id="10e7e-104">The type of the second operand must be an [int](../../../csharp/language-reference/keywords/int.md) or a type that has a predefined implicit numeric conversion to `int`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10e7e-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="10e7e-105">Remarks</span></span>  
 <span data-ttu-id="10e7e-106">Se o primeiro operando for um [int](../../../csharp/language-reference/keywords/int.md) ou [uint](../../../csharp/language-reference/keywords/uint.md) (quantidade de 32 bits), a contagem de deslocamento será determinada pelos cinco bits de ordem inferior do segundo operando.</span><span class="sxs-lookup"><span data-stu-id="10e7e-106">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand.</span></span> <span data-ttu-id="10e7e-107">Ou seja, a contagem real de deslocamento é de 0 a 31 bits.</span><span class="sxs-lookup"><span data-stu-id="10e7e-107">That is, the actual shift count is 0 to 31 bits.</span></span>  
  
 <span data-ttu-id="10e7e-108">Se o primeiro operando for um [long](../../../csharp/language-reference/keywords/long.md) ou [ulong](../../../csharp/language-reference/keywords/ulong.md) (quantidade de 64 bits), a contagem de deslocamento será determinada pelos seis bits de ordem inferior do segundo operando.</span><span class="sxs-lookup"><span data-stu-id="10e7e-108">If the first operand is a [long](../../../csharp/language-reference/keywords/long.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand.</span></span> <span data-ttu-id="10e7e-109">Ou seja, a contagem real de deslocamento é de 0 a 63 bits.</span><span class="sxs-lookup"><span data-stu-id="10e7e-109">That is, the actual shift count is 0 to 63 bits.</span></span>  
  
 <span data-ttu-id="10e7e-110">Quaisquer bits de ordem superior que não estão dentro do intervalo do tipo do primeiro operando após a mudança são descartados e os bits vazios de ordem inferior são preenchidos com zeros.</span><span class="sxs-lookup"><span data-stu-id="10e7e-110">Any high-order bits that are not within the range of the type of the first operand after the shift are discarded, and the low-order empty bits are zero-filled.</span></span> <span data-ttu-id="10e7e-111">As operações de deslocamento nunca causam estouros.</span><span class="sxs-lookup"><span data-stu-id="10e7e-111">Shift operations never cause overflows.</span></span>  
  
 <span data-ttu-id="10e7e-112">Tipos definidos pelo usuário podem sobrecarregar o operador `<<` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)); o tipo do primeiro operando deve ser o tipo definido pelo usuário e o tipo do segundo operando deve ser `int`.</span><span class="sxs-lookup"><span data-stu-id="10e7e-112">User-defined types can overload the `<<` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)); the type of the first operand must be the user-defined type, and the type of the second operand must be `int`.</span></span> <span data-ttu-id="10e7e-113">Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="10e7e-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10e7e-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="10e7e-114">Example</span></span>  
 [!code-csharp[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]  
  
## <a name="comments"></a><span data-ttu-id="10e7e-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="10e7e-115">Comments</span></span>  
 <span data-ttu-id="10e7e-116">Observe que `i<<1` e `i<<33` fornecem o mesmo resultado, porque 1 e 33 têm os mesmos cinco bits de ordem inferior.</span><span class="sxs-lookup"><span data-stu-id="10e7e-116">Note that `i<<1` and `i<<33` give the same result, because 1 and 33 have the same low-order five bits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10e7e-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10e7e-117">See Also</span></span>

- [<span data-ttu-id="10e7e-118">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="10e7e-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="10e7e-119">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="10e7e-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="10e7e-120">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="10e7e-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
