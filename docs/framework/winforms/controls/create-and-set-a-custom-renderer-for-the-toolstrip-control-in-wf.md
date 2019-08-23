---
title: 'Como: Criar e definir um renderizador personalizado para o controle ToolStrip no Windows Forms'
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
ms.openlocfilehash: c354ace3a7d3ce43f549dd1295a85fbee004eb22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929736"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>Como: Criar e definir um renderizador personalizado para o controle ToolStrip no Windows Forms
<xref:System.Windows.Forms.ToolStrip>controles fornecem fácil suporte a temas e estilos. Você pode obter aparência e comportamento completamente personalizados, definindo a <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> propriedade ou a <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> propriedade para um renderizador personalizado.  
  
 Você pode atribuir renderizadores a cada controle <xref:System.Windows.Forms.ToolStrip>individual <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip>,, ou <xref:System.Windows.Forms.StatusStrip> , ou pode usar a <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> propriedade para afetar todos os objetos definindo a <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> Propriedade como <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.  
  
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>retorna <xref:System.Windows.Forms.ToolStripRenderMode.Custom> somente se o valor de <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> não `null`for.  
  
### <a name="to-create-a-custom-renderer"></a>Para criar um renderizador personalizado  
  
1. Estenda a <xref:System.Windows.Forms.ToolStripRenderer> classe.  
  
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
  
1. Para definir o renderizador personalizado para <xref:System.Windows.Forms.ToolStrip>um, defina <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> a propriedade para o renderizador personalizado.  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. Ou para definir o renderizador personalizado para <xref:System.Windows.Forms.ToolStrip> todas as classes contidas em seu aplicativo: Defina a <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> propriedade para o renderizador personalizado e defina <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> a propriedade <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>como.  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [Visão geral do controle ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Arquitetura de controle do ToolStrip](toolstrip-control-architecture.md)
- [Resumo da tecnologia de ToolStrip](toolstrip-technology-summary.md)
