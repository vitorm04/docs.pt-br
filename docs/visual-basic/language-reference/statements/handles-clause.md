---
title: "Cl&#225;usula Handles (Visual Basic) | Microsoft Docs"
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
  - "Handles"
  - "vb.Handles"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "palavra-chave Handles"
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cl&#225;usula Handles (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Declara se um procedimento manipula um evento especificado.  
  
## Sintaxe  
  
```  
  
proceduredeclaration Handles eventlist  
```  
  
## Partes  
 `proceduredeclaration`  
 O `Sub` declaração de procedimento para o procedimento que manipulará o evento.  
  
 `eventlist`  
 Lista de eventos para `proceduredeclaration` para manipular, separados por vírgulas.  Os eventos devem ser gerados pela classe base para a classe atual, ou por um objeto declarado usando a `WithEvents` palavra\-chave.  
  
## Comentários  
 Use o `Handles` palavra\-chave no final de uma declaração de procedimento faz com que ele manipule eventos causados por uma variável de objeto declarada usando o `WithEvents` palavra\-chave.  O `Handles` palavra\-chave também pode ser usado em uma classe derivada para manipular eventos de uma classe base.  
  
 O `Handles` palavra\-chave e o `AddHandler` instrução os dois permitem que você especifique que determinados procedimentos manipulem eventos específicos, mas há diferenças.  Use o `Handles` palavra\-chave ao definir um procedimento para especificar que ele manipula um evento específico.  O `AddHandler` instrução conecta os procedimentos a eventos em tempo de execução.  Para obter mais informações, consulte [Instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md).  
  
 Para eventos personalizados, o aplicativo chama o evento `AddHandler` acessador quando ele adiciona o procedimento como um manipulador de eventos.  Para obter mais informações sobre eventos personalizados, consulte [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## Exemplo  
 [!code-vb[VbVbalrEvents#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_1.vb)]  
  
 O exemplo a seguir demonstra como uma classe derivada pode usar o `Handles` instrução para manipular um evento de uma classe base.  
  
 [!code-vb[VbVbalrEvents#3](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_2.vb)]  
  
## Exemplo  
 O exemplo a seguir contém dois manipuladores de eventos do botão para um **aplicativo WPF** projeto.  
  
 [!code-vb[VbVbalrEvents#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_3.vb)]  
  
## Exemplo  
 O exemplo a seguir é equivalente ao exemplo anterior.  O `eventlist` no `Handles` cláusula contém os eventos para os dois botões.  
  
 [!code-vb[VbVbalrEvents#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_4.vb)]  
  
## Consulte também  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)   
 [Instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [Instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)   
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)   
 [Eventos](../../../visual-basic/programming-guide/language-features/events/events.md)