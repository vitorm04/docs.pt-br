---
title: '&#39;&lt;membername&gt; &#39; não pode expor o tipo &#39; &lt;typename&gt; &#39; fora do projeto por meio de &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 36add48ebee2d1804921eeeec0b59cdd4cbafecc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588087"
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a>&#39;&lt;membername&gt; &#39; não pode expor o tipo &#39; &lt;typename&gt; &#39; fora do projeto por meio de &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;
Uma variável, parâmetro de procedimento ou função de retorno é exposta fora de seu contêiner, mas ele é declarado como um tipo que não deve ser exposto fora do contêiner.  
  
 O seguinte código esqueleto mostra uma situação que gera este erro.  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 Um tipo que é declarado `Protected`, `Friend`, `Protected Friend`, ou `Private` destina-se para ter acesso fora de seu contexto de declaração limitado. Usá-lo como os dados de tipo de uma variável com acesso restrito menos anularia essa finalidade. No código anterior esqueleto, `exposedVar` é `Public` e poderia expor `privateClass` ao código que não deve ter acesso a ele.  
  
 **ID do erro:** BC30909  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Altere o nível de acesso da variável, parâmetro de procedimento ou função de retorno para ser pelo menos tão restritivo quanto o nível de acesso do seu tipo de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
