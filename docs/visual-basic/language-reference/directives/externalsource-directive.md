---
title: "Diretiva #ExternalSource | Microsoft Docs"
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
  - "#Externalsource"
  - "#ExternalSource"
  - "vb.ExternalSource"
  - "Externalsource"
  - "vb.#ExternalSource"
  - "ExternalSource"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Diretiva #ExternalSource"
  - "diretiva ExternalSource (#ExternalSource)"
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
caps.latest.revision: 160
caps.handback.revision: 160
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Diretiva #ExternalSource
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Indica um mapeamento entre linhas específicas do código\-fonte e texto externo a fonte.  
  
## Sintaxe  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## Partes  
 `StringLiteral`  
 O caminho para a fonte externa.  
  
 `IntLiteral`  
 O número de linha da primeira linha da fonte externa.  
  
 `LogicalLine`  
 A linha onde o erro ocorre na fonte externa.  
  
 `#End ExternalSource`  
 Encerra o bloco  `#ExternalSource`.  
  
## Comentários  
 Essa diretiva é usada somente pelo compilador e o depurador.  
  
 Um arquivo de origem pode incluir diretivas de fonte externa, que indicam um mapeamento entre texto externos à origem e linhas específicas do código de arquivo de origem, como um arquivo .aspx.  Se forem encontrados erros no código\-fonte designado durante a compilação, eles são identificados como provenientes de fonte externa.  
  
 Diretivas de fonte externa não têm efeito na compilação e não podem ser aninhadas.  Eles são destinados ao uso interno pelo aplicativo somente.  
  
## Consulte também  
 [Compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)