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
# <a name="-and--null-conditional-operators-visual-basic"></a>?. e? operadores nulo-condicional de () (Visual Basic)

Testa o valor do operando esquerdo para nulo (`Nothing`) antes de executar um acesso de membro (`?.`) ou um índice (`?()`) da operação; retorna `Nothing` se o operando esquerdo for avaliado como `Nothing`. Observe que, em expressões que normalmente retornam tipos de valor, o operador nulo condicional retorna uma <xref:System.Nullable%601>.

Esses operadores ajudam a escrever menos código para lidar com verificações nulas, especialmente quando em ordem decrescente em estruturas de dados. Por exemplo:

```vb
' Nothing if customers is Nothing  
Dim length As Integer? = customers?.Length  

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()   
```

Para comparação, o código alternativo para a primeira dessas expressões sem um operador nulo condicional é:

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

Às vezes você precisa executar uma ação em um objeto que pode ser nulo, com base no valor de um membro booleano naquele objeto (como a propriedade booliana `IsAllowedFreeShipping` no exemplo a seguir):

```vb
  Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.
  
  If customer IsNot Nothing AndAlso customer.IsAllowedFreeShipping Then
   ApplyFreeShippingToOrders(customer)
  End If
```

Você pode reduzir o seu código e evitar manualmente a verificação de null, usando o operador nulo condicional da seguinte maneira:

```vb
 Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.
 
 If customer?.IsAllowedFreeShipping Then ApplyFreeShippingToOrders(customer)
```

Os operadores condicionais nulos estão entrando em curto-circuito.  Se uma operação em uma cadeia de operações de índice e acesso de membro condicionais retornar `Nothing`, o restante das paradas de execução da cadeia.  No exemplo a seguir `C(E)` não é avaliado se `A`, `B`, ou `C` for avaliada como `Nothing`.

```vb
A?.B?.C?(E);
```

Outro uso para acesso de membro condicional nulo é invocar representantes de forma thread-safe com muito menos código.  O exemplo a seguir define dois tipos, uma `NewsBroadcaster` e um `NewsReceiver`. Itens de notícias são enviados para o receptor pela `NewsBroadcaster.SendNews` delegar.

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

Se não houver nenhum elemento na `SendNews` lista de invocação, o `SendNews` delegar lança um <xref:System.NullReferenceException>. Antes de operadores condicionais nulos, de código, como a seguir garante que a lista de invocação de delegado não era `Nothing`:

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
