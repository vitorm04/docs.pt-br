---
title: TextFieldParser não dá suporte a tokens de comentário que contenham espaço em branco
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: 825f999f8eab3563dd77039ef19ae5e329bb4240
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078496"
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-white-space"></a>TextFieldParser não dá suporte a tokens de comentário que contenham espaço em branco

Um token de comentário que contém espaço em branco foi fornecido. O `TextFieldParser` não oferece suporte a tokens de comentário que contenham espaços em branco, a menos que o espaço em branco ocorra no início do token. O espaço em branco que ocorre no início de um token é ignorado.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Forneça um token de comentário correto.  
  
## <a name="see-also"></a>Confira também

- [Propriedade TextFieldParser. CommentTokens](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A)
- [Analisando arquivos de texto com o objeto TextFieldParser](../developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [Objeto TextFieldParser](../language-reference/objects/textfieldparser-object.md)
