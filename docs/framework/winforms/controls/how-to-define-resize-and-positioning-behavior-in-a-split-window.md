---
title: 'Como: Definir o comportamento de redimensionamento e posicionamento em uma janela dividida'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- split windows [Windows Forms], resizing
- splitter windows [Windows Forms], resizing
- SplitContainer control [Windows Forms], resizing
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
ms.openlocfilehash: 8cdcfdfaa135a92ed6a6e96d4a72de2c97f2493d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328667"
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a><span data-ttu-id="7ff48-102">Como: Definir o comportamento de redimensionamento e posicionamento em uma janela dividida</span><span class="sxs-lookup"><span data-stu-id="7ff48-102">How to: Define Resize and Positioning Behavior in a Split Window</span></span>
<span data-ttu-id="7ff48-103">Os painéis do <xref:System.Windows.Forms.SplitContainer> controle prestam bem ao que está sendo redimensionado e manipulados pelos usuários.</span><span class="sxs-lookup"><span data-stu-id="7ff48-103">The panels of the <xref:System.Windows.Forms.SplitContainer> control lend themselves well to being resized and manipulated by users.</span></span> <span data-ttu-id="7ff48-104">No entanto, há momentos em que é útil controlar o divisor com programação, onde ele está posicionado e em que grau pode ser movido.</span><span class="sxs-lookup"><span data-stu-id="7ff48-104">However, there will be times when you will want to programmatically control the splitter—where it is positioned and to what degree it can be moved.</span></span>  
  
 <span data-ttu-id="7ff48-105">O <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> propriedade e outras propriedades no <xref:System.Windows.Forms.SplitContainer> controle oferecem um controle preciso sobre o comportamento da interface do usuário para atender às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="7ff48-105">The <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property and the other properties on the <xref:System.Windows.Forms.SplitContainer> control give you precise control over the behavior of your user interface to suit your needs.</span></span> <span data-ttu-id="7ff48-106">Tais propriedades são listadas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="7ff48-106">These properties are listed in the following table.</span></span>  
  
|<span data-ttu-id="7ff48-107">Nome</span><span class="sxs-lookup"><span data-stu-id="7ff48-107">Name</span></span>|<span data-ttu-id="7ff48-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="7ff48-108">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="7ff48-109">Propriedade <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A></span><span class="sxs-lookup"><span data-stu-id="7ff48-109"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> property</span></span>|<span data-ttu-id="7ff48-110">Determina se o divisor pode ser movido com o teclado ou mouse.</span><span class="sxs-lookup"><span data-stu-id="7ff48-110">Determines if the splitter is movable by means of the keyboard or mouse.</span></span>|  
|<span data-ttu-id="7ff48-111">Propriedade <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A></span><span class="sxs-lookup"><span data-stu-id="7ff48-111"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> property</span></span>|<span data-ttu-id="7ff48-112">Determina a distância em pixels da borda esquerda ou superior para o divisor móvel.</span><span class="sxs-lookup"><span data-stu-id="7ff48-112">Determines the distance in pixels from the left or upper edge to the movable splitter bar.</span></span>|  
|<span data-ttu-id="7ff48-113">Propriedade <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A></span><span class="sxs-lookup"><span data-stu-id="7ff48-113"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property</span></span>|<span data-ttu-id="7ff48-114">Determina a distância mínima, em pixels, que o divisor pode ser movido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="7ff48-114">Determines the minimum distance, in pixels, that the splitter can be moved by the user.</span></span>|  
  
 <span data-ttu-id="7ff48-115">O exemplo a seguir modifica o <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> propriedade para criar um efeito de "divisor ajustado"; quando o usuário arrasta o divisor, ele é incrementado em unidades de 10 pixels, em vez do padrão 1.</span><span class="sxs-lookup"><span data-stu-id="7ff48-115">The example below modifies the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to create a "snapping splitter" effect; when the user drags the splitter, it increments in units of 10 pixels rather than the default 1.</span></span>  
  
### <a name="to-define-splitcontainer-resize-behavior"></a><span data-ttu-id="7ff48-116">Definir o comportamento de redimensionamento do SplitContainer</span><span class="sxs-lookup"><span data-stu-id="7ff48-116">To define SplitContainer resize behavior</span></span>  
  
1. <span data-ttu-id="7ff48-117">Em um procedimento, defina o <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> propriedade para o tamanho desejado, para que o comportamento do separador 'Ajuste' é obtido.</span><span class="sxs-lookup"><span data-stu-id="7ff48-117">In a procedure, set the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to the desired size, so that the 'snapping' behavior of the splitter is achieved.</span></span>  
  
     <span data-ttu-id="7ff48-118">No exemplo de código, dentro do formulário <xref:System.Windows.Forms.Form.Load> evento, o divisor dentro a <xref:System.Windows.Forms.SplitContainer> controle está definido para pular 10 pixels quando arrastado.</span><span class="sxs-lookup"><span data-stu-id="7ff48-118">In the following code example, within the form's <xref:System.Windows.Forms.Form.Load> event, the splitter within the <xref:System.Windows.Forms.SplitContainer> control is set to jump 10 pixels when dragged.</span></span>  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
        ByVal e As System.EventArgs) Handles MyBase.Load  
        Dim splitSnapper as new SplitContainer()  
        splitSnapper.SplitterIncrement = 10  
        splitSnapper.Dock = DockStyle.Fill  
        splitSnapper.Parent = me  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Load(System.Object sender, System.EventArgs e)  
    {  
        SplitContainer splitSnapper = new SplitContainer();  
        splitSnapper.SplitterIncrement = 10;  
        splitSnapper.Dock = DockStyle.Fill;  
        splitSnapper.Parent = this;  
    }  
    ```  
  
     <span data-ttu-id="7ff48-119">(Visual C#) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="7ff48-119">(Visual C#) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     <span data-ttu-id="7ff48-120">Mover o divisor ligeiramente para a esquerda ou direita não terá nenhum efeito; no entanto, quando o ponteiro do mouse se move em 10 pixels em qualquer direção, o divisor se ajustará à nova posição.</span><span class="sxs-lookup"><span data-stu-id="7ff48-120">Moving the splitter slightly to the left or right will have no discernible effect; however, when the mouse pointer goes 10 pixels in either direction, the splitter will snap to the new position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ff48-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ff48-121">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>
