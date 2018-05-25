---
title: Operadores condicionais nulos (C# e Visual Basic)
ms.date: 04/03/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- null-conditional operators [C#]
- null-conditional operators [Visual Basic]
- ?. operator [C#]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
ms.openlocfilehash: 28cf2633d74f047a751ffdad11f1e1db8328cd6f
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2018
---
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a><span data-ttu-id="bc21e-102">?.</span><span class="sxs-lookup"><span data-stu-id="bc21e-102">?.</span></span> <span data-ttu-id="bc21e-103">Operadores condicionais nulos ?. e ?[] (C# e Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc21e-103">and ?[] null-conditional Operators (C# and Visual Basic)</span></span>
<span data-ttu-id="bc21e-104">Testa o valor do operando esquerdo para nulo antes de executar um acesso de membro (`?.`) ou uma operação de índice (`?[]`); retorna `null` se o operando esquerdo é avaliado como `null`.</span><span class="sxs-lookup"><span data-stu-id="bc21e-104">Tests the value of the left-hand operand for null before performing a member access (`?.`) or index (`?[]`) operation; returns `null` if the left-hand operand evaluates to `null`.</span></span> 

<span data-ttu-id="bc21e-105">Esses operadores ajudam a escrever menos código para lidar com verificações de nulidade, especialmente para entrar em estruturas de dados.</span><span class="sxs-lookup"><span data-stu-id="bc21e-105">These operators help you write less code to handle null checks, especially for descending into data structures.</span></span>  
  
```csharp  
int? length = customers?.Length; // null if customers is null   
Customer first = customers?[0];  // null if customers is null  
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
```  
  
```vb  
Dim length = customers?.Length  ' null if customers is null  
Dim first as Customer = customers?(0)  ' null if customers is null  
Dim count as Integer? = customers?(0)?.Orders?.Count()  ' null if customers, the first customer, or Orders is null  
```  
  
 <span data-ttu-id="bc21e-106">Os operadores condicionais nulos estão entrando em curto-circuito.</span><span class="sxs-lookup"><span data-stu-id="bc21e-106">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="bc21e-107">Se uma operação em uma cadeia de operações de índice e acesso de membro condicionais retornar nulo, o restante da execução da cadeia será interrompido.</span><span class="sxs-lookup"><span data-stu-id="bc21e-107">If one operation in a chain of conditional member access and index operation returns null, then the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="bc21e-108">No exemplo a seguir, `E` não será executado se `A`, `B` ou `C` for avaliado como nulo.</span><span class="sxs-lookup"><span data-stu-id="bc21e-108">In the following example, `E` doesn't execute if `A`, `B`, or `C` evaluates to null.</span></span>
  
```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

```vb
A?.B?.C?.Do(E);
A?.B?.C?(E);
```  
  
 <span data-ttu-id="bc21e-109">Outro uso para o acesso de membro condicional nulo é invocar representantes de forma thread-safe com muito menos código.</span><span class="sxs-lookup"><span data-stu-id="bc21e-109">Another use for the null-conditional member access is invoking delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="bc21e-110">A maneira antiga requer código semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="bc21e-110">The old way requires code like the following:</span></span>  
  
```csharp  
var handler = this.PropertyChanged;  
if (handler != null)  
    handler(…);
```  
  
```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```  
  
 <span data-ttu-id="bc21e-111">A nova maneira é muito mais simples:</span><span class="sxs-lookup"><span data-stu-id="bc21e-111">The new way is much simpler:</span></span>  
  
```csharp
PropertyChanged?.Invoke(…)  
```  

```vb
PropertyChanged?.Invoke(…)
```  
  
 <span data-ttu-id="bc21e-112">A nova forma é thread-safe porque o compilador gera código para avaliar `PropertyChanged` somente uma vez, mantendo o resultado em uma variável temporária.</span><span class="sxs-lookup"><span data-stu-id="bc21e-112">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="bc21e-113">Você precisa chamar explicitamente o método `Invoke` porque não há nenhuma sintaxe de invocação de delegado condicional nulo `PropertyChanged?(e)`.</span><span class="sxs-lookup"><span data-stu-id="bc21e-113">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>  
  
## <a name="language-specifications"></a><span data-ttu-id="bc21e-114">Especificações da linguagem</span><span class="sxs-lookup"><span data-stu-id="bc21e-114">Language Specifications</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 <span data-ttu-id="bc21e-115">Para obter mais informações, consulte [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="bc21e-115">For more information, see the [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc21e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc21e-116">See Also</span></span>  
 [<span data-ttu-id="bc21e-117">?? (operador de união nula)</span><span class="sxs-lookup"><span data-stu-id="bc21e-117">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)  
 [<span data-ttu-id="bc21e-118">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="bc21e-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bc21e-119">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="bc21e-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bc21e-120">Guia de programação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bc21e-120">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
