---
title: Elementos gráficos em buffer duplo
ms.date: 03/30/2017
helpviewer_keywords:
- double buffering
- graphics [Windows Forms], double-buffered
- flicker [Windows Forms], reducing with double buffering
- examples [Windows Forms], double-buffered graphics
ms.assetid: 4f6fef99-0972-436e-9d73-0167e4033f71
ms.openlocfilehash: ea4b4b8616ed0b3eab2ddd6b2ec57a39909a0fce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524060"
---
# <a name="double-buffered-graphics"></a>Elementos gráficos em buffer duplo
A cintilação é um problema comum na programação de gráficos. Operações gráficas que requerem várias operações de pintura complexas podem fazer as imagens renderizadas parecerem cintilar ou ter uma aparência inaceitável por outro motivo. Para resolver esses problemas, o .NET Framework dá acesso a buffer duplo.  
  
 O buffer duplo usa um buffer de memória para resolver os problemas de cintilação associados a várias operações de pintura. Quando o buffer duplo estiver habilitado, todas as operações de pintura serão renderizadas primeiro em um buffer de memória, em vez de na superfície de desenho na tela. Depois que todas as operações de pintura estiverem concluídas, o buffer de memória será copiado diretamente para a superfície de desenho associada a ele. Uma vez que somente uma operação gráfica é executada na tela, a cintilação de imagem associada a operações de pintura complexas é eliminada.  
  
## <a name="default-double-buffering"></a>Buffer duplo padrão  
 A maneira mais fácil de usar buffer duplo em seus aplicativos é usar o buffer duplo padrão para formulários e controles que o .NET Framework fornece. Você pode habilitar padrão dupla de buffer para o Windows Forms e autoria de controles do Windows, definindo o <xref:System.Windows.Forms.Control.DoubleBuffered%2A> propriedade `true` ou usando o <xref:System.Windows.Forms.Control.SetStyle%2A> método. Para obter mais informações, confira [Como reduzir a cintilação em elementos gráficos com buffers duplos para formulários e controles](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md).  
  
## <a name="manually-managing-buffered-graphics"></a>Gerenciando elementos gráficos em buffer manualmente  
 Para cenários de buffer duplo mais avançados, como animação ou gerenciamento avançado de memória, você pode usar as classes do .NET Framework para implementar sua própria lógica de buffer duplo. A classe responsável por alocar e gerenciar os buffers de gráficos individuais é o <xref:System.Drawing.BufferedGraphicsContext> classe. Cada domínio de aplicativo tem seu próprio padrão <xref:System.Drawing.BufferedGraphicsContext> instância que gerencia todos o padrão duplo de buffer para o aplicativo. Na maioria dos casos haverá apenas um domínio de aplicativo por aplicativo, portanto, geralmente é um padrão <xref:System.Drawing.BufferedGraphicsContext> por aplicativo. Padrão <xref:System.Drawing.BufferedGraphicsContext> instâncias são gerenciadas pelo <xref:System.Drawing.BufferedGraphicsManager> classe. Você pode recuperar uma referência para o padrão <xref:System.Drawing.BufferedGraphicsContext> instância chamando o <xref:System.Drawing.BufferedGraphicsManager.Current%2A>. Você também pode criar um dedicado <xref:System.Drawing.BufferedGraphicsContext> instância, o que pode melhorar o desempenho de aplicativos com muitos elementos gráficos. Para obter informações sobre como criar um <xref:System.Drawing.BufferedGraphicsContext> da instância, consulte [como: manualmente gerenciar gráficos em buffer](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).  
  
## <a name="manually-displaying-buffered-graphics"></a>Exibindo elementos gráficos em buffer manualmente  
 Você pode usar uma instância do <xref:System.Drawing.BufferedGraphicsContext> classe para criar os buffers de gráficos, chamando o <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A?displayProperty=nameWithType>, que retorna uma instância do <xref:System.Drawing.BufferedGraphics> classe. Um <xref:System.Drawing.BufferedGraphics> objeto gerencia um buffer de memória que está associado uma superfície de renderização, como um formulário ou controle.  
  
 Depois que ele é instanciado, a <xref:System.Drawing.BufferedGraphics> classe gerencia o processamento para um buffer de gráficos na memória. Você pode renderizar elementos gráficos para o buffer de memória por meio de <xref:System.Drawing.BufferedGraphics.Graphics%2A>, que expõe um <xref:System.Drawing.Graphics> objeto que representa diretamente o buffer de memória. Você pode pintar a este <xref:System.Drawing.Graphics> objeto exatamente como você faria para um <xref:System.Drawing.Graphics> objeto que representa um superfície de desenho. Depois que todos os elementos gráficos foram emitidos para o buffer, você pode usar o <xref:System.Drawing.BufferedGraphics.Render%2A?displayProperty=nameWithType> para copiar o conteúdo do buffer para a superfície de desenho na tela.  
  
 Para obter mais informações sobre como usar o <xref:System.Drawing.BufferedGraphics> de classe, consulte [manualmente renderização de gráficos em buffer](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md). Para obter mais informações sobre a renderização de gráficos, consulte [Elementos gráficos e desenho nos Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.BufferedGraphics>  
 <xref:System.Drawing.BufferedGraphicsContext>  
 <xref:System.Drawing.BufferedGraphicsManager>  
 [Como Renderizar Elementos Gráficos em Buffer Manualmente](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)  
 [Como Reduzir a Cintilação em Elementos Gráficos com Buffers Duplos em Formulários e Controles](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 [Como Gerenciar Elementos Gráficos em Buffer Manualmente](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)  
 [Elementos Gráficos e Desenho nos Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
