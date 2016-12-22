---
title: "Nenhum m&#233;todo &#39;Main&#39; acess&#237;vel com uma assinatura apropriada foi encontrado em &#39;&lt;name&gt;&#39; | Microsoft Docs"
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
  - "bc30737"
  - "vbc30737"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30737"
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Nenhum m&#233;todo &#39;Main&#39; acess&#237;vel com uma assinatura apropriada foi encontrado em &#39;&lt;name&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Aplicativos de linha de comando devem ter um `Sub Main` definido.  `Main`deve ser declarado como `Public Shared` se ele for definido em uma classe ou como `Public` se definido em um módulo.  
  
 Para obter mais informações sobre `Main`, consulte: [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/pt-br/9d030b60-e148-4366-a462-69532f02294c).  
  
 **Identificação do erro:**  BC30737  
  
### Para corrigir este erro  
  
-   Defina um procedimento `Public Sub Main` para seu projeto.  Declare\-o como `Shared` somente se você defini\-lo dentro de uma classe.  
  
## Consulte também  
 [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/pt-br/9d030b60-e148-4366-a462-69532f02294c)   
 [Estrutura de um programa Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)   
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)