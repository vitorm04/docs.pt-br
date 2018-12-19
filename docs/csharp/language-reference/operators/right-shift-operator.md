---
title: Operador &gt;&gt; – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: fc3d683f212c71620049ec6adee3d20bd5c1437c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239989"
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="679f0-102">Operador &gt;&gt; (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="679f0-102">&gt;&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="679f0-103">O operador de deslocamento para a direita (`>>`) desloca o primeiro operando à direita pelo número de bits especificado pelo seu segundo operando.</span><span class="sxs-lookup"><span data-stu-id="679f0-103">The right-shift operator (`>>`) shifts its first operand right by the number of bits specified by its second operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="679f0-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="679f0-104">Remarks</span></span>  
 <span data-ttu-id="679f0-105">Se o primeiro operando for um [int](../../../csharp/language-reference/keywords/int.md) ou [uint](../../../csharp/language-reference/keywords/uint.md) (quantidade de 32 bits), a contagem de deslocamento será determinada pelos cinco bits de ordem inferior do segundo operando (segundo operando &0x1f).</span><span class="sxs-lookup"><span data-stu-id="679f0-105">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand (second operand & 0x1f).</span></span>  
  
 <span data-ttu-id="679f0-106">Se o primeiro operando for um [long](../../../csharp/language-reference/keywords/long.md) ou [ulong](../../../csharp/language-reference/keywords/ulong.md) (quantidade de 64 bits), a contagem de deslocamento será determinada pelos seis bits de ordem inferior do segundo operando (segundo operando & 0x3f).</span><span class="sxs-lookup"><span data-stu-id="679f0-106">If the first operand is a [long](../../../csharp/language-reference/keywords/long.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand (second operand & 0x3f).</span></span>  
  
 <span data-ttu-id="679f0-107">Se o primeiro operando for um [int](../../../csharp/language-reference/keywords/int.md) ou [long](../../../csharp/language-reference/keywords/long.md), o deslocamento para a direita será um deslocamento aritmético (bits vazios de ordem superior devem ser definidos como o bit de sinal).</span><span class="sxs-lookup"><span data-stu-id="679f0-107">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [long](../../../csharp/language-reference/keywords/long.md), the right-shift is an arithmetic shift (high-order empty bits are set to the sign bit).</span></span> <span data-ttu-id="679f0-108">Se o primeiro operando for do tipo [uint](../../../csharp/language-reference/keywords/uint.md) ou [ulong](../../../csharp/language-reference/keywords/ulong.md), o deslocamento para a direita será um deslocamento lógico (bits de ordem superior são preenchidos com zero).</span><span class="sxs-lookup"><span data-stu-id="679f0-108">If the first operand is of type [uint](../../../csharp/language-reference/keywords/uint.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md), the right-shift is a logical shift (high-order bits are zero-filled).</span></span>  
  
 <span data-ttu-id="679f0-109">Tipos definidos pelo usuário podem sobrecarregar o operador `>>`; o tipo do primeiro operando deve ser o tipo definido pelo usuário e o tipo do segundo operando deve ser [int](../../../csharp/language-reference/keywords/int.md). Para obter mais informações, consulte [operador](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="679f0-109">User-defined types can overload the `>>` operator; the type of the first operand must be the user-defined type, and the type of the second operand must be [int](../../../csharp/language-reference/keywords/int.md). For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="679f0-110">Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="679f0-110">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="679f0-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="679f0-111">Example</span></span>  
 [!code-csharp[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="679f0-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="679f0-112">See Also</span></span>

- [<span data-ttu-id="679f0-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="679f0-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="679f0-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="679f0-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="679f0-115">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="679f0-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
