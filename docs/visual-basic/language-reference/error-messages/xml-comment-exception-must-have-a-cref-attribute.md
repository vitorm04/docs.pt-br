---
title: A exceção de comentário XML deve ter um atributo 'cref'
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 18e7aa5f6905eaa9c509aa21fe6f5bfcd54d46f0
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163292"
---
# <a name="bc42319-xml-comment-exception-must-have-a-cref-attribute"></a>BC42319: a exceção de comentário XML deve ter um atributo ' cref '

A \<exception> marca fornece uma maneira de documentar as exceções que podem ser geradas por um método. O `cref` Atributo Required designa o nome de um membro, que é verificado pelo gerador de documentação. Se o membro existir, ele será convertido para o nome do elemento canônico no arquivo de documentação.

**ID do erro:** BC42319

## <a name="to-correct-this-error"></a>Para corrigir este erro

Adicione o `cref` atributo à exceção da seguinte maneira:

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a>Veja também

- [\<exception>](../xmldoc/exception.md)
- [Como criar documentação XML](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
- [Marcações de Comentário XML](../xmldoc/index.md)
