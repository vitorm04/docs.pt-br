---
title: Como implementar lógica de validação em objetos personalizados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- checking for validation errors [WPF]
- validation errors [WPF], checking for
- implementing validation logic on custom objects [WPF]
- custom objects [WPF], implementing validation logic on
ms.assetid: 751fda9b-44f9-4d63-b4f2-1df07ac41e0f
ms.openlocfilehash: dbeddb5eb6996d5758717ddd2d4d5af0b6f57f3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555958"
---
# <a name="how-to-implement-validation-logic-on-custom-objects"></a>Como implementar lógica de validação em objetos personalizados
Este exemplo mostra como implementar a lógica de validação em um objeto personalizado e, em seguida, associar a ele.  
  
## <a name="example"></a>Exemplo  
 Você pode fornecer lógica de validação na camada de negócios se seu objeto de origem implementa <xref:System.ComponentModel.IDataErrorInfo>, conforme mostrado no exemplo a seguir:  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 No exemplo a seguir, a propriedade de texto da caixa de texto associa ao `Age` propriedade o `Person` objeto, que foi disponibilizado para associação por meio de uma declaração de recurso que é fornecida o `x:Key``data`. O <xref:System.Windows.Controls.DataErrorValidationRule> verifica os erros de validação gerados pelo <xref:System.ComponentModel.IDataErrorInfo> implementação.  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml#boundtextbox)]  
  
 Como alternativa, em vez de usar o <xref:System.Windows.Controls.DataErrorValidationRule>, você pode definir o <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> propriedade `true`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.ExceptionValidationRule>  
 [Implementar a validação de associação](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
