---
title: 'Como: Rolar conteúdo usando a interface IScrollInfo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], scrolling content
- scrolling content [WPF]
- IScrollInfo interface [WPF]
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
ms.openlocfilehash: 145c58064b8557f9cb4730ec9272c354c7aa9c1b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378972"
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a><span data-ttu-id="19a00-102">Como: Rolar conteúdo usando a interface IScrollInfo</span><span class="sxs-lookup"><span data-stu-id="19a00-102">How to: Scroll Content by Using the IScrollInfo Interface</span></span>
<span data-ttu-id="19a00-103">Este exemplo mostra como rolar conteúdo usando o <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span><span class="sxs-lookup"><span data-stu-id="19a00-103">This example shows how to scroll content by using the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19a00-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="19a00-104">Example</span></span>  
 <span data-ttu-id="19a00-105">O exemplo a seguir demonstra os recursos do <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span><span class="sxs-lookup"><span data-stu-id="19a00-105">The following example demonstrates the features of the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span></span> <span data-ttu-id="19a00-106">O exemplo cria um <xref:System.Windows.Controls.StackPanel> elemento no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] que está aninhado em uma pasta pai <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="19a00-106">The example creates a <xref:System.Windows.Controls.StackPanel> element in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that is nested in a parent <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="19a00-107">Os elementos filho do <xref:System.Windows.Controls.StackPanel> pode ser rolado logicamente usando os métodos definidos pela <xref:System.Windows.Controls.Primitives.IScrollInfo> interface e conversão para a instância do <xref:System.Windows.Controls.StackPanel> (`sp1`) no código.</span><span class="sxs-lookup"><span data-stu-id="19a00-107">The child elements of the <xref:System.Windows.Controls.StackPanel> can be scrolled logically by using the methods defined by the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface and cast to the instance of <xref:System.Windows.Controls.StackPanel> (`sp1`) in code.</span></span>  
  
 [!code-xaml[IScrollInfoMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="19a00-108">Cada <xref:System.Windows.Controls.Button> no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo aciona um método personalizado associado que controla o comportamento de rolagem em <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="19a00-108">Each <xref:System.Windows.Controls.Button> in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file triggers an associated custom method that controls scrolling behavior in <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="19a00-109">O exemplo a seguir mostra como usar o <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> e <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> métodos; também genericamente mostra como usar todos os métodos de posicionamento que o <xref:System.Windows.Controls.Primitives.IScrollInfo> classe define.</span><span class="sxs-lookup"><span data-stu-id="19a00-109">The following example shows how to use the <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> and <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> methods; it also generically shows how to use all the positioning methods that the <xref:System.Windows.Controls.Primitives.IScrollInfo> class defines.</span></span>  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="19a00-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19a00-110">See also</span></span>
- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- <xref:System.Windows.Controls.StackPanel>
- [<span data-ttu-id="19a00-111">Visão geral de ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="19a00-111">ScrollViewer Overview</span></span>](scrollviewer-overview.md)
- [<span data-ttu-id="19a00-112">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="19a00-112">How-to Topics</span></span>](scrollviewer-how-to-topics.md)
- [<span data-ttu-id="19a00-113">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="19a00-113">Panels Overview</span></span>](panels-overview.md)
