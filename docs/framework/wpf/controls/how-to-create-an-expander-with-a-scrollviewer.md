---
title: 'Como: Criar um expansor com um ScrollViewer'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
ms.openlocfilehash: 8d21c7ec0172dca23f218a0d710c3976872f162c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681957"
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a><span data-ttu-id="158b6-102">Como: Criar um expansor com um ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="158b6-102">How to: Create an Expander with a ScrollViewer</span></span>
<span data-ttu-id="158b6-103">Este exemplo mostra como criar um <xref:System.Windows.Controls.Expander> controle que contém conteúdo complexo, como uma imagem e texto.</span><span class="sxs-lookup"><span data-stu-id="158b6-103">This example shows how to create an <xref:System.Windows.Controls.Expander> control that contains complex content, such as an image and text.</span></span> <span data-ttu-id="158b6-104">O exemplo também inclui o conteúdo a <xref:System.Windows.Controls.Expander> em um <xref:System.Windows.Controls.ScrollViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="158b6-104">The example also encloses the content of the <xref:System.Windows.Controls.Expander> in a <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="158b6-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="158b6-105">Example</span></span>  
 <span data-ttu-id="158b6-106">O exemplo a seguir mostra como criar um <xref:System.Windows.Controls.Expander>.</span><span class="sxs-lookup"><span data-stu-id="158b6-106">The following example shows how to create an <xref:System.Windows.Controls.Expander>.</span></span> <span data-ttu-id="158b6-107">O exemplo usa uma <xref:System.Windows.Controls.Primitives.BulletDecorator> controle, que contém uma imagem e texto, para definir o <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span><span class="sxs-lookup"><span data-stu-id="158b6-107">The example uses a <xref:System.Windows.Controls.Primitives.BulletDecorator> control, which contains an image and text, in order to define the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span></span> <span data-ttu-id="158b6-108">Um <xref:System.Windows.Controls.ScrollViewer> controle fornece um método para rolar o conteúdo expandido.</span><span class="sxs-lookup"><span data-stu-id="158b6-108">A <xref:System.Windows.Controls.ScrollViewer> control provides a method for scrolling the expanded content.</span></span>  
  
 <span data-ttu-id="158b6-109">Observe que o exemplo define o <xref:System.Windows.FrameworkElement.Height%2A> propriedade no <xref:System.Windows.Controls.ScrollViewer> em vez de no conteúdo.</span><span class="sxs-lookup"><span data-stu-id="158b6-109">Note that the example sets the <xref:System.Windows.FrameworkElement.Height%2A> property on the <xref:System.Windows.Controls.ScrollViewer> instead of on the content.</span></span> <span data-ttu-id="158b6-110">Se o <xref:System.Windows.FrameworkElement.Height%2A> é definido no conteúdo, o <xref:System.Windows.Controls.ScrollViewer> não permite que o usuário rolar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="158b6-110">If the <xref:System.Windows.FrameworkElement.Height%2A> is set on the content, the <xref:System.Windows.Controls.ScrollViewer> does not allow the user to scroll the content.</span></span> <span data-ttu-id="158b6-111">O <xref:System.Windows.FrameworkElement.Width%2A> propriedade está definida a <xref:System.Windows.Controls.Expander> controle e essa configuração aplica-se ao <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> e o conteúdo expandido.</span><span class="sxs-lookup"><span data-stu-id="158b6-111">The <xref:System.Windows.FrameworkElement.Width%2A> property is set on the <xref:System.Windows.Controls.Expander> control and this setting applies to the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the expanded content.</span></span>  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a><span data-ttu-id="158b6-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="158b6-112">See also</span></span>
- <xref:System.Windows.Controls.Expander>
- [<span data-ttu-id="158b6-113">Visão geral de Expander</span><span class="sxs-lookup"><span data-stu-id="158b6-113">Expander Overview</span></span>](../../../../docs/framework/wpf/controls/expander-overview.md)
- [<span data-ttu-id="158b6-114">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="158b6-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
