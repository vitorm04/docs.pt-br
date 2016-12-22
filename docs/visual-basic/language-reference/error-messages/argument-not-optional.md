---
title: "Argumento n&#227;o opcional (Visual Basic) | Microsoft Docs"
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
  - "vbrID449"
dev_langs: 
  - "VB"
ms.assetid: 76e7bcf3-24ed-4cd5-945b-b98f1c76944b
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Argumento n&#227;o opcional (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O número e tipos dos argumentos devem corresponder a aqueles que são esperados.  Há um número incorreto de argumentos, ou um argumento omitido não é opcional.  Um argumento só pode ser omitido de uma chamada para um procedimento definido pelo usuário se ele foi declarado `Optional` na definição do procedimento.  
  
### Para corrigir este erro  
  
1.  Forneça todos os argumentos necessários.  
  
2.  Certifique\-se de que argumentos omotidos são opcionais.  Se não são, tforneça o argumento na chamada ou declare o parâmetro `Optional` na definição.  
  
## Consulte também  
 [Tipos de erro](../../../visual-basic/programming-guide/language-features/error-types.md)