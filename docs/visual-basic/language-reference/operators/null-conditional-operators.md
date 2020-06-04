---
title: Operadores condicionais nulos
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: bffbba859968e0a050397cd9e685c142f801798a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401466"
---
# <a name="-and--null-conditional-operators-visual-basic"></a><span data-ttu-id="b3eb7-102">?.</span><span class="sxs-lookup"><span data-stu-id="b3eb7-102">?.</span></span> <span data-ttu-id="b3eb7-103">e? () operadores condicionais nulos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3eb7-103">and ?() null-conditional operators (Visual Basic)</span></span>

<span data-ttu-id="b3eb7-104">Testa o valor do operando esquerdo para NULL ( `Nothing` ) antes de executar uma operação de acesso de membro ( `?.` ) ou de índice ( `?()` ); retorna `Nothing` se o operando à esquerda for avaliado como `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="b3eb7-104">Tests the value of the left-hand operand for null (`Nothing`) before performing a member access (`?.`) or index (`?()`) operation; returns `Nothing` if the left-hand operand evaluates to `Nothing`.</span></span> <span data-ttu-id="b3eb7-105">Observe que em expressões que normalmente retornam tipos de valor, o operador NULL-Conditional retorna um <xref:System.Nullable%601> .</span><span class="sxs-lookup"><span data-stu-id="b3eb7-105">Note that in expressions that ordinarily return value types, the null-conditional operator returns a <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="b3eb7-106">Esses operadores ajudam a escrever menos código para lidar com verificações nulas, especialmente quando decrescentes em estruturas de dados.</span><span class="sxs-lookup"><span data-stu-id="b3eb7-106">These operators help you write less code to handle null checks, especially when descending into data structures.</span></span> <span data-ttu-id="b3eb7-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b3eb7-107">For example:</span></span>

```vb
' Nothing if customers is Nothing
Dim length As Integer? = customers?.Length

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()
```

<span data-ttu-id="b3eb7-108">Para comparação, o código alternativo para a primeira dessas expressões sem um operador condicional nulo é:</span><span class="sxs-lookup"><span data-stu-id="b3eb7-108">For comparison, the alternative code for the first of these expressions without a null-conditional operator is:</span></span>

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

<span data-ttu-id="b3eb7-109">Às vezes, você precisa tomar uma ação em um objeto que pode ser nulo, com base no valor de um membro booliano nesse objeto (como a propriedade booliana `IsAllowedFreeShipping` no exemplo a seguir):</span><span class="sxs-lookup"><span data-stu-id="b3eb7-109">Sometimes you need to take an action on an object that may be null, based on the value of a Boolean member on that object (like the Boolean property `IsAllowedFreeShipping` in the following example):</span></span>

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer IsNot Nothing AndAlso customer.IsAllowedFreeShipping Then
  ApplyFreeShippingToOrders(customer)
End If
```

<span data-ttu-id="b3eb7-110">Você pode encurtar seu código e evitar a verificação manual de NULL usando o operador NULL-Conditional da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b3eb7-110">You can shorten your code and avoid manually checking for null by using the null-conditional operator as follows:</span></span>

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer?.IsAllowedFreeShipping Then ApplyFreeShippingToOrders(customer)
```

<span data-ttu-id="b3eb7-111">Os operadores condicionais nulos estão entrando em curto-circuito.</span><span class="sxs-lookup"><span data-stu-id="b3eb7-111">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="b3eb7-112">Se uma operação em uma cadeia de acesso de membro condicional e operações de índice forem retornadas `Nothing` , o restante da execução da cadeia será interrompido.</span><span class="sxs-lookup"><span data-stu-id="b3eb7-112">If one operation in a chain of conditional member access and index operations returns `Nothing`, the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="b3eb7-113">No exemplo a seguir, `C(E)` não é avaliado se `A` , `B` ou `C` é avaliado como `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="b3eb7-113">In the following example, `C(E)` isn't evaluated if `A`, `B`, or `C` evaluates to `Nothing`.</span></span>

```vb
A?.B?.C?(E)
```

<span data-ttu-id="b3eb7-114">Outro uso para acesso de membro condicional nulo é invocar delegados de forma segura para thread com muito menos código.</span><span class="sxs-lookup"><span data-stu-id="b3eb7-114">Another use for null-conditional member access is to invoke delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="b3eb7-115">O exemplo a seguir define dois tipos, a `NewsBroadcaster` e a `NewsReceiver` .</span><span class="sxs-lookup"><span data-stu-id="b3eb7-115">The following example defines two types, a `NewsBroadcaster` and a `NewsReceiver`.</span></span> <span data-ttu-id="b3eb7-116">Os itens de notícias são enviados ao destinatário pelo `NewsBroadcaster.SendNews` delegado.</span><span class="sxs-lookup"><span data-stu-id="b3eb7-116">News items are sent to the receiver by the `NewsBroadcaster.SendNews` delegate.</span></span>

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

<span data-ttu-id="b3eb7-117">Se não houver nenhum elemento na `SendNews` lista de invocação, o `SendNews` delegado lançará um <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="b3eb7-117">If there are no elements in the `SendNews` invocation list, the `SendNews` delegate throws a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="b3eb7-118">Antes de operadores condicionais NULL, o código como o seguinte garantiu que a lista de invocação de delegado não foi `Nothing` :</span><span class="sxs-lookup"><span data-stu-id="b3eb7-118">Before null conditional operators, code like the following ensured that the delegate invocation list was not `Nothing`:</span></span>

```vb
SendNews = SendNews.Combine({SendNews, client})
If SendNews IsNot Nothing Then
   SendNews("Just in...")
End If
```

<span data-ttu-id="b3eb7-119">A nova maneira é muito mais simples:</span><span class="sxs-lookup"><span data-stu-id="b3eb7-119">The new way is much simpler:</span></span>

```vb
SendNews = SendNews.Combine({SendNews, client})
SendNews?.Invoke("Just in...")
```

<span data-ttu-id="b3eb7-120">A nova forma é thread-safe porque o compilador gera código para avaliar `SendNews` somente uma vez, mantendo o resultado em uma variável temporária.</span><span class="sxs-lookup"><span data-stu-id="b3eb7-120">The new way is thread-safe because the compiler generates code to evaluate `SendNews` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="b3eb7-121">Você precisa chamar explicitamente o método `Invoke` porque não há nenhuma sintaxe de invocação de delegado condicional nulo `SendNews?(String)`.</span><span class="sxs-lookup"><span data-stu-id="b3eb7-121">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `SendNews?(String)`.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3eb7-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="b3eb7-122">See also</span></span>

- [<span data-ttu-id="b3eb7-123">Operadores (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3eb7-123">Operators (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="b3eb7-124">Guia de programação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3eb7-124">Visual Basic Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b3eb7-125">Referência de linguagem de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3eb7-125">Visual Basic Language Reference</span></span>](../index.md)
