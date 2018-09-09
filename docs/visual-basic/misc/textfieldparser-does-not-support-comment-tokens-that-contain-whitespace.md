---
title: TextFieldParser não dá suporte a tokens de comentário que contêm espaços em branco
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: a8931d67cd728cf98bc4d83044c65fad6642b021
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252799"
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-white-space"></a>TextFieldParser não dá suporte a tokens de comentário que contêm espaços em branco
Foi fornecido um token de comentário que contém espaço em branco. O `TextFieldParser` não oferece suporte a tokens de comentário que contêm espaços em branco, a menos que o espaço em branco ocorre no início do token. Espaço em branco que ocorrem no início de um token é ignorado.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Fornece um token de comentário corretos.  
  
## <a name="see-also"></a>Consulte também

- [Propriedade CommentTokens](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A)  
- [Analisando arquivos de texto com o objeto TextFieldParser](../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
- [Objeto TextFieldParser](../../visual-basic/language-reference/objects/textfieldparser-object.md)
