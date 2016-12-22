---
title: "Instru&#231;&#245;es &#39;Line&#39; n&#227;o s&#227;o mais compat&#237;veis (erro de compilador do Visual Basic) | Microsoft Docs"
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
  - "bc30830"
  - "vbc30830"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30830"
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es &#39;Line&#39; n&#227;o s&#227;o mais compat&#237;veis (erro de compilador do Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Declarações Linha não são mais suportadas  A funcionalidade de E\/S de arquivos está disponível como `Microsoft.VisualBasic.FileSystem.LineInput` e funcionalidade de elementos gráficos está disponível como `System.Drawing.Graphics.DrawLine`.  
  
 **Identificação do erro:**  BC30830  
  
### Para corrigir este erro  
  
1.  Se executar o acesso a arquivos, use `Microsoft.VisualBasic.FileSystem.LineInput`.  
  
2.  Se executar elementos gráficos, use `System.Drawing.Graphics.Drawline`.  
  
## Consulte também  
 <xref:System.IO>   
 <xref:System.Drawing>   
 [Access de arquivo com o Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)