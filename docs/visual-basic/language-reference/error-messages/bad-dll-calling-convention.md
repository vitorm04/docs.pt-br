---
title: "Conven&#231;&#227;o de chamada de DLL inv&#225;lida | Microsoft Docs"
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
  - "vbrID49"
dev_langs: 
  - "VB"
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Conven&#231;&#227;o de chamada de DLL inv&#225;lida
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Argumentos passados para uma biblioteca de vínculo dinâmico \(DLL\) devem corresponder exatamente àqueles esperado pela rotina.  Convenções de chamada lidar com número, tipo e ordem dos argumentos.  Seu programa pode ser chamando uma rotina em uma DLL que é passada a tipo errado ou o número de argumentos.  
  
### Para corrigir este erro  
  
1.  Certifique\-se de que todos os tipos de argumento de acordo com aquelas especificadas na declaração de rotina que você está chamando.  
  
2.  Certifique\-se de que você está passando o mesmo número de argumentos indicado na declaração de rotina que você está chamando.  
  
3.  Se a rotina DLL espera argumentos por valor, certifique\-se que `ByVal` é especificado para esses argumentos na declaração para a rotina.  
  
## Consulte também  
 [Tipos de erro](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [Instrução Call](../../../visual-basic/language-reference/statements/call-statement.md)   
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)