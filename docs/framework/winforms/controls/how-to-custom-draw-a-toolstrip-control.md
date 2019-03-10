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
ms.openlocfilehash: d9a58dbaeae3f0cd165d72b8fd281b903ad9cca2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705743"
---
# <a name="how-to-custom-draw-a-toolstrip-control"></a>Como: Personalizar o desenho de um controle ToolStrip
O <xref:System.Windows.Forms.ToolStrip> controles têm o seguinte associado (pintura) classes de renderização:  
  
-   <xref:System.Windows.Forms.ToolStripSystemRenderer> fornece a aparência e o estilo do seu sistema operacional.  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer> fornece a aparência e o estilo do Microsoft Office.  
  
-   <xref:System.Windows.Forms.ToolStripRenderer> é a classe base abstrata para as outras duas classes de renderização.  
  
 Para desenho personalizado (também conhecido como desenho do proprietário) um <xref:System.Windows.Forms.ToolStrip>, você pode substituir uma das classes de renderizador e alterar um aspecto da lógica de processamento.  
  
 Os procedimentos a seguir descrevem vários aspectos do desenho personalizado.  
  
### <a name="to-switch-between-the-provided-renderers"></a>Alternar entre os renderizadores fornecidos  
  
-   Defina a <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> propriedade para o <xref:System.Windows.Forms.ToolStripRenderMode> valor desejado.  
  
     Com o <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, estático <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> determina o renderizador do seu aplicativo. Os outros valores de <xref:System.Windows.Forms.ToolStripRenderMode> estão <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, e <xref:System.Windows.Forms.ToolStripRenderMode.System>.  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a>Alterar as bordas de estilo do Microsoft Office para simples  
  
-   Substituir <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, mas não chame a classe base.  
  
> [!NOTE]
>  Há uma versão desse método para <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, e <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.  
  
### <a name="to-change-the-professionalcolortable"></a>Alterar o ProfessionalColorTable  
  
-   Substituir <xref:System.Windows.Forms.ProfessionalColorTable> e alterar as cores que você deseja.  
  
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
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a>Alterar o processamento para todos os controles ToolStrip em seu aplicativo  
  
1.  Use o <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> propriedade para escolher um dos renderizadores fornecidos.  
  
2.  Use <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> para atribuir um renderizador personalizado.  
  
3.  Certifique-se de que <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> é definido como o valor padrão de <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a>Desligar as cores do Microsoft Office para todo o aplicativo inteiro  
  
-   Defina <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> como `false`.  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a>Desligar as cores do Microsoft Office para um controle ToolStrip  
  
-   Use um código semelhante ao seguinte exemplo.  
  
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
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripRenderer>
- [Controles com suporte para desenho do proprietário interno](controls-with-built-in-owner-drawing-support.md)
- [Como: Criar e definir um renderizador personalizado para o controle ToolStrip nos Windows Forms](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)
- [Visão geral do controle ToolStrip](toolstrip-control-overview-windows-forms.md)
