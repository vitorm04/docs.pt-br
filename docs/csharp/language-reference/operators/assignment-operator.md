---
title: Operador = (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 979250c91cfe2abdf7295ae3866cd6b4294285cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269274"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="430ea-102">Operador = (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="430ea-102">= Operator (C# Reference)</span></span>
<span data-ttu-id="430ea-103">O operador de atribuição (`=`) armazena o valor do operando direito no local de armazenamento, propriedade ou indexador indicado pelo operando esquerdo e retorna o valor como resultado.</span><span class="sxs-lookup"><span data-stu-id="430ea-103">The assignment operator (`=`) stores the value of its right-hand operand in the storage location, property, or indexer denoted by its left-hand operand and returns the value as its result.</span></span> <span data-ttu-id="430ea-104">Os operandos devem ser do mesmo tipo (ou o operando direito deve ser implicitamente conversível para o tipo do operando esquerdo).</span><span class="sxs-lookup"><span data-stu-id="430ea-104">The operands must be of the same type (or the right-hand operand must be implicitly convertible to the type of the left-hand operand).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="430ea-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="430ea-105">Remarks</span></span>  
 <span data-ttu-id="430ea-106">O operador de atribuição não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="430ea-106">The assignment operator cannot be overloaded.</span></span> <span data-ttu-id="430ea-107">No entanto, é possível definir operadores de conversão implícita para um tipo, o que permite usar o operador de atribuição com esses tipos.</span><span class="sxs-lookup"><span data-stu-id="430ea-107">However, you can define implicit conversion operators for a type, which enable you to use the assignment operator with those types.</span></span> <span data-ttu-id="430ea-108">Para obter mais informações, consulte [Usando Operadores de Conversão](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="430ea-108">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="430ea-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="430ea-109">Example</span></span>  
 [!code-csharp[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="430ea-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="430ea-110">See Also</span></span>  
 [<span data-ttu-id="430ea-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="430ea-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="430ea-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="430ea-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="430ea-113">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="430ea-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
