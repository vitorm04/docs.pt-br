---
title: "O ordinal n&#227;o &#233; v&#225;lido | Microsoft Docs"
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
  - "vbrID452"
dev_langs: 
  - "VB"
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O ordinal n&#227;o &#233; v&#225;lido
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Sua chamada à biblioteca de link dinâmico \(DLL\) indicada usa um número ao invés de um nome de procedimento, usando a sintaxe `#num`.  Este erro possui as seguintes causas possíveis:  
  
-   Uma tentativa de converter a eexpressão `#num` a um ordinal falhou.  
  
-   O `#num` especificado não especifica qualquer unção no DLL.  
  
-   Uma bilbioteca de tipo possui uma declaração inválida resultando num número ordinal inválido.  
  
### Para corrigir este erro  
  
1.  Certifique\-se de que a expressão representa um número válido, ou chame o procedimento pelo nome.  
  
2.  Certifique\-se de que `#num` identifica uma função válida no DLL.  
  
3.  Isole a chamada de procedimento causando o problema comentando pelo código.  Escreva uma declaração `Declare` para o procedimento, e relate o problema ao vendedor de biblioteca de tipo.  
  
## Consulte também  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)