---
title: Como definir o comportamento de redimensionamento e posicionamento em uma janela dividida
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
- split windows [Windows Forms], resizing
- splitter windows [Windows Forms], resizing
- SplitContainer control [Windows Forms], resizing
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed78a49119c87c52a07cc2ade030e66087d3f420
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a><span data-ttu-id="15810-102">Como definir o comportamento de redimensionamento e posicionamento em uma janela dividida</span><span class="sxs-lookup"><span data-stu-id="15810-102">How to: Define Resize and Positioning Behavior in a Split Window</span></span>
<span data-ttu-id="15810-103">Os painéis do <xref:System.Windows.Forms.SplitContainer> controle se prestam a que está sendo redimensionada e manipulados pelos usuários.</span><span class="sxs-lookup"><span data-stu-id="15810-103">The panels of the <xref:System.Windows.Forms.SplitContainer> control lend themselves well to being resized and manipulated by users.</span></span> <span data-ttu-id="15810-104">No entanto, há momentos em que é útil controlar o divisor com programação, onde ele está posicionado e em que grau pode ser movido.</span><span class="sxs-lookup"><span data-stu-id="15810-104">However, there will be times when you will want to programmatically control the splitter—where it is positioned and to what degree it can be moved.</span></span>  
  
 <span data-ttu-id="15810-105">O <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> propriedade e as outras propriedades de <xref:System.Windows.Forms.SplitContainer> proporciona controle preciso sobre o comportamento da interface do usuário para atender às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="15810-105">The <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property and the other properties on the <xref:System.Windows.Forms.SplitContainer> control give you precise control over the behavior of your user interface to suit your needs.</span></span> <span data-ttu-id="15810-106">Tais propriedades são listadas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="15810-106">These properties are listed in the following table.</span></span>  
  
|<span data-ttu-id="15810-107">Nome</span><span class="sxs-lookup"><span data-stu-id="15810-107">Name</span></span>|<span data-ttu-id="15810-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="15810-108">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="15810-109">Propriedade <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A></span><span class="sxs-lookup"><span data-stu-id="15810-109"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> property</span></span>|<span data-ttu-id="15810-110">Determina se o divisor pode ser movido com o teclado ou mouse.</span><span class="sxs-lookup"><span data-stu-id="15810-110">Determines if the splitter is movable by means of the keyboard or mouse.</span></span>|  
|<span data-ttu-id="15810-111">Propriedade <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A></span><span class="sxs-lookup"><span data-stu-id="15810-111"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> property</span></span>|<span data-ttu-id="15810-112">Determina a distância em pixels da borda esquerda ou superior para o divisor móvel.</span><span class="sxs-lookup"><span data-stu-id="15810-112">Determines the distance in pixels from the left or upper edge to the movable splitter bar.</span></span>|  
|<span data-ttu-id="15810-113">Propriedade <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A></span><span class="sxs-lookup"><span data-stu-id="15810-113"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property</span></span>|<span data-ttu-id="15810-114">Determina a distância mínima, em pixels, que o divisor pode ser movido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="15810-114">Determines the minimum distance, in pixels, that the splitter can be moved by the user.</span></span>|  
  
 <span data-ttu-id="15810-115">O exemplo a seguir modifica o <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> propriedade para criar um efeito "ajuste divisor"; quando o usuário arrasta o divisor, ele é incrementado em unidades de 10 pixels em vez do padrão 1.</span><span class="sxs-lookup"><span data-stu-id="15810-115">The example below modifies the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to create a "snapping splitter" effect; when the user drags the splitter, it increments in units of 10 pixels rather than the default 1.</span></span>  
  
### <a name="to-define-splitcontainer-resize-behavior"></a><span data-ttu-id="15810-116">Definir o comportamento de redimensionamento do SplitContainer</span><span class="sxs-lookup"><span data-stu-id="15810-116">To define SplitContainer resize behavior</span></span>  
  
1.  <span data-ttu-id="15810-117">Em um procedimento, defina o <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> propriedade para o tamanho desejado, para que o comportamento do separador 'Ajuste' é obtido.</span><span class="sxs-lookup"><span data-stu-id="15810-117">In a procedure, set the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to the desired size, so that the 'snapping' behavior of the splitter is achieved.</span></span>  
  
     <span data-ttu-id="15810-118">No seguinte exemplo de código, dentro do formulário <xref:System.Windows.Forms.Form.Load> evento, o separador de dentro do <xref:System.Windows.Forms.SplitContainer> controle está definido para 10 pixels quando arrastado de salto.</span><span class="sxs-lookup"><span data-stu-id="15810-118">In the following code example, within the form's <xref:System.Windows.Forms.Form.Load> event, the splitter within the <xref:System.Windows.Forms.SplitContainer> control is set to jump 10 pixels when dragged.</span></span>  
  
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
  
     <span data-ttu-id="15810-119">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) Coloque o seguinte código no construtor de formulários para registrar o manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="15810-119">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     <span data-ttu-id="15810-120">Mover o divisor ligeiramente para a esquerda ou direita não terá nenhum efeito; no entanto, quando o ponteiro do mouse se move em 10 pixels em qualquer direção, o divisor se ajustará à nova posição.</span><span class="sxs-lookup"><span data-stu-id="15810-120">Moving the splitter slightly to the left or right will have no discernible effect; however, when the mouse pointer goes 10 pixels in either direction, the splitter will snap to the new position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15810-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15810-121">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>
