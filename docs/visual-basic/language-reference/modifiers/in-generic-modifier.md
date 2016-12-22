---
title: "In (modificador gen&#233;rico) (Visual Basic) | Microsoft Docs"
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
  - "vb.VarianceIn"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "contravariância, palavra-chave In [Visual Basic]"
  - "palavra-chave In [Visual Basic]"
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# In (modificador gen&#233;rico) (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Para os parâmetros de tipo genérico, o `In` palavra\-chave especifica que o parâmetro de tipo é contravariant.  
  
## Comentários  
 \/ Contravariância permite que você use um tipo derivado menos do que o especificado pelo parâmetro genérico.  Isso permite a conversão implícita de classes que implementam interfaces variant e conversão implícita de tipos delegate.  
  
 Para obter mais informações, consulte [Covariância e contravariância](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Regras  
 Você pode usar o `In` palavra\-chave em delegados e interfaces genéricas.  
  
 Um parâmetro de tipo pode ser declarado contravariant em uma interface genérica ou delegado se ele é usado apenas como um tipo de argumentos de método e não é usado como um tipo de retorno do método.  `ByRef`parâmetros não podem ser covariant ou contravariant.  
  
 Covariância\/contravariância são suporte para tipos de referência e não há suporte para tipos de valor.  
  
 No Visual Basic, você não pode declarar eventos em interfaces contravariant sem especificar o tipo delegate.  Além disso, contravariant interfaces não podem ter aninhadas classes, enumerações ou estruturas, mas pode ter aninhados interfaces.  
  
## Comportamento  
 Uma interface que possui um parâmetro de tipo contravariant permite que os seus métodos aceitar os argumentos de menos tipos derivados além daqueles especificados pelo parâmetro de tipo de interface.  Por exemplo, porque no.NET Framework 4, no <xref:System.Collections.Generic.IComparer%601> interface, tipo t contravariant, você pode atribuir um objeto da `IComparer(Of Person)` a um objeto do tipo da `IComparer(Of Employee)` tipo sem usar quaisquer métodos de conversão especial se `Person` herda `Employee`.  
  
 Um delegado contravariant pode ser atribuído a outro representante do mesmo tipo, mas com um parâmetro de tipo genérico menos derivado.  
  
## Exemplo  
 O exemplo a seguir mostra como declarar, estender e implementar uma interface genérica de contravariant.  Ele também mostra como você pode usar a conversão implícita para classes que implementam esta interface.  
  
 [!code-vb[vbVarianceKeywords#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_1.vb)]  
  
## Exemplo  
 O exemplo a seguir mostra como declarar, instanciar e invocar um delegado genérico do contravariant.  Ele também mostra como você pode converter implicitamente um tipo delegate.  
  
 [!code-vb[vbVarianceKeywords#2](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_2.vb)]  
  
## Consulte também  
 [Variação em interfaces genéricas](../Topic/Variance%20in%20Generic%20Interfaces%20\(C%23%20and%20Visual%20Basic\).md)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)