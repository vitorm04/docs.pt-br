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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59974994"
---
# <a name="how-to-change-the-textwrapping-property-programmatically"></a>Como: Alterar a propriedade TextWrapping de forma programática
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como alterar o valor da <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> propriedade programaticamente.  
  
 Três <xref:System.Windows.Controls.Button> elementos são colocados dentro de uma <xref:System.Windows.Controls.StackPanel> elemento em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Cada <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento para um <xref:System.Windows.Controls.Button> corresponde a um manipulador de eventos no código. Os manipuladores de eventos usam o mesmo nome que o <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> valor que elas se aplicarão `txt2` quando o botão é clicado. Além disso, o texto no `txt1` (uma <xref:System.Windows.Controls.TextBlock> não são mostrados no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) é atualizada para refletir a alteração na propriedade.  
  
 [!code-xaml[TextWrapProperty#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>
- <xref:System.Windows.TextWrapping>
