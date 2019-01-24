---
title: 'Como: Pesquisar em uma cadeia de caracteres (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: 6ac75c99270deb14e23691d32e8ebf4e8b0a91b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542538"
---
# <a name="how-to-search-within-a-string-visual-basic"></a>Como: Pesquisar em uma cadeia de caracteres (Visual Basic)
Este exemplo chama o <xref:System.String.IndexOf%2A> método em um <xref:System.String> objeto para relatar o índice da primeira ocorrência de uma subcadeia de caracteres.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrStrings#71](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Uma `Imports` instrução que especifica o <xref:System> namespace. Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Programação robusta  
 O <xref:System.String.IndexOf%2A> método relata o local do primeiro caractere da primeira ocorrência da subcadeia de caracteres. O índice é baseado em 0, o que significa que o primeiro caractere de uma cadeia de caracteres tem um índice de 0.  
  
 Se <xref:System.String.IndexOf%2A> não localizar a subcadeia de caracteres, ele retornará -1.  
  
 O <xref:System.String.IndexOf%2A> método diferencia maiusculas de minúsculas e usa a cultura atual.  
  
 Para controle de erro ideal, você talvez queira incluir a pesquisa de cadeia de caracteres na `Try` block de um [tente... Catch... Instrução Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) construção.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.String.IndexOf%2A>
- [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Introdução às cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [Cadeias de Caracteres](../../../../visual-basic/programming-guide/language-features/strings/index.md)
