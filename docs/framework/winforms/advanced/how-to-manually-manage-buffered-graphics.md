---
title: 'Como: Gerenciar elementos gráficos em buffer manualmente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
ms.openlocfilehash: b27a013d2cf66fb12365bffc35a07ed32bc25a2e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554485"
---
# <a name="how-to-manually-manage-buffered-graphics"></a>Como: Gerenciar elementos gráficos em buffer manualmente
Para cenários mais avançados de armazenamento em buffer duplos, é possível usar as classes [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para implementar sua própria lógica de buffer duplo. A classe responsável por alocar e gerenciar buffers gráficos individuais é o <xref:System.Drawing.BufferedGraphicsContext> classe. Cada aplicativo tem seu próprio padrão <xref:System.Drawing.BufferedGraphicsContext> que gerencia todo o buffer duplo padrão para esse aplicativo. Você pode recuperar uma referência a essa instância chamando o <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a>Para obter uma referência para o BufferedGraphicsContext padrão  
  
-   Defina o <xref:System.Drawing.BufferedGraphicsManager.Current%2A> propriedade, conforme mostrado no exemplo de código a seguir.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    >  Você não precisará chamar o `Dispose` método na <xref:System.Drawing.BufferedGraphicsContext> referência que você receber o <xref:System.Drawing.BufferedGraphicsManager> classe. O <xref:System.Drawing.BufferedGraphicsManager> manipula toda a alocação de memória e a distribuição para padrão <xref:System.Drawing.BufferedGraphicsContext> instâncias.  
  
     Para aplicações graficamente intensas como animação, você pode, às vezes, melhorar o desempenho usando um dedicado <xref:System.Drawing.BufferedGraphicsContext> em vez do <xref:System.Drawing.BufferedGraphicsContext> fornecidas pelo <xref:System.Drawing.BufferedGraphicsManager>. Isso permite que você crie e gerencie buffers de gráficos individualmente, sem incorrer na sobrecarga de desempenho de gerenciar todos os outros elementos gráficos em buffer associados à sua aplicação, embora a memória consumida pela aplicação será maior.  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a>Para criar um BufferedGraphicsContext dedicado  
  
-   Declare e crie uma nova instância do <xref:System.Drawing.BufferedGraphicsContext> de classe, conforme mostrado no exemplo de código a seguir.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Drawing.BufferedGraphicsContext>
- [Elementos Gráficos em Buffer Duplo](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)
- [Como: Renderizar elementos gráficos em buffer manualmente](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)
