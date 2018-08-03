---
title: Término &lt;palavra-chave&gt; Statement (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 8137434bfd8c26144d78b1761b784cdba4894eaf
ms.sourcegitcommit: 7fe772c6c05a982153655d618c826e9839d39cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/03/2018
ms.locfileid: "33605258"
---
# <a name="end-ltkeywordgt-statement-visual-basic"></a>Término &lt;palavra-chave&gt; Statement (Visual Basic)

Quando seguido por uma palavra-chave adicional, finaliza a definição do bloco de instrução introduzido por essa palavra-chave.

## <a name="syntax"></a>Sintaxe

```vb
End AddHandler
End Class
End Enum
End Event
End Function
End Get
End If
End Interface
End Module
End Namespace
End Operator
End Property
End RaiseEvent  
End RemoveHandler  
End Select
End Set
End Structure
End Sub
End SyncLock
End Try
End While
End With  
```  
  
## <a name="parts"></a>Partes

|Parte|Descrição|
|---|---|
|`End`|Necessário. Finaliza a definição do elemento de programação.|
|`AddHandler`|Necessário para finalizar uma `AddHandler` iniciado por uma correspondência de acessador `AddHandler` instrução em um personalizado [instrução Event](event-statement.md).|
|`Class`|Necessário para finalizar uma definição de classe iniciada por uma correspondência [declaração de classe](class-statement.md).|
|`Enum`|Necessário para finalizar uma definição de enumeração iniciada por uma correspondência [instrução Enum](enum-statement.md).|
|`Event`|Necessário para finalizar uma `Custom` iniciada por uma correspondência de definição de evento [instrução Event](event-statement.md).|  
|`Function`|Necessário para finalizar uma `Function` iniciada por uma definição do procedimento [instrução Function](function-statement.md). Se a execução encontrar um `End Function` instrução, o controle retorna para o código de chamada.|
|`Get`|Necessário para finalizar uma `Property` iniciada por uma definição do procedimento [instrução Get](get-statement.md). Se a execução encontrar um `End Get` instrução, o controle retorna para a instrução solicitando o valor da propriedade.|
|`If`|Necessário para finalizar uma `If`... `Then`... `Else` iniciada por uma correspondência `If` instrução. Consulte [se... Then... Instrução else](if-then-else-statement.md).|
|`Interface`|Necessário para finalizar uma definição de interface iniciada por uma correspondência [declaração de Interface](interface-statement.md).|
|`Module`|Necessário para finalizar uma definição de módulo iniciada por uma correspondência [declaração de módulo](module-statement.md).|
|`Namespace`|Necessário para finalizar uma definição de namespace iniciada por uma correspondência [declaração de Namespace](namespace-statement.md).|
|`Operator`|Necessário para finalizar uma definição de operador iniciada por uma correspondência [instrução Operator](operator-statement.md).|
|`Property`|Necessário para finalizar uma definição de propriedade iniciada por uma correspondência [declaração de propriedade](property-statement.md).|
|`RaiseEvent`|Necessário para finalizar uma `RaiseEvent` iniciado por uma correspondência de acessador `RaiseEvent` instrução em um personalizado [instrução Event](event-statement.md).|
|`RemoveHandler`|Necessário para finalizar uma `RemoveHandler` iniciado por uma correspondência de acessador `RemoveHandler` instrução em um personalizado [instrução Event](event-statement.md).|
|`Select`|Necessário para finalizar uma `Select`... `Case` iniciada por uma correspondência `Select` instrução. Consulte [selecione... Instrução de caso](select-case-statement.md).  
|`Set`|Necessário para finalizar uma `Property` iniciada por uma definição do procedimento [instrução Set](set-statement.md). Se a execução encontrar um `End Set` instrução, o controle retorna para a instrução que configura o valor da propriedade.  
|`Structure`|Necessário para finalizar uma definição de estrutura iniciada por uma correspondência [instrução Structure](structure-statement.md).  
|`Sub`|Necessário para finalizar uma `Sub` iniciada por uma definição do procedimento [instrução Sub](sub-statement.md). Se a execução encontrar um `End Sub` instrução, o controle retorna para o código de chamada.  
|`SyncLock`|Necessário para finalizar uma `SyncLock` iniciada por uma correspondência `SyncLock` instrução. Ver [Instrução SyncLock](synclock-statement.md).  
|`Try`|Necessário para finalizar uma `Try`... `Catch`... `Finally` iniciada por uma correspondência `Try` instrução. Consulte [tente... Catch... Instrução Finally](try-catch-finally-statement.md).  
|`While`|Necessário para finalizar uma `While` iniciada por uma correspondência de definição de loop `While` instrução. Consulte [enquanto... Finalizar instrução While](while-end-while-statement.md).  
|`With`| Necessário para finalizar uma `With` iniciada por uma correspondência `With` instrução. Consulte [com... Terminar com a instrução](with-end-with-statement.md).  
|||
  
## <a name="directives"></a>Diretivas

Quando precedido por um sinal numérico (`#`), o `End` palavra-chave encerra um bloco de pré-processamento introduzido pela diretiva correspondente.  

```vb
#End ExternalSource
#End If
#End Region
```

|Parte|Descrição|
|---|---|
|`#End`|Necessário. Finaliza a definição do bloco de pré-processamento.|
|`ExternalSource`|Necessário para finalizar um bloco de origem externa iniciado por uma correspondência [#ExternalSource diretiva](../directives/externalsource-directive.md).|
|`If`|Necessário para finalizar um bloco de compilação condicional iniciado por uma correspondência `#If` diretiva. Consulte [#If... Then... #Else diretivas](../directives/if-then-else-directives.md).|
|`Region`|Necessário para finalizar um bloco de região de origem iniciado por uma correspondência [#Region diretiva](../directives/region-directive.md).|
|||

## <a name="remarks"></a>Comentários

O [instrução End](end-statement.md), sem uma palavra-chave adicional, finaliza a execução imediatamente.

## <a name="smart-device-developer-notes"></a>Notas do desenvolvedor de dispositivo inteligente  

O `End` instrução sem uma palavra-chave adicional, não é suportada.  
  
## <a name="see-also"></a>Consulte também

[Instrução End](end-statement.md)
