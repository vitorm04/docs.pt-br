---
title: "Cl&#225;usula Alias (Visual Basic) | Microsoft Docs"
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
  - "vb.Alias"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "palavra-chave Alias"
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cl&#225;usula Alias (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Indica que um procedimento externo tem outro nome na sua DLL.  
  
## Comentários  
 A palavra\-chave `Alias` pode ser usada nos seguintes contextos:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 No exemplo a seguir, o `Alias` palavra\-chave é usada para fornecer o nome da função no Advapi32. dll, `GetUserNameA`, que `getUserName` é usado no lugar de neste exemplo.  Função `getUserName` é chamado em sub `getUser`, que exibe o nome do usuário atual.  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/alias-clause_1.vb)]  
  
## Consulte também  
 [Palavras\-chave](../../../visual-basic/language-reference/keywords/index.md)