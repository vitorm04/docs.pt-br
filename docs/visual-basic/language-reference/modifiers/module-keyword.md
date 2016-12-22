---
title: "M&#243;dulo &lt;keyword&gt; (Visual Basic) | Microsoft Docs"
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
  - "vb.ModuleAttribute"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "blocos de atributo, palavra-chave Module"
  - "palavra-chave Module"
  - "Modificador de módulo"
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# M&#243;dulo &lt;keyword&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que um atributo no início de um arquivo de origem se aplica ao módulo de assembly atual.  
  
## Comentários  
 Muitos atributos referem\-se a um elemento de programação individual, tal como uma classe ou propriedade.  Você aplicar tal um atributo, anexando o bloco de atributo, entre colchetes angulares \(`< >`\), diretamente à instrução de declaração.  
  
 Se um atributo pertence não apenas para o seguinte elemento, mas para o módulo do assembly atual, você pode colocar o bloco de atributo no início do arquivo de origem e identificar o atributo com o `Module` palavra\-chave.  Se ela se aplica ao assembly inteiro, se você usa o [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) palavra\-chave.  
  
 O `Module` o modificador não é igual a [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md).  
  
## Consulte também  
 [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)   
 [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)   
 [Atributos](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)