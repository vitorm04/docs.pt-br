---
title: 'Como: Obter o objeto de associação de uma propriedade de destino associada'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: c7aacc2145ffe98ec7b58afb3b2e3dca151ef0ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965431"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a><span data-ttu-id="22430-102">Como: Obter o objeto de associação de uma propriedade de destino associada</span><span class="sxs-lookup"><span data-stu-id="22430-102">How to: Get the Binding Object from a Bound Target Property</span></span>
<span data-ttu-id="22430-103">Este exemplo mostra como obter o objeto de associação de uma propriedade de destino associada a dados.</span><span class="sxs-lookup"><span data-stu-id="22430-103">This example shows how to obtain the binding object from a data-bound target property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22430-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="22430-104">Example</span></span>  
 <span data-ttu-id="22430-105">Você pode fazer o seguinte para obter o <xref:System.Windows.Data.Binding> objeto:</span><span class="sxs-lookup"><span data-stu-id="22430-105">You can do the following to get the <xref:System.Windows.Data.Binding> object:</span></span>  
  
 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
> <span data-ttu-id="22430-106">Você deve especificar a propriedade de dependência para a associação desejada porque é possível que mais de uma propriedade do objeto de destino esteja usando a associação de dados.</span><span class="sxs-lookup"><span data-stu-id="22430-106">You must specify the dependency property for the binding you want because it is possible that more than one property of the target object is using data binding.</span></span>  
  
 <span data-ttu-id="22430-107">Como alternativa, você pode obter o <xref:System.Windows.Data.BindingExpression> e obter o valor <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> da propriedade.</span><span class="sxs-lookup"><span data-stu-id="22430-107">Alternatively, you can get the <xref:System.Windows.Data.BindingExpression> and then get the value of the <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> property.</span></span>  
  
 <span data-ttu-id="22430-108">Para obter o exemplo completo, consulte [exemplo de validação de associação](https://go.microsoft.com/fwlink/?LinkID=159972).</span><span class="sxs-lookup"><span data-stu-id="22430-108">For the complete example see [Binding Validation Sample](https://go.microsoft.com/fwlink/?LinkID=159972).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22430-109">Se sua associação for a <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="22430-109">If your binding is a <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.</span></span> <span data-ttu-id="22430-110">Se for um <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="22430-110">If it is a <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>.</span></span> <span data-ttu-id="22430-111">Se você não tiver certeza se a propriedade de destino está associada <xref:System.Windows.Data.Binding>usando um <xref:System.Windows.Data.MultiBinding>, um ou <xref:System.Windows.Data.PriorityBinding>um, você pode <xref:System.Windows.Data.BindingOperations>usar<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>..</span><span class="sxs-lookup"><span data-stu-id="22430-111">If you are uncertain whether the target property is bound using a <xref:System.Windows.Data.Binding>, a <xref:System.Windows.Data.MultiBinding>, or a <xref:System.Windows.Data.PriorityBinding>, you can use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22430-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22430-112">See also</span></span>

- [<span data-ttu-id="22430-113">Criar uma associação no código</span><span class="sxs-lookup"><span data-stu-id="22430-113">Create a Binding in Code</span></span>](how-to-create-a-binding-in-code.md)
- [<span data-ttu-id="22430-114">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="22430-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
