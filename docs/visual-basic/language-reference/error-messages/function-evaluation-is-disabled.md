---
title: "A avalia&#231;&#227;o de fun&#231;&#227;o est&#225; desabilitada porque uma avalia&#231;&#227;o de fun&#231;&#227;o anterior atingiu o tempo limite | Microsoft Docs"
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
  - "bc30957"
  - "vbc30957"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30957"
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A avalia&#231;&#227;o de fun&#231;&#227;o est&#225; desabilitada porque uma avalia&#231;&#227;o de fun&#231;&#227;o anterior atingiu o tempo limite
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A avaliação de função está desabilitada porque o tempo limite de uma avaliação de função anterior foi alcançado.Para habilitar novamente a avaliação de função, execute a etapa outra vez ou reinicie a depuração.  
  
 O depurador Visual Studio, uma expressão especifica um chamada de procedimento, mas outra avaliação expirou.  
  
 As possíveis causas para um chamada de procedimento ter seu tempo esgotado incluem um loop infinito ou *loop sem fim* .  Para obter mais informações, consulte [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md).  
  
 Um caso especial de um loop infinito é  *recursão* .  Para obter mais informações, consulte [Procedimentos recursivos](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).  
  
 **Identificação do Erro:**BC30957  
  
### Para corrigir este erro  
  
1.  Se possível, determine qual foi a avaliação da função anterior e o que causou o esgotamento do tempo limite.  Caso contrário, você pode encontrar esse erro novamente.  
  
2.  Passe para o próximo passo do depurador novamente, ou encerre e reinicie a depuração.  
  
## Consulte também  
 [Depurando no Visual Studio](/visual-studio/debugger/debugging-in-visual-studio)   
 [Navegar pelo Código com o Depurador](/visual-studio/debugger/navigating-through-code-with-the-debugger)   
 [Expressões no Visual Basic](../Topic/Expressions%20in%20Visual%20Basic.md)