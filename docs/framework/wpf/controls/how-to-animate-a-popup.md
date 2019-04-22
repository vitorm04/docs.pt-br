---
title: 'Como: Animar um pop-up'
ms.date: 03/30/2017
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
ms.openlocfilehash: b70d9c4cb1bca26a6c77d3a7c50add517ca8ef92
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150105"
---
# <a name="how-to-animate-a-popup"></a>Como: Animar um pop-up
Este exemplo mostra duas maneiras de animar uma <xref:System.Windows.Controls.Primitives.Popup> controle.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define o <xref:System.Windows.Controls.Primitives.PopupAnimation> propriedade para um valor de <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, que faz com que o <xref:System.Windows.Controls.Primitives.Popup> como "slide-in" quando ele for exibido.  
  
 Para girar o <xref:System.Windows.Controls.Primitives.Popup>, este exemplo atribui um <xref:System.Windows.Media.RotateTransform> para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade o <xref:System.Windows.Controls.Canvas>, que é o elemento filho do <xref:System.Windows.Controls.Primitives.Popup>.  
  
 Para a transformação funcione corretamente, o exemplo deve definir a <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> propriedade para `true`. Além disso, o <xref:System.Windows.FrameworkElement.Margin%2A> sobre o <xref:System.Windows.Controls.Canvas> conteúdo deve especificar espaço suficiente para o <xref:System.Windows.Controls.Primitives.Popup> para girar.  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 A exemplo a seguir mostra como uma <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento, que ocorre quando um <xref:System.Windows.Controls.Button> é clicado, dispara o <xref:System.Windows.Media.Animation.Storyboard> que inicia a animação.  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Controls.Primitives.BulletDecorator>
- <xref:System.Windows.Media.RotateTransform>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Controls.Primitives.Popup>
- [Tópicos de instruções](popup-how-to-topics.md)
- [Visão geral do pop-up](popup-overview.md)
