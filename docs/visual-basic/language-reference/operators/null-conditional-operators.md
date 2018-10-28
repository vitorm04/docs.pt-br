---
title: Operadores condicionais nulos (Visual Basic)
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: c29362a1e335e18b66821919e266b1ce57774692
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195984"
---
# <a name="-and--null-conditional-operators-visual-basic"></a>?. e? operadores nulo-condicional de () (Visual Basic)

Testa o valor do operando esquerdo para nulo (`Nothing`) antes de executar um acesso de membro (`?.`) ou um índice (`?()`) da operação; retorna `Nothing` se o operando esquerdo for avaliado como `Nothing`. Observe que, nas expressões que normalmente retornaria tipos de valor, o operador nulo condicional retorna a um <xref:System.Nullable%601>.

Esses operadores ajudam a escrever menos código para lidar com verificações nulas, especialmente quando em ordem decrescente em estruturas de dados. Por exemplo:

```vb
Dim length As Integer? = customers?.Length  ' Nothing if customers is Nothing  
Dim first As Customer = customers?(0)  ' Nothing if customers is Nothing  
Dim count As Integer? = customers?(0)?.Orders?.Count()  ' Nothing if customers, the first customer, or Orders is Nothing  
```

Para comparação, o código alternativo para a primeira dessas expressões sem um operador nulo condicional é:

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

Os operadores condicionais nulos estão entrando em curto-circuito.  Se uma operação em uma cadeia de operações de índice e acesso de membro condicional não retorne nada, o restante da execução da cadeia será interrompida.  No exemplo a seguir, c (e) não é avaliado, se `A`, `B`, ou `C` for avaliada como nada.

```vb
A?.B?.C?(E);
```

Outro uso para acesso de membro condicional nulo é invocar representantes de forma thread-safe com muito menos código.  A maneira antiga requer código semelhante ao seguinte:  

```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```

A nova maneira é muito mais simples:  

```vb
PropertyChanged?.Invoke(…)
```

A nova forma é thread-safe porque o compilador gera código para avaliar `PropertyChanged` somente uma vez, mantendo o resultado em uma variável temporária. Você precisa chamar explicitamente o método `Invoke` porque não há nenhuma sintaxe de invocação de delegado condicional nulo `PropertyChanged?(e)`.  

## <a name="see-also"></a>Consulte também

- [Operadores (Visual Basic)](index.md)
- [Guia de programação do Visual Basic](../../../visual-basic/programming-guide/index.md)
- [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md)  
