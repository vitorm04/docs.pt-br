---
title: 'Como: Personalizar o desenho de um controle ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], custom drawing
- drawing [Windows Forms], owner
- ProfessionalColorTable class [Windows Forms], overriding
- examples [Windows Forms], toolbars
- drawing [Windows Forms], custom
- toolbars [Windows Forms], changing colors
- ToolStrip control [Windows Forms], drawing
- ToolStrip control [Windows Forms], changing colors
- custom drawing
- owner drawing
ms.assetid: 94e7d7bd-a752-441c-b5b3-7acf98881163
ms.openlocfilehash: 6df1f2bf3190fb1453930c0553266cc27234f46d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701424"
---
# <a name="how-to-custom-draw-a-toolstrip-control"></a><span data-ttu-id="a1aa6-102">Como: Personalizar o desenho de um controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a1aa6-102">How to: Custom Draw a ToolStrip Control</span></span>
<span data-ttu-id="a1aa6-103">O <xref:System.Windows.Forms.ToolStrip> controles têm o seguinte associado (pintura) classes de renderização:</span><span class="sxs-lookup"><span data-stu-id="a1aa6-103">The <xref:System.Windows.Forms.ToolStrip> controls have the following associated rendering (painting) classes:</span></span>  
  
-   <span data-ttu-id="a1aa6-104"><xref:System.Windows.Forms.ToolStripSystemRenderer> fornece a aparência e o estilo do seu sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="a1aa6-104"><xref:System.Windows.Forms.ToolStripSystemRenderer> provides the appearance and style of your operating system.</span></span>  
  
-   <span data-ttu-id="a1aa6-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer> fornece a aparência e o estilo do Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="a1aa6-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer> provides the appearance and style of Microsoft Office.</span></span>  
  
-   <span data-ttu-id="a1aa6-106"><xref:System.Windows.Forms.ToolStripRenderer> é a classe base abstrata para as outras duas classes de renderização.</span><span class="sxs-lookup"><span data-stu-id="a1aa6-106"><xref:System.Windows.Forms.ToolStripRenderer> is the abstract base class for the other two rendering classes.</span></span>  
  
 <span data-ttu-id="a1aa6-107">Para desenho personalizado (também conhecido como desenho do proprietário) um <xref:System.Windows.Forms.ToolStrip>, você pode substituir uma das classes de renderizador e alterar um aspecto da lógica de processamento.</span><span class="sxs-lookup"><span data-stu-id="a1aa6-107">To custom draw (also known as owner draw) a <xref:System.Windows.Forms.ToolStrip>, you can override one of the renderer classes and change an aspect of the rendering logic.</span></span>  
  
 <span data-ttu-id="a1aa6-108">Os procedimentos a seguir descrevem vários aspectos do desenho personalizado.</span><span class="sxs-lookup"><span data-stu-id="a1aa6-108">The following procedures describe various aspects of custom drawing.</span></span>  
  
### <a name="to-switch-between-the-provided-renderers"></a><span data-ttu-id="a1aa6-109">Alternar entre os renderizadores fornecidos</span><span class="sxs-lookup"><span data-stu-id="a1aa6-109">To switch between the provided renderers</span></span>  
  
-   <span data-ttu-id="a1aa6-110">Defina a <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> propriedade para o <xref:System.Windows.Forms.ToolStripRenderMode> valor desejado.</span><span class="sxs-lookup"><span data-stu-id="a1aa6-110">Set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to the <xref:System.Windows.Forms.ToolStripRenderMode> value you want.</span></span>  
  
     <span data-ttu-id="a1aa6-111">Com o <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, estático <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> determina o renderizador do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a1aa6-111">With <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, the static <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> determines the renderer for your application.</span></span> <span data-ttu-id="a1aa6-112">Os outros valores de <xref:System.Windows.Forms.ToolStripRenderMode> estão <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, e <xref:System.Windows.Forms.ToolStripRenderMode.System>.</span><span class="sxs-lookup"><span data-stu-id="a1aa6-112">The other values of <xref:System.Windows.Forms.ToolStripRenderMode> are <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, and <xref:System.Windows.Forms.ToolStripRenderMode.System>.</span></span>  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a><span data-ttu-id="a1aa6-113">Alterar as bordas de estilo do Microsoft Office para simples</span><span class="sxs-lookup"><span data-stu-id="a1aa6-113">To change the Microsoft Office–style borders to straight</span></span>  
  
