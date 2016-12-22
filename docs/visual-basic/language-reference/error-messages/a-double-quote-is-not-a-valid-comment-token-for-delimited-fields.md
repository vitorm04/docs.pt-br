---
title: "Aspas duplas n&#227;o formam um token de coment&#225;rio v&#225;lido para campos delimitados em que EscapeQuote esteja definido como True | Microsoft Docs"
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
  - "vbrTextFieldParser_InvalidComment"
dev_langs: 
  - "VB"
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Aspas duplas n&#227;o formam um token de coment&#225;rio v&#225;lido para campos delimitados em que EscapeQuote esteja definido como True
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Aspas foram fornecido como o delimitador para a `TextFieldParser`, mas `EscapeQuotes` é definido como `True`.  
  
### Para corrigir este erro  
  
-   Defina `EscapeQuotes` para `False`.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>   
 [Como ler a partir de arquivos de texto separados por vírgulas](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)