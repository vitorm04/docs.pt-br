---
title: "&#39;&lt;typename&gt;&#39; n&#227;o pode ser herdado de &lt;type&gt; &#39;&lt;basetypename&gt;&#39; porque ele expande o acesso do &lt;type&gt; base fora do assembly | Microsoft Docs"
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
  - "vbc30910"
  - "bc30910"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30910"
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; n&#227;o pode ser herdado de &lt;type&gt; &#39;&lt;basetypename&gt;&#39; porque ele expande o acesso do &lt;type&gt; base fora do assembly
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma classe ou interface herda de uma classe base ou interface, mas tem um nível de acesso menos restritivo.  
  
 Por exemplo, uma interface `Public` herda de uma interface `Friend`, ou uma classe `Protected`herda a partir de uma classe `Private`.  Isso expõe a classe base ou interface para acesso além do nível desejado.  
  
 **Identificação do erro:**  BC30910  
  
### Para corrigir este erro  
  
-   Altere o nível de acesso da classe derivada ou interface para que seja pelo menos tão restritivo quanto a classe base ou interface.  
  
     \- ou \-  
  
-   Se você precisar que o nível de acesso seja menos restritivo, remova a declaração `Inherits`.  Você não pode herdar de uma classe base ou interface mais restritivas.  
  
## Consulte também  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)