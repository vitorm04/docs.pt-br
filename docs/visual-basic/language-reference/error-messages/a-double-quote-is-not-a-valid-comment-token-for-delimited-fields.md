---
title: Aspas duplas não formam um token de comentário válido para campos delimitados em que EscapeQuote esteja definido como True
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
ms.openlocfilehash: df7868c510eaacbad1d4421259234f4187f60cd7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976211"
---
# <a name="a-double-quote-is-not-a-valid-comment-token-for-delimited-fields-where-escapequote-is-set-to-true"></a>Aspas duplas não formam um token de comentário válido para campos delimitados em que EscapeQuote esteja definido como True

Uma aspa foi fornecida como o delimitador para o `TextFieldParser`, mas `EscapeQuotes` está definido como `True`.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Defina `EscapeQuotes` como `False`.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- [Como ler a partir de arquivos de texto separados por vírgulas](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
