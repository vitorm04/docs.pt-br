---
title: Exceção de comentário XML deve ter um &#39;cref&#39; atributo
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 0f276781165e80b2d869da2518dbe34b33085d5c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649941"
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
- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [Como: Criar documentação XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
