---
title: 'Como: Personalizar o tamanho de elevador em um ScrollBar'
ms.date: 03/30/2017
helpviewer_keywords:
- ScrollBar control [WPF]
- customizing thumb size [WPF]
- thumb size [WPF]
ms.assetid: fa32b866-5ca1-4e73-85e7-2ac64b80d194
ms.openlocfilehash: 2c77eb23c1a42051a7c2d81f3454eb51425fa034
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590858"
---
# <a name="how-to-customize-the-thumb-size-on-a-scrollbar"></a><span data-ttu-id="f077c-102">Como: Personalizar o tamanho de elevador em um ScrollBar</span><span class="sxs-lookup"><span data-stu-id="f077c-102">How to: Customize the Thumb Size on a ScrollBar</span></span>
<span data-ttu-id="f077c-103">Este tópico explica como definir as <xref:System.Windows.Controls.Primitives.Thumb> de um <xref:System.Windows.Controls.Primitives.ScrollBar> para um tamanho fixo e como especificar um tamanho mínimo para o <xref:System.Windows.Controls.Primitives.Thumb> de um <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="f077c-103">This topic explains how to set the <xref:System.Windows.Controls.Primitives.Thumb> of a <xref:System.Windows.Controls.Primitives.ScrollBar> to a fixed size and how to specify a minimum size for the <xref:System.Windows.Controls.Primitives.Thumb> of a <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f077c-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f077c-104">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="f077c-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="f077c-105">Description</span></span>  
 <span data-ttu-id="f077c-106">O exemplo a seguir cria uma <xref:System.Windows.Controls.Primitives.ScrollBar> que tem um <xref:System.Windows.Controls.Primitives.Thumb> com um tamanho fixo.</span><span class="sxs-lookup"><span data-stu-id="f077c-106">The following example creates a <xref:System.Windows.Controls.Primitives.ScrollBar> that has a <xref:System.Windows.Controls.Primitives.Thumb> with a fixed size.</span></span> <span data-ttu-id="f077c-107">O exemplo define o <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> propriedade do <xref:System.Windows.Controls.Primitives.Thumb> à <xref:System.Double.NaN> e define a altura do <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="f077c-107">The example sets the <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> property of the <xref:System.Windows.Controls.Primitives.Thumb> to <xref:System.Double.NaN> and sets the height of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  <span data-ttu-id="f077c-108">Para criar um horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> com um <xref:System.Windows.Controls.Primitives.Thumb> que tem uma largura fixa, defina a largura do <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="f077c-108">To create a horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> with a <xref:System.Windows.Controls.Primitives.Thumb> that has a fixed width, set the width of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="f077c-109">Código</span><span class="sxs-lookup"><span data-stu-id="f077c-109">Code</span></span>  
 [!code-xaml[ScrollBarCustomThumbSize#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#1)]  
  
## <a name="description"></a><span data-ttu-id="f077c-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="f077c-110">Description</span></span>  
 <span data-ttu-id="f077c-111">O exemplo a seguir cria uma <xref:System.Windows.Controls.Primitives.ScrollBar> que tem um <xref:System.Windows.Controls.Primitives.Thumb> com um tamanho mínimo.</span><span class="sxs-lookup"><span data-stu-id="f077c-111">The following example creates a <xref:System.Windows.Controls.Primitives.ScrollBar> that has a <xref:System.Windows.Controls.Primitives.Thumb> with a minimum size.</span></span> <span data-ttu-id="f077c-112">O exemplo define o valor de <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="f077c-112">The example sets the value of <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>.</span></span> <span data-ttu-id="f077c-113">Para criar um horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> com um <xref:System.Windows.Controls.Primitives.Thumb> que tem uma largura mínima, defina o <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="f077c-113">To create a horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> with a <xref:System.Windows.Controls.Primitives.Thumb> that has a minimum width, set the <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="f077c-114">Código</span><span class="sxs-lookup"><span data-stu-id="f077c-114">Code</span></span>  
 [!code-xaml[ScrollBarCustomThumbSize#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f077c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f077c-115">See also</span></span>
- [<span data-ttu-id="f077c-116">Estilos e modelos ScrollBar</span><span class="sxs-lookup"><span data-stu-id="f077c-116">ScrollBar Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)
