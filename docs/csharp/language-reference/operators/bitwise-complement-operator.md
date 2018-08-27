---
title: Operador ~ (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
ms.openlocfilehash: 8af25217f9e7e66796192783a0b8e3415604dc90
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933176"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="5000e-102">Operador ~ (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="5000e-102">~ Operator (C# Reference)</span></span>
<span data-ttu-id="5000e-103">O operador `~` executa uma operação de complemento bit a bit em seu operando, que tem o efeito de reverter cada bit.</span><span class="sxs-lookup"><span data-stu-id="5000e-103">The `~` operator performs a bitwise complement operation on its operand, which has the effect of reversing each bit.</span></span> <span data-ttu-id="5000e-104">Operadores de complemento bit a bit são predefinidos para [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md) e [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="5000e-104">Bitwise complement operators are predefined for [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), and [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5000e-105">O símbolo `~` também é usado para declarar finalizadores.</span><span class="sxs-lookup"><span data-stu-id="5000e-105">The `~` symbol also is used to declare finalizers.</span></span> <span data-ttu-id="5000e-106">Para mais informações, consulte [Finalizadores](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="5000e-106">For more information, see [Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5000e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="5000e-107">Remarks</span></span>  
 <span data-ttu-id="5000e-108">Os tipos definidos pelo usuário podem sobrecarregar o operador `~`.</span><span class="sxs-lookup"><span data-stu-id="5000e-108">User-defined types can overload the `~` operator.</span></span> <span data-ttu-id="5000e-109">Para obter mais informações, consulte [operador](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="5000e-109">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="5000e-110">As operações em tipos integrais geralmente são permitidas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="5000e-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5000e-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5000e-111">Example</span></span>  
 [!code-csharp[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5000e-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5000e-112">See Also</span></span>

- [<span data-ttu-id="5000e-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="5000e-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="5000e-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="5000e-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="5000e-115">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="5000e-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="5000e-116">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="5000e-116">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
