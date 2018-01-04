---
title: Como animar um pop-up
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd79b29849510f40034dd0e2f1d9668c9b742929
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-popup"></a>Como animar um pop-up
Este exemplo mostra duas maneiras para animar uma <xref:System.Windows.Controls.Primitives.Popup> controle.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define o <xref:System.Windows.Controls.Primitives.PopupAnimation> propriedade com um valor de <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, que faz com que o <xref:System.Windows.Controls.Primitives.Popup> "deslize para dentro" quando ele for exibido.  
  
 Para girar o <xref:System.Windows.Controls.Primitives.Popup>, este exemplo atribui uma <xref:System.Windows.Media.RotateTransform> para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade o <xref:System.Windows.Controls.Canvas>, que é o elemento filho do <xref:System.Windows.Controls.Primitives.Popup>.  
  
 Para que a transformação funcione corretamente, o exemplo deve definir a <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> propriedade `true`. Além disso, o <xref:System.Windows.FrameworkElement.Margin%2A> no <xref:System.Windows.Controls.Canvas> conteúdo deve especificar espaço suficiente para o <xref:System.Windows.Controls.Primitives.Popup> para girar.  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 A exemplo a seguir mostra como um <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento que ocorre quando um <xref:System.Windows.Controls.Button> é clicado, dispara o <xref:System.Windows.Media.Animation.Storyboard> que inicia a animação.  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.UIElement.RenderTransform%2A>  
 <xref:System.Windows.Controls.Primitives.BulletDecorator>  
 <xref:System.Windows.Media.RotateTransform>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)  
 [Visão geral do pop-up](../../../../docs/framework/wpf/controls/popup-overview.md)
