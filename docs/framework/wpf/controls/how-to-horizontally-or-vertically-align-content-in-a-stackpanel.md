---
title: Como alinhar horizontal e verticalmente o conteúdo em um StackPanel
description: Saiba como ajustar a orientação do conteúdo em um Windows Presentation Foundation StackPanel e o HorizontalAlignment e o VerticalAlignment de conteúdo filho.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: d3c7215d8193d1d8a72597c44cf265f5bd400ea1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167626"
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a><span data-ttu-id="45217-103">Como alinhar horizontal e verticalmente o conteúdo em um StackPanel</span><span class="sxs-lookup"><span data-stu-id="45217-103">How to: Horizontally or Vertically Align Content in a StackPanel</span></span>
<span data-ttu-id="45217-104">Este exemplo mostra como ajustar o <xref:System.Windows.Controls.StackPanel.Orientation%2A> conteúdo dentro de um <xref:System.Windows.Controls.StackPanel> elemento e também como ajustar o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> e o <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> conteúdo filho.</span><span class="sxs-lookup"><span data-stu-id="45217-104">This example shows how to adjust the <xref:System.Windows.Controls.StackPanel.Orientation%2A> of content within a <xref:System.Windows.Controls.StackPanel> element, and also how to adjust the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> of child content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45217-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45217-105">Example</span></span>  
 <span data-ttu-id="45217-106">O exemplo a seguir cria três <xref:System.Windows.Controls.ListBox> elementos no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="45217-106">The following example creates three <xref:System.Windows.Controls.ListBox> elements in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="45217-107">Cada <xref:System.Windows.Controls.ListBox> um representa os valores possíveis das <xref:System.Windows.Controls.StackPanel.Orientation%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> Propriedades, e <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> de a <xref:System.Windows.Controls.StackPanel> .</span><span class="sxs-lookup"><span data-stu-id="45217-107">Each <xref:System.Windows.Controls.ListBox> represents the possible values of the <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> properties of a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="45217-108">Quando um usuário seleciona um valor em qualquer um dos <xref:System.Windows.Controls.ListBox> elementos, a propriedade associada do <xref:System.Windows.Controls.StackPanel> e seus elementos filho são <xref:System.Windows.Controls.Button> alterados.</span><span class="sxs-lookup"><span data-stu-id="45217-108">When a user selects a value in any of the <xref:System.Windows.Controls.ListBox> elements, the associated property of the <xref:System.Windows.Controls.StackPanel> and its child <xref:System.Windows.Controls.Button> elements change.</span></span>  
  
 [!code-xaml[StackPanelIntroSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="45217-109">O arquivo code-behind a seguir define as alterações nos eventos associados às <xref:System.Windows.Controls.ListBox> alterações de seleção.</span><span class="sxs-lookup"><span data-stu-id="45217-109">The following code-behind file defines the changes to the events that are associated with the <xref:System.Windows.Controls.ListBox> selection changes.</span></span> <span data-ttu-id="45217-110"><xref:System.Windows.Controls.StackPanel>é identificado pelo <xref:System.Windows.FrameworkElement.Name%2A> `sp1` .</span><span class="sxs-lookup"><span data-stu-id="45217-110"><xref:System.Windows.Controls.StackPanel> is identified by the <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.</span></span>  
  
 [!code-csharp[StackPanelIntroSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="45217-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="45217-111">See also</span></span>

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- [<span data-ttu-id="45217-112">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="45217-112">Panels Overview</span></span>](panels-overview.md)
