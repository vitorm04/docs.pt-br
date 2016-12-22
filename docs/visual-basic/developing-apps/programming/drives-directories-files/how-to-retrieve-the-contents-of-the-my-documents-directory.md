---
title: "Como recuperar o conte&#250;do do diret&#243;rio Meus Documentos no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "Diretório Meus Documentos"
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como recuperar o conte&#250;do do diret&#243;rio Meus Documentos no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> objeto pode ser usado para ler de muitos a  **Todos os usuários** diretórios, como  **Meus documentos** ou  **Desktop**.  
  
### Ao ler a pasta My Documents  
  
-   Use o método `ReadAllText` para ler o texto de cada arquivo em um diretório específico.  O código a seguir especifica um diretório e arquivo e em seguida usa `ReadAllText` para lê\-los para a sequência de caracteres denominada `patients`.  
  
     [!code-vb[VbVbcnMyFileSystem#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-retrieve-the-contents-of-the-my-documents-directory_1.vb)]  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>