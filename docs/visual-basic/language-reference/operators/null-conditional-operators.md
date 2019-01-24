---
title: Operadores condicionais nulos (Visual Basic)
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: d30d452a7c140a0c56529386b14ef3a3512df490
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722147"
---
# <a name="-and--null-conditional-operators-visual-basic"></a><span data-ttu-id="6203b-102">?.</span><span class="sxs-lookup"><span data-stu-id="6203b-102">?.</span></span> <span data-ttu-id="6203b-103">e? operadores nulo-condicional de () (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6203b-103">and ?() null-conditional operators (Visual Basic)</span></span>

<span data-ttu-id="6203b-104">Testa o valor do operando esquerdo para nulo (`Nothing`) antes de executar um acesso de membro (`?.`) ou um índice (`?()`) da operação; retorna `Nothing` se o operando esquerdo for avaliado como `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="6203b-104">Tests the value of the left-hand operand for null (`Nothing`) before performing a member access (`?.`) or index (`?()`) operation; returns `Nothing` if the left-hand operand evaluates to `Nothing`.</span></span> <span data-ttu-id="6203b-105">Observe que, nas expressões que normalmente retornaria tipos de valor, o operador nulo condicional retorna a um <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="6203b-105">Note that, in the expressions that would ordinarily return value types, the null-conditional operator returns a <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="6203b-106">Esses operadores ajudam a escrever menos código para lidar com verificações nulas, especialmente quando em ordem decrescente em estruturas de dados.</span><span class="sxs-lookup"><span data-stu-id="6203b-106">These operators help you write less code to handle null checks, especially when descending into data structures.</span></span> <span data-ttu-id="6203b-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6203b-107">For example:</span></span>

```vb
Dim length As Integer? = customers?.Length  ' Nothing if customers is Nothing  
Dim first As Customer = customers?(0)  ' Nothing if customers is Nothing  
Dim count As Integer? = customers?(0)?.Orders?.Count()  ' Nothing if customers, the first customer, or Orders is Nothing  
```

<span data-ttu-id="6203b-108">Para comparação, o código alternativo para a primeira dessas expressões sem um operador nulo condicional é:</span><span class="sxs-lookup"><span data-stu-id="6203b-108">For comparison, the alternative code for the first of these expressions without a null-conditional operator is:</span></span>

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

<span data-ttu-id="6203b-109">Os operadores condicionais nulos estão entrando em curto-circuito.</span><span class="sxs-lookup"><span data-stu-id="6203b-109">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="6203b-110">Se uma operação em uma cadeia de operações de índice e acesso de membro condicional não retorne nada, o restante da execução da cadeia será interrompida.</span><span class="sxs-lookup"><span data-stu-id="6203b-110">If one operation in a chain of conditional member access and index operations returns Nothing, the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="6203b-111">No exemplo a seguir, c (e) não é avaliado, se `A`, `B`, ou `C` for avaliada como nada.</span><span class="sxs-lookup"><span data-stu-id="6203b-111">In the following example, C(E) isn't evaluated if `A`, `B`, or `C` evaluates to Nothing.</span></span>

```vb
A?.B?.C?(E);
```

<span data-ttu-id="6203b-112">Outro uso para acesso de membro condicional nulo é invocar representantes de forma thread-safe com muito menos código.</span><span class="sxs-lookup"><span data-stu-id="6203b-112">Another use for null-conditional member access is to invoke delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="6203b-113">A maneira antiga requer código semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="6203b-113">The old way requires code like the following:</span></span>  

```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```

<span data-ttu-id="6203b-114">A nova maneira é muito mais simples:</span><span class="sxs-lookup"><span data-stu-id="6203b-114">The new way is much simpler:</span></span>  

```vb
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="6203b-115">A nova forma é thread-safe porque o compilador gera código para avaliar `PropertyChanged` somente uma vez, mantendo o resultado em uma variável temporária.</span><span class="sxs-lookup"><span data-stu-id="6203b-115">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="6203b-116">Você precisa chamar explicitamente o método `Invoke` porque não há nenhuma sintaxe de invocação de delegado condicional nulo `PropertyChanged?(e)`.</span><span class="sxs-lookup"><span data-stu-id="6203b-116">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>  

## <a name="see-also"></a><span data-ttu-id="6203b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6203b-117">See also</span></span>

- [<span data-ttu-id="6203b-118">Operadores (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6203b-118">Operators (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="6203b-119">Guia de programação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6203b-119">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="6203b-120">Referência da linguagem Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6203b-120">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
