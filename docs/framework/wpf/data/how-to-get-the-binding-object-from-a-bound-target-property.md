---
title: Como obter o objeto de associação de uma propriedade de destino associada
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: 7cebaf1077fb66420d77d656db32f444dd932b85
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210861"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a><span data-ttu-id="cf0ec-102">Como obter o objeto de associação de uma propriedade de destino associada</span><span class="sxs-lookup"><span data-stu-id="cf0ec-102">How to: Get the Binding Object from a Bound Target Property</span></span>
<span data-ttu-id="cf0ec-103">Este exemplo mostra como obter o objeto de associação de uma propriedade de destino de associação de dados.</span><span class="sxs-lookup"><span data-stu-id="cf0ec-103">This example shows how to obtain the binding object from a data-bound target property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf0ec-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cf0ec-104">Example</span></span>  
 <span data-ttu-id="cf0ec-105">Você pode fazer o seguinte para obter o <xref:System.Windows.Data.Binding> objeto:</span><span class="sxs-lookup"><span data-stu-id="cf0ec-105">You can do the following to get the <xref:System.Windows.Data.Binding> object:</span></span>  
  
 [!code-csharp[BindValidation#GetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
>  <span data-ttu-id="cf0ec-106">Você deve especificar a propriedade de dependência para a associação que desejar, pois é possível que mais de uma propriedade do objeto de destino está usando a associação de dados.</span><span class="sxs-lookup"><span data-stu-id="cf0ec-106">You must specify the dependency property for the binding you want because it is possible that more than one property of the target object is using data binding.</span></span>  
  
 <span data-ttu-id="cf0ec-107">Como alternativa, você pode obter o <xref:System.Windows.Data.BindingExpression> e, em seguida, obter o valor da <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="cf0ec-107">Alternatively, you can get the <xref:System.Windows.Data.BindingExpression> and then get the value of the <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> property.</span></span>  
  
 <span data-ttu-id="cf0ec-108">Para um exemplo completo, consulte [exemplo de validação de associação](https://go.microsoft.com/fwlink/?LinkID=159972).</span><span class="sxs-lookup"><span data-stu-id="cf0ec-108">For the complete example see [Binding Validation Sample](https://go.microsoft.com/fwlink/?LinkID=159972).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf0ec-109">Se a associação for um <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="cf0ec-109">If your binding is a <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.</span></span> <span data-ttu-id="cf0ec-110">Se for um <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="cf0ec-110">If it is a <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>.</span></span> <span data-ttu-id="cf0ec-111">Se você não tiver certeza se a propriedade de destino está associada usando um <xref:System.Windows.Data.Binding>, um <xref:System.Windows.Data.MultiBinding>, ou uma <xref:System.Windows.Data.PriorityBinding>, você pode usar <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="cf0ec-111">If you are uncertain whether the target property is bound using a <xref:System.Windows.Data.Binding>, a <xref:System.Windows.Data.MultiBinding>, or a <xref:System.Windows.Data.PriorityBinding>, you can use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf0ec-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf0ec-112">See Also</span></span>  
 [<span data-ttu-id="cf0ec-113">Criar uma associação no código</span><span class="sxs-lookup"><span data-stu-id="cf0ec-113">Create a Binding in Code</span></span>](../../../../docs/framework/wpf/data/how-to-create-a-binding-in-code.md)  
 [<span data-ttu-id="cf0ec-114">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="cf0ec-114">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
