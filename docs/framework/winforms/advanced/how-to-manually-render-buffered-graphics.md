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
# <a name="how-to-manually-render-buffered-graphics"></a><span data-ttu-id="08db2-102">Como: Renderizar elementos gráficos em buffer manualmente</span><span class="sxs-lookup"><span data-stu-id="08db2-102">How to: Manually Render Buffered Graphics</span></span>
<span data-ttu-id="08db2-103">Se você gerenciar seus próprios elementos gráficos em buffer, precisará ser capaz de criar e renderizar buffers gráficos.</span><span class="sxs-lookup"><span data-stu-id="08db2-103">If you are managing your own buffered graphics, you will need to be able to create and render graphics buffers.</span></span> <span data-ttu-id="08db2-104">Você pode criar instâncias do <xref:System.Drawing.BufferedGraphics> classe que está associado com superfícies de desenho na tela chamando o <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> método.</span><span class="sxs-lookup"><span data-stu-id="08db2-104">You can create instances of the <xref:System.Drawing.BufferedGraphics> class that is associated with drawing surfaces on your screen by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method.</span></span> <span data-ttu-id="08db2-105">Esse método cria um <xref:System.Drawing.BufferedGraphics> instância que está associada uma superfície de renderização específica, como um formulário ou controle.</span><span class="sxs-lookup"><span data-stu-id="08db2-105">This method creates a <xref:System.Drawing.BufferedGraphics> instance that is associated with a particular rendering surface, such as a form or control.</span></span> <span data-ttu-id="08db2-106">Depois de criar uma <xref:System.Drawing.BufferedGraphics> instância, você pode desenhar gráficos no buffer que ele representa usando o <xref:System.Drawing.BufferedGraphics.Graphics%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="08db2-106">After you have created a <xref:System.Drawing.BufferedGraphics> instance, you can draw graphics to the buffer it represents through the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="08db2-107">Depois de realizar todas as operações de gráficos, você pode copiar o conteúdo do buffer para a tela chamando o <xref:System.Drawing.BufferedGraphics.Render%2A> método.</span><span class="sxs-lookup"><span data-stu-id="08db2-107">After you have performed all graphics operations, you can copy the contents of the buffer to the screen by calling the <xref:System.Drawing.BufferedGraphics.Render%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08db2-108">Se você executar sua própria renderização, o consumo de memória aumentará, embora o aumento possa ser pequeno.</span><span class="sxs-lookup"><span data-stu-id="08db2-108">If you perform your own rendering, memory consumption will increase, though the increase may only be slight.</span></span>  
  
### <a name="to-manually-display-buffered-graphics"></a><span data-ttu-id="08db2-109">Exibir elementos gráficos em buffer manualmente</span><span class="sxs-lookup"><span data-stu-id="08db2-109">To manually display buffered graphics</span></span>  
  
1.  <span data-ttu-id="08db2-110">Obtenha uma referência a uma instância da <xref:System.Drawing.BufferedGraphicsContext> classe.</span><span class="sxs-lookup"><span data-stu-id="08db2-110">Obtain a reference to an instance of the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="08db2-111">Para obter mais informações, confira [Como: Gerenciar elementos gráficos em buffer manualmente](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).</span><span class="sxs-lookup"><span data-stu-id="08db2-111">For more information, see [How to: Manually Manage Buffered Graphics](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).</span></span>  
  
2.  <span data-ttu-id="08db2-112">Criar uma instância das <xref:System.Drawing.BufferedGraphics> classe chamando o <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> método, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="08db2-112">Create an instance of the <xref:System.Drawing.BufferedGraphics> class by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3.  <span data-ttu-id="08db2-113">Desenhar gráficos no buffer gráfico Configurando a <xref:System.Drawing.BufferedGraphics.Graphics%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="08db2-113">Draw graphics to the graphics buffer by setting the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="08db2-114">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="08db2-114">For example:</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4.  <span data-ttu-id="08db2-115">Quando você tiver concluído todas as suas operações de desenho no buffer gráfico, chame o <xref:System.Drawing.BufferedGraphics.Render%2A> método para renderizar o buffer, seja para a superfície de desenho associada a esse buffer ou a uma superfície de desenho especificada, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="08db2-115">When you have completed all of your drawing operations to the graphics buffer, call the <xref:System.Drawing.BufferedGraphics.Render%2A> method to render the buffer, either to the drawing surface associated with that buffer, or to a specified drawing surface, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5.  <span data-ttu-id="08db2-116">Depois de terminar de processamento de gráficos, chame o `Dispose` método no <xref:System.Drawing.BufferedGraphics> instância para liberar recursos do sistema.</span><span class="sxs-lookup"><span data-stu-id="08db2-116">After you are finished rendering graphics, call the `Dispose` method on the <xref:System.Drawing.BufferedGraphics> instance to free system resources.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a><span data-ttu-id="08db2-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08db2-117">See also</span></span>
- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphics>
- [<span data-ttu-id="08db2-118">Elementos Gráficos em Buffer Duplo</span><span class="sxs-lookup"><span data-stu-id="08db2-118">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)
- [<span data-ttu-id="08db2-119">Como: Gerenciar elementos gráficos em buffer manualmente</span><span class="sxs-lookup"><span data-stu-id="08db2-119">How to: Manually Manage Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)
