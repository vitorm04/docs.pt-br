---
title: "'<membername>' não pode expor o tipo '<typename>' fora do projeto por meio de <containertype> '<containertypename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: a3972eabfe297b89c0e4d0f36943ac58e5bdf688
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162460"
---
# <a name="bc30909-membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a>BC30909: ' \<membername> ' não pode expor o tipo ' \<typename> ' fora do projeto por meio de \<containertype> ' \<containertypename> '

Uma variável, um parâmetro de procedimento ou um retorno de função é exposto fora de seu contêiner, mas é declarado como um tipo que não deve ser exposto fora do contêiner.

 O código esqueleto a seguir mostra uma situação que gera esse erro.

```vb
Private Class privateClass
End Class
Public Class mainClass
    Public exposedVar As New privateClass
End Class
```

 Um tipo declarado `Protected` , `Friend` , `Protected Friend` ou `Private` destinado a ter acesso limitado fora de seu contexto de declaração. Usá-lo como o tipo de dados de uma variável com acesso menos restrito anularia essa finalidade. No código esqueleto anterior, `exposedVar` é `Public` e seria exposto `privateClass` ao código que não deveria ter acesso a ele.

 **ID do erro:** BC30909

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Altere o nível de acesso da variável, do parâmetro de procedimento ou da função retornar para ser pelo menos tão restritivo quanto o nível de acesso de seu tipo de dados.

## <a name="see-also"></a>Veja também

- [Níveis de acesso no Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
