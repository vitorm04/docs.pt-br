---
title: "Out (modificador genérico) (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.VarianceOut
dev_langs:
- VB
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 9210c07e469ab3b7968ac813730fec963f01d96b
ms.lasthandoff: 03/13/2017

---
# <a name="out-generic-modifier-visual-basic"></a>Out (modificador genérico) (Visual Basic)
Para parâmetros de tipo genérico, o `Out` palavra-chave especifica que o tipo é covariante.  
  
## <a name="remarks"></a>Comentários  
 Covariância permite que você use um tipo mais derivado que o especificado pelo parâmetro genérico. Isso permite a conversão implícita de classes que implementam interfaces variantes e conversão implícita de tipos de delegado.  
  
 Para obter mais informações, consulte [covariância e contravariância](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8).  
  
## <a name="rules"></a>Regras  
 Você pode usar o `Out` palavra-chave em interfaces e delegados genéricos.  
  
 Em uma interface genérica, um parâmetro de tipo pode ser declarado covariante se ele satisfaz as condições a seguir:  
  
-   O parâmetro de tipo é usado apenas como um tipo de retorno dos métodos de interface e não é usado como um tipo de argumentos do método.  
  
    > [!NOTE]
    >  Há uma exceção a essa regra. Se tiver um delegado genérico contravariant como um parâmetro de método em uma interface covariante, você pode usar o tipo covariante como um parâmetro de tipo genérico para este delegado. Para obter mais informações sobre covariant e contravariant delegados genéricos, consulte [variação em delegações](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca) e [usando variação para ação delegações genéricas Func e](http://msdn.microsoft.com/library/e69c4f39-09aa-4c6d-a752-08cc767d8290).  
  
-   O parâmetro de tipo não é usado como uma restrição genérica para os métodos de interface.  
  
 Um delegado genérico, um parâmetro de tipo pode ser declarado covariante se ele for usado apenas como um tipo de retorno do método e não usado para argumentos de método.  
  
 Covariância e contravariância têm suporte para tipos de referência, mas eles não têm suporte para tipos de valor.  
  
 No Visual Basic, você não pode declarar os eventos em interfaces covariantes sem especificar o tipo de delegado. Também não podem ter aninhados interfaces covariantes classes, enums ou estruturas, mas podem ter aninhados interfaces.  
  
## <a name="behavior"></a>Comportamento  
 Uma interface que tem um parâmetro de tipo covariant permite que seus métodos retornar mais tipos derivados que o especificado pelo parâmetro de tipo. Por exemplo, porque no .NET Framework 4, em <xref:System.Collections.Generic.IEnumerable%601>, T tipo é covariante, você pode atribuir um objeto do `IEnumerabe(Of String)` tipo para um objeto do `IEnumerable(Of Object)` tipo sem usar qualquer método de conversão especial.</xref:System.Collections.Generic.IEnumerable%601>  
  
 Um delegado de covariante pode ser atribuído a outro representante do mesmo tipo, mas com um parâmetro de tipo genérico mais derivado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como declarar, estender e implementar uma interface genérica covariante. Ele também mostra como usar a conversão implícita para classes que implementam uma interface covariante.  
  
 [!code-vb[vbVarianceKeywords n º&3;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como declarar e instanciar e invocar um delegado genérico covariante. Ele também mostra como você pode usar a conversão implícita de tipos delegados.  
  
 [!code-vb[vbVarianceKeywords n º&4;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Variação em Interfaces genéricas](http://msdn.microsoft.com/library/e14322da-1db3-42f2-9a67-397daddd6b6a)   
 [Em](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
