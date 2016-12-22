---
title: "&#39;&lt;typename&gt;&#39; &#233; um tipo delegado | Microsoft Docs"
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
  - "bc32008"
  - "vbc32008"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32008"
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; &#233; um tipo delegado
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

'\<typename\> ' é um tipo delegate.A construção delegate permite somente uma única expressão AddressOf como uma lista de argumentos.Geralmente, uma expressão AddressOf pode ser usada em vez de uma construção delegate.  
  
 A `New` cláusula criando uma instância de uma classe de delegado fornece uma lista de argumento inválido para o construtor delegate.  
  
 Você pode fornecer um único `AddressOf` ao criar uma nova instância do delegado de expressão.  
  
 Esse erro pode resultar se você não passar argumentos para o construtor delegate, se você passar mais de um argumento, ou se você passar um argumento único que não é válido `AddressOf` expressão.  
  
 **Identificação do erro:**  BC32008  
  
### Para corrigir este erro  
  
-   Usar um único `AddressOf` a expressão na lista de argumentos para a classe de delegado na `New` cláusula.  
  
## Consulte também  
 [Operador New](../../../visual-basic/language-reference/operators/new-operator.md)   
 [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Delegados](../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [Como invocar um método delegado](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)