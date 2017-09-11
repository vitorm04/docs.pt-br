---
title: Operadores condicionais nulos (C# e Visual Basic)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
caps.latest.revision: 3
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
ms.sourcegitcommit: 6118956a5681ddbeb110f6e01f090b85cdd65089
ms.openlocfilehash: 465a395a33c027132b7890e02d540438096e2073
ms.contentlocale: pt-br
ms.lasthandoff: 08/23/2017

---
# <a name="null-conditional-operators-c-and-visual-basic"></a><span data-ttu-id="e5763-102">Operadores condicionais nulos (C# e Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5763-102">Null-conditional Operators (C# and Visual Basic)</span></span>
<span data-ttu-id="e5763-103">Usado para testar a presença de nulos antes de executar uma operação de acesso de membro (`?.`) ou de índice (`?[`).</span><span class="sxs-lookup"><span data-stu-id="e5763-103">Used to test for null before performing a member access (`?.`) or index (`?[`) operation.</span></span>  <span data-ttu-id="e5763-104">Esses operadores ajudam a escrever menos código para lidar com verificações de nulidade, especialmente para entrar em estruturas de dados.</span><span class="sxs-lookup"><span data-stu-id="e5763-104">These operators help you write less code to handle null checks, especially for descending into data structures.</span></span>  
  
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
  
 <span data-ttu-id="e5763-105">O último exemplo demonstra que os operadores condicionais nulos estão em curto-circuito.</span><span class="sxs-lookup"><span data-stu-id="e5763-105">The last example demonstrates that the null-condition operators are short-circuiting.</span></span>  <span data-ttu-id="e5763-106">Se uma operação em uma cadeia de operações de índice e acesso de membro condicionais retornar nulo, o restante da execução da cadeia será interrompido.</span><span class="sxs-lookup"><span data-stu-id="e5763-106">If one operation in a chain of conditional member access and index operation returns null, then the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="e5763-107">Outras operações com menor precedência na expressão continuarão.</span><span class="sxs-lookup"><span data-stu-id="e5763-107">Other operations with lower precedence in the expression continue.</span></span>  <span data-ttu-id="e5763-108">Por exemplo, `E` a seguir, executa na segunda linha, e as operações `??` e `==` são executadas.</span><span class="sxs-lookup"><span data-stu-id="e5763-108">For example, `E` in the following executes in the second line, and the `??` and `==` operations execute.</span></span>  <span data-ttu-id="e5763-109">Na primeira linha, o `??` entra em curto circuito e `E` não é executado quando o lado esquerdo é avaliado como não nulo.</span><span class="sxs-lookup"><span data-stu-id="e5763-109">In the first line, the `??` short circuits and `E` does not execute when the left side evaluates to non-null.</span></span>
  
```csharp
A?.B?.C?[0] ?? E  
A?.B?.C?[0] == E  
```

```vb
A?.B?.C?(0) ?? E  
A?.B?.C?(0) == E  
```  
  
 <span data-ttu-id="e5763-110">Outro uso para o acesso de membro condicional nulo é invocar representantes de forma thread-safe com muito menos código.</span><span class="sxs-lookup"><span data-stu-id="e5763-110">Another use for the null-condition member access is invoking delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="e5763-111">A maneira antiga requer código semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="e5763-111">The old way requires code like the following:</span></span>  
  
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
  
 <span data-ttu-id="e5763-112">A nova maneira é muito mais simples:</span><span class="sxs-lookup"><span data-stu-id="e5763-112">The new way is much simpler:</span></span>  
  
```csharp
PropertyChanged?.Invoke(e)  
```  

```vb
PropertyChanged?.Invoke(e)
```  
  
 <span data-ttu-id="e5763-113">A nova forma é thread-safe porque o compilador gera código para avaliar `PropertyChanged` somente uma vez, mantendo o resultado em uma variável temporária.</span><span class="sxs-lookup"><span data-stu-id="e5763-113">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span>  
  
 <span data-ttu-id="e5763-114">Você precisa chamar explicitamente o método `Invoke` porque não há nenhuma sintaxe de invocação de delegado condicional nulo `PropertyChanged?(e)`.</span><span class="sxs-lookup"><span data-stu-id="e5763-114">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>  <span data-ttu-id="e5763-115">Havia muitas situações de análise ambíguas para permitir isso.</span><span class="sxs-lookup"><span data-stu-id="e5763-115">There were too many ambiguous parsing situations to allow it.</span></span>  
  
## <a name="language-specifications"></a><span data-ttu-id="e5763-116">Especificações da linguagem</span><span class="sxs-lookup"><span data-stu-id="e5763-116">Language Specifications</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 <span data-ttu-id="e5763-117">Para obter mais informações, consulte [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="e5763-117">For more information, see the [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5763-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5763-118">See Also</span></span>  
 <span data-ttu-id="e5763-119">[?? (operador de união nula)](null-conditional-operator.md) </span><span class="sxs-lookup"><span data-stu-id="e5763-119">[?? (null-coalescing operator)](null-conditional-operator.md) </span></span>  
 <span data-ttu-id="e5763-120">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="e5763-120">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="e5763-121">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e5763-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="e5763-122">[Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="e5763-122">[Visual Basic Language Reference](../../../visual-basic/language-reference/index.md) </span></span>  
 [<span data-ttu-id="e5763-123">Guia de programação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e5763-123">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)

