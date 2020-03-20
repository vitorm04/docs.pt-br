---
title: 'Como: Criar e definir um renderizador personalizado para o controle de tiras de ferramentas'
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
ms.openlocfilehash: 49db0d785155f19b7220ac64011eaf4253aaa7e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182399"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>Como criar e definir um renderizador personalizado para o controle ToolStrip nos Windows Forms
<xref:System.Windows.Forms.ToolStrip>controles dão suporte fácil a temas e estilos. Você pode obter aparência e comportamento completamente personalizados (olhar e sentir) definindo a <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> propriedade ou a <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> propriedade para um renderizador personalizado.  
  
 Você pode atribuir renderizadores <xref:System.Windows.Forms.ToolStrip>a <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip>cada <xref:System.Windows.Forms.StatusStrip> indivíduo, ou controle, <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> ou pode usar a <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> propriedade <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>para afetar todos os objetos definindo a propriedade para .  
  
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>retorna <xref:System.Windows.Forms.ToolStripRenderMode.Custom> somente se <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> o `null`valor de não é .  
  
### <a name="to-create-a-custom-renderer"></a>Para criar um renderizador personalizado  
  
1. Estender <xref:System.Windows.Forms.ToolStripRenderer> a aula.  
  
2. Implemente a renderização personalizada desejada substituindo o *On...* adequado membros  
  
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
  
1. Para definir o renderizador <xref:System.Windows.Forms.ToolStrip>personalizado <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> para um, defina a propriedade como renderizador personalizado.  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. Ou para definir o renderizador personalizado para <xref:System.Windows.Forms.ToolStrip> todas <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> as classes contidas em <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> seu <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>aplicativo: Defina a propriedade no renderizador personalizado e defina a propriedade como .  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [Visão geral do controle ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Arquitetura de controle ToolStrip](toolstrip-control-architecture.md)
- [Resumo da tecnologia de ToolStrip](toolstrip-technology-summary.md)
