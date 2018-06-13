---
title: Como criar um expansor com um ScrollViewer
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
ms.openlocfilehash: 6c014d4f6a12bfb58c2ae68f580f632c9478c82f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553056"
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a><span data-ttu-id="02260-102">Como criar um expansor com um ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="02260-102">How to: Create an Expander with a ScrollViewer</span></span>
<span data-ttu-id="02260-103">Este exemplo mostra como criar um <xref:System.Windows.Controls.Expander> controle que contém conteúdo complexo, como uma imagem e texto.</span><span class="sxs-lookup"><span data-stu-id="02260-103">This example shows how to create an <xref:System.Windows.Controls.Expander> control that contains complex content, such as an image and text.</span></span> <span data-ttu-id="02260-104">O exemplo também inclui o conteúdo do <xref:System.Windows.Controls.Expander> em um <xref:System.Windows.Controls.ScrollViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="02260-104">The example also encloses the content of the <xref:System.Windows.Controls.Expander> in a <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02260-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="02260-105">Example</span></span>  
 <span data-ttu-id="02260-106">O exemplo a seguir mostra como criar um <xref:System.Windows.Controls.Expander>.</span><span class="sxs-lookup"><span data-stu-id="02260-106">The following example shows how to create an <xref:System.Windows.Controls.Expander>.</span></span> <span data-ttu-id="02260-107">O exemplo usa um <xref:System.Windows.Controls.Primitives.BulletDecorator> controle, que contém uma imagem e texto, para definir o <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span><span class="sxs-lookup"><span data-stu-id="02260-107">The example uses a <xref:System.Windows.Controls.Primitives.BulletDecorator> control, which contains an image and text, in order to define the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span></span> <span data-ttu-id="02260-108">Um <xref:System.Windows.Controls.ScrollViewer> controle fornece um método para rolar o conteúdo expandido.</span><span class="sxs-lookup"><span data-stu-id="02260-108">A <xref:System.Windows.Controls.ScrollViewer> control provides a method for scrolling the expanded content.</span></span>  
  
 <span data-ttu-id="02260-109">Observe que o exemplo define o <xref:System.Windows.FrameworkElement.Height%2A> propriedade o <xref:System.Windows.Controls.ScrollViewer> em vez de no conteúdo.</span><span class="sxs-lookup"><span data-stu-id="02260-109">Note that the example sets the <xref:System.Windows.FrameworkElement.Height%2A> property on the <xref:System.Windows.Controls.ScrollViewer> instead of on the content.</span></span> <span data-ttu-id="02260-110">Se o <xref:System.Windows.FrameworkElement.Height%2A> é definido no conteúdo, o <xref:System.Windows.Controls.ScrollViewer> não permite que o usuário role o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="02260-110">If the <xref:System.Windows.FrameworkElement.Height%2A> is set on the content, the <xref:System.Windows.Controls.ScrollViewer> does not allow the user to scroll the content.</span></span> <span data-ttu-id="02260-111">O <xref:System.Windows.FrameworkElement.Width%2A> propriedade é definida no <xref:System.Windows.Controls.Expander> controle e essa configuração aplica-se ao <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> e o conteúdo expandido.</span><span class="sxs-lookup"><span data-stu-id="02260-111">The <xref:System.Windows.FrameworkElement.Width%2A> property is set on the <xref:System.Windows.Controls.Expander> control and this setting applies to the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the expanded content.</span></span>  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a><span data-ttu-id="02260-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02260-112">See Also</span></span>  
 <xref:System.Windows.Controls.Expander>  
 [<span data-ttu-id="02260-113">Visão geral de Expander</span><span class="sxs-lookup"><span data-stu-id="02260-113">Expander Overview</span></span>](../../../../docs/framework/wpf/controls/expander-overview.md)  
 [<span data-ttu-id="02260-114">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="02260-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
