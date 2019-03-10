---
title: 'Como: Exibir guias alinhadas lateralmente com TabControl'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tab pages [Windows Forms], displaying side-aligned tabs
- tabs [Windows Forms], displaying side-aligned tabs
- TabControl control [Windows Forms], displaying side-aligned tabs
ms.assetid: 110d5abd-3ae3-4ded-95bf-778aaac798a0
ms.openlocfilehash: 8715cb1a1f0d5795afc4003afcecdb3fb89912c3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705176"
---
# <a name="how-to-display-side-aligned-tabs-with-tabcontrol"></a><span data-ttu-id="fe763-102">Como: Exibir guias alinhadas lateralmente com TabControl</span><span class="sxs-lookup"><span data-stu-id="fe763-102">How to: Display Side-Aligned Tabs with TabControl</span></span>
<span data-ttu-id="fe763-103">O <xref:System.Windows.Forms.TabControl.Alignment%2A> propriedade de <xref:System.Windows.Forms.TabControl> dá suporte à exibição de guias verticalmente (na borda esquerda ou direita do controle), em vez de horizontalmente (na parte superior ou inferior do controle).</span><span class="sxs-lookup"><span data-stu-id="fe763-103">The <xref:System.Windows.Forms.TabControl.Alignment%2A> property of <xref:System.Windows.Forms.TabControl> supports displaying tabs vertically (along the left or right edge of the control), as opposed to horizontally (across the top or bottom of the control).</span></span> <span data-ttu-id="fe763-104">Por padrão, essa exibição vertical resulta em uma experiência de usuário ruim, porque o <xref:System.Windows.Forms.TabPage.Text%2A> propriedade do <xref:System.Windows.Forms.TabPage> objeto não exibe na guia de quando estilos visuais estiverem habilitados.</span><span class="sxs-lookup"><span data-stu-id="fe763-104">By default, this vertical display results in a poor user experience, because the <xref:System.Windows.Forms.TabPage.Text%2A> property of the <xref:System.Windows.Forms.TabPage> object does not display in the tab when visual styles are enabled.</span></span> <span data-ttu-id="fe763-105">Também não há nenhuma maneira direta de controlar a direção do texto dentro da guia. Você pode usar o proprietário traçam <xref:System.Windows.Forms.TabControl> para aprimorar essa experiência.</span><span class="sxs-lookup"><span data-stu-id="fe763-105">There is also no direct way to control the direction of the text within the tab. You can use owner draw on <xref:System.Windows.Forms.TabControl> to improve this experience.</span></span>  
  
 <span data-ttu-id="fe763-106">O procedimento a seguir mostra como renderizar guias alinhadas à direita, com o texto da guia indo da esquerda para a direita, usando o recurso de “desenho do proprietário”.</span><span class="sxs-lookup"><span data-stu-id="fe763-106">The following procedure shows how to render right-aligned tabs, with the tab text running from left to right, by using the "owner draw" feature.</span></span>  
  
### <a name="to-display-right-aligned-tabs"></a><span data-ttu-id="fe763-107">Exibir guias alinhadas à direita</span><span class="sxs-lookup"><span data-stu-id="fe763-107">To display right-aligned tabs</span></span>  
  
1.  <span data-ttu-id="fe763-108">Adicionar um <xref:System.Windows.Forms.TabControl> ao seu formulário.</span><span class="sxs-lookup"><span data-stu-id="fe763-108">Add a <xref:System.Windows.Forms.TabControl> to your form.</span></span>  
  
2.  <span data-ttu-id="fe763-109">Defina a propriedade <xref:System.Windows.Forms.TabControl.Alignment%2A> como <xref:System.Windows.Forms.TabAlignment.Right>.</span><span class="sxs-lookup"><span data-stu-id="fe763-109">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property to <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
3.  <span data-ttu-id="fe763-110">Defina as <xref:System.Windows.Forms.TabControl.SizeMode%2A> propriedade para <xref:System.Windows.Forms.TabSizeMode.Fixed>, de modo que todas as guias têm a mesma largura.</span><span class="sxs-lookup"><span data-stu-id="fe763-110">Set the <xref:System.Windows.Forms.TabControl.SizeMode%2A> property to <xref:System.Windows.Forms.TabSizeMode.Fixed>, so that all tabs are the same width.</span></span>  
  
4.  <span data-ttu-id="fe763-111">Defina o <xref:System.Windows.Forms.TabControl.ItemSize%2A> tamanho para as guias de fixo de propriedade para o preferencial.</span><span class="sxs-lookup"><span data-stu-id="fe763-111">Set the <xref:System.Windows.Forms.TabControl.ItemSize%2A> property to the preferred fixed size for the tabs.</span></span> <span data-ttu-id="fe763-112">Tenha em mente que o <xref:System.Windows.Forms.TabControl.ItemSize%2A> propriedade se comporta como se foram de guias na parte superior, embora sejam alinhadas à direita.</span><span class="sxs-lookup"><span data-stu-id="fe763-112">Keep in mind that the <xref:System.Windows.Forms.TabControl.ItemSize%2A> property behaves as though the tabs were on top, although they are right-aligned.</span></span> <span data-ttu-id="fe763-113">Como resultado, para tornar as guias mais largas, você deve alterar o <xref:System.Drawing.Size.Height%2A> propriedade, e para torná-las mais alto, você deve alterar o <xref:System.Drawing.Size.Width%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="fe763-113">As a result, in order to make the tabs wider, you must change the <xref:System.Drawing.Size.Height%2A> property, and in order to make them taller, you must change the <xref:System.Drawing.Size.Width%2A> property.</span></span>  
  
     <span data-ttu-id="fe763-114">Para obter melhor resultado com o exemplo de código abaixo, defina as <xref:System.Drawing.Size.Width%2A> das guias para 25 e o <xref:System.Drawing.Size.Height%2A> a 100.</span><span class="sxs-lookup"><span data-stu-id="fe763-114">For best result with the code example below, set the <xref:System.Drawing.Size.Width%2A> of the tabs to 25 and the <xref:System.Drawing.Size.Height%2A> to 100.</span></span>  
  
5.  <span data-ttu-id="fe763-115">Defina a propriedade <xref:System.Windows.Forms.TabControl.DrawMode%2A> como <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.</span><span class="sxs-lookup"><span data-stu-id="fe763-115">Set the <xref:System.Windows.Forms.TabControl.DrawMode%2A> property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.</span></span>  
  
6.  <span data-ttu-id="fe763-116">Definir um manipulador para o <xref:System.Windows.Forms.TabControl.DrawItem> eventos de <xref:System.Windows.Forms.TabControl> que renderiza o texto da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="fe763-116">Define a handler for the <xref:System.Windows.Forms.TabControl.DrawItem> event of <xref:System.Windows.Forms.TabControl> that renders the text from left to right.</span></span>  
  
     [!code-csharp[TabControl.RightAlignedTabs#1](~/samples/snippets/csharp/VS_Snippets_Winforms/TabControl.RightAlignedTabs/CS/Form1.cs#1)]
     [!code-vb[TabControl.RightAlignedTabs#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/TabControl.RightAlignedTabs/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fe763-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe763-117">See also</span></span>
- [<span data-ttu-id="fe763-118">Controle TabControl</span><span class="sxs-lookup"><span data-stu-id="fe763-118">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
