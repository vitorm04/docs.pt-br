---
title: End &lt;palavra-chave&gt; Statement (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.EndDefinition
dev_langs:
- VB
helpviewer_keywords:
- End keyword
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0cdeee6c37e4a71f8b887f552756117f89cde4d9
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="end-ltkeywordgt-statement-visual-basic"></a>End &lt;palavra-chave&gt; Statement (Visual Basic)
Quando seguido por uma palavra-chave adicional, finaliza a definição do bloco de declaração introduzido por essa palavra-chave.  
  
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
 Necessário para finalizar uma `AddHandler` acessador iniciado por uma `AddHandler` instrução em um personalizado [declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `Class`  
 Necessário para finalizar uma definição de classe iniciada por uma correspondência [instrução Class](../../../visual-basic/language-reference/statements/class-statement.md).  
  
 `Enum`  
 Necessário para finalizar uma definição de enumeração iniciada por uma correspondência [instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
 `Event`  
 Necessário para finalizar uma `Custom` iniciada por uma definição do evento [declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `Function`  
 Necessário para finalizar uma `Function` iniciada por uma definição do procedimento [declaração de função](../../../visual-basic/language-reference/statements/function-statement.md). Se a execução encontrar uma `End``Function` instrução, o controle retorna para o código de chamada.  
  
 `Get`  
 Necessário para finalizar uma `Property` iniciada por uma definição do procedimento [obter instrução](../../../visual-basic/language-reference/statements/get-statement.md). Se a execução encontrar uma `End``Get` declaração para a instrução solicitando o valor da propriedade.  
  
 `If`  
 Necessário para finalizar uma `If`... `Then`... `Else` iniciada por uma correspondência `If` instrução. Consulte [se... Then... Instrução else](../../../visual-basic/language-reference/statements/if-then-else-statement.md).  
  
 `Interface`  
 Necessário para finalizar uma definição de interface iniciada por uma correspondência [instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md).  
  
 `Module`  
 Necessário para finalizar uma definição de módulo iniciada por uma correspondência [instrução Module](../../../visual-basic/language-reference/statements/module-statement.md).  
  
 `Namespace`  
 Necessário para finalizar uma definição de namespace iniciada por uma [declaração de Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md).  
  
 `Operator`  
 Necessário para finalizar uma definição de operador iniciada por uma correspondência [instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 `Property`  
 Necessário para finalizar uma definição de propriedade iniciada por uma correspondência [declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md).  
  
 `RaiseEvent`  
 Necessário para finalizar uma `RaiseEvent` acessador iniciado por uma `RaiseEvent` instrução em um personalizado [declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `RemoveHandler`  
 Necessário para finalizar uma `RemoveHandler` acessador iniciado por uma `RemoveHandler` instrução em um personalizado [declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md).  
  
 `Select`  
 Necessário para finalizar uma `Select`... `Case` iniciada por uma correspondência `Select` instrução. Consulte [selecione... Instrução Case](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
 `Set`  
 Necessário para finalizar uma `Property` iniciada por uma definição do procedimento [instrução Set](../../../visual-basic/language-reference/statements/set-statement.md). Se a execução encontrar uma `End``Set` declaração para a instrução Configurando o valor da propriedade.  
  
 `Structure`  
 Necessário para finalizar uma definição de estrutura iniciada por uma correspondência [declaração de estrutura](../../../visual-basic/language-reference/statements/structure-statement.md).  
  
 `Sub`  
 Necessário para finalizar uma `Sub` iniciada por uma definição do procedimento [instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md). Se a execução encontrar uma `End``Sub` instrução, o controle retorna para o código de chamada.  
  
 `SyncLock`  
 Necessário para finalizar uma `SyncLock` iniciada por uma correspondência `SyncLock` instrução. Consulte [Instrução SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md).  
  
 `Try`  
 Necessário para finalizar uma `Try`... `Catch`... `Finally` iniciada por uma correspondência `Try` instrução. Consulte [Try... Catch... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 `While`  
 Necessário para finalizar uma `While` definição iniciada por uma correspondência de loop `While` instrução. Consulte [enquanto... End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md).  
  
 `With`  
 Necessário para finalizar uma `With` iniciada por uma correspondência `With` instrução. Consulte [com... Terminar com a instrução](../../../visual-basic/language-reference/statements/with-end-with-statement.md).  
  
## <a name="remarks"></a>Comentários  
 O [instrução End](../../../visual-basic/language-reference/statements/end-statement.md), sem uma palavra-chave adicional, finaliza a execução imediatamente.  
  
 Quando precedido por um sinal numérico (`#`), o `End` palavra-chave Finaliza um bloco de pré-processamento introduzido pela diretiva correspondente.  
  
 `#End`  
 Necessário. Finaliza a definição do bloco de pré-processamento.  
  
 `#ExternalSource`  
 Necessário para finalizar um bloco de origem externa iniciado por uma [#ExternalSource diretiva](../../../visual-basic/language-reference/directives/externalsource-directive.md).  
  
 `#If`  
 Necessário para finalizar um bloco de compilação condicional iniciado por uma `#If` diretiva. Consulte [#If... Then... #Else diretivas](../../../visual-basic/language-reference/directives/if-then-else-directives.md).  
  
 `#Region`  
 Necessário para finalizar um bloco de região de origem iniciado por uma [#Region diretiva](../../../visual-basic/language-reference/directives/region-directive.md).  
  
## <a name="smart-device-developer-notes"></a>Anotações de desenvolvedor de dispositivo inteligente  
 O `End` instrução, sem uma palavra-chave adicional, não é suportada.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md)

