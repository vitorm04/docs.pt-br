---
title: "?? Operador (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1a49d36b8580812c08e9ee080a9602d9fc2027ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="4013e-103">??</span><span class="sxs-lookup"><span data-stu-id="4013e-103">??</span></span> <span data-ttu-id="4013e-104">Operador (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="4013e-104">Operator (C# Reference)</span></span>
<span data-ttu-id="4013e-105">O operador `??` é chamado operador de coalescência nula.</span><span class="sxs-lookup"><span data-stu-id="4013e-105">The `??` operator is called the null-coalescing operator.</span></span>  <span data-ttu-id="4013e-106">Ele retornará o operando esquerdo se o operando não for nulo; caso contrário, ele retornará o operando direito.</span><span class="sxs-lookup"><span data-stu-id="4013e-106">It returns the left-hand operand if the operand is not null; otherwise it returns the right hand operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4013e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="4013e-107">Remarks</span></span>  
 <span data-ttu-id="4013e-108">Um tipo anulável pode representar um valor de domínio do tipo ou o valor pode ser indefinido (nesse caso, o valor será nulo).</span><span class="sxs-lookup"><span data-stu-id="4013e-108">A nullable type can represent a value from the type’s domain, or the value can be undefined (in which case the value is null).</span></span> <span data-ttu-id="4013e-109">Você pode usar o `??` a expressividade sintática do operador para retornar um valor apropriado (o operando direito) quando o operando esquerdo tenha um tipo anulável cujo valor é nulo.</span><span class="sxs-lookup"><span data-stu-id="4013e-109">You can use the `??` operator’s syntactic expressiveness to return an appropriate value (the right hand operand) when the left operand has a nullable type whose value is null.</span></span> <span data-ttu-id="4013e-110">Se você tentar atribuir um tipo de valor anulável a um tipo de valor não anulável sem usar o operador `??`, um erro de tempo de compilação será gerado.</span><span class="sxs-lookup"><span data-stu-id="4013e-110">If you try to assign a nullable value type to a non-nullable value type without using the `??` operator, you will generate a compile-time error.</span></span> <span data-ttu-id="4013e-111">Se você usar uma conversão e o tipo de valor anulável estiver atualmente indefinido, uma exceção `InvalidOperationException` será acionada.</span><span class="sxs-lookup"><span data-stu-id="4013e-111">If you use a cast, and the nullable value type is currently undefined, an `InvalidOperationException` exception will be thrown.</span></span>  
  
 <span data-ttu-id="4013e-112">Para obter mais informações, consulte [Nullable Types (Tipos que permitem valores nulos)](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="4013e-112">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="4013e-113">O resultado de um operador</span><span class="sxs-lookup"><span data-stu-id="4013e-113">The result of a ??</span></span> <span data-ttu-id="4013e-114">?? não será considerado constante, mesmo se os dois argumentos forem constantes.</span><span class="sxs-lookup"><span data-stu-id="4013e-114">operator is not considered to be a constant even if both its arguments are constants.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4013e-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4013e-115">Example</span></span>  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4013e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4013e-116">See Also</span></span>  
 [<span data-ttu-id="4013e-117">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="4013e-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4013e-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="4013e-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4013e-119">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="4013e-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="4013e-120">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="4013e-120">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="4013e-121">O que exatamente “levantado” significa?</span><span class="sxs-lookup"><span data-stu-id="4013e-121">What Exactly Does 'Lifted' mean?</span></span>](http://go.microsoft.com/fwlink/?LinkID=112382)
