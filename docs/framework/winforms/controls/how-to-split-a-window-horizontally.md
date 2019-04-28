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
ms.openlocfilehash: a43d632a82678f362a1cdf6b3ee4486a8db5adde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012926"
---
# <a name="how-to-split-a-window-horizontally"></a>Como: Dividir uma janela horizontalmente
O exemplo de código a seguir torna o separador que divide o <xref:System.Windows.Forms.SplitContainer> horizontal do controle.  
  
> [!NOTE]
>  O <xref:System.Windows.Forms.SplitContainer.Orientation%2A> propriedade do <xref:System.Windows.Forms.SplitContainer> controle determina a direção do divisor, não do próprio controle.  
  
### <a name="to-split-a-window-horizontally"></a>Para dividir uma janela horizontalmente  
  
1. Dentro de um procedimento, defina as <xref:System.Windows.Forms.SplitContainer.Orientation%2A> propriedade do <xref:System.Windows.Forms.SplitContainer> o controle para <xref:System.Windows.Forms.Orientation.Horizontal>.  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.SplitContainer>
- [Controle SplitContainer](splitcontainer-control-windows-forms.md)
