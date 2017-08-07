---
title: "out (modificador genérico) (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 40d2c13ad4218952b143e6403851a1027bd7c161
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="out-generic-modifier-c-reference"></a>out (modificador genérico) (Referência de C#)
Para parâmetros de tipo genérico, a palavra-chave `out` especifica que o parâmetro de tipo é covariante. Você pode usar a palavra-chave `out` em delegados e interfaces genéricas.  
  
 A covariância permite que você use um tipo mais derivado do que aquele especificado pelo parâmetro genérico. Isso permite a conversão implícita de classes que implementam interfaces variantes e a conversão implícita de tipos delegados. A covariância e a contravariância têm suporte para tipos de referência, mas não para tipos de valor.  
  
 Uma interface que tem um parâmetro de tipo covariante permite que seus métodos retornem tipos mais derivados do que aqueles especificados pelo parâmetro de tipo. Por exemplo, já que no .NET Framework 4, em <xref:System.Collections.Generic.IEnumerable%601>, o tipo T é covariante, você pode atribuir um objeto do tipo `IEnumerabe(Of String)` a um objeto do tipo `IEnumerable(Of Object)` sem usar nenhum método de conversão especial.  
  
 Pode ser atribuído a um delegado covariante outro delegado do mesmo tipo, mas com um parâmetro de tipo genérico mais derivado.  
  
 Para obter mais informações, consulte [Covariância e contravariância](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como declarar, estender e implementar uma interface genérica covariante. Ele também mostra como usar a conversão implícita para classes que implementam uma interface covariante.  
  
 [!code-cs[csVarianceKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_1.cs)]  
  
 Em uma interface genérica, um parâmetro de tipo pode ser declarado covariante se ele satisfizer as condições a seguir:  
  
-   O parâmetro de tipo é usado apenas como um tipo de retorno dos métodos de interface e não é usado como um tipo de argumentos de método.  
  
    > [!NOTE]
    >  Há uma exceção a essa regra. Se, em uma interface covariante, você tiver um delegado genérico contravariante como um parâmetro de método, você poderá usar o tipo covariante como um parâmetro de tipo genérico para o delegado. Para obter mais informações sobre delegados genéricos covariantes e contravariantes, consulte [Variância em delegados](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca) e [Usando variância para delegados genéricos Func e Action](http://msdn.microsoft.com/library/e69c4f39-09aa-4c6d-a752-08cc767d8290).  
  
-   O parâmetro de tipo não é usado como uma restrição genérica para os métodos de interface.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como declarar, instanciar e invocar um delegado genérico covariante. Ele também mostra como converter implicitamente os tipos delegados.  
  
 [!code-cs[csVarianceKeywords#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_2.cs)]  
  
 Um delegado genérico, um tipo pode ser declarado covariante se for usado apenas como um tipo de retorno do método e não usado para argumentos de método.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Variação em interfaces genéricas](http://msdn.microsoft.com/library/e14322da-1db3-42f2-9a67-397daddd6b6a)   
 [in](../../../csharp/language-reference/keywords/in-generic-modifier.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)

