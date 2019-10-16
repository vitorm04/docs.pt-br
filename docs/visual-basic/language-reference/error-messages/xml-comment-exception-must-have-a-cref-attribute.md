---
title: A exceção de comentário XML deve ter um atributo 'cref'
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 54965f3796b6c5ef0e387cd354abcb5740476257
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321170"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>A exceção de comentário XML deve ter um atributo 'cref'

A marca > \<exception fornece uma maneira de documentar as exceções que podem ser geradas por um método. O atributo `cref` necessário designa o nome de um membro, que é verificado pelo gerador de documentação. Se o membro existir, ele será convertido para o nome do elemento canônico no arquivo de documentação.

**ID do erro:** BC42319

## <a name="to-correct-this-error"></a>Para corrigir este erro

Adicione o atributo `cref` à exceção da seguinte maneira:

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a>Consulte também

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [Como criar documentação XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
