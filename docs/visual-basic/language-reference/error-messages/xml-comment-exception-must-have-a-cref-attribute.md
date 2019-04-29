---
title: A exceção de comentário XML deve ter um atributo 'cref'
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: a974df5d2305b88946981d0d258a8088b23d3fc3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766590"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>A exceção de comentário XML deve ter um atributo 'cref'
O \<exceção > marca fornece uma maneira de documentar as exceções que podem ser lançadas por um método. Necessário `cref` atributo designa o nome de um membro, que é verificado pelo gerador de documentação. Se o membro existe, ele é convertido para o nome de elemento canônico no arquivo de documentação.  
  
 **ID do erro:** BC42319  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Adicionar o `cref` atributo à exceção da seguinte maneira:  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a>Consulte também

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [Como: Criar documentação XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
