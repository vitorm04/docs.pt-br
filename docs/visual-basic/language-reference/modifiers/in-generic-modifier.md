---
title: In (modificador genérico) (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 83e9aab4fc361754cfd750ae68f04b36dce13d0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="in-generic-modifier-visual-basic"></a>In (modificador genérico) (Visual Basic)
Para parâmetros de tipo genérico, a palavra-chave `In` especifica que o parâmetro de tipo é contravariante.  
  
## <a name="remarks"></a>Comentários  
 A contravariância permite que você use um tipo menos derivado do que aquele especificado pelo parâmetro genérico. Isso permite a conversão implícita de classes que implementam interfaces variantes e a conversão implícita de tipos delegados.  
  
 Para obter mais informações, consulte [Covariância e contravariância](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="rules"></a>Regras  
 Você pode usar a palavra-chave `In` em delegados e interfaces genéricas.  
  
 Um parâmetro de tipo pode ser declarado contravariant em uma interface genérica ou representante se ele é usado apenas como um tipo de argumentos de método e não é usado como um tipo de retorno do método. `ByRef`parâmetros não podem ser covariantes ou contravariant.  
  
 Covariância e contravariância são com suporte para tipos de referência e não tem suporte para tipos de valor.  
  
 No Visual Basic, você não pode declarar eventos em interfaces contravariant sem especificar o tipo delegado. Além disso, contravariant interfaces não podem ter aninhados classes, enumerações ou estruturas, mas eles podem ter aninhados interfaces.  
  
## <a name="behavior"></a>Comportamento  
 Uma interface que tem um parâmetro de tipo contravariante permite que os seus métodos aceitem argumentos de tipos menos derivados que aqueles especificados pelo parâmetro de tipo de interface. Por exemplo, como no .NET Framework 4, na interface <xref:System.Collections.Generic.IComparer%601>, o tipo T é contravariante, você poderá atribuir um objeto do tipo `IComparer(Of Person)` a um objeto do tipo `IComparer(Of Employee)`, sem usar qualquer método de conversão especial se o `Person` herdar o `Employee`.  
  
 Um delegado contravariante pode ser atribuído a outro delegado do mesmo tipo, mas com um parâmetro de tipo genérico menos derivado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como declarar, estender e implementar uma interface genérica contravariante. Ele também mostra como você pode usar a conversão implícita para classes que implementam essa interface.  
  
 [!code-vb[vbVarianceKeywords#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como declarar, instanciar e invocar um delegado genérico contravariante. Ele também mostra como você pode converter implicitamente um tipo delegado.  
  
 [!code-vb[vbVarianceKeywords#2](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Variação em Interfaces Genéricas](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [Saída](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
