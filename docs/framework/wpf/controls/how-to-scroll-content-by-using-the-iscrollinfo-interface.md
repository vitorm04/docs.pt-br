---
title: "Como rolar conteúdo usando a interface IScrollInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], scrolling content
- scrolling content [WPF]
- IScrollInfo interface [WPF]
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae6d9439ad76258105d615960bd05ecf458eb613
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a><span data-ttu-id="afe7a-102">Como rolar conteúdo usando a interface IScrollInfo</span><span class="sxs-lookup"><span data-stu-id="afe7a-102">How to: Scroll Content by Using the IScrollInfo Interface</span></span>
<span data-ttu-id="afe7a-103">Este exemplo mostra como rolar conteúdo usando o <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span><span class="sxs-lookup"><span data-stu-id="afe7a-103">This example shows how to scroll content by using the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afe7a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="afe7a-104">Example</span></span>  
 <span data-ttu-id="afe7a-105">O exemplo a seguir demonstra os recursos do <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span><span class="sxs-lookup"><span data-stu-id="afe7a-105">The following example demonstrates the features of the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span></span> <span data-ttu-id="afe7a-106">O exemplo cria um <xref:System.Windows.Controls.StackPanel> elemento [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] que é aninhado em um pai <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="afe7a-106">The example creates a <xref:System.Windows.Controls.StackPanel> element in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that is nested in a parent <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="afe7a-107">Os elementos filho do <xref:System.Windows.Controls.StackPanel> podem ser rolados logicamente usando os métodos definidos pelo <xref:System.Windows.Controls.Primitives.IScrollInfo> interface e a conversão para a instância do <xref:System.Windows.Controls.StackPanel> (`sp1`) no código.</span><span class="sxs-lookup"><span data-stu-id="afe7a-107">The child elements of the <xref:System.Windows.Controls.StackPanel> can be scrolled logically by using the methods defined by the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface and cast to the instance of <xref:System.Windows.Controls.StackPanel> (`sp1`) in code.</span></span>  
  
 [!code-xaml[IScrollInfoMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="afe7a-108">Cada <xref:System.Windows.Controls.Button> no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo aciona um método personalizado associado que controla o comportamento de rolagem no <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="afe7a-108">Each <xref:System.Windows.Controls.Button> in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file triggers an associated custom method that controls scrolling behavior in <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="afe7a-109">O exemplo a seguir mostra como usar o <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> e <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> métodos; também genericamente mostra como usar todos os métodos de posicionamento que a <xref:System.Windows.Controls.Primitives.IScrollInfo> classe define.</span><span class="sxs-lookup"><span data-stu-id="afe7a-109">The following example shows how to use the <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> and <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> methods; it also generically shows how to use all the positioning methods that the <xref:System.Windows.Controls.Primitives.IScrollInfo> class defines.</span></span>  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="afe7a-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="afe7a-110">See Also</span></span>  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>  
 <xref:System.Windows.Controls.StackPanel>  
 [<span data-ttu-id="afe7a-111">Visão geral de ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="afe7a-111">ScrollViewer Overview</span></span>](../../../../docs/framework/wpf/controls/scrollviewer-overview.md)  
 [<span data-ttu-id="afe7a-112">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="afe7a-112">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/scrollviewer-how-to-topics.md)  
 [<span data-ttu-id="afe7a-113">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="afe7a-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
