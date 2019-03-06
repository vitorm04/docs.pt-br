---
title: 'Como: Usar a propriedade BetweenShowDelay'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
ms.openlocfilehash: e0653fbcb8eb052b12be7344ffe239431b67a951
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370952"
---
# <a name="how-to-use-the-betweenshowdelay-property"></a>Como: Usar a propriedade BetweenShowDelay
Este exemplo mostra como usar o <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> propriedade de tempo para que apareçam dicas de ferramentas rapidamente — com pouco ou nenhum atraso — quando um usuário move o ponteiro do mouse de uma dica de ferramenta diretamente para outra.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> estiver definida como um segundo (1000 milissegundos) e o <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> é definido como dois segundos (2000 milissegundos) para as dicas de ferramentas de ambos <xref:System.Windows.Shapes.Ellipse> controles. Se você exibir a dica de ferramentas para uma das elipses e mover o ponteiro do mouse para outra elipse dentro de dois segundos e pausar nela, a dica de ferramenta da segunda elipse será exibida imediatamente.  
  
 Em qualquer um dos cenários a seguir, o <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> se aplica, que faz com que a dica de ferramenta para a segunda elipse espere um segundo antes que ela apareça:  
  
-   Se o tempo levado para mover para o segundo botão for maior do que dois segundos.  
  
-   Se a dica de ferramenta não estiver visível no início do intervalo de tempo para a primeira elipse.  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Tópicos de instruções](tooltip-how-to-topics.md)
- [Visão geral de ToolTip](tooltip-overview.md)
