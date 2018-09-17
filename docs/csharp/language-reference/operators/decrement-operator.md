---
title: Operador -- (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
ms.openlocfilehash: 615b100447233856ab3740d075d69e3ae19285fd
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45648776"
---
# <a name="---operator-c-reference"></a><span data-ttu-id="3ed0b-102">Operador -- (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="3ed0b-102">-- Operator (C# Reference)</span></span>
<span data-ttu-id="3ed0b-103">O operador de decremento (`--`) decrementa o operando em 1.</span><span class="sxs-lookup"><span data-stu-id="3ed0b-103">The decrement operator (`--`) decrements its operand by 1.</span></span> <span data-ttu-id="3ed0b-104">O operador de decremento pode aparecer antes ou depois de seu operando: `--variable` e `variable--`.</span><span class="sxs-lookup"><span data-stu-id="3ed0b-104">The decrement operator can appear before or after its operand: `--variable` and `variable--`.</span></span> <span data-ttu-id="3ed0b-105">A primeira forma é uma operação de decremento de prefixo.</span><span class="sxs-lookup"><span data-stu-id="3ed0b-105">The first form is a prefix decrement operation.</span></span> <span data-ttu-id="3ed0b-106">O resultado da operação será o valor do operando "depois" que ele for decrementado.</span><span class="sxs-lookup"><span data-stu-id="3ed0b-106">The result of the operation is the value of the operand "after" it has been decremented.</span></span> <span data-ttu-id="3ed0b-107">A segunda forma é uma operação de decremento sufixo.</span><span class="sxs-lookup"><span data-stu-id="3ed0b-107">The second form is a postfix decrement operation.</span></span> <span data-ttu-id="3ed0b-108">O resultado da operação será o valor do operando "antes" de ser decrementado.</span><span class="sxs-lookup"><span data-stu-id="3ed0b-108">The result of the operation is the value of the operand "before" it has been decremented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ed0b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="3ed0b-109">Remarks</span></span>  
 <span data-ttu-id="3ed0b-110">Tipos numéricos e de enumeração têm operadores de decremento predefinidos.</span><span class="sxs-lookup"><span data-stu-id="3ed0b-110">Numeric and enumeration types have predefined decrement operators.</span></span>  
  
 <span data-ttu-id="3ed0b-111">Os tipos definidos pelo usuário podem sobrecarregar o operador `--` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="3ed0b-111">User-defined types can overload the `--` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="3ed0b-112">As operações em tipos integrais geralmente são permitidas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="3ed0b-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ed0b-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3ed0b-113">Example</span></span>  
 [!code-csharp[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3ed0b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ed0b-114">See Also</span></span>

- [<span data-ttu-id="3ed0b-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="3ed0b-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="3ed0b-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="3ed0b-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="3ed0b-117">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="3ed0b-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
