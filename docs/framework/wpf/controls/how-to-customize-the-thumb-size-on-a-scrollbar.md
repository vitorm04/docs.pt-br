---
title: 'Como: Personalizar o tamanho de elevador em um ScrollBar'
ms.date: 03/30/2017
helpviewer_keywords:
- ScrollBar control [WPF]
- customizing thumb size [WPF]
- thumb size [WPF]
ms.assetid: fa32b866-5ca1-4e73-85e7-2ac64b80d194
ms.openlocfilehash: 30fc72e3f0631b01777bf058c7a7470cc376a547
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354317"
---
# <a name="how-to-customize-the-thumb-size-on-a-scrollbar"></a><span data-ttu-id="9ae5e-102">Como: Personalizar o tamanho de elevador em um ScrollBar</span><span class="sxs-lookup"><span data-stu-id="9ae5e-102">How to: Customize the Thumb Size on a ScrollBar</span></span>
<span data-ttu-id="9ae5e-103">Este tópico explica como definir as <xref:System.Windows.Controls.Primitives.Thumb> de um <xref:System.Windows.Controls.Primitives.ScrollBar> para um tamanho fixo e como especificar um tamanho mínimo para o <xref:System.Windows.Controls.Primitives.Thumb> de um <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="9ae5e-103">This topic explains how to set the <xref:System.Windows.Controls.Primitives.Thumb> of a <xref:System.Windows.Controls.Primitives.ScrollBar> to a fixed size and how to specify a minimum size for the <xref:System.Windows.Controls.Primitives.Thumb> of a <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ae5e-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ae5e-104">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="9ae5e-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ae5e-105">Description</span></span>  
 <span data-ttu-id="9ae5e-106">O exemplo a seguir cria uma <xref:System.Windows.Controls.Primitives.ScrollBar> que tem um <xref:System.Windows.Controls.Primitives.Thumb> com um tamanho fixo.</span><span class="sxs-lookup"><span data-stu-id="9ae5e-106">The following example creates a <xref:System.Windows.Controls.Primitives.ScrollBar> that has a <xref:System.Windows.Controls.Primitives.Thumb> with a fixed size.</span></span> <span data-ttu-id="9ae5e-107">O exemplo define o <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> propriedade do <xref:System.Windows.Controls.Primitives.Thumb> à <xref:System.Double.NaN> e define a altura do <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="9ae5e-107">The example sets the <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> property of the <xref:System.Windows.Controls.Primitives.Thumb> to <xref:System.Double.NaN> and sets the height of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  <span data-ttu-id="9ae5e-108">Para criar um horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> com um <xref:System.Windows.Controls.Primitives.Thumb> que tem uma largura fixa, defina a largura do <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="9ae5e-108">To create a horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> with a <xref:System.Windows.Controls.Primitives.Thumb> that has a fixed width, set the width of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="9ae5e-109">Código</span><span class="sxs-lookup"><span data-stu-id="9ae5e-109">Code</span></span>  
 [!code-xaml[ScrollBarCustomThumbSize#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#1)]  
  
## <a name="description"></a><span data-ttu-id="9ae5e-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ae5e-110">Description</span></span>  
 <span data-ttu-id="9ae5e-111">O exemplo a seguir cria uma <xref:System.Windows.Controls.Primitives.ScrollBar> que tem um <xref:System.Windows.Controls.Primitives.Thumb> com um tamanho mínimo.</span><span class="sxs-lookup"><span data-stu-id="9ae5e-111">The following example creates a <xref:System.Windows.Controls.Primitives.ScrollBar> that has a <xref:System.Windows.Controls.Primitives.Thumb> with a minimum size.</span></span> <span data-ttu-id="9ae5e-112">O exemplo define o valor de <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ae5e-112">The example sets the value of <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>.</span></span> <span data-ttu-id="9ae5e-113">Para criar um horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> com um <xref:System.Windows.Controls.Primitives.Thumb> que tem uma largura mínima, defina o <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ae5e-113">To create a horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> with a <xref:System.Windows.Controls.Primitives.Thumb> that has a minimum width, set the <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="9ae5e-114">Código</span><span class="sxs-lookup"><span data-stu-id="9ae5e-114">Code</span></span>  
 [!code-xaml[ScrollBarCustomThumbSize#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9ae5e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ae5e-115">See also</span></span>
- [<span data-ttu-id="9ae5e-116">Estilos e modelos ScrollBar</span><span class="sxs-lookup"><span data-stu-id="9ae5e-116">ScrollBar Styles and Templates</span></span>](scrollbar-styles-and-templates.md)
