---
title: Como especificar uma posição de pop-up personalizada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: ea8d73c51dd018608b95104f00bf341ff434225c
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344960"
---
# <a name="how-to-specify-a-custom-popup-position"></a><span data-ttu-id="4f280-102">Como especificar uma posição de pop-up personalizada</span><span class="sxs-lookup"><span data-stu-id="4f280-102">How to: Specify a Custom Popup Position</span></span>
<span data-ttu-id="4f280-103">Este exemplo mostra como especificar <xref:System.Windows.Controls.Primitives.Popup> uma posição <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> personalizada para <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>um controle quando a propriedade é definida como .</span><span class="sxs-lookup"><span data-stu-id="4f280-103">This example shows how to specify a custom position for a <xref:System.Windows.Controls.Primitives.Popup> control when the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f280-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4f280-104">Example</span></span>  
 <span data-ttu-id="4f280-105">Quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> a propriedade <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>é <xref:System.Windows.Controls.Primitives.Popup> definida para , <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> a chamada é uma instância definida do delegado.</span><span class="sxs-lookup"><span data-stu-id="4f280-105">When the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, the <xref:System.Windows.Controls.Primitives.Popup> calls a defined instance of the <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate.</span></span> <span data-ttu-id="4f280-106">Este delegado retorna um conjunto de possíveis pontos que são relativos ao canto <xref:System.Windows.Controls.Primitives.Popup>superior esquerdo da área alvo e ao canto superior esquerdo do .</span><span class="sxs-lookup"><span data-stu-id="4f280-106">This delegate returns a set of possible points that are relative to the top left corner of the target area and the top left corner of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span> <span data-ttu-id="4f280-107">A <xref:System.Windows.Controls.Primitives.Popup> colocação ocorre no ponto que proporciona a melhor visibilidade.</span><span class="sxs-lookup"><span data-stu-id="4f280-107">The <xref:System.Windows.Controls.Primitives.Popup> placement occurs at the point that provides the best visibility.</span></span>  
  
 <span data-ttu-id="4f280-108">O exemplo a seguir mostra como <xref:System.Windows.Controls.Primitives.Popup> definir <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> a <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>posição de a definindo a propriedade como .</span><span class="sxs-lookup"><span data-stu-id="4f280-108">The following example shows how to define the position of a <xref:System.Windows.Controls.Primitives.Popup> by setting the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span> <span data-ttu-id="4f280-109">Ele também mostra como criar <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> e atribuir um <xref:System.Windows.Controls.Primitives.Popup>delegado a fim de posicionar o .</span><span class="sxs-lookup"><span data-stu-id="4f280-109">It also shows how to create and assign a <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate in order to position the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  <span data-ttu-id="4f280-110">O delegado de <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> retorno retorna dois objetos.</span><span class="sxs-lookup"><span data-stu-id="4f280-110">The callback delegate returns two <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objects.</span></span>  <span data-ttu-id="4f280-111">Se <xref:System.Windows.Controls.Primitives.Popup> o estiver escondido por uma borda <xref:System.Windows.Controls.Primitives.Popup> de tela na primeira posição, o é colocado na segunda posição.</span><span class="sxs-lookup"><span data-stu-id="4f280-111">If the <xref:System.Windows.Controls.Primitives.Popup> is hidden by a screen edge at the first position, the <xref:System.Windows.Controls.Primitives.Popup> is placed at the second position.</span></span>  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 <span data-ttu-id="4f280-112">Para ver o exemplo completo, confira [Exemplo de posicionamento do pop-up](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS).</span><span class="sxs-lookup"><span data-stu-id="4f280-112">For the complete sample, see [Popup Placement Sample](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f280-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="4f280-113">See also</span></span>

- <xref:System.Windows.Controls.Primitives.Popup>
- [<span data-ttu-id="4f280-114">Visão geral do pop-up</span><span class="sxs-lookup"><span data-stu-id="4f280-114">Popup Overview</span></span>](popup-overview.md)
- [<span data-ttu-id="4f280-115">Tópicos explicativos </span><span class="sxs-lookup"><span data-stu-id="4f280-115">How-to Topics</span></span>](popup-how-to-topics.md)
