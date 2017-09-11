---
title: "Operador = (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- =_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
caps.latest.revision: 14
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
ms.openlocfilehash: e40b2f221717461443a5d0247b3401eb527a7b5a
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="22dc4-102">Operador = (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="22dc4-102">= Operator (C# Reference)</span></span>
<span data-ttu-id="22dc4-103">O operador de atribuição (`=`) armazena o valor do operando direito no local de armazenamento, propriedade ou indexador indicado pelo operando esquerdo e retorna o valor como resultado.</span><span class="sxs-lookup"><span data-stu-id="22dc4-103">The assignment operator (`=`) stores the value of its right-hand operand in the storage location, property, or indexer denoted by its left-hand operand and returns the value as its result.</span></span> <span data-ttu-id="22dc4-104">Os operandos devem ser do mesmo tipo (ou o operando direito deve ser implicitamente conversível para o tipo do operando esquerdo).</span><span class="sxs-lookup"><span data-stu-id="22dc4-104">The operands must be of the same type (or the right-hand operand must be implicitly convertible to the type of the left-hand operand).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22dc4-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="22dc4-105">Remarks</span></span>  
 <span data-ttu-id="22dc4-106">O operador de atribuição não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="22dc4-106">The assignment operator cannot be overloaded.</span></span> <span data-ttu-id="22dc4-107">No entanto, é possível definir operadores de conversão implícita para um tipo, o que permite usar o operador de atribuição com esses tipos.</span><span class="sxs-lookup"><span data-stu-id="22dc4-107">However, you can define implicit conversion operators for a type, which enable you to use the assignment operator with those types.</span></span> <span data-ttu-id="22dc4-108">Para obter mais informações, consulte [Usando Operadores de Conversão](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="22dc4-108">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="22dc4-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="22dc4-109">Example</span></span>  
 <span data-ttu-id="22dc4-110">[!code-cs[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="22dc4-110">[!code-cs[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22dc4-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22dc4-111">See Also</span></span>  
 <span data-ttu-id="22dc4-112">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="22dc4-112">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="22dc4-113">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="22dc4-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="22dc4-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="22dc4-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

