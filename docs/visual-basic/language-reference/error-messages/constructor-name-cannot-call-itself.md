---
title: "O construtor &#39;&lt;name&gt;&#39; n&#227;o pode se chamar | Microsoft Docs"
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
  - "bc30298"
  - "vbc30298"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30298"
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O construtor &#39;&lt;name&gt;&#39; n&#227;o pode se chamar
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um procedimento `Sub New` numa classe ou estrutura chama a si próprio.  
  
 O propósito de um construtor é inicializar uma instância de uma classe ou estrutura quando ela é criada primeiramente.  A classe ou estrutura pode ter vários contrutores, desde que cada um tenha diferentes listas de parâmetros.  Um construtor pode chamar outro construtor para performar uma funcionalidade adicional a sua própria.  Mas não faz sentido um construtor chamar a si mesmo, e na verdade isso resultaria numa recursão infinita se permitido.  
  
 **Identificação do erro:**  BC30298  
  
### Para corrigir este erro  
  
1.  Verifique a lista de parâmetro do construtor sendo chamado.  Deve ser diferente da do construtor fazendo a chamada.  
  
2.  Se você não pretende chamar um construtor diferente, remova a chamada `Sub New` inteiramente.  
  
## Consulte também  
 [Tempo de vida do objeto: como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)