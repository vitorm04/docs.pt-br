---
title: 'Como: Dividir uma janela horizontalmente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SplitContainer control [Windows Forms], horizontal splitter
- splitter windows [Windows Forms], changing splitter orientation
- splitter windows [Windows Forms], horizontal
- windows [Windows Forms], splitting horizontally
ms.assetid: a1f74f29-048c-4723-85fa-b9d375ab8f4b
ms.openlocfilehash: e11e1d6730c6c8c9c0a1ac170aeb5393bf3153b7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708035"
---
# <a name="how-to-split-a-window-horizontally"></a><span data-ttu-id="fd66f-102">Como: Dividir uma janela horizontalmente</span><span class="sxs-lookup"><span data-stu-id="fd66f-102">How to: Split a Window Horizontally</span></span>
<span data-ttu-id="fd66f-103">O exemplo de código a seguir torna o separador que divide o <xref:System.Windows.Forms.SplitContainer> horizontal do controle.</span><span class="sxs-lookup"><span data-stu-id="fd66f-103">The following code example makes the splitter that divides the <xref:System.Windows.Forms.SplitContainer> control horizontal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd66f-104">O <xref:System.Windows.Forms.SplitContainer.Orientation%2A> propriedade do <xref:System.Windows.Forms.SplitContainer> controle determina a direção do divisor, não do próprio controle.</span><span class="sxs-lookup"><span data-stu-id="fd66f-104">The <xref:System.Windows.Forms.SplitContainer.Orientation%2A> property of the <xref:System.Windows.Forms.SplitContainer> control determines the direction of the splitter, not of the control itself.</span></span>  
  
### <a name="to-split-a-window-horizontally"></a><span data-ttu-id="fd66f-105">Para dividir uma janela horizontalmente</span><span class="sxs-lookup"><span data-stu-id="fd66f-105">To split a window horizontally</span></span>  
  
1.  <span data-ttu-id="fd66f-106">Dentro de um procedimento, defina as <xref:System.Windows.Forms.SplitContainer.Orientation%2A> propriedade do <xref:System.Windows.Forms.SplitContainer> o controle para <xref:System.Windows.Forms.Orientation.Horizontal>.</span><span class="sxs-lookup"><span data-stu-id="fd66f-106">Within a procedure, set the <xref:System.Windows.Forms.SplitContainer.Orientation%2A> property of the <xref:System.Windows.Forms.SplitContainer> control to <xref:System.Windows.Forms.Orientation.Horizontal>.</span></span>  
  
    ```vb  
    Sub ShowSplitContainer()  
        Dim splitContainer1 as new SplitContainer()  
        splitContainer1.BorderStyle = BorderStyle.Fixed3D  
        splitContainer1.Location = New System.Drawing.Point(74, 20)  
        splitContainer1.Name = "DemoSplitContainer"  
        splitContainer1.Size = New System.Drawing.Size(212, 435)  
        splitContainer1.TabIndex = 0  
        splitContainer1.Orientation = Orientation.Horizontal  
        Controls.Add(splitContainer1)  
    End Sub  
    ```  
  
    ```csharp  
    public void showSplitContainer()  
    {  
        SplitContainer splitContainer1 = new SplitContainer ();  
        splitContainer1.BorderStyle = BorderStyle.Fixed3D;  
        splitContainer1.Location = new System.Drawing.Point (74, 20);  
        splitContainer1.Name = "DemoSplitContainer";  
        splitContainer1.Size = new System.Drawing.Size (212, 435);  
        splitContainer1.TabIndex = 0;  
        splitContainer1.Orientation = Orientation.Horizontal;  
        this.Controls.Add (splitContainer1);  
  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fd66f-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd66f-107">See also</span></span>
- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="fd66f-108">Controle SplitContainer</span><span class="sxs-lookup"><span data-stu-id="fd66f-108">SplitContainer Control</span></span>](splitcontainer-control-windows-forms.md)
