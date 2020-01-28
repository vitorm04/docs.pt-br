---
title: 'Como: criar e definir um renderizador personalizado para o controle ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], custom rendering
- toolbars [Windows Forms], rendering
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], rendering
ms.assetid: 88a804ba-679f-4ba3-938a-0dc396199c5b
ms.openlocfilehash: ad5ced42754fba6a714452220dd824c4f54fb5e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743415"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>Como criar e definir um renderizador personalizado para o controle ToolStrip nos Windows Forms
<xref:System.Windows.Forms.ToolStrip> controles fornecem fácil suporte a temas e estilos. Você pode obter aparência e comportamento completamente personalizados, definindo a propriedade <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> ou a propriedade <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> como um renderizador personalizado.  
  
 Você pode atribuir renderizadores a cada <xref:System.Windows.Forms.ToolStrip>individuais, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>ou controle de <xref:System.Windows.Forms.StatusStrip>, ou pode usar a propriedade <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> para afetar todos os objetos, definindo a propriedade <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> como <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.  
  
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> retornará <xref:System.Windows.Forms.ToolStripRenderMode.Custom> somente se o valor de <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> não for `null`.  
  
### <a name="to-create-a-custom-renderer"></a>Para criar um renderizador personalizado  
  
1. Estenda a classe <xref:System.Windows.Forms.ToolStripRenderer>.  
  
2. Implemente a renderização personalizada desejada substituindo o *On...* adequado Membros do  
  
    ```vb  
    Public Class RedTextRenderer  
        Inherits System.Windows.Forms.ToolStripRenderer  
        Protected Overrides Sub OnRenderItemText(ByVal e As _  
            ToolStripItemTextRenderEventArgs)   
            e.TextColor = Color.Red  
            e.TextFont = New Font("Helvetica", 7, FontStyle.Bold)  
            MyBase.OnRenderItemText(e)  
        End Sub  
    End Class  
    ```  
  
    ```csharp  
    public class RedTextRenderer : _  
        System.Windows.Forms.ToolStripRenderer  
    {  
        protected override void _  
            OnRenderItemText(ToolStripItemTextRenderEventArgs e)  
        {  
            e.TextColor = Color.Red;  
            e.TextFont = new Font("Helvetica", 7, FontStyle.Bold);  
           base.OnRenderItemText(e);  
        }  
    }  
    ```  
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a>Para definir o renderizador personalizado para ser o processador atual  
  
1. Para definir o renderizador personalizado para um <xref:System.Windows.Forms.ToolStrip>, defina a propriedade <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> como o renderizador personalizado.  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. Ou para definir o renderizador personalizado para todas as classes de <xref:System.Windows.Forms.ToolStrip> contidas em seu aplicativo: defina a propriedade <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> para o renderizador personalizado e defina a propriedade <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> como <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [Visão geral do controle ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Arquitetura de controle do ToolStrip](toolstrip-control-architecture.md)
- [Resumo da tecnologia de ToolStrip](toolstrip-technology-summary.md)
