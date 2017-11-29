---
title: "Como especificar uma posição de pop-up personalizada"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0ab9baca1103adf8de96204bdb1b3353a5456b94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-a-custom-popup-position"></a>Como especificar uma posição de pop-up personalizada
Este exemplo mostra como especificar uma posição personalizada para um <xref:System.Windows.Controls.Primitives.Popup> controlar quando o <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> está definida como <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.  
  
## <a name="example"></a>Exemplo  
 Quando o <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> está definida como <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, o <xref:System.Windows.Controls.Primitives.Popup> chama uma instância definida do <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate. Este delegado retorna um conjunto de pontos possíveis que são relativas ao canto superior esquerdo da área de destino e o canto superior esquerdo do <xref:System.Windows.Controls.Primitives.Popup>. O <xref:System.Windows.Controls.Primitives.Popup> posicionamento ocorre no ponto em que fornece melhor visibilidade.  
  
 O exemplo a seguir mostra como definir a posição de um <xref:System.Windows.Controls.Primitives.Popup> definindo o <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriedade <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Ele também mostra como criar e atribuir uma <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegado para posicionar o <xref:System.Windows.Controls.Primitives.Popup>.  O representante de retorno de chamada retorna dois <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objetos.  Se o <xref:System.Windows.Controls.Primitives.Popup> está oculto por uma borda de tela na primeira posição, o <xref:System.Windows.Controls.Primitives.Popup> é colocado na posição de segundo.  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 Para ver o exemplo completo, confira [Exemplo de posicionamento do pop-up](http://go.microsoft.com/fwlink/?LinkID=160032).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [Visão geral do pop-up](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [Tópicos explicativos](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)
