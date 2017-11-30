---
title: Como pesquisar em uma cadeia de caracteres (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c828d0b32fdf90e121e9d5da0bb60ab11c212f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-search-within-a-string-visual-basic"></a>Como pesquisar em uma cadeia de caracteres (Visual Basic)
Este exemplo chama o <xref:System.String.IndexOf%2A> método em um <xref:System.String> objeto para relatar o índice da primeira ocorrência de uma subcadeia de caracteres.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrStrings#71](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um `Imports` instrução especificando o <xref:System> namespace. Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Programação robusta  
 O <xref:System.String.IndexOf%2A> método reporta a localização do primeiro caractere da primeira ocorrência da subcadeia de caracteres. O índice é baseado em 0, o que significa que o primeiro caractere de uma cadeia de caracteres tem um índice de 0.  
  
 Se <xref:System.String.IndexOf%2A> não encontre a subcadeia de caracteres, ele retornará -1.  
  
 O <xref:System.String.IndexOf%2A> método diferencia maiusculas de minúsculas e usa a cultura atual.  
  
 Para o controle de erro ideal, talvez você queira colocar a pesquisa de cadeia de caracteres no `Try` block de um [tente... Catch... Instrução Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) construção.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.String.IndexOf%2A>  
 [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Introdução às cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [Cadeias de Caracteres](../../../../visual-basic/programming-guide/language-features/strings/index.md)
