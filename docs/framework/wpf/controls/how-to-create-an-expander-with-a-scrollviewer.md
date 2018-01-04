---
title: Como criar um expansor com um ScrollViewer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2066ccce28138cfecf4e0b4574d45783a9ba4ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a><span data-ttu-id="cc38d-102">Como criar um expansor com um ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="cc38d-102">How to: Create an Expander with a ScrollViewer</span></span>
<span data-ttu-id="cc38d-103">Este exemplo mostra como criar um <xref:System.Windows.Controls.Expander> controle que contém conteúdo complexo, como uma imagem e texto.</span><span class="sxs-lookup"><span data-stu-id="cc38d-103">This example shows how to create an <xref:System.Windows.Controls.Expander> control that contains complex content, such as an image and text.</span></span> <span data-ttu-id="cc38d-104">O exemplo também inclui o conteúdo do <xref:System.Windows.Controls.Expander> em um <xref:System.Windows.Controls.ScrollViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="cc38d-104">The example also encloses the content of the <xref:System.Windows.Controls.Expander> in a <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc38d-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cc38d-105">Example</span></span>  
 <span data-ttu-id="cc38d-106">O exemplo a seguir mostra como criar um <xref:System.Windows.Controls.Expander>.</span><span class="sxs-lookup"><span data-stu-id="cc38d-106">The following example shows how to create an <xref:System.Windows.Controls.Expander>.</span></span> <span data-ttu-id="cc38d-107">O exemplo usa um <xref:System.Windows.Controls.Primitives.BulletDecorator> controle, que contém uma imagem e texto, para definir o <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span><span class="sxs-lookup"><span data-stu-id="cc38d-107">The example uses a <xref:System.Windows.Controls.Primitives.BulletDecorator> control, which contains an image and text, in order to define the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span></span> <span data-ttu-id="cc38d-108">Um <xref:System.Windows.Controls.ScrollViewer> controle fornece um método para rolar o conteúdo expandido.</span><span class="sxs-lookup"><span data-stu-id="cc38d-108">A <xref:System.Windows.Controls.ScrollViewer> control provides a method for scrolling the expanded content.</span></span>  
  
 <span data-ttu-id="cc38d-109">Observe que o exemplo define o <xref:System.Windows.FrameworkElement.Height%2A> propriedade o <xref:System.Windows.Controls.ScrollViewer> em vez de no conteúdo.</span><span class="sxs-lookup"><span data-stu-id="cc38d-109">Note that the example sets the <xref:System.Windows.FrameworkElement.Height%2A> property on the <xref:System.Windows.Controls.ScrollViewer> instead of on the content.</span></span> <span data-ttu-id="cc38d-110">Se o <xref:System.Windows.FrameworkElement.Height%2A> é definido no conteúdo, o <xref:System.Windows.Controls.ScrollViewer> não permite que o usuário role o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="cc38d-110">If the <xref:System.Windows.FrameworkElement.Height%2A> is set on the content, the <xref:System.Windows.Controls.ScrollViewer> does not allow the user to scroll the content.</span></span> <span data-ttu-id="cc38d-111">O <xref:System.Windows.FrameworkElement.Width%2A> propriedade é definida no <xref:System.Windows.Controls.Expander> controle e essa configuração aplica-se ao <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> e o conteúdo expandido.</span><span class="sxs-lookup"><span data-stu-id="cc38d-111">The <xref:System.Windows.FrameworkElement.Width%2A> property is set on the <xref:System.Windows.Controls.Expander> control and this setting applies to the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the expanded content.</span></span>  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a><span data-ttu-id="cc38d-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc38d-112">See Also</span></span>  
 <xref:System.Windows.Controls.Expander>  
 [<span data-ttu-id="cc38d-113">Visão geral de Expander</span><span class="sxs-lookup"><span data-stu-id="cc38d-113">Expander Overview</span></span>](../../../../docs/framework/wpf/controls/expander-overview.md)  
 [<span data-ttu-id="cc38d-114">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="cc38d-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
