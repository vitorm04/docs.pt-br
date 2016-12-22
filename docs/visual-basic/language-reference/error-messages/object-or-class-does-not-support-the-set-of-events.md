---
title: "O objeto ou a classe n&#227;o d&#225; suporte ao conjunto de eventos | Microsoft Docs"
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
  - "vbrID459"
dev_langs: 
  - "VB"
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O objeto ou a classe n&#227;o d&#225; suporte ao conjunto de eventos
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você tentou usar uma variável `WithEvents` com um componente que não pode trabalhar como uma fonte de evento para o conjunto de eventos especificado.  Por exemplo, você quis afundar os eventos de um objeto, então criar outro objeto que `Implements` o primeiro objeto.  Embora você possa imaginar que você poderia coletor de eventos do objeto implementado, isso nem sempre é o caso.  `Implements`apenas implementa uma interface para métodos e propriedades.  `WithEvents`Não há suporte para private`UserControls`, porque as informações de tipo necessários para aumentar a `ObjectEvent` não está disponível em tempo de execução.  
  
### Para corrigir este erro  
  
1.  Você não pode afundar eventos para um componente que não faz eventos fonte.  
  
## Consulte também  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)   
 [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)