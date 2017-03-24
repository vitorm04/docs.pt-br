---
title: "TextFieldParser não dá suporte a tokens de comentário que contêm espaços em branco | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
caps.latest.revision: 8
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: dccbf3b31876cfff92841ffd6813561c08f9b388
ms.lasthandoff: 03/13/2017

---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-whitespace"></a>TextFieldParser não dá suporte a tokens de comentário que contêm espaços em branco
Foi fornecido um token de comentário que contém espaço em branco. O `TextFieldParser` não oferece suporte a tokens de comentário que contêm espaços em branco, a menos que o espaço em branco ocorra no início do token. Espaço em branco ocorrendo no início de um token é ignorado.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Forneça um símbolo de comentário corretos.  
  
## <a name="see-also"></a>Consulte também  
 [Propriedade CommentTokens](http://msdn.microsoft.com/en-us/2e6b6435-4bee-4c14-a353-e8f2c82e2d61)   
 [Analisando arquivos de texto com o objeto TextFieldParser](../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)   
 [Objeto TextFieldParser](../../visual-basic/language-reference/objects/textfieldparser-object.md)