-   <span data-ttu-id="a1aa6-114">Substituir <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, mas não chame a classe base.</span><span class="sxs-lookup"><span data-stu-id="a1aa6-114">Override <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, but do not call the base class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1aa6-115">Há uma versão desse método para <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, e <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.</span><span class="sxs-lookup"><span data-stu-id="a1aa6-115">There is a version of this method for <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, and <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.</span></span>  
  
### <a name="to-change-the-professionalcolortable"></a><span data-ttu-id="a1aa6-116">Alterar o ProfessionalColorTable</span><span class="sxs-lookup"><span data-stu-id="a1aa6-116">To change the ProfessionalColorTable</span></span>  
  
-   <span data-ttu-id="a1aa6-117">Substituir <xref:System.Windows.Forms.ProfessionalColorTable> e alterar as cores que você deseja.</span><span class="sxs-lookup"><span data-stu-id="a1aa6-117">Override <xref:System.Windows.Forms.ProfessionalColorTable> and change the colors you want.</span></span>  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As _  
    System.EventArgs) Handles Me.Load  
        Dim t As MyColorTable = New MyColorTable  
        ToolStrip1.Renderer = New ToolStripProfessionalRenderer(t)  
    End Sub  
  
    Class MyColorTable   
    Inherits ProfessionalColorTable  
  
    Public Overrides ReadOnly Property ButtonPressedGradientBegin() As Color  
        Get  
            Return Color.Red  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientMiddle() _  
    As System.Drawing.Color  
        Get  
            Return Color.Blue  
        End Get  
            End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Green  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientBegin() _  
    As Color  
        Get  
            Return Color.Yellow  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientMiddle() As System.Drawing.Color  
        Get  
            Return Color.Orange  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Violet  
        End Get  
    End Property  
    End Class  
    ```  
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a><span data-ttu-id="a1aa6-118">Alterar o processamento para todos os controles ToolStrip em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="a1aa6-118">To change the rendering for all ToolStrip controls in your application</span></span>  
  
1.  <span data-ttu-id="a1aa6-119">Use o <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> propriedade para escolher um dos renderizadores fornecidos.</span><span class="sxs-lookup"><span data-stu-id="a1aa6-119">Use the <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> property to choose one of the provided renderers.</span></span>  
  
2.  <span data-ttu-id="a1aa6-120">Use <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> para atribuir um renderizador personalizado.</span><span class="sxs-lookup"><span data-stu-id="a1aa6-120">Use <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> to assign a custom renderer.</span></span>  
  
3.  <span data-ttu-id="a1aa6-121">Certifique-se de que <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> é definido como o valor padrão de <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span><span class="sxs-lookup"><span data-stu-id="a1aa6-121">Ensure that <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> is set to the default value of <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a><span data-ttu-id="a1aa6-122">Desligar as cores do Microsoft Office para todo o aplicativo inteiro</span><span class="sxs-lookup"><span data-stu-id="a1aa6-122">To turn off the Microsoft Office colors for the entire application</span></span>  
  
-   <span data-ttu-id="a1aa6-123">Defina <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> como `false`.</span><span class="sxs-lookup"><span data-stu-id="a1aa6-123">Set <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> to `false`.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a><span data-ttu-id="a1aa6-124">Desligar as cores do Microsoft Office para um controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a1aa6-124">To turn off the Microsoft Office colors for one ToolStrip control</span></span>  
  
-   <span data-ttu-id="a1aa6-125">Use um código semelhante ao seguinte exemplo.</span><span class="sxs-lookup"><span data-stu-id="a1aa6-125">Use code similar to the following code example.</span></span>  
  
    ```vb  
    Dim colorTable As ProfessionalColorTable()  
    colorTable.UseSystemColors = True  
    Dim toolStrip.Renderer As ToolStripProfessionalRenderer(colorTable)  
    ```  
  
    ```csharp  
    ProfessionalColorTable colorTable = new ProfessionalColorTable();  
    colorTable.UseSystemColors = true;  
    toolStrip.Renderer = new ToolStripProfessionalRenderer(colorTable);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a1aa6-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1aa6-126">See also</span></span>
- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripRenderer>
- [<span data-ttu-id="a1aa6-127">Controles com suporte para desenho do proprietário interno</span><span class="sxs-lookup"><span data-stu-id="a1aa6-127">Controls with Built-In Owner-Drawing Support</span></span>](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)
- [<span data-ttu-id="a1aa6-128">Como: Criar e definir um renderizador personalizado para o controle ToolStrip nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a1aa6-128">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)
- [<span data-ttu-id="a1aa6-129">Visão geral do controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a1aa6-129">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
