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
# <a name="how-to-manually-render-buffered-graphics"></a><span data-ttu-id="e5a3f-102">Como: renderizar elementos gráficos em buffer manualmente</span><span class="sxs-lookup"><span data-stu-id="e5a3f-102">How to: Manually Render Buffered Graphics</span></span>
<span data-ttu-id="e5a3f-103">Se você gerenciar seus próprios elementos gráficos em buffer, precisará ser capaz de criar e renderizar buffers gráficos.</span><span class="sxs-lookup"><span data-stu-id="e5a3f-103">If you are managing your own buffered graphics, you will need to be able to create and render graphics buffers.</span></span> <span data-ttu-id="e5a3f-104">Você pode criar instâncias da <xref:System.Drawing.BufferedGraphics> classe que está associada a superfícies de desenho na tela chamando o <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> método.</span><span class="sxs-lookup"><span data-stu-id="e5a3f-104">You can create instances of the <xref:System.Drawing.BufferedGraphics> class that is associated with drawing surfaces on your screen by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method.</span></span> <span data-ttu-id="e5a3f-105">Esse método cria uma <xref:System.Drawing.BufferedGraphics> instância associada a uma determinada superfície de renderização, como um formulário ou controle.</span><span class="sxs-lookup"><span data-stu-id="e5a3f-105">This method creates a <xref:System.Drawing.BufferedGraphics> instance that is associated with a particular rendering surface, such as a form or control.</span></span> <span data-ttu-id="e5a3f-106">Depois de criar uma <xref:System.Drawing.BufferedGraphics> instância, você pode desenhar gráficos para o buffer que ele representa por meio da <xref:System.Drawing.BufferedGraphics.Graphics%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="e5a3f-106">After you have created a <xref:System.Drawing.BufferedGraphics> instance, you can draw graphics to the buffer it represents through the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="e5a3f-107">Depois de executar todas as operações de gráficos, você pode copiar o conteúdo do buffer na tela chamando o <xref:System.Drawing.BufferedGraphics.Render%2A> método.</span><span class="sxs-lookup"><span data-stu-id="e5a3f-107">After you have performed all graphics operations, you can copy the contents of the buffer to the screen by calling the <xref:System.Drawing.BufferedGraphics.Render%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5a3f-108">Se você executar sua própria renderização, o consumo de memória aumentará, embora o aumento possa ser pequeno.</span><span class="sxs-lookup"><span data-stu-id="e5a3f-108">If you perform your own rendering, memory consumption will increase, though the increase may only be slight.</span></span>  
  
### <a name="to-manually-display-buffered-graphics"></a><span data-ttu-id="e5a3f-109">Exibir elementos gráficos em buffer manualmente</span><span class="sxs-lookup"><span data-stu-id="e5a3f-109">To manually display buffered graphics</span></span>  
  
1. <span data-ttu-id="e5a3f-110">Obtenha uma referência a uma instância da <xref:System.Drawing.BufferedGraphicsContext> classe.</span><span class="sxs-lookup"><span data-stu-id="e5a3f-110">Obtain a reference to an instance of the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="e5a3f-111">Para obter mais informações, confira [Como: Gerencie manualmente os gráficos](how-to-manually-manage-buffered-graphics.md)em buffer.</span><span class="sxs-lookup"><span data-stu-id="e5a3f-111">For more information, see [How to: Manually Manage Buffered Graphics](how-to-manually-manage-buffered-graphics.md).</span></span>  
  
2. <span data-ttu-id="e5a3f-112">Crie uma instância da <xref:System.Drawing.BufferedGraphics> classe chamando o <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> método, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e5a3f-112">Create an instance of the <xref:System.Drawing.BufferedGraphics> class by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3. <span data-ttu-id="e5a3f-113">Desenhe gráficos para o buffer de gráficos definindo a <xref:System.Drawing.BufferedGraphics.Graphics%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="e5a3f-113">Draw graphics to the graphics buffer by setting the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="e5a3f-114">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e5a3f-114">For example:</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4. <span data-ttu-id="e5a3f-115">Quando você tiver concluído todas as suas operações de desenho para o buffer de gráficos, <xref:System.Drawing.BufferedGraphics.Render%2A> chame o método para renderizar o buffer, seja para a superfície de desenho associada a esse buffer ou para uma superfície de desenho especificada, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e5a3f-115">When you have completed all of your drawing operations to the graphics buffer, call the <xref:System.Drawing.BufferedGraphics.Render%2A> method to render the buffer, either to the drawing surface associated with that buffer, or to a specified drawing surface, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5. <span data-ttu-id="e5a3f-116">Depois de terminar de renderizar os gráficos, `Dispose` chame o método <xref:System.Drawing.BufferedGraphics> na instância para liberar recursos do sistema.</span><span class="sxs-lookup"><span data-stu-id="e5a3f-116">After you are finished rendering graphics, call the `Dispose` method on the <xref:System.Drawing.BufferedGraphics> instance to free system resources.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a><span data-ttu-id="e5a3f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5a3f-117">See also</span></span>

- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphics>
- [<span data-ttu-id="e5a3f-118">Elementos Gráficos em Buffer Duplo</span><span class="sxs-lookup"><span data-stu-id="e5a3f-118">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="e5a3f-119">Como: Gerenciar manualmente gráficos em buffer</span><span class="sxs-lookup"><span data-stu-id="e5a3f-119">How to: Manually Manage Buffered Graphics</span></span>](how-to-manually-manage-buffered-graphics.md)
