---
title: Operadores condicionais nulos (Visual Basic)
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: 40cb63705eda563b4c3cfd30fa9836a8f632dccf
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581630"
---
# <a name="-and--null-conditional-operators-visual-basic"></a>?. e? () operadores condicionais nulos (Visual Basic)

Testa o valor do operando esquerdo para NULL (`Nothing`) antes de executar uma operação de acesso de membro (`?.`) ou de índice (`?()`); retornará `Nothing` se o operando esquerdo for avaliado como `Nothing`. Observe que em expressões que normalmente retornam tipos de valor, o operador NULL-Conditional retorna um <xref:System.Nullable%601>.

Esses operadores ajudam a escrever menos código para lidar com verificações nulas, especialmente quando decrescentes em estruturas de dados. Por exemplo:

```vb
' Nothing if customers is Nothing
Dim length As Integer? = customers?.Length

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()
```

Para comparação, o código alternativo para a primeira dessas expressões sem um operador condicional nulo é:

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

Às vezes, você precisa tomar uma ação em um objeto que pode ser nulo, com base no valor de um membro booliano nesse objeto (como a propriedade booliana `IsAllowedFreeShipping` no exemplo a seguir):

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer IsNot Nothing AndAlso customer.IsAllowedFreeShipping Then
  ApplyFreeShippingToOrders(customer)
End If
```

Você pode encurtar seu código e evitar a verificação manual de NULL usando o operador NULL-Conditional da seguinte maneira:

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer?.IsAllowedFreeShipping Then ApplyFreeShippingToOrders(customer)
```

Os operadores condicionais nulos estão entrando em curto-circuito.  Se uma operação em uma cadeia de operações de acesso de membro condicional e de índice retornar `Nothing`, o restante da execução da cadeia será interrompido.  No exemplo a seguir, `C(E)` não será avaliada se `A`, `B` ou `C` for avaliada como `Nothing`.

```vb
A?.B?.C?(E);
```

Outro uso para acesso de membro condicional nulo é invocar delegados de forma segura para thread com muito menos código.  O exemplo a seguir define dois tipos, um `NewsBroadcaster` e um `NewsReceiver`. Os itens de notícias são enviados ao destinatário pelo `NewsBroadcaster.SendNews` delegado.

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

Se não houver nenhum elemento na lista de invocação `SendNews`, o delegado `SendNews` gerará uma <xref:System.NullReferenceException>. Antes de operadores condicionais NULL, um código semelhante ao seguinte garantiu que a lista de invocação de delegado não foi `Nothing`:

```vb
SendNews = SendNews.Combine({SendNews, client})
If SendNews IsNot Nothing Then
   SendNews("Just in...")
End If
```

A nova maneira é muito mais simples:

```vb
SendNews = SendNews.Combine({SendNews, client})
SendNews?.Invoke("Just in...")
```

A nova forma é thread-safe porque o compilador gera código para avaliar `SendNews` somente uma vez, mantendo o resultado em uma variável temporária. Você precisa chamar explicitamente o método `Invoke` porque não há nenhuma sintaxe de invocação de delegado condicional nulo `SendNews?(String)`.

## <a name="see-also"></a>Consulte também

- [Operadores (Visual Basic)](index.md)
- [Guia de programação do Visual Basic](../../../visual-basic/programming-guide/index.md)
- [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md)
