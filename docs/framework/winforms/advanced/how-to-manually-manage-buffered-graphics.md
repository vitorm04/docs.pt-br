---
title: 'Como: gerenciar elementos gráficos em buffer manualmente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
ms.openlocfilehash: 6010d52750b20c07db51917621f8643e9d9b47d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968596"
---
# <a name="how-to-manually-manage-buffered-graphics"></a>Como: gerenciar elementos gráficos em buffer manualmente
Para cenários de buffer duplo mais avançados, você pode usar as classes de .NET Framework para implementar sua própria lógica de buffer duplo. A classe responsável por alocar e gerenciar buffers de gráficos individuais <xref:System.Drawing.BufferedGraphicsContext> é a classe. Cada aplicativo tem seu próprio padrão <xref:System.Drawing.BufferedGraphicsContext> que gerencia todo o buffer duplo padrão para esse aplicativo. Você pode recuperar uma referência a essa instância chamando o <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a>Para obter uma referência para o BufferedGraphicsContext padrão  
  
- Defina a <xref:System.Drawing.BufferedGraphicsManager.Current%2A> Propriedade, conforme mostrado no exemplo de código a seguir.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    > Você não precisa chamar o `Dispose` método <xref:System.Drawing.BufferedGraphicsContext> na referência <xref:System.Drawing.BufferedGraphicsManager> que você recebe da classe. O <xref:System.Drawing.BufferedGraphicsManager> lida com toda a alocação e distribuição de memória para <xref:System.Drawing.BufferedGraphicsContext> instâncias padrão.  
  
     Para aplicativos com uso gráfico intensivo, como animação, às vezes você pode melhorar o <xref:System.Drawing.BufferedGraphicsContext> <xref:System.Drawing.BufferedGraphicsContext> desempenho usando um dedicado, em vez do <xref:System.Drawing.BufferedGraphicsManager>fornecido pelo. Isso permite que você crie e gerencie buffers de gráficos individualmente, sem incorrer na sobrecarga de desempenho de gerenciar todos os outros elementos gráficos em buffer associados à sua aplicação, embora a memória consumida pela aplicação será maior.  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a>Para criar um BufferedGraphicsContext dedicado  
  
- Declare e crie uma nova instância da <xref:System.Drawing.BufferedGraphicsContext> classe, conforme mostrado no exemplo de código a seguir.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.BufferedGraphicsContext>
- [Elementos Gráficos em Buffer Duplo](double-buffered-graphics.md)
- [Como: Renderizar manualmente gráficos em buffer](how-to-manually-render-buffered-graphics.md)
