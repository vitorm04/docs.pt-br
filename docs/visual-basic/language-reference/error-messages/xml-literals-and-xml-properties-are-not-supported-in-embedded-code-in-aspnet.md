---
title: "Literais e propriedades de XML n&#227;o s&#227;o suportados em c&#243;digo inserido dentro do ASP.NET | Microsoft Docs"
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
  - "vbc31200"
  - "bc31200"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31200"
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Literais e propriedades de XML n&#227;o s&#227;o suportados em c&#243;digo inserido dentro do ASP.NET
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Não há suporte para literais XML e propriedades XML em código incorporado no ASP.NET.Para usar os recursos XML, mova o código para code\-behind.  
  
 Um literal XML ou uma propriedade de eixo XML é definida no código incorporado \(`<%= =>`\) em um arquivo do ASP.NET.  
  
 **Identificação do erro:**  BC31200  
  
### Para corrigir este erro  
  
-   Mova o código que inclui o literal XML ou arquivo de eixo XML para um arquivo code\-behind do ASP.NET.  
  
## Consulte também  
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Propriedades do eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)