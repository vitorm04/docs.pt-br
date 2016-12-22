---
title: "Esta matriz &#233; fixa ou est&#225; temporariamente bloqueada (Visual Basic) | Microsoft Docs"
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
  - "vbrID10"
dev_langs: 
  - "VB"
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Esta matriz &#233; fixa ou est&#225; temporariamente bloqueada (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este erro possui as seguintes causas possíveis:  
  
-   Usando `ReDim` para alterar o número de elementos de uma matriz de tamanho fixo.  
  
-   Redimensioning uma matriz dinâmica do nível de módulo, em que um elemento foi passado como um argumento para um procedimento.  Se um elemento for passado, o array está bloqueado para impedir a desalocação de memória para o parâmetro de referência dentro do procedimento.  
  
-   Tentativa de atribuir um valor para um `Variant` variável contendo uma matriz, mas o `Variant` está bloqueado no momento.  
  
### Para corrigir este erro  
  
1.  Verifique a matriz original dinâmico em vez de fixo, declarando\-o com o `ReDim` \(se a matriz é declarada dentro de um procedimento\), ou, declarando\-o sem especificar o número de elementos \(se a matriz é declarada no nível de módulo.  
  
2.  Determine se você realmente precisa passar o elemento, uma vez que é visível em todos os procedimentos no módulo.  
  
3.  Determinar o que está bloqueando a `Variant` e corrigi\-lo.  
  
## Consulte também  
 [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)