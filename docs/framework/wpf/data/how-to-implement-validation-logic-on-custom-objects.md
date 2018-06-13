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
# <a name="how-to-implement-validation-logic-on-custom-objects"></a><span data-ttu-id="f625a-102">Como implementar lógica de validação em objetos personalizados</span><span class="sxs-lookup"><span data-stu-id="f625a-102">How to: Implement Validation Logic on Custom Objects</span></span>
<span data-ttu-id="f625a-103">Este exemplo mostra como implementar a lógica de validação em um objeto personalizado e, em seguida, associar a ele.</span><span class="sxs-lookup"><span data-stu-id="f625a-103">This example shows how to implement validation logic on a custom object and then bind to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f625a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f625a-104">Example</span></span>  
 <span data-ttu-id="f625a-105">Você pode fornecer lógica de validação na camada de negócios se seu objeto de origem implementa <xref:System.ComponentModel.IDataErrorInfo>, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f625a-105">You can provide validation logic on the business layer if your source object implements <xref:System.ComponentModel.IDataErrorInfo>, as in the following example:</span></span>  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 <span data-ttu-id="f625a-106">No exemplo a seguir, a propriedade de texto da caixa de texto associa ao `Age` propriedade o `Person` objeto, que foi disponibilizado para associação por meio de uma declaração de recurso que é fornecida o `x:Key``data`.</span><span class="sxs-lookup"><span data-stu-id="f625a-106">In the following example, the text property of the text box binds to the `Age` property of the `Person` object, which has been made available for binding through a resource declaration that is given the `x:Key``data`.</span></span> <span data-ttu-id="f625a-107">O <xref:System.Windows.Controls.DataErrorValidationRule> verifica os erros de validação gerados pelo <xref:System.ComponentModel.IDataErrorInfo> implementação.</span><span class="sxs-lookup"><span data-stu-id="f625a-107">The <xref:System.Windows.Controls.DataErrorValidationRule> checks for the validation errors raised by the <xref:System.ComponentModel.IDataErrorInfo> implementation.</span></span>  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml#boundtextbox)]  
  
 <span data-ttu-id="f625a-108">Como alternativa, em vez de usar o <xref:System.Windows.Controls.DataErrorValidationRule>, você pode definir o <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="f625a-108">Alternatively, instead of using the <xref:System.Windows.Controls.DataErrorValidationRule>, you can set the <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f625a-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f625a-109">See Also</span></span>  
 <xref:System.Windows.Controls.ExceptionValidationRule>  
 [<span data-ttu-id="f625a-110">Implementar a validação de associação</span><span class="sxs-lookup"><span data-stu-id="f625a-110">Implement Binding Validation</span></span>](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [<span data-ttu-id="f625a-111">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="f625a-111">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
