---
title: "&quot;&lt;membername&gt;&quot;não pode expor o tipo&quot;&lt;typename&gt;&quot; fora do projeto por meio de &lt;containertype&gt; &quot;&lt;containertypename&gt;&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30909
- vbc30909
dev_langs:
- VB
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
caps.latest.revision: 8
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7e1f96262300e18dcadb425d37afc3829593f312
ms.lasthandoff: 03/13/2017

---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a>'&lt;membername&gt;'não pode expor o tipo'&lt;typename&gt;' fora do projeto por meio de &lt;containertype&gt; '&lt;containertypename&gt;'
Uma variável, parâmetro de procedimento ou função de retorno é exposta fora de seu contêiner, mas ele é declarado como um tipo que não deve ser exposto fora do contêiner.  
  
 O seguinte código de esqueleto mostra uma situação que gera esse erro.  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 Um tipo que é declarado `Protected`, `Friend`, `Protected Friend`, ou `Private` destina-se para ter acesso limitado à fora de seu contexto de declaração. Usá-lo como dados de tipo de uma variável com acesso menos restrito acabaria com essa finalidade. No código anterior esqueleto, `exposedVar` é `Public` e poderia expor `privateClass` ao código que não deve ter acesso a ele.  
  
 **ID do erro:** BC30909  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Alterar o nível de acesso da variável, parâmetro de procedimento ou função de retorno para ser pelo menos tão restritivo quanto o nível de acesso de seu tipo de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
