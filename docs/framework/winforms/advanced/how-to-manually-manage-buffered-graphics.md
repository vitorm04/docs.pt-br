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
ms.openlocfilehash: 965e3225f8cf1af6d61b81434089ebacac8ad13a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138665"
---
# <a name="how-to-manually-manage-buffered-graphics"></a><span data-ttu-id="a42cb-102">Como: gerenciar elementos gráficos em buffer manualmente</span><span class="sxs-lookup"><span data-stu-id="a42cb-102">How to: Manually Manage Buffered Graphics</span></span>
<span data-ttu-id="a42cb-103">Para cenários mais avançados de armazenamento em buffer duplos, é possível usar as classes [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para implementar sua própria lógica de buffer duplo.</span><span class="sxs-lookup"><span data-stu-id="a42cb-103">For more advanced double buffering scenarios, you can use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] classes to implement your own double-buffering logic.</span></span> <span data-ttu-id="a42cb-104">A classe responsável por alocar e gerenciar buffers gráficos individuais é o <xref:System.Drawing.BufferedGraphicsContext> classe.</span><span class="sxs-lookup"><span data-stu-id="a42cb-104">The class responsible for allocating and managing individual graphics buffers is the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="a42cb-105">Cada aplicativo tem seu próprio padrão <xref:System.Drawing.BufferedGraphicsContext> que gerencia todo o buffer duplo padrão para esse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a42cb-105">Every application has its own default <xref:System.Drawing.BufferedGraphicsContext> that manages all of the default double buffering for that application.</span></span> <span data-ttu-id="a42cb-106">Você pode recuperar uma referência a essa instância chamando o <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="a42cb-106">You can retrieve a reference to this instance by calling the <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span></span>  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a><span data-ttu-id="a42cb-107">Para obter uma referência para o BufferedGraphicsContext padrão</span><span class="sxs-lookup"><span data-stu-id="a42cb-107">To obtain a reference to the default BufferedGraphicsContext</span></span>  
  
-   <span data-ttu-id="a42cb-108">Defina o <xref:System.Drawing.BufferedGraphicsManager.Current%2A> propriedade, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a42cb-108">Set the <xref:System.Drawing.BufferedGraphicsManager.Current%2A> property, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    >  <span data-ttu-id="a42cb-109">Você não precisará chamar o `Dispose` método na <xref:System.Drawing.BufferedGraphicsContext> referência que você receber o <xref:System.Drawing.BufferedGraphicsManager> classe.</span><span class="sxs-lookup"><span data-stu-id="a42cb-109">You do not need to call the `Dispose` method on the <xref:System.Drawing.BufferedGraphicsContext> reference that you receive from the <xref:System.Drawing.BufferedGraphicsManager> class.</span></span> <span data-ttu-id="a42cb-110">O <xref:System.Drawing.BufferedGraphicsManager> manipula toda a alocação de memória e a distribuição para padrão <xref:System.Drawing.BufferedGraphicsContext> instâncias.</span><span class="sxs-lookup"><span data-stu-id="a42cb-110">The <xref:System.Drawing.BufferedGraphicsManager> handles all of the memory allocation and distribution for default <xref:System.Drawing.BufferedGraphicsContext> instances.</span></span>  
  
     <span data-ttu-id="a42cb-111">Para aplicações graficamente intensas como animação, você pode, às vezes, melhorar o desempenho usando um dedicado <xref:System.Drawing.BufferedGraphicsContext> em vez do <xref:System.Drawing.BufferedGraphicsContext> fornecidas pelo <xref:System.Drawing.BufferedGraphicsManager>.</span><span class="sxs-lookup"><span data-stu-id="a42cb-111">For graphically intensive applications such as animation, you can sometimes improve performance by using a dedicated <xref:System.Drawing.BufferedGraphicsContext> instead of the <xref:System.Drawing.BufferedGraphicsContext> provided by the <xref:System.Drawing.BufferedGraphicsManager>.</span></span> <span data-ttu-id="a42cb-112">Isso permite que você crie e gerencie buffers de gráficos individualmente, sem incorrer na sobrecarga de desempenho de gerenciar todos os outros elementos gráficos em buffer associados à sua aplicação, embora a memória consumida pela aplicação será maior.</span><span class="sxs-lookup"><span data-stu-id="a42cb-112">This enables you to create and manage graphics buffers individually, without incurring the performance overhead of managing all the other buffered graphics associated with your application, though the memory consumed by the application will be greater.</span></span>  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a><span data-ttu-id="a42cb-113">Para criar um BufferedGraphicsContext dedicado</span><span class="sxs-lookup"><span data-stu-id="a42cb-113">To create a dedicated BufferedGraphicsContext</span></span>  
  
-   <span data-ttu-id="a42cb-114">Declare e crie uma nova instância do <xref:System.Drawing.BufferedGraphicsContext> de classe, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a42cb-114">Declare and create a new instance of the <xref:System.Drawing.BufferedGraphicsContext> class, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="a42cb-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a42cb-115">See also</span></span>

- <xref:System.Drawing.BufferedGraphicsContext>
- [<span data-ttu-id="a42cb-116">Elementos gráficos em buffer duplo</span><span class="sxs-lookup"><span data-stu-id="a42cb-116">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="a42cb-117">Como: renderizar elementos gráficos em buffer manualmente</span><span class="sxs-lookup"><span data-stu-id="a42cb-117">How to: Manually Render Buffered Graphics</span></span>](how-to-manually-render-buffered-graphics.md)
