---
title: "Retomar sem erro | Microsoft Docs"
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
  - "vbrID20"
dev_langs: 
  - "VB"
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Retomar sem erro
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A `Resume` instrução apareceu fora do código de tratamento de erros, ou o código entrou em um manipulador de erro, mesmo que não ocorreu nenhum erro.  
  
### Para corrigir este erro  
  
1.  Mover o `Resume`instrução em um manipulador de erro, ou excluí\-la.  
  
2.  Portanto, salta para rótulos não pode ocorrer em vários procedimentos, pesquise o procedimento para o rótulo que identifica o manipulador de erro.  Se você encontrar um rótulo duplicado especificado como o destino de um `GoTo` instrução que não seja um `On Error GoTo` instrução, alterar o rótulo de linha para concordar com o seu destino.  
  
## Consulte também  
 [Instrução Resume](../../../visual-basic/language-reference/statements/resume-statement.md)   
 [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)