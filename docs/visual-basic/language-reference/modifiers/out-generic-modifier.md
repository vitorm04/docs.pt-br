---
title: Out (modificador genérico) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
ms.openlocfilehash: 367cbd373df2a38a56e5362f66bedd5c0ec24efb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522747"
---
# <a name="out-generic-modifier-visual-basic"></a>Out (modificador genérico) (Visual Basic)
Para parâmetros de tipo genérico, o `Out` palavra-chave especifica que o tipo é covariante.  
  
## <a name="remarks"></a>Comentários  
 A covariância permite que você use um tipo mais derivado do que aquele especificado pelo parâmetro genérico. Isso permite a conversão implícita de classes que implementam interfaces variantes e a conversão implícita de tipos delegados.  
  
 Para obter mais informações, consulte [Covariância e contravariância](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="rules"></a>Regras  
 Você pode usar a palavra-chave `Out` em delegados e interfaces genéricas.  
  
 Em uma interface genérica, um parâmetro de tipo pode ser declarado covariante se ele satisfizer as condições a seguir:  
  
-   O parâmetro de tipo é usado apenas como um tipo de retorno dos métodos de interface e não é usado como um tipo de argumentos de método.  
  
    > [!NOTE]
    >  Há uma exceção a essa regra. Se, em uma interface covariante, você tiver um delegado genérico contravariante como um parâmetro de método, você poderá usar o tipo covariante como um parâmetro de tipo genérico para o delegado. Para obter mais informações sobre delegados genéricos covariantes e contravariantes, consulte [Variância em delegados](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) e [Usando variância para delegados genéricos Func e Action](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
-   O parâmetro de tipo não é usado como uma restrição genérica para os métodos de interface.  
  
 Um delegado genérico, um parâmetro de tipo pode ser declarado covariante se ele for usado apenas como um tipo de retorno do método e não é usado para argumentos de método.  
  
 A covariância e a contravariância têm suporte para tipos de referência, mas não para tipos de valor.  
  
 No Visual Basic, você não pode declarar eventos em interfaces de covariantes sem especificar o tipo de delegado. Além disso, covariantes interfaces não podem ter aninhados, classes, enumerações ou estruturas, mas eles podem ter interfaces aninhados.  
  
## <a name="behavior"></a>Comportamento  
 Uma interface que tem um parâmetro de tipo covariante permite que seus métodos retornem tipos mais derivados do que aqueles especificados pelo parâmetro de tipo. Por exemplo, já que no .NET Framework 4, em <xref:System.Collections.Generic.IEnumerable%601>, o tipo T é covariante, você pode atribuir um objeto do tipo `IEnumerabe(Of String)` a um objeto do tipo `IEnumerable(Of Object)` sem usar nenhum método de conversão especial.  
  
 Pode ser atribuído a um delegado covariante outro delegado do mesmo tipo, mas com um parâmetro de tipo genérico mais derivado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como declarar, estender e implementar uma interface genérica covariante. Ele também mostra como usar a conversão implícita para classes que implementam uma interface covariante.  
  
 [!code-vb[vbVarianceKeywords#3](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como declarar, instanciar e invocar um delegado genérico covariante. Ele também mostra como você pode usar a conversão implícita para tipos de delegado.  
  
 [!code-vb[vbVarianceKeywords#4](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_2.vb)]  
  
## <a name="see-also"></a>Consulte também
- [Variação em Interfaces Genéricas](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
