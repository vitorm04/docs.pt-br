---
title: "Como reduzir a cintilação em elementos gráficos com buffers duplos para formulários e controles"
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
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc782ba262527a319cbb05cc6d36ca568afc55c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a><span data-ttu-id="4800c-102">Como reduzir a cintilação em elementos gráficos com buffers duplos para formulários e controles</span><span class="sxs-lookup"><span data-stu-id="4800c-102">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>
<span data-ttu-id="4800c-103">O buffer duplo usa um buffer de memória para resolver os problemas de cintilação associados a várias operações de pintura.</span><span class="sxs-lookup"><span data-stu-id="4800c-103">Double buffering uses a memory buffer to address the flicker problems associated with multiple paint operations.</span></span> <span data-ttu-id="4800c-104">Quando o buffer duplo estiver habilitado, todas as operações de pintura serão renderizadas primeiro em um buffer de memória, em vez de na superfície de desenho na tela.</span><span class="sxs-lookup"><span data-stu-id="4800c-104">When double buffering is enabled, all paint operations are first rendered to a memory buffer instead of the drawing surface on the screen.</span></span> <span data-ttu-id="4800c-105">Depois que todas as operações de pintura estiverem concluídas, o buffer de memória será copiado diretamente para a superfície de desenho associada a ele.</span><span class="sxs-lookup"><span data-stu-id="4800c-105">After all paint operations are completed, the memory buffer is copied directly to the drawing surface associated with it.</span></span> <span data-ttu-id="4800c-106">Como apenas uma operação de elemento gráfico é executada na tela, a cintilação da imagem associada a operações de pintura complexas é eliminada. Para a maioria dos aplicativos, o buffer duplo padrão fornecido pelo [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] oferecerá os melhores resultados.</span><span class="sxs-lookup"><span data-stu-id="4800c-106">Because only one graphics operation is performed on the screen, the image flickering associated with complex painting operations is eliminated.For most applications, the default double buffering provided by the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] will provide the best results.</span></span> <span data-ttu-id="4800c-107">Controles padrão dos Windows Forms são buffers duplos por padrão.</span><span class="sxs-lookup"><span data-stu-id="4800c-107">Standard Windows Forms controls are double buffered by default.</span></span> <span data-ttu-id="4800c-108">Você pode habilitar o buffer duplo padrão em seus formulários e controles criados de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="4800c-108">You can enable default double buffering in your forms and authored controls in two ways.</span></span> <span data-ttu-id="4800c-109">Você pode definir o <xref:System.Windows.Forms.Control.DoubleBuffered%2A> propriedade `true`, ou você pode chamar o <xref:System.Windows.Forms.Control.SetStyle%2A> método para definir o <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> sinalizador como `true`.</span><span class="sxs-lookup"><span data-stu-id="4800c-109">You can either set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`, or you can call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span> <span data-ttu-id="4800c-110">Ambos os métodos habilitarão o buffer duplo padrão para o formulário ou controle e fornecerão a renderização de gráficos sem cintilações.</span><span class="sxs-lookup"><span data-stu-id="4800c-110">Both methods will enable default double buffering for your form or control and provide flicker-free graphics rendering.</span></span> <span data-ttu-id="4800c-111">Chamar o <xref:System.Windows.Forms.Control.SetStyle%2A> método é recomendado apenas para controles personalizados para os quais você gravou todo o código de renderização.</span><span class="sxs-lookup"><span data-stu-id="4800c-111">Calling the <xref:System.Windows.Forms.Control.SetStyle%2A> method is recommended only for custom controls for which you have written all the rendering code.</span></span>  
  
 <span data-ttu-id="4800c-112">Para cenários de buffer duplo mais avançados, como animação ou gerenciamento avançado de memória, você pode implementar sua própria lógica de buffer duplo.</span><span class="sxs-lookup"><span data-stu-id="4800c-112">For more advanced double buffering scenarios, such as animation or advanced memory management, you can implement your own double buffering logic.</span></span> <span data-ttu-id="4800c-113">Para obter mais informações, consulte [Como gerenciar elementos gráficos em buffer manualmente](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).</span><span class="sxs-lookup"><span data-stu-id="4800c-113">For more information, see [How to: Manually Manage Buffered Graphics](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).</span></span>  
  
### <a name="to-reduce-flicker"></a><span data-ttu-id="4800c-114">Para reduzir a cintilação</span><span class="sxs-lookup"><span data-stu-id="4800c-114">To reduce flicker</span></span>  
  
-   <span data-ttu-id="4800c-115">Defina a propriedade <xref:System.Windows.Forms.Control.DoubleBuffered%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="4800c-115">Set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 <span data-ttu-id="4800c-116">\- ou -</span><span class="sxs-lookup"><span data-stu-id="4800c-116">\- or -</span></span>  
  
-   <span data-ttu-id="4800c-117">Chamar o <xref:System.Windows.Forms.Control.SetStyle%2A> método para definir o <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> sinalizador como `true`.</span><span class="sxs-lookup"><span data-stu-id="4800c-117">Call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="4800c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4800c-118">See Also</span></span>  
 <xref:System.Windows.Forms.Control.DoubleBuffered%2A>  
 <xref:System.Windows.Forms.Control.SetStyle%2A>  
 [<span data-ttu-id="4800c-119">Elementos Gráficos em Buffer Duplo</span><span class="sxs-lookup"><span data-stu-id="4800c-119">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [<span data-ttu-id="4800c-120">Elementos Gráficos e Desenho nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4800c-120">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
