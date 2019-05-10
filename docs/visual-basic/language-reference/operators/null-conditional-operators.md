---
title: Operadores condicionais nulos (Visual Basic)
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: 4815fe7ad337634cfb56127fbd24a47a37fdd74b
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65062935"
---
# <a name="-and--null-conditional-operators-visual-basic"></a><span data-ttu-id="e6f90-102">?.</span><span class="sxs-lookup"><span data-stu-id="e6f90-102">?.</span></span> <span data-ttu-id="e6f90-103">e? operadores nulo-condicional de () (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6f90-103">and ?() null-conditional operators (Visual Basic)</span></span>

<span data-ttu-id="e6f90-104">Testa o valor do operando esquerdo para nulo (`Nothing`) antes de executar um acesso de membro (`?.`) ou um índice (`?()`) da operação; retorna `Nothing` se o operando esquerdo for avaliado como `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="e6f90-104">Tests the value of the left-hand operand for null (`Nothing`) before performing a member access (`?.`) or index (`?()`) operation; returns `Nothing` if the left-hand operand evaluates to `Nothing`.</span></span> <span data-ttu-id="e6f90-105">Observe que, em expressões que normalmente retornam tipos de valor, o operador nulo condicional retorna uma <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="e6f90-105">Note that in expressions that ordinarily return value types, the null-conditional operator returns a <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="e6f90-106">Esses operadores ajudam a escrever menos código para lidar com verificações nulas, especialmente quando em ordem decrescente em estruturas de dados.</span><span class="sxs-lookup"><span data-stu-id="e6f90-106">These operators help you write less code to handle null checks, especially when descending into data structures.</span></span> <span data-ttu-id="e6f90-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e6f90-107">For example:</span></span>

```vb
' Nothing if customers is Nothing  
Dim length As Integer? = customers?.Length  

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()   
```

<span data-ttu-id="e6f90-108">Para comparação, o código alternativo para a primeira dessas expressões sem um operador nulo condicional é:</span><span class="sxs-lookup"><span data-stu-id="e6f90-108">For comparison, the alternative code for the first of these expressions without a null-conditional operator is:</span></span>

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

<span data-ttu-id="e6f90-109">Às vezes você precisa executar uma ação em um objeto que pode ser nulo, com base no valor de um membro booleano naquele objeto (como a propriedade booliana `IsAllowedFreeShipping` no exemplo a seguir):</span><span class="sxs-lookup"><span data-stu-id="e6f90-109">Sometimes you need to take an action on an object that may be null, based on the value of a Boolean member on that object (like the Boolean property `IsAllowedFreeShipping` in the following example):</span></span>

```vb
  Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.
  
  If customer IsNot Nothing AndAlso customer.IsAllowedFreeShipping Then
   ApplyFreeShippingToOrders(customer)
  End If
```

<span data-ttu-id="e6f90-110">Você pode reduzir o seu código e evitar manualmente a verificação de null, usando o operador nulo condicional da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e6f90-110">You can shorten your code and avoid manually checking for null by using the null-conditional operator as follows:</span></span>

```vb
 Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.
 
 If customer?.IsAllowedFreeShipping Then ApplyFreeShippingToOrders(customer)
```

<span data-ttu-id="e6f90-111">Os operadores condicionais nulos estão entrando em curto-circuito.</span><span class="sxs-lookup"><span data-stu-id="e6f90-111">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="e6f90-112">Se uma operação em uma cadeia de operações de índice e acesso de membro condicionais retornar `Nothing`, o restante das paradas de execução da cadeia.</span><span class="sxs-lookup"><span data-stu-id="e6f90-112">If one operation in a chain of conditional member access and index operations returns `Nothing`, the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="e6f90-113">No exemplo a seguir `C(E)` não é avaliado se `A`, `B`, ou `C` for avaliada como `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="e6f90-113">In the following example, `C(E)` isn't evaluated if `A`, `B`, or `C` evaluates to `Nothing`.</span></span>

```vb
A?.B?.C?(E);
```

<span data-ttu-id="e6f90-114">Outro uso para acesso de membro condicional nulo é invocar representantes de forma thread-safe com muito menos código.</span><span class="sxs-lookup"><span data-stu-id="e6f90-114">Another use for null-conditional member access is to invoke delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="e6f90-115">O exemplo a seguir define dois tipos, uma `NewsBroadcaster` e um `NewsReceiver`.</span><span class="sxs-lookup"><span data-stu-id="e6f90-115">The following example defines two types, a `NewsBroadcaster` and a `NewsReceiver`.</span></span> <span data-ttu-id="e6f90-116">Itens de notícias são enviados para o receptor pela `NewsBroadcaster.SendNews` delegar.</span><span class="sxs-lookup"><span data-stu-id="e6f90-116">News items are sent to the receiver by the `NewsBroadcaster.SendNews` delegate.</span></span>

```vb
Public Module NewsBroadcaster
   Dim SendNews As Action(Of String) 

   Public Sub Main()
      Dim rec As New NewsReceiver()
      Dim rec2 As New NewsReceiver()
      SendNews?.Invoke("Just in: A newsworthy item...")
   End Sub

   Public Sub Register(client As Action(Of String))
      SendNews = SendNews.Combine({SendNews, client})
   End Sub
End Module

Public Class NewsReceiver
   Public Sub New()
      NewsBroadcaster.Register(AddressOf Me.DisplayNews)
   End Sub

   Public Sub DisplayNews(newsItem As String)
      Console.WriteLine(newsItem)
   End Sub
End Class
```

<span data-ttu-id="e6f90-117">Se não houver nenhum elemento na `SendNews` lista de invocação, o `SendNews` delegar lança um <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="e6f90-117">If there are no elements in the `SendNews` invocation list, the `SendNews` delegate throws a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="e6f90-118">Antes de operadores condicionais nulos, de código, como a seguir garante que a lista de invocação de delegado não era `Nothing`:</span><span class="sxs-lookup"><span data-stu-id="e6f90-118">Before null conditional operators, code like the following ensured that the delegate invocation list was not `Nothing`:</span></span>

```vb  
SendNews = SendNews.Combine({SendNews, client})  
If SendNews IsNot Nothing Then 
   SendNews("Just in...")
End If
```

<span data-ttu-id="e6f90-119">A nova maneira é muito mais simples:</span><span class="sxs-lookup"><span data-stu-id="e6f90-119">The new way is much simpler:</span></span>  

```vb
SendNews = SendNews.Combine({SendNews, client})  
SendNews?.Invoke("Just in...")
```

<span data-ttu-id="e6f90-120">A nova forma é thread-safe porque o compilador gera código para avaliar `SendNews` somente uma vez, mantendo o resultado em uma variável temporária.</span><span class="sxs-lookup"><span data-stu-id="e6f90-120">The new way is thread-safe because the compiler generates code to evaluate `SendNews` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="e6f90-121">Você precisa chamar explicitamente o método `Invoke` porque não há nenhuma sintaxe de invocação de delegado condicional nulo `SendNews?(String)`.</span><span class="sxs-lookup"><span data-stu-id="e6f90-121">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `SendNews?(String)`.</span></span>  

## <a name="see-also"></a><span data-ttu-id="e6f90-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6f90-122">See also</span></span>

- [<span data-ttu-id="e6f90-123">Operadores (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6f90-123">Operators (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="e6f90-124">Guia de programação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e6f90-124">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="e6f90-125">Referência da linguagem Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e6f90-125">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
