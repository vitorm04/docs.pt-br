---
title: "Como pesquisar em uma cadeia de caracteres (Visual Basic) | Microsoft Docs"
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
  - "exemplos [Visual Basic], cadeias de caracteres"
  - "cadeias de caracteres {Visual Basic], localizando"
  - "cadeias de caracteres {Visual Basic], procurando"
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como pesquisar em uma cadeia de caracteres (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este exemplo chama o <xref:System.String.IndexOf%2A> método em um <xref:System.String> o objeto para relatar o índice da primeira ocorrência de uma substring.  
  
## Exemplo  
 [!code-vb[VbVbalrStrings#71](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]  
  
## Compilando o código  
 Este exemplo requer:  
  
-   Uma declaração `Imports` especificando o namespace <xref:System>.  Para mais informações, consulte [Instrução Imports \(tipo e namespace .NET\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## Programação robusta  
 O método <xref:System.String.IndexOf%2A> reporta a localização do primeiro caractere da primeira ocorrência da subseqüência de caracteres.  O índice é baseado em 0, o que significa que o primeiro caractere de uma seqüência tem um índice de 0.  
  
 Se <xref:System.String.IndexOf%2A> não encontra a subseqüência de caracteres, ele retornará \-1.  
  
 O método <xref:System.String.IndexOf%2A> é sensível a maiúsculas e usa a cultura em questão.  
  
 Para controle otimizado de erro, coloque a pesquisa de cadeia de caracteres no bloco `Try` de uma construção [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## Consulte também  
 <xref:System.String.IndexOf%2A>   
 [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Introdução a cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)   
 [Cadeias de caracteres](../../../../visual-basic/programming-guide/language-features/strings/index.md)