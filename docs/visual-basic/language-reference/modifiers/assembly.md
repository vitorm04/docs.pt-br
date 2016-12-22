---
title: "Assembly (Visual Basic) | Microsoft Docs"
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
  - "vb.Assembly"
  - "vb.AssemblyAttribute"
  - "Assembly"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "palavra-chave Assembly"
  - "modificador Assembly"
  - "blocos de atributo, palavra-chave Assembly"
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Assembly (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que um atributo no início de um arquivo de origem se aplica ao conjunto inteiro.  
  
## Comentários  
 Muitos atributos referem\-se a um elemento de programação individual, tal como uma classe ou propriedade.  Você aplicar tal um atributo, anexando o bloco de atributo, entre colchetes angulares \(`< >`\), diretamente à instrução de declaração.  
  
 Se um atributo pertence não apenas ao seguinte elemento mas ao conjunto inteiro, você coloca o bloco de atributo no início do arquivo de origem e identifica o atributo com a palavra\-chave `Assembly`.  Se ele se aplica ao conjunto de módulos atual \(assembly\), use a palavra\-chave [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md).  
  
 Você também pode aplicar um atributo a um conjunto de módulos \(assembly\) no arquivo AssemblyInfo.vb, nesse caso, você não precisa usar um bloco de atributo em seu arquivo de código fonte principal.  
  
## Consulte também  
 [Módulo \<keyword\>](../../../visual-basic/language-reference/modifiers/module-keyword.md)   
 [Atributos](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)