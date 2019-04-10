---
title: 'Como: Associar um adorno a um elemento'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: b6909fec466c2b31a7f4156c43b21a0c724f0217
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307282"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a><span data-ttu-id="36d03-102">Como: Associar um adorno a um elemento</span><span class="sxs-lookup"><span data-stu-id="36d03-102">How to: Bind an Adorner to an Element</span></span>
<span data-ttu-id="36d03-103">Este exemplo mostra como programaticamente associar um adorno a um especificado <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="36d03-103">This example shows how to programmatically bind an adorner to a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36d03-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="36d03-104">Example</span></span>  
 <span data-ttu-id="36d03-105">Para associar um adorno a um determinado <xref:System.Windows.UIElement>, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="36d03-105">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1. <span data-ttu-id="36d03-106">Chame o `static` método <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> para obter uma <xref:System.Windows.Documents.AdornerLayer> do objeto para o <xref:System.Windows.UIElement> a ser adornado.</span><span class="sxs-lookup"><span data-stu-id="36d03-106">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> <span data-ttu-id="36d03-107">percorre a árvore visual, iniciando no local especificado **UIElement**e retorna a primeira camada de adorno que encontra.</span><span class="sxs-lookup"><span data-stu-id="36d03-107">walks up the visual tree, starting at the specified **UIElement**, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="36d03-108">(Se nenhuma camada de adorno for encontrada, o método retornará nulo.)</span><span class="sxs-lookup"><span data-stu-id="36d03-108">(If no adorner layers are found, the method returns null.)</span></span>  
  
2. <span data-ttu-id="36d03-109">Chame o <xref:System.Windows.Documents.AdornerLayer.Add%2A> método para associar o adorno ao destino **UIElement**.</span><span class="sxs-lookup"><span data-stu-id="36d03-109">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target **UIElement**.</span></span>  
  
 <span data-ttu-id="36d03-110">O exemplo a seguir associa um SimpleCircleAdorner (mostrado acima) para um <xref:System.Windows.Controls.TextBox> nomeado *myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="36d03-110">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  <span data-ttu-id="36d03-111">No momento, não há suporte para usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para associar um adorno a outro elemento.</span><span class="sxs-lookup"><span data-stu-id="36d03-111">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36d03-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36d03-112">See also</span></span>

- [<span data-ttu-id="36d03-113">Visão geral de adornos</span><span class="sxs-lookup"><span data-stu-id="36d03-113">Adorners Overview</span></span>](adorners-overview.md)
