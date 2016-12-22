---
title: "Arquivo n&#227;o localizado (erro de tempo de execu&#231;&#227;o do Visual Basic) | Microsoft Docs"
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
  - "vbrID53"
dev_langs: 
  - "VB"
ms.assetid: 57addb16-6f9a-444d-8af8-dda52431daca
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Arquivo n&#227;o localizado (erro de tempo de execu&#231;&#227;o do Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O arquivo não foi encontrado onde especificado.  O erro tem as seguintes possíveis causas:  
  
-   Uma instrução refere\-se a um arquivo que não existe.  
  
-   Foi feita uma tentativa para chamar um procedimento em uma biblioteca de vínculo dinâmico \(DLL\), mas a biblioteca especificada na cláusula `Lib` da declaração `Declare` não pode ser encontrada.  
  
-   Você tentou abrir um projeto ou carregar um arquivo de texto que não existe.  
  
### Para corrigir este erro  
  
1.  Verifique a digitação do nome de arquivo e a especificação do caminho.  
  
## Consulte também  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)