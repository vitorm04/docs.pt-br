---
title: 'Como: renderizar elementos gráficos em buffer manualmente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually rendering graphics
- graphics [Windows Forms], rendering
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
ms.openlocfilehash: a6655652a7c5dedb8e183356688972c07a705cbc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931845"
---
# <a name="how-to-manually-render-buffered-graphics"></a>Como: renderizar elementos gráficos em buffer manualmente
Se você gerenciar seus próprios elementos gráficos em buffer, precisará ser capaz de criar e renderizar buffers gráficos. Você pode criar instâncias da <xref:System.Drawing.BufferedGraphics> classe que está associada a superfícies de desenho na tela chamando o <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> método. Esse método cria uma <xref:System.Drawing.BufferedGraphics> instância associada a uma determinada superfície de renderização, como um formulário ou controle. Depois de criar uma <xref:System.Drawing.BufferedGraphics> instância, você pode desenhar gráficos para o buffer que ele representa por meio da <xref:System.Drawing.BufferedGraphics.Graphics%2A> propriedade. Depois de executar todas as operações de gráficos, você pode copiar o conteúdo do buffer na tela chamando o <xref:System.Drawing.BufferedGraphics.Render%2A> método.  
  
> [!NOTE]
> Se você executar sua própria renderização, o consumo de memória aumentará, embora o aumento possa ser pequeno.  
  
### <a name="to-manually-display-buffered-graphics"></a>Exibir elementos gráficos em buffer manualmente  
  
1. Obtenha uma referência a uma instância da <xref:System.Drawing.BufferedGraphicsContext> classe. Para obter mais informações, confira [Como: Gerencie manualmente os gráficos](how-to-manually-manage-buffered-graphics.md)em buffer.  
  
2. Crie uma instância da <xref:System.Drawing.BufferedGraphics> classe chamando o <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> método, conforme mostrado no exemplo de código a seguir.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3. Desenhe gráficos para o buffer de gráficos definindo a <xref:System.Drawing.BufferedGraphics.Graphics%2A> propriedade. Por exemplo:  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4. Quando você tiver concluído todas as suas operações de desenho para o buffer de gráficos, <xref:System.Drawing.BufferedGraphics.Render%2A> chame o método para renderizar o buffer, seja para a superfície de desenho associada a esse buffer ou para uma superfície de desenho especificada, conforme mostrado no exemplo de código a seguir.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5. Depois de terminar de renderizar os gráficos, `Dispose` chame o método <xref:System.Drawing.BufferedGraphics> na instância para liberar recursos do sistema.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphics>
- [Elementos Gráficos em Buffer Duplo](double-buffered-graphics.md)
- [Como: Gerenciar manualmente gráficos em buffer](how-to-manually-manage-buffered-graphics.md)
