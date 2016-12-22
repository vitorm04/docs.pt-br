---
title: "&#39;&lt;functionname&gt;&#39; n&#227;o est&#225; declarado (dispositivo inteligente/erro de compilador do Visual Basic) | Microsoft Docs"
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
  - "bc30766"
  - "vbc30766"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30766"
ms.assetid: 13918600-6087-40d7-8134-32aa9d3bfda4
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;functionname&gt;&#39; n&#227;o est&#225; declarado (dispositivo inteligente/erro de compilador do Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

\<`functionname`\> não foi declarado.  Funcionalidade do arquivo I\/O está normalmente disponível no namespace `Microsoft.VisualBasic`, mas a versão de destino da estrutura .NET Compact não a suporta.  
  
 **Identificação do erro:**  BC30766  
  
### Para corrigir este erro  
  
-   Realize operações de arquivo com funções definidas no namespace `System.IO`.  
  
## Consulte também  
 <xref:System.IO>   
 [Access de arquivo com o Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)