---
title: 'Como: Usar os métodos de rolagem de conteúdo do ScrollViewer'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IScrollInfo interface [WPF]
- scrolling methods [WPF]
- ScrollViewer control [WPF], scrolling methods
ms.assetid: 4708cc65-6510-45f8-82e6-30b0d3e30045
ms.openlocfilehash: e81c63de16d09de8435d5ec49a013bf8dc5927cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697298"
---
# <a name="how-to-use-the-content-scrolling-methods-of-scrollviewer"></a><span data-ttu-id="c57d3-102">Como: Usar os métodos de rolagem de conteúdo do ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="c57d3-102">How to: Use the Content-Scrolling Methods of ScrollViewer</span></span>
<span data-ttu-id="c57d3-103">Este exemplo mostra como usar os métodos de rolagem a <xref:System.Windows.Controls.ScrollViewer> elemento.</span><span class="sxs-lookup"><span data-stu-id="c57d3-103">This example shows how to use the scrolling methods of the <xref:System.Windows.Controls.ScrollViewer> element.</span></span> <span data-ttu-id="c57d3-104">Esses métodos fornecem rolagem incremental do conteúdo, por linha ou por página, em um <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="c57d3-104">These methods provide incremental scrolling of content, either by line or by page, in a <xref:System.Windows.Controls.ScrollViewer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c57d3-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c57d3-105">Example</span></span>  
 <span data-ttu-id="c57d3-106">O exemplo a seguir cria uma <xref:System.Windows.Controls.ScrollViewer> nomeado `sv1`, que hospeda um filho <xref:System.Windows.Controls.TextBlock> elemento.</span><span class="sxs-lookup"><span data-stu-id="c57d3-106">The following example creates a <xref:System.Windows.Controls.ScrollViewer> named `sv1`, which hosts a child <xref:System.Windows.Controls.TextBlock> element.</span></span> <span data-ttu-id="c57d3-107">Porque o <xref:System.Windows.Controls.TextBlock> é maior do que o pai <xref:System.Windows.Controls.ScrollViewer>, barras de rolagem aparecem para permitir a rolagem.</span><span class="sxs-lookup"><span data-stu-id="c57d3-107">Because the <xref:System.Windows.Controls.TextBlock> is larger than the parent <xref:System.Windows.Controls.ScrollViewer>, scroll bars appear in order to enable scrolling.</span></span> <span data-ttu-id="c57d3-108"><xref:System.Windows.Controls.Button> elementos que representam os diversos métodos de rolagem são encaixados à esquerda em um separado <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="c57d3-108"><xref:System.Windows.Controls.Button> elements that represent the various scrolling methods are docked on the left in a separate <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="c57d3-109">Cada <xref:System.Windows.Controls.Button> no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo chama um método personalizado relacionado que controla o comportamento de rolagem em <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="c57d3-109">Each <xref:System.Windows.Controls.Button> in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file calls a related custom method that controls scrolling behavior in <xref:System.Windows.Controls.ScrollViewer>.</span></span>  
  
 [!code-xaml[ScrollViewerMethods#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="c57d3-110">O exemplo a seguir usa o <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> e <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> métodos.</span><span class="sxs-lookup"><span data-stu-id="c57d3-110">The following example uses the <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> and <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> methods.</span></span>  
  
 [!code-csharp[ScrollViewerMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="c57d3-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c57d3-111">See also</span></span>

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.StackPanel>
