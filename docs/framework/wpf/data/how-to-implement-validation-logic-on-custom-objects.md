---
title: Como implementar lógica de validação em objetos personalizados
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
ms.openlocfilehash: dbeddb5eb6996d5758717ddd2d4d5af0b6f57f3c
ms.sourcegitcommit: 78bcb629abdbdbde0e295b4e81f350a477864aba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/08/2018
ms.locfileid: "33555958"
---
# <a name="how-to-implement-validation-logic-on-custom-objects"></a><span data-ttu-id="f24a0-102">Como implementar lógica de validação em objetos personalizados</span><span class="sxs-lookup"><span data-stu-id="f24a0-102">How to: Implement Validation Logic on Custom Objects</span></span>
<span data-ttu-id="f24a0-103">Este exemplo mostra como implementar lógica de validação em um objeto personalizado e, em seguida, associar a ele.</span><span class="sxs-lookup"><span data-stu-id="f24a0-103">This example shows how to implement validation logic on a custom object and then bind to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f24a0-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f24a0-104">Example</span></span>  
 <span data-ttu-id="f24a0-105">Você pode fornecer lógica de validação na camada de negócios se seu objeto de origem implementa <xref:System.ComponentModel.IDataErrorInfo>, conforme mostrado no exemplo a seguir, que define uma `Person` objeto que implementa <xref:System.ComponentModel.IDataErrorInfo>:</span><span class="sxs-lookup"><span data-stu-id="f24a0-105">You can provide validation logic on the business layer if your source object implements <xref:System.ComponentModel.IDataErrorInfo>, as in the following example, which defines a `Person` object that implements <xref:System.ComponentModel.IDataErrorInfo>:</span></span>  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 <span data-ttu-id="f24a0-106">No exemplo a seguir, a propriedade text da caixa de texto se associa à `Person.Age` propriedade, que foi disponibilizada para associação por meio de uma declaração de recurso que é fornecida a `x:Key` `data`.</span><span class="sxs-lookup"><span data-stu-id="f24a0-106">In the following example, the text property of the text box binds to the `Person.Age` property, which has been made available for binding through a resource declaration that is given the `x:Key` `data`.</span></span> <span data-ttu-id="f24a0-107">O <xref:System.Windows.Controls.DataErrorValidationRule> verifica os erros de validação gerados pelo <xref:System.ComponentModel.IDataErrorInfo> implementação.</span><span class="sxs-lookup"><span data-stu-id="f24a0-107">The <xref:System.Windows.Controls.DataErrorValidationRule> checks for the validation errors raised by the <xref:System.ComponentModel.IDataErrorInfo> implementation.</span></span>  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml?highlight=8,11-19,25-42)]  
  
 <span data-ttu-id="f24a0-108">Como alternativa, em vez de usar o <xref:System.Windows.Controls.DataErrorValidationRule>, você pode definir o <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="f24a0-108">Alternatively, instead of using the <xref:System.Windows.Controls.DataErrorValidationRule>, you can set the <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f24a0-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f24a0-109">See Also</span></span>  
 <xref:System.Windows.Controls.ExceptionValidationRule>  
 [<span data-ttu-id="f24a0-110">Implementar a validação de associação</span><span class="sxs-lookup"><span data-stu-id="f24a0-110">Implement Binding Validation</span></span>](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [<span data-ttu-id="f24a0-111">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="f24a0-111">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
