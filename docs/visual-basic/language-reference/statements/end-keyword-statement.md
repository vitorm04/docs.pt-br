---
title: Final &lt;palavra-chave&gt; instrução (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 8137434bfd8c26144d78b1761b784cdba4894eaf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605258"
---
# <a name="end-ltkeywordgt-statement-visual-basic"></a>Final &lt;palavra-chave&gt; instrução (Visual Basic)
Quando seguido por uma palavra-chave adicional, finaliza a definição do bloco de instrução introduzido por essa palavra-chave.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
 `End`  
 Necessário. Finaliza a definição do elemento de programação.  
  
 `AddHandler`  
 Necessário para finalizar uma `AddHandler` acessador iniciado por uma `AddHandler` instrução em um personalizado [instrução Event](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `Class`  
 Necessário para finalizar uma definição de classe iniciada por uma correspondência [instrução Class](../../../visual-basic/language-reference/statements/class-statement.md).  
  
 `Enum`  
 Necessário para finalizar uma definição de enumeração iniciada por uma correspondência [instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
 `Event`  
 Necessário para finalizar uma `Custom` definição de evento iniciada por uma [instrução Event](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `Function`  
 Necessário para finalizar uma `Function` iniciada por uma definição do procedimento [instrução Function](../../../visual-basic/language-reference/statements/function-statement.md). Se a execução encontrar um `End``Function` declaração ao código de chamada.  
  
 `Get`  
 Necessário para finalizar uma `Property` iniciada por uma definição do procedimento [obter instrução](../../../visual-basic/language-reference/statements/get-statement.md). Se a execução encontrar um `End``Get` declaração para a instrução solicitando o valor da propriedade.  
  
 `If`  
 Necessário para finalizar uma `If`... `Then`... `Else` iniciada por uma correspondência `If` instrução. Consulte [se... Then... Instrução else](../../../visual-basic/language-reference/statements/if-then-else-statement.md).  
  
 `Interface`  
 Necessário para finalizar uma definição de interface iniciada por uma correspondência [declaração Interface](../../../visual-basic/language-reference/statements/interface-statement.md).  
  
 `Module`  
 Necessário para finalizar uma definição de módulo iniciada por uma correspondência [instrução Module](../../../visual-basic/language-reference/statements/module-statement.md).  
  
 `Namespace`  
 Necessário para finalizar uma definição de namespace iniciada por uma correspondência [declaração de Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md).  
  
 `Operator`  
 Necessário para finalizar uma definição de operador iniciada por uma correspondência [instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 `Property`  
 Necessário para finalizar uma definição de propriedade iniciada por uma correspondência [declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md).  
  
 `RaiseEvent`  
 Necessário para finalizar uma `RaiseEvent` acessador iniciado por uma `RaiseEvent` instrução em um personalizado [instrução Event](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `RemoveHandler`  
 Necessário para finalizar uma `RemoveHandler` acessador iniciado por uma `RemoveHandler` instrução em um personalizado [instrução Event](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `Select`  
 Necessário para finalizar uma `Select`... `Case` iniciada por uma correspondência `Select` instrução. Consulte [selecione... Caso a instrução](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
 `Set`  
 Necessário para finalizar uma `Property` iniciada por uma definição do procedimento [instrução Set](../../../visual-basic/language-reference/statements/set-statement.md). Se a execução encontrar um `End``Set` declaração para a instrução Configurando o valor da propriedade.  
  
 `Structure`  
 Necessário para finalizar uma definição de estrutura iniciada por uma correspondência [instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md).  
  
 `Sub`  
 Necessário para finalizar uma `Sub` iniciada por uma definição do procedimento [instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md). Se a execução encontrar um `End``Sub` declaração ao código de chamada.  
  
 `SyncLock`  
 Necessário para finalizar uma `SyncLock` iniciada por uma correspondência `SyncLock` instrução. Consulte [Instrução SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md).  
  
 `Try`  
 Necessário para finalizar uma `Try`... `Catch`... `Finally` iniciada por uma correspondência `Try` instrução. Consulte [tente... Catch... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 `While`  
 Necessário para finalizar uma `While` definição iniciada por uma correspondência de loop `While` instrução. Consulte [enquanto... End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md).  
  
 `With`  
 Necessário para finalizar uma `With` iniciada por uma correspondência `With` instrução. Consulte [com... Terminar com a instrução](../../../visual-basic/language-reference/statements/with-end-with-statement.md).  
  
## <a name="remarks"></a>Comentários  
 O [instrução End](../../../visual-basic/language-reference/statements/end-statement.md), sem uma palavra-chave adicional, finaliza a execução imediatamente.  
  
 Quando precedido por um sinal numérico (`#`), o `End` palavra-chave encerra um bloco de pré-processamento introduzido pela diretiva correspondente.  
  
 `#End`  
 Necessário. Finaliza a definição do bloco de pré-processamento.  
  
 `#ExternalSource`  
 Necessário para finalizar um bloco de origem externa iniciado por uma [#ExternalSource diretiva](../../../visual-basic/language-reference/directives/externalsource-directive.md).  
  
 `#If`  
 Necessário para finalizar um bloco de compilação condicional iniciado por uma correspondência `#If` diretiva. Consulte [#If... Then... #Else diretivas](../../../visual-basic/language-reference/directives/if-then-else-directives.md).  
  
 `#Region`  
 Necessário para finalizar um bloco de regiões de origem iniciado por uma correspondência [#Region diretiva](../../../visual-basic/language-reference/directives/region-directive.md).  
  
## <a name="smart-device-developer-notes"></a>Notas do desenvolvedor de dispositivo inteligente  
 O `End` instrução, sem uma palavra-chave adicional, não é suportada.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md)
