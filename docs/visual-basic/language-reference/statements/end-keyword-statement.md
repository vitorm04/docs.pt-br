---
title: "Instru&#231;&#227;o End &lt;keyword&gt; (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.EndDefinition"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "palavra-chave End"
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o End &lt;keyword&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Quando seguido por uma palavra\-chave adicional, finaliza a definição do bloco de declaração introduzido por aquela palavra\-chave.  
  
## Sintaxe  
  
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
  
## Partes  
 `End`  
 Obrigatório.  Finaliza a definição de elemento de programação.  
  
 `AddHandler`  
 Necessário para encerrar um acessador `AddHandler` iniciado por uma instrução `AddHandler` correspondente em um [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md) personalizado.  
  
 `Class`  
 Necessário para encerrar um definição de classe iniciada por um [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md) correspondente.  
  
 `Enum`  
 Necessário para finalizar uma definição de enumeração iniciada por um [Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md) correspondente.  
  
 `Event`  
 Necessário para finalizar uma definição de eventos `Custom` iniciada por um [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md) correspondente.  
  
 `Function`  
 Necessário para finalizar uma definição de procedimento `Function` iniciada por uma [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md) correspondente.  Se a execução encontra uma instrução `End` `Function`, controle retorna para o código de chamada.  
  
 `Get`  
 Necessário para finalizar uma definição de procedimento `Property` iniciada por uma [Instrução Get](../../../visual-basic/language-reference/statements/get-statement.md) correspondente.  Se a execução encontrar uma instrução `End` `Get`, o controle retornará para a instrução solicitando o valor da propriedade.  
  
 `If`  
 Necessário para finalizar uma definição de bloco `If`... `Then`... `Else` iniciada por uma instrução `If` correspondente.  Consulte [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md).  
  
 `Interface`  
 Necessário para finalizar uma definição de interface iniciada por um [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md) correspondente.  
  
 `Module`  
 Necessário para finalizar uma definição de módulo iniciada por uma [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md) correspondente.  
  
 `Namespace`  
 Necessário para finalizar uma definição de Espaço de Nomes iniciada por um [Instrução Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md) correspondente.  
  
 `Operator`  
 Necessário para finalizar uma definição de operador iniciada por um [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md) correspondente.  
  
 `Property`  
 Necessário para finalizar uma definição de propriedade iniciada por um [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md) correspondente.  
  
 `RaiseEvent`  
 Necessário para encerrar um acessador `RaiseEvent` iniciado por uma instrução `RaiseEvent` correspondente em um [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md) personalizado.  
  
 `RemoveHandler`  
 Necessário para encerrar um acessador `RemoveHandler` iniciado por uma instrução `RemoveHandler` correspondente em um [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md) personalizado.  
  
 `Select`  
 Necessário para finalizar uma definição de bloco `Select`... `Case` iniciada por uma instrução  `Select` correspondente.  Consulte [Instrução Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
 `Set`  
 Necessário para finalizar uma definição de procedimento `Property` iniciada por uma [Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md) correspondente.  Se a execução encontrar uma instrução `End` `Set`, o controle retornará para a instrução configurando o valor da propriedade.  
  
 `Structure`  
 Necessário para finalizar uma definição de estrutura iniciada por uma [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md) correspondente.  
  
 `Sub`  
 Necessário para finalizar uma definição de procedimento `Sub` iniciada por uma [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md) correspondente.  Se a execução encontra uma instrução `End` `Sub`, controle retorna para o código de chamada.  
  
 `SyncLock`  
 Necessário para finalizar uma definição de bloco `SyncLock` iniciada por uma instrução `SyncLock` correspondente.  Consulte [Instrução SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md).  
  
 `Try`  
 Necessário para finalizar uma definição de bloco `Try`... `Catch` ... `Finally` iniciada por uma instrução `Try` correspondente.  Consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 `While`  
 Necessário para finalizar uma definição de loop `While` iniciada por uma instrução `While` correspondente.  Consulte [Instrução While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md).  
  
 `With`  
 Necessário para finalizar uma definição de bloco `With` iniciada por uma instrução `With` correspondente.  Consulte [Instrução With ... End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md).  
  
## Comentários  
 O [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md), sem uma palavra\-chave adicional, finaliza a execução imediatamente.  
  
 Quando precedido por um sinal numérico \(`#`\), a palavra\-chave `End` encerra um bloco de pré\-processamento introduzido pela diretiva correspondente.  
  
 `#End`  
 Obrigatório.  Finaliza a definição de bloco de pré\-processamento.  
  
 `#ExternalSource`  
 Necessário para finalizar um bloco de origem externa iniciado por uma [Diretiva \#ExternalSource](../../../visual-basic/language-reference/directives/externalsource-directive.md) correspondente.  
  
 `#If`  
 Necessário para finalizar um bloco de compilação condicional iniciado por uma diretiva `#If`.  Consulte [Diretivas \#If...Then...\#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md).  
  
 `#Region`  
 Necessário para finalizar um bloco de origem de região iniciado por uma [Diretiva \#Region](../../../visual-basic/language-reference/directives/region-directive.md) correspondente.  
  
## Anotações Developer Dispositivo Inteligente  
 Não há suporte para a instrução `End`, sem uma palavra\-chave adicional.  
  
## Consulte também  
 [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md)