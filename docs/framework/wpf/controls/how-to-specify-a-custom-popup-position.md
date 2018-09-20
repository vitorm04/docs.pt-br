---
title: Como especificar uma posição de pop-up personalizada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: e6e81a6e0819ba3eb39a1c568e6872414e671544
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46473366"
---
# <a name="how-to-specify-a-custom-popup-position"></a><span data-ttu-id="23652-102">Como especificar uma posição de pop-up personalizada</span><span class="sxs-lookup"><span data-stu-id="23652-102">How to: Specify a Custom Popup Position</span></span>
<span data-ttu-id="23652-103">Este exemplo mostra como especificar uma posição personalizada para um <xref:System.Windows.Controls.Primitives.Popup> controlar quando o <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> estiver definida como <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="23652-103">This example shows how to specify a custom position for a <xref:System.Windows.Controls.Primitives.Popup> control when the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23652-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="23652-104">Example</span></span>  
 <span data-ttu-id="23652-105">Quando o <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> estiver definida como <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, o <xref:System.Windows.Controls.Primitives.Popup> chama uma instância definida do <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegar.</span><span class="sxs-lookup"><span data-stu-id="23652-105">When the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, the <xref:System.Windows.Controls.Primitives.Popup> calls a defined instance of the <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate.</span></span> <span data-ttu-id="23652-106">Esse delegado retorna um conjunto de pontos possíveis que são relativas ao canto superior esquerdo da área de destino e o canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="23652-106">This delegate returns a set of possible points that are relative to the top left corner of the target area and the top left corner of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span> <span data-ttu-id="23652-107">O <xref:System.Windows.Controls.Primitives.Popup> posicionamento ocorre no ponto em que oferece melhor visibilidade.</span><span class="sxs-lookup"><span data-stu-id="23652-107">The <xref:System.Windows.Controls.Primitives.Popup> placement occurs at the point that provides the best visibility.</span></span>  
  
 <span data-ttu-id="23652-108">O exemplo a seguir mostra como definir a posição de um <xref:System.Windows.Controls.Primitives.Popup> definindo o <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriedade <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="23652-108">The following example shows how to define the position of a <xref:System.Windows.Controls.Primitives.Popup> by setting the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span> <span data-ttu-id="23652-109">Ele também mostra como criar e atribuir uma <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegado para posicionar o <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="23652-109">It also shows how to create and assign a <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate in order to position the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  <span data-ttu-id="23652-110">O delegado de retorno de chamada retorna dois <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objetos.</span><span class="sxs-lookup"><span data-stu-id="23652-110">The callback delegate returns two <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objects.</span></span>  <span data-ttu-id="23652-111">Se o <xref:System.Windows.Controls.Primitives.Popup> está oculto pela borda de tela na primeira posição, o <xref:System.Windows.Controls.Primitives.Popup> é colocado na segunda posição.</span><span class="sxs-lookup"><span data-stu-id="23652-111">If the <xref:System.Windows.Controls.Primitives.Popup> is hidden by a screen edge at the first position, the <xref:System.Windows.Controls.Primitives.Popup> is placed at the second position.</span></span>  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 <span data-ttu-id="23652-112">Para ver o exemplo completo, confira [Exemplo de posicionamento do pop-up](https://go.microsoft.com/fwlink/?LinkID=160032).</span><span class="sxs-lookup"><span data-stu-id="23652-112">For the complete sample, see [Popup Placement Sample](https://go.microsoft.com/fwlink/?LinkID=160032).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23652-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23652-113">See Also</span></span>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [<span data-ttu-id="23652-114">Visão geral do pop-up</span><span class="sxs-lookup"><span data-stu-id="23652-114">Popup Overview</span></span>](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [<span data-ttu-id="23652-115">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="23652-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)
