---
title: 'Como: Renderizar elementos gráficos em buffer manualmente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually rendering graphics
- graphics [Windows Forms], rendering
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
ms.openlocfilehash: f901350b1cb63f385eba52665785c8d0f7fd7e5f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636346"
---
# <a name="how-to-manually-render-buffered-graphics"></a>Como: Renderizar elementos gráficos em buffer manualmente
Se você gerenciar seus próprios elementos gráficos em buffer, precisará ser capaz de criar e renderizar buffers gráficos. Você pode criar instâncias do <xref:System.Drawing.BufferedGraphics> classe que está associado com superfícies de desenho na tela chamando o <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> método. Esse método cria um <xref:System.Drawing.BufferedGraphics> instância que está associada uma superfície de renderização específica, como um formulário ou controle. Depois de criar uma <xref:System.Drawing.BufferedGraphics> instância, você pode desenhar gráficos no buffer que ele representa usando o <xref:System.Drawing.BufferedGraphics.Graphics%2A> propriedade. Depois de realizar todas as operações de gráficos, você pode copiar o conteúdo do buffer para a tela chamando o <xref:System.Drawing.BufferedGraphics.Render%2A> método.  
  
> [!NOTE]
>  Se você executar sua própria renderização, o consumo de memória aumentará, embora o aumento possa ser pequeno.  
  
### <a name="to-manually-display-buffered-graphics"></a>Exibir elementos gráficos em buffer manualmente  
  
1.  Obtenha uma referência a uma instância da <xref:System.Drawing.BufferedGraphicsContext> classe. Para obter mais informações, confira [Como: Gerenciar elementos gráficos em buffer manualmente](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).  
  
2.  Criar uma instância das <xref:System.Drawing.BufferedGraphics> classe chamando o <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> método, conforme mostrado no exemplo de código a seguir.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3.  Desenhar gráficos no buffer gráfico Configurando a <xref:System.Drawing.BufferedGraphics.Graphics%2A> propriedade. Por exemplo:  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4.  Quando você tiver concluído todas as suas operações de desenho no buffer gráfico, chame o <xref:System.Drawing.BufferedGraphics.Render%2A> método para renderizar o buffer, seja para a superfície de desenho associada a esse buffer ou a uma superfície de desenho especificada, conforme mostrado no exemplo de código a seguir.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5.  Depois de terminar de processamento de gráficos, chame o `Dispose` método no <xref:System.Drawing.BufferedGraphics> instância para liberar recursos do sistema.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphics>
- [Elementos Gráficos em Buffer Duplo](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)
- [Como: Gerenciar elementos gráficos em buffer manualmente](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)
