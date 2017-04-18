---
title: "Aspas duplas não são um símbolo de comentário válido para campos delimitados onde quando EscapeQuote está definido como True | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrTextFieldParser_InvalidComment
dev_langs:
- VB
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a409349ff5f60d07a538c1eac22d3bb4d294a87d
ms.lasthandoff: 03/13/2017

---
# <a name="a-double-quote-is-not-a-valid-comment-token-for-delimited-fields-where-escapequote-is-set-to-true"></a>Aspas duplas não formam um token de comentário válido para campos delimitados em que EscapeQuote esteja definido como True
Aspas foram fornecido como o delimitador para a `TextFieldParser`, mas `EscapeQuotes` é definido como `True`.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Set `EscapeQuotes` to `False`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A></xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A></xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser></xref:Microsoft.VisualBasic.FileIO.TextFieldParser>   
 [Como ler a partir de arquivos de texto separados por vírgulas](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
