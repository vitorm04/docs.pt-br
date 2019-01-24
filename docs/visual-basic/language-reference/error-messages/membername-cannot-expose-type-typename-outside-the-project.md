---
title: '&#39;&lt;membername&gt; &#39; não é possível expor o tipo &#39; &lt;typename&gt; &#39; fora do projeto até &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 39d316aca5ec306de4b1e43e2eb2d1495f5525d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672338"
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a>&#39;&lt;membername&gt; &#39; não é possível expor o tipo &#39; &lt;typename&gt; &#39; fora do projeto até &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;
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
