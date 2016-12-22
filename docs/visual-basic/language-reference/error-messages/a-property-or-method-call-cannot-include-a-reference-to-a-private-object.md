---
title: "Uma chamada de propriedade ou m&#233;todo n&#227;o pode incluir uma refer&#234;ncia a um objeto particular, como um argumento ou um valor de retorno | Microsoft Docs"
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
  - "vbrID98"
dev_langs: 
  - "VB"
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Uma chamada de propriedade ou m&#233;todo n&#227;o pode incluir uma refer&#234;ncia a um objeto particular, como um argumento ou um valor de retorno
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Entre as causas possíveis desse erro são:  
  
-   Um cliente chamou uma propriedade ou método de um componente fora de processo e tentou passar uma referência a um objeto particular como um dos argumentos.  
  
-   Um componente fora de processo chamou um método de retorno de chamada no seu cliente e tentou passar uma referência a um objeto particular.  
  
-   Um componente fora de processo tentou passar uma referência a um objeto particular como um argumento de um evento que ele estava lançando.  
  
-   Um cliente tentou atribuir uma referência de objeto particular para um `ByRef` argumento de um evento que ele estava tratando.  
  
### Para corrigir este erro  
  
1.  Remova a referência.  
  
## Consulte também  
 [Particular](../../../visual-basic/language-reference/modifiers/private.md)