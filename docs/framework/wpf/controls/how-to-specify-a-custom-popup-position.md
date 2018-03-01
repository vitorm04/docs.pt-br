---
title: "Como especificar uma posição de pop-up personalizada"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ae10153f31b79a220b84cae7a6525eca0ce0bd9c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-custom-popup-position"></a><span data-ttu-id="8018b-102">Como especificar uma posição de pop-up personalizada</span><span class="sxs-lookup"><span data-stu-id="8018b-102">How to: Specify a Custom Popup Position</span></span>
<span data-ttu-id="8018b-103">Este exemplo mostra como especificar uma posição personalizada para um <xref:System.Windows.Controls.Primitives.Popup> controlar quando o <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> está definida como <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="8018b-103">This example shows how to specify a custom position for a <xref:System.Windows.Controls.Primitives.Popup> control when the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8018b-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8018b-104">Example</span></span>  
 <span data-ttu-id="8018b-105">Quando o <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> está definida como <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, o <xref:System.Windows.Controls.Primitives.Popup> chama uma instância definida do <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate.</span><span class="sxs-lookup"><span data-stu-id="8018b-105">When the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, the <xref:System.Windows.Controls.Primitives.Popup> calls a defined instance of the <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate.</span></span> <span data-ttu-id="8018b-106">Este delegado retorna um conjunto de pontos possíveis que são relativas ao canto superior esquerdo da área de destino e o canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="8018b-106">This delegate returns a set of possible points that are relative to the top left corner of the target area and the top left corner of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span> <span data-ttu-id="8018b-107">O <xref:System.Windows.Controls.Primitives.Popup> posicionamento ocorre no ponto em que fornece melhor visibilidade.</span><span class="sxs-lookup"><span data-stu-id="8018b-107">The <xref:System.Windows.Controls.Primitives.Popup> placement occurs at the point that provides the best visibility.</span></span>  
  
 <span data-ttu-id="8018b-108">O exemplo a seguir mostra como definir a posição de um <xref:System.Windows.Controls.Primitives.Popup> definindo o <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriedade <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="8018b-108">The following example shows how to define the position of a <xref:System.Windows.Controls.Primitives.Popup> by setting the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span> <span data-ttu-id="8018b-109">Ele também mostra como criar e atribuir uma <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegado para posicionar o <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="8018b-109">It also shows how to create and assign a <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate in order to position the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  <span data-ttu-id="8018b-110">O representante de retorno de chamada retorna dois <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objetos.</span><span class="sxs-lookup"><span data-stu-id="8018b-110">The callback delegate returns two <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objects.</span></span>  <span data-ttu-id="8018b-111">Se o <xref:System.Windows.Controls.Primitives.Popup> está oculto por uma borda de tela na primeira posição, o <xref:System.Windows.Controls.Primitives.Popup> é colocado na posição de segundo.</span><span class="sxs-lookup"><span data-stu-id="8018b-111">If the <xref:System.Windows.Controls.Primitives.Popup> is hidden by a screen edge at the first position, the <xref:System.Windows.Controls.Primitives.Popup> is placed at the second position.</span></span>  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 <span data-ttu-id="8018b-112">Para ver o exemplo completo, confira [Exemplo de posicionamento do pop-up](http://go.microsoft.com/fwlink/?LinkID=160032).</span><span class="sxs-lookup"><span data-stu-id="8018b-112">For the complete sample, see [Popup Placement Sample](http://go.microsoft.com/fwlink/?LinkID=160032).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8018b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8018b-113">See Also</span></span>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [<span data-ttu-id="8018b-114">Visão geral do pop-up</span><span class="sxs-lookup"><span data-stu-id="8018b-114">Popup Overview</span></span>](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [<span data-ttu-id="8018b-115">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="8018b-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)
