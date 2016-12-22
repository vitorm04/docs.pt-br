---
title: "Chin&#234;s simplificado e TraditionalChinese n&#227;o podem ser combinados | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrArgument_StrConvSCandTC"
ms.assetid: d8e6a11b-f549-43b5-8337-0594340e1325
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Chin&#234;s simplificado e TraditionalChinese n&#227;o podem ser combinados
Seu aplicativo está tentando combinar o `VbStrConv` membros de enumeração `SimplifiedChinese` e `TraditionalChinese`, que são mutuamente exclusivos.  
  
### Para corrigir este erro  
  
-   Remova `VbStrConv.SimplifiedChinese` ou `VbStrConv.TraditionalChinese`.  
  
## Consulte também  
 <xref:System.Globalization>   
 [NOTINBUILD VbStrConv Enumeration](http://msdn.microsoft.com/pt-br/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [Introdução a aplicativos internacionais com base no .NET Framework](/visual-studio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)