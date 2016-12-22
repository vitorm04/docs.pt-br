---
title: "Substitu&#237;vel (Visual Basic) | Microsoft Docs"
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
  - "Overridable"
  - "vb.Overridable"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "elementos concretos"
  - "elementos, concreto"
  - "elementos, virtual"
  - "palavra-chave Overridable"
  - "substituição, palavra-chave Overridable"
  - "procedimentos, substituição"
  - "procedimentos, redefinindo"
  - "propriedades [Visual Basic], substituição"
  - "propriedades [Visual Basic], redefinindo"
  - "elementos virtuais"
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Substitu&#237;vel (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que uma propriedade ou um procedimento pode ser sobreposto por uma propriedade nomeada de forma idêntica ou procedimento em um classe derivada.  
  
## Comentários  
 O `Overridable` modificador permite que uma propriedade ou método em uma classe para ser substituído em uma classe derivada.  O [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modificador impede que uma propriedade ou método que está sendo substituído em uma classe derivada.  Para obter mais informações, consulte [Noções básicas de herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Se a `Overridable` ou `NotOverridable` modificador não for especificado, a configuração padrão depende se a propriedade ou método substitui um método ou propriedade de classe base.  Se a propriedade ou método substitui um método ou propriedade de classe base, a configuração padrão é `Overridable`; Caso contrário, ele é `NotOverridable`.  
  
 Você pode sombrear ou substituir para redefinir um elemento herdado, mas há diferenças significativas entre as duas abordagens.  Para obter mais informações, consulte [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
 Um elemento que pode ser substituído às vezes é conhecido como um elemento *Virtual*.  Se ele pode ser substituído, mas não precisa ser, ele é às vezes também chamado um elemento *Concrete*.  
  
 Você pode usar `Overridable` somente na declaração de uma propriedade ou procedimento.  
  
## Modificadores combinados  
 Não é possível especificar `Overridable` ou `NotOverridable` para um `Private` método.  
  
 Não é possível especificar `Overridable` em conjunto com `MustOverride`, `NotOverridable`, ou `Shared` na mesma declaração.  
  
 Como um elemento de substituição é implicitamente substituível, você não pode combinar `Overridable` com `Overrides`.  
  
## Uso  
 O modificador `Overridable` pode ser utilizado nestes contextos:  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Consulte também  
 [Modificadores](../../../visual-basic/language-reference/modifiers/index.md)   
 [Noções básicas de herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)   
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)   
 [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Palavras\-chave](../../../visual-basic/language-reference/keywords/index.md)   
 [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)