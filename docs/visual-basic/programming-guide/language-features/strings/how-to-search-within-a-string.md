---
title: 'Como: pesquisar em uma cadeia de caracteres (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 32b42dfd7be8027d22186b212b3388985544d334
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-search-within-a-string-visual-basic"></a>Como pesquisar em uma cadeia de caracteres (Visual Basic)
Este exemplo chama o <xref:System.String.IndexOf%2A>método em uma <xref:System.String>objeto para relatar o índice da primeira ocorrência de uma subcadeia.</xref:System.String> </xref:System.String.IndexOf%2A>  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrStrings&#71;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um `Imports` instrução especificando o <xref:System>namespace.</xref:System> Para obter mais informações, consulte [instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Programação robusta  
 O <xref:System.String.IndexOf%2A>método reporta a localização do primeiro caractere da primeira ocorrência da subsequência.</xref:System.String.IndexOf%2A> O índice é baseado em 0, o que significa que o primeiro caractere de uma cadeia de caracteres tem um índice 0.  
  
 Se <xref:System.String.IndexOf%2A>não localizar a subcadeia de caracteres, ele retornará -1.</xref:System.String.IndexOf%2A>  
  
 O <xref:System.String.IndexOf%2A>método diferencia maiusculas de minúsculas e usa a cultura atual.</xref:System.String.IndexOf%2A>  
  
 Para controle de erro ideal, talvez você queira incluir a pesquisa de cadeia de caracteres no `Try` bloco de um [Try... Catch... Instrução Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) construção.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.String.IndexOf%2A></xref:System.String.IndexOf%2A>   
 [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Introdução a cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)   
 [Cadeias de Caracteres](../../../../visual-basic/programming-guide/language-features/strings/index.md)
