---
title: 'Como: Implementar a lógica de validação em objetos personalizados'
ms.date: 08/02/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- checking for validation errors [WPF]
- validation errors [WPF], checking for
- implementing validation logic on custom objects [WPF]
- custom objects [WPF], implementing validation logic on
ms.assetid: 751fda9b-44f9-4d63-b4f2-1df07ac41e0f
ms.openlocfilehash: 8520504757e9e9ec9557b84ca2608b4cb99daf62
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085916"
---
# <a name="how-to-implement-validation-logic-on-custom-objects"></a>Como: Implementar a lógica de validação em objetos personalizados
Este exemplo mostra como implementar lógica de validação em um objeto personalizado e, em seguida, associar a ele.  
  
## <a name="example"></a>Exemplo  
 Você pode fornecer lógica de validação na camada de negócios se seu objeto de origem implementa <xref:System.ComponentModel.IDataErrorInfo>, conforme mostrado no exemplo a seguir, que define uma `Person` objeto que implementa <xref:System.ComponentModel.IDataErrorInfo>:  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](~/samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 No exemplo a seguir, a propriedade text da caixa de texto se associa à `Person.Age` propriedade, que foi disponibilizada para associação por meio de uma declaração de recurso que é fornecida a `x:Key` `data`. O <xref:System.Windows.Controls.DataErrorValidationRule> verifica os erros de validação gerados pelo <xref:System.ComponentModel.IDataErrorInfo> implementação.  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml?highlight=8,11-19,25-42)]  
  
 Como alternativa, em vez de usar o <xref:System.Windows.Controls.DataErrorValidationRule>, você pode definir o <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> propriedade `true`.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.ExceptionValidationRule>
- [Implementar a validação de associação](how-to-implement-binding-validation.md)
- [Tópicos explicativos ](data-binding-how-to-topics.md)
