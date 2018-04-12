---
title: '&#39; &lt;membername&gt;&#39; não pode expor o tipo de &#39;&lt; TypeName&gt;&#39; fora do projeto por meio de &lt;containertype&gt; &#39;&lt; containertypename&gt;&#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd64c815286a5ffec111bcf1f68674a8e3558403
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a>&#39; &lt;membername&gt;&#39; não pode expor o tipo de &#39;&lt; TypeName&gt;&#39; fora do projeto por meio de &lt;containertype&gt; &#39;&lt; containertypename&gt;&#39;
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
