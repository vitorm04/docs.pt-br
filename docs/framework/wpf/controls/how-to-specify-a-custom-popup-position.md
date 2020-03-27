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
# <a name="how-to-specify-a-custom-popup-position"></a>Como especificar uma posição de pop-up personalizada
Este exemplo mostra como especificar <xref:System.Windows.Controls.Primitives.Popup> uma posição <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> personalizada para <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>um controle quando a propriedade é definida como .  
  
## <a name="example"></a>Exemplo  
 Quando <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> a propriedade <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>é <xref:System.Windows.Controls.Primitives.Popup> definida para , <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> a chamada é uma instância definida do delegado. Este delegado retorna um conjunto de possíveis pontos que são relativos ao canto <xref:System.Windows.Controls.Primitives.Popup>superior esquerdo da área alvo e ao canto superior esquerdo do . A <xref:System.Windows.Controls.Primitives.Popup> colocação ocorre no ponto que proporciona a melhor visibilidade.  
  
 O exemplo a seguir mostra como <xref:System.Windows.Controls.Primitives.Popup> definir <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> a <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>posição de a definindo a propriedade como . Ele também mostra como criar <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> e atribuir um <xref:System.Windows.Controls.Primitives.Popup>delegado a fim de posicionar o .  O delegado de <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> retorno retorna dois objetos.  Se <xref:System.Windows.Controls.Primitives.Popup> o estiver escondido por uma borda <xref:System.Windows.Controls.Primitives.Popup> de tela na primeira posição, o é colocado na segunda posição.  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 Para ver o exemplo completo, confira [Exemplo de posicionamento do pop-up](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Controls.Primitives.Popup>
- [Visão geral do pop-up](popup-overview.md)
- [Tópicos explicativos ](popup-how-to-topics.md)
