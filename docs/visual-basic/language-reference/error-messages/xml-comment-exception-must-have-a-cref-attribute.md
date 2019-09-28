---
title: A exceção de comentário XML deve ter um atributo 'cref'
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 2e57dc63cb7ad8b2e061296a082d6fa79b464f08
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592035"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>A exceção de comentário XML deve ter um atributo 'cref'
A marca > \<exception fornece uma maneira de documentar as exceções que podem ser geradas por um método. O atributo `cref` necessário designa o nome de um membro, que é verificado pelo gerador de documentação. Se o membro existir, ele será convertido para o nome do elemento canônico no arquivo de documentação.  
  
 **ID do erro:** BC42319  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Adicione o atributo `cref` à exceção da seguinte maneira:  
  
    xml  
    <exception cref="member">Descrição</exception> de ' ' '  
    ```  
  
## See also

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md)
