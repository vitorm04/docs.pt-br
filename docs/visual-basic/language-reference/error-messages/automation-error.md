---
title: "Erro de automa&#231;&#227;o | Microsoft Docs"
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
  - "vbrID440"
dev_langs: 
  - "VB"
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Erro de automa&#231;&#227;o
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Ocorreu um erro ao executar um método ou ao obter ou configurar uma propriedade de uma variável de objeto.  O erro foi relatado pelo aplicativo que criou o objeto.  
  
### Para corrigir este erro  
  
1.  Verifique as propriedades do objeto `Err` para determinar a origem e a natureza do erro.  
  
2.  Use a instrução `On Error Resume Next` imediatamente antes de acessar a instrução e, em seguida, verifique se há erros imediatamente após acessar a instrução.  
  
## Consulte também  
 [Tipos de erro](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [Fale conosco](/visual-studio/ide/talk-to-us)