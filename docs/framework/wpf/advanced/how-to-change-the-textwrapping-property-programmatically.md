---
title: 'Como: Alterar a propriedade TextWrapping de forma programática'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], changing TextWrapping property programmatically
- TextWrapping property [WPF], changing programmatically
ms.assetid: 30d25554-4c82-4df9-a8d6-35683a4a13bb
ms.openlocfilehash: 21ca31d24121492fe6927cd533d5b3c0785b5a28
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095835"
---
# <a name="how-to-change-the-textwrapping-property-programmatically"></a><span data-ttu-id="2b67e-102">Como: Alterar a propriedade TextWrapping de forma programática</span><span class="sxs-lookup"><span data-stu-id="2b67e-102">How to: Change the TextWrapping Property Programmatically</span></span>
## <a name="example"></a><span data-ttu-id="2b67e-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b67e-103">Example</span></span>  
 <span data-ttu-id="2b67e-104">O exemplo de código a seguir mostra como alterar o valor da <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> propriedade programaticamente.</span><span class="sxs-lookup"><span data-stu-id="2b67e-104">The following code example shows how to change the value of the <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> property programmatically.</span></span>  
  
 <span data-ttu-id="2b67e-105">Três <xref:System.Windows.Controls.Button> elementos são colocados dentro de uma <xref:System.Windows.Controls.StackPanel> elemento em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2b67e-105">Three <xref:System.Windows.Controls.Button> elements are placed within a <xref:System.Windows.Controls.StackPanel> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="2b67e-106">Cada <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento para um <xref:System.Windows.Controls.Button> corresponde a um manipulador de eventos no código.</span><span class="sxs-lookup"><span data-stu-id="2b67e-106">Each <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event for a <xref:System.Windows.Controls.Button> corresponds with an event handler in the code.</span></span> <span data-ttu-id="2b67e-107">Os manipuladores de eventos usam o mesmo nome que o <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> valor que elas se aplicarão `txt2` quando o botão é clicado.</span><span class="sxs-lookup"><span data-stu-id="2b67e-107">The event handlers use the same name as the <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> value they will apply to `txt2` when the button is clicked.</span></span> <span data-ttu-id="2b67e-108">Além disso, o texto no `txt1` (uma <xref:System.Windows.Controls.TextBlock> não são mostrados no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) é atualizada para refletir a alteração na propriedade.</span><span class="sxs-lookup"><span data-stu-id="2b67e-108">Also, the text in `txt1` (a <xref:System.Windows.Controls.TextBlock> not shown in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) is updated to reflect the change in the property.</span></span>  
  
 [!code-xaml[TextWrapProperty#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2b67e-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b67e-109">See also</span></span>

- <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>
- <xref:System.Windows.TextWrapping>
