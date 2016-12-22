---
title: "&#39;&lt;membername&gt;&#39; n&#227;o pode expor o tipo &#39;&lt;typename&gt;&#39; fora do projeto por meio de &lt;containertype&gt; &#39;&lt;containertypename&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30909"
  - "vbc30909"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30909"
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;membername&gt;&#39; n&#227;o pode expor o tipo &#39;&lt;typename&gt;&#39; fora do projeto por meio de &lt;containertype&gt; &#39;&lt;containertypename&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma variável, o parâmetro de procedimento ou função de retorno é exposta fora de seu recipiente, mas ela é declarada como um tipo que não deve ser exposto fora do contêiner.  
  
 O esqueleto código a seguir mostra uma situação que gera esse erro.  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 Um tipo que é declarado `Protected`, `Friend`, `Protected Friend`, ou `Private` destina\-se tenham acesso fora de seu contexto de declaração limitado.  Usá\-lo como dados de tipo de uma variável com acesso menos restrito acabaria com essa finalidade.  No código anterior esqueleto, `exposedVar` é `Public` e exporia `privateClass` ao código que não deveria ter acesso a ele.  
  
 **Identificação do erro:**  BC30909  
  
### Para corrigir este erro  
  
-   Alterar o nível de acesso do parâmetro de procedimento, variável ou função retornar ao ser pelo menos, tão restritivos quanto o nível de acesso de seu tipo de dados.  
  
## Consulte também  
 [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)