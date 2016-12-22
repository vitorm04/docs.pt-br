---
title: "Acesso &#224; cadeia de caracteres com base em zero versus em um no Visual Basic | Microsoft Docs"
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
  - "cadeias de caracteres {Visual Basic], indexação"
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Acesso &#224; cadeia de caracteres com base em zero versus em um no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico compara como [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] e o [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] fornecem acesso aos caracteres de uma cadeia de caracteres.  O [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] sempre fornece acesso baseado em zero aos caracteres em uma cadeia de caracteres, enquanto [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece acesso baseado em zero e em um, dependendo da função.  
  
## Baseado em um  
 Para um exemplo de uma função [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] com base em um, considere a função `Mid`.  Ele leva um argumento que indica a posição do caractere no qual a subseqüência de caracteres será iniciado, começando na posição 1.  O [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]<xref:System.String.Substring%2A?displayProperty=fullName> método usa um índice do caractere na seqüência em que a subseqüência deve começar, iniciando com a posição 0.   Assim, se você tiver uma seqüência de caracteres "ABCDE", os caracteres individuais são numerados 1,2,3,4,5 para uso com o `Mid` função, mas 0,1,2,3,4 para uso com o <xref:System.String.Substring%2A?displayProperty=fullName> método.  
  
## Baseado em zero  
 Para um exemplo de uma função [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] com base em zero, considere a função `Split`.  Ela divide uma cadeia de caracteres e retorna uma matriz que contém as subcadeias de caracteres.  O método [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.String.Split%2A?displayProperty=fullName> também divide uma cadeia de caracteres e retorna uma matriz que contém as subcadeias de caracteres.  Como a função `Split` e o método <xref:System.String.Split%2A> retornam matrizes [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)], eles devem ser baseados em zero.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>   
 <xref:Microsoft.VisualBasic.Strings.Split%2A>   
 <xref:System.String.Substring%2A>   
 <xref:System.String.Split%2A>   
 [Introdução a cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)