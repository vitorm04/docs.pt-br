---
title: "Como converter cadeias de caracteres hexadecimais em n&#250;meros (Visual Basic) | Microsoft Docs"
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
  - "decimais, hexadecimais"
  - "exemplos [Visual Basic], conversão de cadeia de caracteres"
  - "hexadecimais, decimais"
  - "números, hexadecimais"
  - "conversão de cadeia de caracteres, hexadecimais em números"
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como converter cadeias de caracteres hexadecimais em n&#250;meros (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este exemplo converte uma cadeia hexadecimal de caracteres em um inteiro usando o método <xref:System.Convert.ToInt32%2A>.  
  
### Para conveter uma cadeia hexadecimal de caracteres em um número  
  
-   Use o método <xref:System.Convert.ToInt32%2A> para converter o número expresso na base\-16 a um inteiro.  
  
     O primeiro argumento do método <xref:System.Convert.ToInt32%2A> é a cadeia de caracteres a converter.  O segundo argumento descreve em qual base o número é expresso; hexadecimal é base 16.  
  
     [!code-vb[VbVbalrStrings#62](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>   
 <xref:System.Convert.ToInt32%2A>