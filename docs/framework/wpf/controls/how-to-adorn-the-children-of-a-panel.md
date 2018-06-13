---
title: Como adornar os filhos de um painel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
ms.openlocfilehash: 4babbf1df57f340a3f6be218f213ad1c868ec9f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550213"
---
# <a name="how-to-adorn-the-children-of-a-panel"></a><span data-ttu-id="feb8d-102">Como adornar os filhos de um painel</span><span class="sxs-lookup"><span data-stu-id="feb8d-102">How to: Adorn the Children of a Panel</span></span>
<span data-ttu-id="feb8d-103">Este exemplo mostra como programaticamente associar um adorno aos filhos de um <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="feb8d-103">This example shows how to programmatically bind an adorner to the children of a specified <xref:System.Windows.Controls.Panel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="feb8d-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="feb8d-104">Example</span></span>  
 <span data-ttu-id="feb8d-105">Para associar um adorno aos filhos de um <xref:System.Windows.Controls.Panel>, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="feb8d-105">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="feb8d-106">Declarar um novo <xref:System.Windows.Documents.AdornerLayer> objeto e a chamada a `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> método para encontrar uma camada de adorno para o elemento cujos filhos serão adornados.</span><span class="sxs-lookup"><span data-stu-id="feb8d-106">Declare a new <xref:System.Windows.Documents.AdornerLayer> object and call the `static`<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> method to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2.  <span data-ttu-id="feb8d-107">Enumerar todos os filhos do elemento pai e chamada de <xref:System.Windows.Documents.AdornerLayer.Add%2A> método para associar um adorno a cada elemento filho.</span><span class="sxs-lookup"><span data-stu-id="feb8d-107">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="feb8d-108">O exemplo a seguir associa um SimpleCircleAdorner (mostrado acima) aos filhos de um <xref:System.Windows.Controls.StackPanel> chamado *myStackPanel*.</span><span class="sxs-lookup"><span data-stu-id="feb8d-108">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  <span data-ttu-id="feb8d-109">No momento, não há suporte para usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para associar um adorno a outro elemento.</span><span class="sxs-lookup"><span data-stu-id="feb8d-109">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feb8d-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="feb8d-110">See Also</span></span>  
 [<span data-ttu-id="feb8d-111">Visão geral de adornos</span><span class="sxs-lookup"><span data-stu-id="feb8d-111">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
