---
title: "NotOverridable (Visual Basic) | Microsoft Docs"
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
  - "vb.NotOverridable"
  - "NotOverridable"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "elementos, autenticada"
  - "métodos [Visual Basic], autenticada"
  - "Palavra-chave NotOverridable"
  - "substituição"
  - "procedimentos, substituição"
  - "procedimentos, redefinindo"
  - "propriedades [Visual Basic], substituição"
  - "propriedades [Visual Basic], redefinindo"
  - "elementos lacrados"
  - "Método lacrado"
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# NotOverridable (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que uma propriedade ou procedimento não podem ser substituídos em um classe derivada.  
  
## Comentários  
 O `NotOverridable` modificador impede que uma propriedade ou método que está sendo substituído em uma classe derivada.  O [Substituível](../../../visual-basic/language-reference/modifiers/overridable.md) modificador permite que uma propriedade ou método em uma classe para ser substituído em uma classe derivada.  Para obter mais informações, consulte [Noções básicas de herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Se a `Overridable` ou `NotOverridable` modificador não for especificado, a configuração padrão depende se a propriedade ou método substitui um método ou propriedade de classe base.  Se a propriedade ou método substitui um método ou propriedade de classe base, a configuração padrão é `Overridable`; Caso contrário, ele é `NotOverridable`.  
  
 Um elemento que não pode ser substituído às vezes é chamado um elemento *lacrado*.  
  
 Você pode usar `NotOverridable` somente na declaração de uma propriedade ou procedimento.  Você pode especificar `NotOverridable` apenas em uma propriedade ou procedimento que substitui outra propriedade ou procedimento, ou seja, somente em combinação com `Overrides`.  
  
## Modificadores combinados  
 Não é possível especificar `Overridable` ou `NotOverridable` para um `Private` método.  
  
 Não é possível especificar `NotOverridable` em conjunto com `MustOverride`, `Overridable`, ou `Shared` na mesma declaração.  
  
## Uso  
 O modificador `NotOverridable` pode ser utilizado nestes contextos:  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Consulte também  
 [Modificadores](../../../visual-basic/language-reference/modifiers/index.md)   
 [Noções básicas de herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)   
 [Substituível](../../../visual-basic/language-reference/modifiers/overridable.md)   
 [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Palavras\-chave](../../../visual-basic/language-reference/keywords/index.md)   
 [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)