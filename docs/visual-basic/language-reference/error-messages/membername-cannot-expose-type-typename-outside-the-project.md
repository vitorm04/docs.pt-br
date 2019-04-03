---
title: "'<membername>' não pode expor o tipo '<typename>' fora do projeto por meio de <containertype> '<containertypename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 16f579a05236ba8977a071cb08068be8e98799f8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818327"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a>'\<membername >' não pode expor o tipo '\<typename >' fora do projeto até \<containertype > '\<containertypename >'
Uma variável, parâmetro de procedimento ou função de retorno seja exposta fora de seu contêiner, mas ele é declarado como um tipo que não deve ser exposto fora do contêiner.  
  
 O seguinte código de esqueleto mostra uma situação que gera esse erro.  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 Um tipo que é declarado `Protected`, `Friend`, `Protected Friend`, ou `Private` destina-se para ter acesso fora de seu contexto de declaração limitado. Usando-a como os dados de tipo de uma variável com acesso restrito menos acabaria com essa finalidade. No código de esqueleto anterior, `exposedVar` está `Public` e poderia expor `privateClass` ao código que não deveriam ter acesso a ele.  
  
 **ID do erro:** BC30909  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Alterar o nível de acesso da variável, parâmetro de procedimento ou função de retorno para ser, pelo menos, tão restritivos quanto o nível de acesso de seu tipo de dados.  
  
## <a name="see-also"></a>Consulte também

- [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
