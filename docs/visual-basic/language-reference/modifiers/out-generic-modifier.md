---
title: "Out (modificador gen&#233;rico) (Visual Basic) | Microsoft Docs"
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
  - "vb.VarianceOut"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "covariância, palavra-chave Out [Visual Basic]"
  - "palavra-chave Out [Visual Basic]"
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Out (modificador gen&#233;rico) (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Para os parâmetros de tipo genérico, o `Out` palavra\-chave especifica que o tipo covariant.  
  
## Comentários  
 Covariância permite que você use um tipo mais derivado do que o especificado pelo parâmetro genérico.  Isso permite a conversão implícita de classes que implementam interfaces variant e conversão implícita de tipos delegate.  
  
 Para obter mais informações, consulte [Covariância e contravariância](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Regras  
 Você pode usar o `Out` palavra\-chave em delegados e interfaces genéricas.  
  
 Em uma interface genérica, um parâmetro de tipo pode ser declarado covariant se ele satisfaz as condições a seguir:  
  
-   O parâmetro de tipo é usado apenas como um tipo de retorno dos métodos de interface e não é usado como um tipo de argumentos do método.  
  
    > [!NOTE]
    >  Há uma exceção a essa regra.  Se tiver um delegado genérico do contravariant como um parâmetro de método em uma interface covariant, você pode usar o tipo covariant como um parâmetro de tipo genérico para este delegado.  Para obter mais informações sobre covariant e representantes de contravariant genéricos, consulte [Variação em delegações](../Topic/Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md) e [Usando variação para delegações genéricas Func e Action](../Topic/Using%20Variance%20for%20Func%20and%20Action%20Generic%20Delegates%20\(C%23%20and%20Visual%20Basic\).md).  
  
-   O parâmetro de tipo não é usado como restrição genérica para os métodos de interface.  
  
 Em um delegado genérico, um parâmetro de tipo pode ser declarado covariant se ele é usado apenas como um tipo de retorno do método e não é usado para argumentos de método.  
  
 Covariância\/contravariância há suporte para e para tipos de referência, mas eles não são suportados para tipos de valor.  
  
 No Visual Basic, você não pode declarar eventos em interfaces covariant sem especificar o tipo delegate.  Além disso, covariant interfaces não podem ter aninhadas classes, enumerações ou estruturas, mas pode ter aninhados interfaces.  
  
## Comportamento  
 Uma interface que possui um parâmetro de tipo covariant permite que os seus métodos retornar mais tipos derivados além daqueles especificados pelo parâmetro de tipo.  Por exemplo, porque no.NET Framework 4, em <xref:System.Collections.Generic.IEnumerable%601>, o tipo t é covariant, você pode atribuir um objeto da `IEnumerabe(Of String)` a um objeto do tipo da `IEnumerable(Of Object)` digitar sem usar quaisquer métodos de conversão especial.  
  
 Um delegado covariant pode ser atribuído a outro representante do mesmo tipo, mas com um parâmetro de tipo genérico mais derivado.  
  
## Exemplo  
 O exemplo a seguir mostra como declarar, estender e implementar uma interface genérica covariant.  Ele também mostra como usar a conversão implícita de classes que implementam uma interface covariant.  
  
 [!code-vb[vbVarianceKeywords#3](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_1.vb)]  
  
## Exemplo  
 O exemplo a seguir mostra como declarar, instanciar e invocar um delegado genérico covariant.  Ele também mostra como você pode usar a conversão implícita de tipos delegate.  
  
 [!code-vb[vbVarianceKeywords#4](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_2.vb)]  
  
## Consulte também  
 [Variação em interfaces genéricas](../Topic/Variance%20in%20Generic%20Interfaces%20\(C%23%20and%20Visual%20Basic\).md)   
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)