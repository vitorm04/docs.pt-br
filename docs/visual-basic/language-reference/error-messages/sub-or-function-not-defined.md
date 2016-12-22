---
title: "Sub ou fun&#231;&#227;o n&#227;o definida (Visual Basic) | Microsoft Docs"
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
  - "vbrID35"
dev_langs: 
  - "VB"
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Sub ou fun&#231;&#227;o n&#227;o definida (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um `Sub` ou `Function` deve ser definido para ser chamado.  Possíveis causas do erro incluem:  
  
-   Digitar incorretamente o nome do procedimento.  
  
-   Tentar chamar um procedimento de outro projeto sem adicionar explicitamente uma referência a esse projeto na caixa de diálogo o **Referências**.  
  
-   Especificar um procedimento que não é visível para o procedimento de chamada.  
  
-   Declarar uma rotina da biblioteca de vínculo dinâmico \(DLL\) do Windows ou Macintosh recursos de código que não esteja na biblioteca ou recurso de código especificado.  
  
### Para corrigir este erro  
  
1.  Certifique\-se de que o nome do procedimento está digitado corretamente.  
  
2.  Localize o nome do projeto que contém o procedimento que você deseja chamar na caixa de diálogo **Referências**.  Se ele não aparecer, clique no botão **Procurar** para procurá\-lo.  Selecione a check box à esquerda do nome do projeto e em seguida, clique em  **OK** .  
  
3.  Verifique o nome da rotina.  
  
## Consulte também  
 [Tipos de erro](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [Gerenciando referências em um projeto](/visual-studio/ide/managing-references-in-a-project)   
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)