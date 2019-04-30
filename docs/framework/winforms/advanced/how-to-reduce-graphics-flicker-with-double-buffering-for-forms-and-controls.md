---
title: 'Como: reduzir a cintilação em elementos gráficos com buffers duplos em formulários e controles'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: ef05b72b33d3f28d1811389dfae65554a1567d43
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967122"
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a><span data-ttu-id="09301-102">Como: reduzir a cintilação em elementos gráficos com buffers duplos em formulários e controles</span><span class="sxs-lookup"><span data-stu-id="09301-102">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>
<span data-ttu-id="09301-103">O buffer duplo usa um buffer de memória para resolver os problemas de cintilação associados a várias operações de pintura.</span><span class="sxs-lookup"><span data-stu-id="09301-103">Double buffering uses a memory buffer to address the flicker problems associated with multiple paint operations.</span></span> <span data-ttu-id="09301-104">Quando o buffer duplo estiver habilitado, todas as operações de pintura serão renderizadas primeiro em um buffer de memória, em vez de na superfície de desenho na tela.</span><span class="sxs-lookup"><span data-stu-id="09301-104">When double buffering is enabled, all paint operations are first rendered to a memory buffer instead of the drawing surface on the screen.</span></span> <span data-ttu-id="09301-105">Depois que todas as operações de pintura estiverem concluídas, o buffer de memória será copiado diretamente para a superfície de desenho associada a ele.</span><span class="sxs-lookup"><span data-stu-id="09301-105">After all paint operations are completed, the memory buffer is copied directly to the drawing surface associated with it.</span></span> <span data-ttu-id="09301-106">Como apenas uma operação de elemento gráfico é executada na tela, a cintilação da imagem associada a operações de pintura complexas é eliminada. Para a maioria dos aplicativos, o buffer duplo padrão fornecido pelo [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] oferecerá os melhores resultados.</span><span class="sxs-lookup"><span data-stu-id="09301-106">Because only one graphics operation is performed on the screen, the image flickering associated with complex painting operations is eliminated.For most applications, the default double buffering provided by the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] will provide the best results.</span></span> <span data-ttu-id="09301-107">Controles padrão dos Windows Forms são buffers duplos por padrão.</span><span class="sxs-lookup"><span data-stu-id="09301-107">Standard Windows Forms controls are double buffered by default.</span></span> <span data-ttu-id="09301-108">Você pode habilitar o buffer duplo padrão em seus formulários e controles criados de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="09301-108">You can enable default double buffering in your forms and authored controls in two ways.</span></span> <span data-ttu-id="09301-109">Você pode definir as <xref:System.Windows.Forms.Control.DoubleBuffered%2A> propriedade para `true`, ou você pode chamar o <xref:System.Windows.Forms.Control.SetStyle%2A> método para definir a <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> sinalizador como `true`.</span><span class="sxs-lookup"><span data-stu-id="09301-109">You can either set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`, or you can call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span> <span data-ttu-id="09301-110">Ambos os métodos habilitarão o buffer duplo padrão para o formulário ou controle e fornecerão a renderização de gráficos sem cintilações.</span><span class="sxs-lookup"><span data-stu-id="09301-110">Both methods will enable default double buffering for your form or control and provide flicker-free graphics rendering.</span></span> <span data-ttu-id="09301-111">Chamar o <xref:System.Windows.Forms.Control.SetStyle%2A> método é recomendado somente para controles personalizados para o qual você tenha escrito o código de renderização.</span><span class="sxs-lookup"><span data-stu-id="09301-111">Calling the <xref:System.Windows.Forms.Control.SetStyle%2A> method is recommended only for custom controls for which you have written all the rendering code.</span></span>  
  
 <span data-ttu-id="09301-112">Para cenários de buffer duplo mais avançados, como animação ou gerenciamento avançado de memória, você pode implementar sua própria lógica de buffer duplo.</span><span class="sxs-lookup"><span data-stu-id="09301-112">For more advanced double buffering scenarios, such as animation or advanced memory management, you can implement your own double buffering logic.</span></span> <span data-ttu-id="09301-113">Para obter mais informações, confira [Como: Gerenciar elementos gráficos em buffer manualmente](how-to-manually-manage-buffered-graphics.md).</span><span class="sxs-lookup"><span data-stu-id="09301-113">For more information, see [How to: Manually Manage Buffered Graphics](how-to-manually-manage-buffered-graphics.md).</span></span>  
  
### <a name="to-reduce-flicker"></a><span data-ttu-id="09301-114">Para reduzir a cintilação</span><span class="sxs-lookup"><span data-stu-id="09301-114">To reduce flicker</span></span>  
  
- <span data-ttu-id="09301-115">Defina a propriedade <xref:System.Windows.Forms.Control.DoubleBuffered%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="09301-115">Set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 <span data-ttu-id="09301-116">\- ou -</span><span class="sxs-lookup"><span data-stu-id="09301-116">\- or -</span></span>  
  
- <span data-ttu-id="09301-117">Chame o <xref:System.Windows.Forms.Control.SetStyle%2A> método para definir o <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> sinalizador como `true`.</span><span class="sxs-lookup"><span data-stu-id="09301-117">Call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="09301-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09301-118">See also</span></span>

- <xref:System.Windows.Forms.Control.DoubleBuffered%2A>
- <xref:System.Windows.Forms.Control.SetStyle%2A>
- [<span data-ttu-id="09301-119">Elementos Gráficos em Buffer Duplo</span><span class="sxs-lookup"><span data-stu-id="09301-119">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="09301-120">Elementos Gráficos e Desenho nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="09301-120">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
