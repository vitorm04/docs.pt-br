---
title: "A primeira instru&#231;&#227;o deste &#39; Sub New &#39; deve ser uma chamada para &#39;MyBase.New&#39; ou &#39;MyClass.New&#39; (nenhum construtor acess&#237;vel sem par&#226;metros) | Microsoft Docs"
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
  - "bc30148"
  - "vbc30148"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30148"
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A primeira instru&#231;&#227;o deste &#39; Sub New &#39; deve ser uma chamada para &#39;MyBase.New&#39; ou &#39;MyClass.New&#39; (nenhum construtor acess&#237;vel sem par&#226;metros)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A primeira declaração deste ' Sub New ' deve ser uma chamada para 'MyBase.New' ou 'MyClass.New' porque a classe base '\< base \>' de '\< derived \>' tem mais de um 'Sub New ' acessível que pode ser chamado sem argumentos.  
  
 Em um classe derivada, cada Construtor deve chamar um construtor classe base \(`MyBase.New`\).  Se o classe base tem um construtor sem nenhum parâmetro que seja acessível a classes derivadas, `MyBase.New` pode ser chamado automaticamente.  Caso contrário, um construtor classe base deve ser chamado com parâmetros, e isso não pode ser feito automaticamente.  Nesse caso, a primeira instrução de cada construtor classe derivada deve ligar o classe base, um construtor com parâmetros ou chamar outro construtor no que torna um construtor classe base chamada classe derivada.  
  
 **Identificação do erro:**  BC30140  
  
### Para corrigir este erro  
  
-   Chame `MyBase.New` fornecendo os parâmetros necessários ou chame um construtor de mesmo nível que faça tal chamada.  
  
     Por exemplo, se a classe base tem um construtor que é declarado como `Public Sub New(ByVal index as Integer)`, a primeira instrução na derivada pode ser um construtor de classe `MyBase.New(100)`.  
  
## Consulte também  
 [Noções básicas de herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)