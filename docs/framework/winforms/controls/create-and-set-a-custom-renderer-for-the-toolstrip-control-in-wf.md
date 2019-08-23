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
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="5e9a2-102">Como: Criar e definir um renderizador personalizado para o controle ToolStrip no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5e9a2-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<span data-ttu-id="5e9a2-103"><xref:System.Windows.Forms.ToolStrip>controles fornecem fácil suporte a temas e estilos.</span><span class="sxs-lookup"><span data-stu-id="5e9a2-103"><xref:System.Windows.Forms.ToolStrip> controls give easy support to themes and styles.</span></span> <span data-ttu-id="5e9a2-104">Você pode obter aparência e comportamento completamente personalizados, definindo a <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> propriedade ou a <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> propriedade para um renderizador personalizado.</span><span class="sxs-lookup"><span data-stu-id="5e9a2-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="5e9a2-105">Você pode atribuir renderizadores a cada controle <xref:System.Windows.Forms.ToolStrip>individual <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip>,, ou <xref:System.Windows.Forms.StatusStrip> , ou pode usar a <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> propriedade para afetar todos os objetos definindo a <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> Propriedade como <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5e9a2-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5e9a2-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A>retorna <xref:System.Windows.Forms.ToolStripRenderMode.Custom> somente se o valor de <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> não `null`for.</span><span class="sxs-lookup"><span data-stu-id="5e9a2-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="5e9a2-107">Para criar um renderizador personalizado</span><span class="sxs-lookup"><span data-stu-id="5e9a2-107">To create a custom renderer</span></span>  
  
1. <span data-ttu-id="5e9a2-108">Estenda a <xref:System.Windows.Forms.ToolStripRenderer> classe.</span><span class="sxs-lookup"><span data-stu-id="5e9a2-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2. <span data-ttu-id="5e9a2-109">Implemente a renderização personalizada desejada substituindo o *On...* adequado</span><span class="sxs-lookup"><span data-stu-id="5e9a2-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="5e9a2-110">membros</span><span class="sxs-lookup"><span data-stu-id="5e9a2-110">members</span></span>  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="5e9a2-111">Para definir o renderizador personalizado para ser o processador atual</span><span class="sxs-lookup"><span data-stu-id="5e9a2-111">To set the custom renderer to be the current renderer</span></span>  
  
1. <span data-ttu-id="5e9a2-112">Para definir o renderizador personalizado para <xref:System.Windows.Forms.ToolStrip>um, defina <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> a propriedade para o renderizador personalizado.</span><span class="sxs-lookup"><span data-stu-id="5e9a2-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. <span data-ttu-id="5e9a2-113">Ou para definir o renderizador personalizado para <xref:System.Windows.Forms.ToolStrip> todas as classes contidas em seu aplicativo: Defina a <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> propriedade para o renderizador personalizado e defina <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> a propriedade <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>como.</span><span class="sxs-lookup"><span data-stu-id="5e9a2-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5e9a2-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e9a2-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [<span data-ttu-id="5e9a2-115">Visão geral do controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="5e9a2-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="5e9a2-116">Arquitetura de controle do ToolStrip</span><span class="sxs-lookup"><span data-stu-id="5e9a2-116">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="5e9a2-117">Resumo da tecnologia de ToolStrip</span><span class="sxs-lookup"><span data-stu-id="5e9a2-117">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
