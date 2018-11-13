---
title: ?? Operador (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: fbcfda07cc55628aeed82eb7561516f7012bc4fe
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2018
ms.locfileid: "50980668"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="22f80-103">??</span><span class="sxs-lookup"><span data-stu-id="22f80-103">??</span></span> <span data-ttu-id="22f80-104">Operador (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="22f80-104">Operator (C# Reference)</span></span>
<span data-ttu-id="22f80-105">O operador `??` é chamado operador de coalescência nula.</span><span class="sxs-lookup"><span data-stu-id="22f80-105">The `??` operator is called the null-coalescing operator.</span></span>  <span data-ttu-id="22f80-106">Ele retornará o operando esquerdo se o operando não for nulo; caso contrário, ele retornará o operando direito.</span><span class="sxs-lookup"><span data-stu-id="22f80-106">It returns the left-hand operand if the operand is not null; otherwise it returns the right hand operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22f80-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="22f80-107">Remarks</span></span>  
 <span data-ttu-id="22f80-108">Um tipo anulável pode representar um valor de domínio do tipo ou o valor pode ser indefinido (nesse caso, o valor será nulo).</span><span class="sxs-lookup"><span data-stu-id="22f80-108">A nullable type can represent a value from the type’s domain, or the value can be undefined (in which case the value is null).</span></span> <span data-ttu-id="22f80-109">Você pode usar a expressividade sintática do operador `??` para retornar um valor adequado (o operando direito) quando o operando esquerdo tiver um tipo que permite valor nulo cujo valor seja nulo.</span><span class="sxs-lookup"><span data-stu-id="22f80-109">You can use the `??` operator’s syntactic expressiveness to return an appropriate value (the right hand operand) when the left operand has a nullable type whose value is null.</span></span> <span data-ttu-id="22f80-110">Se você tentar atribuir um tipo de valor anulável a um tipo de valor não anulável sem usar o operador `??`, um erro de tempo de compilação será gerado.</span><span class="sxs-lookup"><span data-stu-id="22f80-110">If you try to assign a nullable value type to a non-nullable value type without using the `??` operator, you will generate a compile-time error.</span></span> <span data-ttu-id="22f80-111">Se você usar uma conversão e o tipo de valor anulável estiver atualmente indefinido, uma exceção `InvalidOperationException` será acionada.</span><span class="sxs-lookup"><span data-stu-id="22f80-111">If you use a cast, and the nullable value type is currently undefined, an `InvalidOperationException` exception will be thrown.</span></span>  
  
 <span data-ttu-id="22f80-112">Para obter mais informações, consulte [Tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="22f80-112">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="22f80-113">O resultado de um operador</span><span class="sxs-lookup"><span data-stu-id="22f80-113">The result of a ??</span></span> <span data-ttu-id="22f80-114">?? não será considerado constante, mesmo se os dois argumentos forem constantes.</span><span class="sxs-lookup"><span data-stu-id="22f80-114">operator is not considered to be a constant even if both its arguments are constants.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22f80-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="22f80-115">Example</span></span>  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="22f80-116">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="22f80-116">C# Language Specification</span></span>  

<span data-ttu-id="22f80-117">Para obter mais informações, veja [O operador coalescente nulo](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) na [Especificação da Linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="22f80-117">For more information, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="22f80-118">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="22f80-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="22f80-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22f80-119">See Also</span></span>

- [<span data-ttu-id="22f80-120">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="22f80-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="22f80-121">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="22f80-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="22f80-122">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="22f80-122">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="22f80-123">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="22f80-123">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
- [<span data-ttu-id="22f80-124">O que exatamente “levantado” significa?</span><span class="sxs-lookup"><span data-stu-id="22f80-124">What Exactly Does 'Lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
