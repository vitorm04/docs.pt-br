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
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43860612"
---
# <a name="how-to-specify-a-custom-popup-position"></a>Como especificar uma posição de pop-up personalizada
Este exemplo mostra como especificar uma posição personalizada para um <xref:System.Windows.Controls.Primitives.Popup> controlar quando o <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> estiver definida como <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.  
  
## <a name="example"></a>Exemplo  
 Quando o <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> estiver definida como <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, o <xref:System.Windows.Controls.Primitives.Popup> chama uma instância definida do <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegar. Esse delegado retorna um conjunto de pontos possíveis que são relativas ao canto superior esquerdo da área de destino e o canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>. O <xref:System.Windows.Controls.Primitives.Popup> posicionamento ocorre no ponto em que oferece melhor visibilidade.  
  
 O exemplo a seguir mostra como definir a posição de um <xref:System.Windows.Controls.Primitives.Popup> definindo o <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriedade <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Ele também mostra como criar e atribuir uma <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegado para posicionar o <xref:System.Windows.Controls.Primitives.Popup>.  O delegado de retorno de chamada retorna dois <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objetos.  Se o <xref:System.Windows.Controls.Primitives.Popup> está oculto pela borda de tela na primeira posição, o <xref:System.Windows.Controls.Primitives.Popup> é colocado na segunda posição.  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 Para ver o exemplo completo, confira [Exemplo de posicionamento do pop-up](https://go.microsoft.com/fwlink/?LinkID=160032).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [Visão geral do pop-up](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)
