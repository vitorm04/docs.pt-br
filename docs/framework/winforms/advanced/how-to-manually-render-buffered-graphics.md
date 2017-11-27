---
title: "Como renderizar elementos gráficos em buffer manualmente"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually rendering graphics
- graphics [Windows Forms], rendering
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8fd742e7fa2b7870b8988e889a0df2b18a240bd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-manually-render-buffered-graphics"></a><span data-ttu-id="a7ea9-102">Como renderizar elementos gráficos em buffer manualmente</span><span class="sxs-lookup"><span data-stu-id="a7ea9-102">How to: Manually Render Buffered Graphics</span></span>
<span data-ttu-id="a7ea9-103">Se você gerenciar seus próprios elementos gráficos em buffer, precisará ser capaz de criar e renderizar buffers gráficos.</span><span class="sxs-lookup"><span data-stu-id="a7ea9-103">If you are managing your own buffered graphics, you will need to be able to create and render graphics buffers.</span></span> <span data-ttu-id="a7ea9-104">Você pode criar instâncias da <xref:System.Drawing.BufferedGraphics> classe associada com superfícies de desenho na tela chamando o <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> método.</span><span class="sxs-lookup"><span data-stu-id="a7ea9-104">You can create instances of the <xref:System.Drawing.BufferedGraphics> class that is associated with drawing surfaces on your screen by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method.</span></span> <span data-ttu-id="a7ea9-105">Esse método cria um <xref:System.Drawing.BufferedGraphics> instância que está associada uma superfície de renderização específico, como um formulário ou controle.</span><span class="sxs-lookup"><span data-stu-id="a7ea9-105">This method creates a <xref:System.Drawing.BufferedGraphics> instance that is associated with a particular rendering surface, such as a form or control.</span></span> <span data-ttu-id="a7ea9-106">Depois de ter criado um <xref:System.Drawing.BufferedGraphics> instância, você pode desenhar gráficos ao buffer representa por meio de <xref:System.Drawing.BufferedGraphics.Graphics%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a7ea9-106">After you have created a <xref:System.Drawing.BufferedGraphics> instance, you can draw graphics to the buffer it represents through the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="a7ea9-107">Depois que você executou todas as operações de gráficos, você pode copiar o conteúdo do buffer para a tela chamando o <xref:System.Drawing.BufferedGraphics.Render%2A> método.</span><span class="sxs-lookup"><span data-stu-id="a7ea9-107">After you have performed all graphics operations, you can copy the contents of the buffer to the screen by calling the <xref:System.Drawing.BufferedGraphics.Render%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7ea9-108">Se você executar sua própria renderização, o consumo de memória aumentará, embora o aumento possa ser pequeno.</span><span class="sxs-lookup"><span data-stu-id="a7ea9-108">If you perform your own rendering, memory consumption will increase, though the increase may only be slight.</span></span>  
  
### <a name="to-manually-display-buffered-graphics"></a><span data-ttu-id="a7ea9-109">Exibir elementos gráficos em buffer manualmente</span><span class="sxs-lookup"><span data-stu-id="a7ea9-109">To manually display buffered graphics</span></span>  
  
1.  <span data-ttu-id="a7ea9-110">Obter uma referência a uma instância do <xref:System.Drawing.BufferedGraphicsContext> classe.</span><span class="sxs-lookup"><span data-stu-id="a7ea9-110">Obtain a reference to an instance of the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="a7ea9-111">Para obter mais informações, consulte [Como gerenciar elementos gráficos em buffer manualmente](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).</span><span class="sxs-lookup"><span data-stu-id="a7ea9-111">For more information, see [How to: Manually Manage Buffered Graphics](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).</span></span>  
  
2.  <span data-ttu-id="a7ea9-112">Criar uma instância do <xref:System.Drawing.BufferedGraphics> classe chamando o <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> método, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a7ea9-112">Create an instance of the <xref:System.Drawing.BufferedGraphics> class by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3.  <span data-ttu-id="a7ea9-113">Desenhar gráficos para o buffer de gráficos, definindo o <xref:System.Drawing.BufferedGraphics.Graphics%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a7ea9-113">Draw graphics to the graphics buffer by setting the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="a7ea9-114">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a7ea9-114">For example:</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4.  <span data-ttu-id="a7ea9-115">Quando você concluiu todas as operações de desenho ao buffer de gráfico, chame o <xref:System.Drawing.BufferedGraphics.Render%2A> método para renderizar o buffer, seja para a superfície de desenho associada a esse buffer, ou a uma superfície de desenho especificada, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a7ea9-115">When you have completed all of your drawing operations to the graphics buffer, call the <xref:System.Drawing.BufferedGraphics.Render%2A> method to render the buffer, either to the drawing surface associated with that buffer, or to a specified drawing surface, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5.  <span data-ttu-id="a7ea9-116">Depois de terminar de processamento de gráficos, chame o `Dispose` método sobre o <xref:System.Drawing.BufferedGraphics> instância para liberar recursos do sistema.</span><span class="sxs-lookup"><span data-stu-id="a7ea9-116">After you are finished rendering graphics, call the `Dispose` method on the <xref:System.Drawing.BufferedGraphics> instance to free system resources.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a><span data-ttu-id="a7ea9-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7ea9-117">See Also</span></span>  
 <xref:System.Drawing.BufferedGraphicsContext>  
 <xref:System.Drawing.BufferedGraphics>  
 [<span data-ttu-id="a7ea9-118">Elementos Gráficos em Buffer Duplo</span><span class="sxs-lookup"><span data-stu-id="a7ea9-118">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [<span data-ttu-id="a7ea9-119">Como Gerenciar Elementos Gráficos em Buffer Manualmente</span><span class="sxs-lookup"><span data-stu-id="a7ea9-119">How to: Manually Manage Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)
