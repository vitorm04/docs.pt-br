---
title: Como obter o objeto de associação de uma propriedade de destino associada
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: c528515124898c7deb6114e620ce21766123ab3c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453046"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a><span data-ttu-id="362dc-102">Como obter o objeto de associação de uma propriedade de destino associada</span><span class="sxs-lookup"><span data-stu-id="362dc-102">How to: Get the Binding Object from a Bound Target Property</span></span>
<span data-ttu-id="362dc-103">Este exemplo mostra como obter o objeto de associação de uma propriedade de destino associada a dados.</span><span class="sxs-lookup"><span data-stu-id="362dc-103">This example shows how to obtain the binding object from a data-bound target property.</span></span>

## <a name="example"></a><span data-ttu-id="362dc-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="362dc-104">Example</span></span>
 <span data-ttu-id="362dc-105">Você pode fazer o seguinte para obter o objeto <xref:System.Windows.Data.Binding>:</span><span class="sxs-lookup"><span data-stu-id="362dc-105">You can do the following to get the <xref:System.Windows.Data.Binding> object:</span></span>

 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]

> [!NOTE]
> <span data-ttu-id="362dc-106">Você deve especificar a propriedade de dependência para a associação desejada porque é possível que mais de uma propriedade do objeto de destino esteja usando a associação de dados.</span><span class="sxs-lookup"><span data-stu-id="362dc-106">You must specify the dependency property for the binding you want because it is possible that more than one property of the target object is using data binding.</span></span>

 <span data-ttu-id="362dc-107">Como alternativa, você pode obter a <xref:System.Windows.Data.BindingExpression> e obter o valor da propriedade <xref:System.Windows.Data.BindingExpression.ParentBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="362dc-107">Alternatively, you can get the <xref:System.Windows.Data.BindingExpression> and then get the value of the <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> property.</span></span>

 <span data-ttu-id="362dc-108">Para obter o exemplo completo, consulte [exemplo de validação de associação](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).</span><span class="sxs-lookup"><span data-stu-id="362dc-108">For the complete example see [Binding Validation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).</span></span>

> [!NOTE]
> <span data-ttu-id="362dc-109">Se sua associação for uma <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="362dc-109">If your binding is a <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="362dc-110">Se for um <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="362dc-110">If it is a <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="362dc-111">Se você não tiver certeza se a propriedade de destino está associada usando uma <xref:System.Windows.Data.Binding>, uma <xref:System.Windows.Data.MultiBinding>ou uma <xref:System.Windows.Data.PriorityBinding>, você pode usar <xref:System.Windows.Data.BindingOperations.GetBindingBase%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="362dc-111">If you are uncertain whether the target property is bound using a <xref:System.Windows.Data.Binding>, a <xref:System.Windows.Data.MultiBinding>, or a <xref:System.Windows.Data.PriorityBinding>, you can use <xref:System.Windows.Data.BindingOperations.GetBindingBase%2A?displayProperty=nameWithType>.</span></span>

## <a name="see-also"></a><span data-ttu-id="362dc-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="362dc-112">See also</span></span>

- [<span data-ttu-id="362dc-113">Criar uma associação no código</span><span class="sxs-lookup"><span data-stu-id="362dc-113">Create a Binding in Code</span></span>](how-to-create-a-binding-in-code.md)
- [<span data-ttu-id="362dc-114">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="362dc-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
