---
title: "In (modificador genérico) (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.VarianceIn
dev_langs:
- VB
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 66f093e1fb1682268aef89fd215c1923c83da6fb
ms.lasthandoff: 03/13/2017

---
# <a name="in-generic-modifier-visual-basic"></a>In (modificador genérico) (Visual Basic)
Para parâmetros de tipo genérico, o `In` palavra-chave especifica o parâmetro de tipo é contravariante.  
  
## <a name="remarks"></a>Comentários  
 Contravariância permite que você use um tipo derivado que o especificado pelo parâmetro genérico. Isso permite a conversão implícita de classes que implementam interfaces variantes e conversão implícita de tipos de delegado.  
  
 Para obter mais informações, consulte [covariância e contravariância](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8).  
  
## <a name="rules"></a>Regras  
 Você pode usar o `In` palavra-chave em interfaces e delegados genéricos.  
  
 Um parâmetro de tipo pode ser declarado contravariant em uma interface genérica ou delegado se ele for usado apenas como um tipo de argumentos de método e não é usado como um tipo de retorno do método. `ByRef`parâmetros não podem ser covariantes ou contravariant.  
  
 Covariância e contravariância são tem suporte para tipos de referência e não tem suporte para tipos de valor.  
  
 No Visual Basic, você não pode declarar os eventos em interfaces contravariant sem especificar o tipo de delegado. Além disso, contravariant interfaces não podem ter aninhados classes, enums ou estruturas, mas podem ter aninhados interfaces.  
  
## <a name="behavior"></a>Comportamento  
 Uma interface que tem um parâmetro de tipo contravariant permite que os seus métodos aceitam argumentos de menos tipos derivados que o especificado pelo parâmetro de tipo de interface. Por exemplo, porque no .NET Framework 4, no <xref:System.Collections.Generic.IComparer%601>interface, tipo T contravariant, você pode atribuir um objeto do `IComparer(Of Person)` um objeto do tipo o `IComparer(Of Employee)` tipo sem usar qualquer método de conversão especial se `Person` herda `Employee`.</xref:System.Collections.Generic.IComparer%601>  
  
 Um delegado contravariant pode ser atribuído a outro representante do mesmo tipo, mas com um parâmetro de tipo genérico menos derivado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como declarar, estender e implementar uma interface genérica contravariant. Ele também mostra como você pode usar a conversão implícita para classes que implementam esta interface.  
  
 [!code-vb[vbVarianceKeywords n º&1;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como declarar e instanciar e invocar um delegado genérico contravariant. Ele também mostra como você pode converter implicitamente um tipo delegado.  
  
 [!code-vb[vbVarianceKeywords n º&2;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Variação em Interfaces genéricas](http://msdn.microsoft.com/library/e14322da-1db3-42f2-9a67-397daddd6b6a)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
