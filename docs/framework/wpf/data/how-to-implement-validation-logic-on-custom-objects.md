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
# <a name="how-to-implement-validation-logic-on-custom-objects"></a><span data-ttu-id="88b45-102">Como: Implementar a lógica de validação em objetos personalizados</span><span class="sxs-lookup"><span data-stu-id="88b45-102">How to: Implement Validation Logic on Custom Objects</span></span>
<span data-ttu-id="88b45-103">Este exemplo mostra como implementar lógica de validação em um objeto personalizado e, em seguida, associar a ele.</span><span class="sxs-lookup"><span data-stu-id="88b45-103">This example shows how to implement validation logic on a custom object and then bind to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88b45-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="88b45-104">Example</span></span>  
 <span data-ttu-id="88b45-105">Você pode fornecer lógica de validação na camada de negócios se seu objeto de origem implementa <xref:System.ComponentModel.IDataErrorInfo>, conforme mostrado no exemplo a seguir, que define uma `Person` objeto que implementa <xref:System.ComponentModel.IDataErrorInfo>:</span><span class="sxs-lookup"><span data-stu-id="88b45-105">You can provide validation logic on the business layer if your source object implements <xref:System.ComponentModel.IDataErrorInfo>, as in the following example, which defines a `Person` object that implements <xref:System.ComponentModel.IDataErrorInfo>:</span></span>  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](~/samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 <span data-ttu-id="88b45-106">No exemplo a seguir, a propriedade text da caixa de texto se associa à `Person.Age` propriedade, que foi disponibilizada para associação por meio de uma declaração de recurso que é fornecida a `x:Key` `data`.</span><span class="sxs-lookup"><span data-stu-id="88b45-106">In the following example, the text property of the text box binds to the `Person.Age` property, which has been made available for binding through a resource declaration that is given the `x:Key` `data`.</span></span> <span data-ttu-id="88b45-107">O <xref:System.Windows.Controls.DataErrorValidationRule> verifica os erros de validação gerados pelo <xref:System.ComponentModel.IDataErrorInfo> implementação.</span><span class="sxs-lookup"><span data-stu-id="88b45-107">The <xref:System.Windows.Controls.DataErrorValidationRule> checks for the validation errors raised by the <xref:System.ComponentModel.IDataErrorInfo> implementation.</span></span>  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml?highlight=8,11-19,25-42)]  
  
 <span data-ttu-id="88b45-108">Como alternativa, em vez de usar o <xref:System.Windows.Controls.DataErrorValidationRule>, você pode definir o <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="88b45-108">Alternatively, instead of using the <xref:System.Windows.Controls.DataErrorValidationRule>, you can set the <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88b45-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88b45-109">See also</span></span>

- <xref:System.Windows.Controls.ExceptionValidationRule>
- [<span data-ttu-id="88b45-110">Implementar a validação de associação</span><span class="sxs-lookup"><span data-stu-id="88b45-110">Implement Binding Validation</span></span>](how-to-implement-binding-validation.md)
- [<span data-ttu-id="88b45-111">Tópicos explicativos </span><span class="sxs-lookup"><span data-stu-id="88b45-111">How-to Topics</span></span>](data-binding-how-to-topics.md)
