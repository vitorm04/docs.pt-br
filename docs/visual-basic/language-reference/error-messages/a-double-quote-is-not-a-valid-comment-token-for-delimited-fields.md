---
title: "Aspas duplas não formam um token de comentário válido para campos delimitados em que EscapeQuote esteja definido como True"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5677ee7415fe385805413ccbdec20762ac0573a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="a-double-quote-is-not-a-valid-comment-token-for-delimited-fields-where-escapequote-is-set-to-true"></a>Aspas duplas não formam um token de comentário válido para campos delimitados em que EscapeQuote esteja definido como True
Aspas foram fornecido como o delimitador para a `TextFieldParser`, mas `EscapeQuotes` é definido como `True`.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Defina `EscapeQuotes` como `False`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>  
 [Como ler a partir de arquivos de texto separados por vírgulas](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
