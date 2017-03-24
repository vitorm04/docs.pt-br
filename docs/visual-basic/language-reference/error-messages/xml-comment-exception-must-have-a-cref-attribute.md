---
title: "O comentário XML exceção deve ter um atributo &quot;cref&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42319
- vbc42319
dev_langs:
- VB
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: d476766478f67f39126bd374033f6604f0653d70
ms.lasthandoff: 03/13/2017

---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a>Exceção de comentário XML deve ter um atributo 'cref'
O \<exceção > marca fornece uma maneira para documentar as exceções que podem ser lançadas por um método. Necessário `cref` atributo designa o nome de um membro, que é verificado pelo gerador de documentação. Se o membro existe, ele é convertido para o nome canônico de elemento no arquivo de documentação.  
  
 **ID do erro:** BC42319  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Adicionar o `cref` atributo à exceção da seguinte maneira:  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [\<exceção >](../../../visual-basic/language-reference/xmldoc/exception.md)   
 [Como: criar documentação XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)   
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
