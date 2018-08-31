---
title: Exceção de comentário XML deve ter um &#39;cref&#39; atributo
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: abe9fe0f6216f81fa223fe83a122b580577e1c32
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43255639"
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a>Exceção de comentário XML deve ter um &#39;cref&#39; atributo
O \<exceção > marca fornece uma maneira de documentar as exceções que podem ser lançadas por um método. Necessário `cref` atributo designa o nome de um membro, que é verificado pelo gerador de documentação. Se o membro existe, ele é convertido para o nome de elemento canônico no arquivo de documentação.  
  
 **ID do erro:** BC42319  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Adicionar o `cref` atributo à exceção da seguinte maneira:  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [Como criar documentação XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
