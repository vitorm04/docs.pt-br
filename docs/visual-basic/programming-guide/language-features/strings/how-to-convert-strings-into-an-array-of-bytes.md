---
title: "Como converter cadeias de caracteres em uma matriz de bytes no Visual Basic | Microsoft Docs"
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
  - "matrizes [Visual Basic], matrizes de bytes"
  - "matrizes [Visual Basic], convertendo cadeias de caracteres em"
  - "matrizes de bytes"
  - "exemplos [Visual Basic], conversão de cadeia de caracteres"
  - "conversão de cadeia de caracteres, matrizes"
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como converter cadeias de caracteres em uma matriz de bytes no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico mostra como converter uma seqüência de caracteres em uma matriz de bytes.  
  
## Exemplo  
 Este exemplo usa a <xref:System.Text.Encoding.GetBytes%2A> método da <xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName> classe para converter uma seqüência de caracteres em uma matriz de bytes de codificação.  
  
 [!code-vb[VbVbalrStrings#74](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-strings-into-an-array-of-bytes_1.vb)]  
  
 Você pode escolher entre várias opções de codificação para converter uma seqüência de caracteres em uma matriz de bytes:  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=fullName>: Obtém uma codificação de caracteres ASCII \(7 bits\) de definir.  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=fullName>: Obtém uma codificação para o formato UTF\-16 usando a ordem de bytes big\-endian.  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=fullName>: Obtém uma codificação para a página de código ANSI atual do sistema.  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName>: Obtém uma codificação para o formato UTF\-16 usando a ordem de bytes little\-endian.  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=fullName>: Obtém uma codificação para o formato UTF\-32, usando a ordem de bytes little\-endian.  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=fullName>: Obtém uma codificação para o formato UTF\-7.  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=fullName>: Obtém uma codificação para o formato UTF\-8.  
  
## Consulte também  
 <xref:System.Text.Encoding?displayProperty=fullName>   
 <xref:System.Text.Encoding.GetBytes%2A>   
 [Como converter uma matriz de bytes em uma cadeia de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)