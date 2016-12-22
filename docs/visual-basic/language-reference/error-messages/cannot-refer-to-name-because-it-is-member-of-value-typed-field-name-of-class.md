---
title: "N&#227;o &#233; poss&#237;vel fazer refer&#234;ncia a &#39;&lt;name&gt;&#39; porque ele &#233; um membro do campo de tipo de valor &#39;&lt;name&gt;&#39; da classe &#39;&lt;classname&gt;&#39; que tem &#39;System.MarshalByRefObject&#39; como uma classe base | Microsoft Docs"
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
  - "vbc30310"
  - "bc30310"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30310"
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o &#233; poss&#237;vel fazer refer&#234;ncia a &#39;&lt;name&gt;&#39; porque ele &#233; um membro do campo de tipo de valor &#39;&lt;name&gt;&#39; da classe &#39;&lt;classname&gt;&#39; que tem &#39;System.MarshalByRefObject&#39; como uma classe base
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A classe `System.MarshalByRefObject` libera aplicações que suportam acesso remoto a objetos fora dos limites do domínio da aplicação.  Tipos devem herdar da classe `MarshalByRejectObject` quando o tipo é usado além dos limites do domínio da aplicação.  O estado do objeto não deve ser copiado porque os membros do objeto não são usáveis fora do domínio da aplicação em que foram criados.  
  
 **Identificação do erro:**  BC30310  
  
### Para corrigir este erro  
  
1.  Verifique a referência para ter certeza que o membro sendo referenciado é válido.  
  
2.  Qualifique explicitamente o membro com a palavra chave `Me`.  
  
## Consulte também  
 <xref:System.MarshalByRefObject>   
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)