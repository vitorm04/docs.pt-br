---
title: "A classe n&#227;o d&#225; suporte &#224; automa&#231;&#227;o ou &#224; interface esperada | Microsoft Docs"
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
  - "vbrID430"
dev_langs: 
  - "VB"
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A classe n&#227;o d&#225; suporte &#224; automa&#231;&#227;o ou &#224; interface esperada
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A classe especificada na chamada de função `GetObject` ou `CreateObject` não expôs uma interface de programação ou você alterou um projeto de .dll para .exe, ou vice\-versa.  
  
### Para corrigir este erro  
  
1.  Verifique a documentação do aplicativo que criou o objeto para obter as limitações sobre o uso de automação com esta classe de objeto.  
  
2.  Se você alterou um projeto de .dll para .exe, ou vice\-versa, deverá cancelar o registro manualmente do .dll ou do .exe antigo.  
  
## Consulte também  
 [Tipos de erro](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [Fale conosco](/visual-studio/ide/talk-to-us)