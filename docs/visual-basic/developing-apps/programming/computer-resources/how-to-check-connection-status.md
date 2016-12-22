---
title: "Como verificar o status da conex&#227;o no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "status da conexão"
  - "conexões, verificando status"
  - "Propriedade IsAvailable, Sobre IsAvailable"
  - "Conexões da Web"
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
caps.latest.revision: 26
caps.handback.revision: 26
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como verificar o status da conex&#227;o no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable%2A> propriedade pode ser usada para determinar se o computador tem uma rede ou conexão com a Internet.  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### Para verificar se um computador tem uma conexão ativa  
  
-   Determine se a propriedade `IsAvailable` é `True` ou `False`.  O código a seguir verifica o estado da propriedade e o reporta:  
  
     [!code-vb[VbResourceTasks#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-check-connection-status_1.vb)]  
  
     Este exemplo de código também está disponível como um trecho de código IntelliSense.  No selecionador de trechos de código, ele está localizado em **Connectivity and Networking**.  Para mais informações, consulte [Trechos de código](/visual-studio/ide/code-snippets).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable%2A>