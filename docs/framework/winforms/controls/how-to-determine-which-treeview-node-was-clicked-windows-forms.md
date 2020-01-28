---
title: Como determinar qual nó TreeView foi clicado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TreeNode
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- tree nodes in TreeView control [Windows Forms], determining node clicked
- TreeView control [Windows Forms], determining node clicked
ms.assetid: 06a4a191-d918-42af-9f49-956c93eff261
ms.openlocfilehash: 7a0e2b69bbec0eb03d40bee2c8e2d4bc9c3558f9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742004"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>Como determinar qual nó TreeView foi clicado (Windows Forms)
Ao trabalhar com o controle de <xref:System.Windows.Forms.TreeView> de Windows Forms, uma tarefa comum é determinar qual nó foi clicado e responder adequadamente.  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>Para determinar qual nó TreeView foi clicado  
  
1. Use o objeto <xref:System.EventArgs> para retornar uma referência ao objeto node clicado.  
  
2. Determine qual nó foi clicado verificando a classe <xref:System.Windows.Forms.TreeViewEventArgs>, que contém dados relacionados ao evento.  
  
    ```vb  
    Private Sub TreeView1_AfterSelect(ByVal sender As System.Object, _  
    ByVal e As System.Windows.Forms.TreeViewEventArgs) Handles TreeView1.AfterSelect  
       ' Determine by checking the Node property of the TreeViewEventArgs.  
       MessageBox.Show(e.Node.Text)  
    End Sub  
    ```  
  
    ```csharp  
    protected void treeView1_AfterSelect (object sender,   
    System.Windows.Forms.TreeViewEventArgs e)  
    {  
       // Determine by checking the Text property.  
       MessageBox.Show(e.Node.Text);  
    }  
    ```  
  
    ```cpp  
    private:  
       void treeView1_AfterSelect(System::Object ^  sender,  
          System::Windows::Forms::TreeViewEventArgs ^  e)  
       {  
          // Determine by checking the Text property.  
          MessageBox::Show(e->Node->Text);  
       }  
    ```  
  
    > [!NOTE]
    > Como alternativa, você pode usar a <xref:System.Windows.Forms.MouseEventArgs> do evento <xref:System.Windows.Forms.Control.MouseDown> ou <xref:System.Windows.Forms.Control.MouseUp> para obter os valores <xref:System.Drawing.Point.X%2A> e <xref:System.Drawing.Point.Y%2A> coordenada do <xref:System.Drawing.Point> em que o clique ocorreu. Em seguida, use o método <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> do controle de <xref:System.Windows.Forms.TreeView> para determinar qual nó foi clicado.  
  
## <a name="see-also"></a>Veja também

- [Controle TreeView](treeview-control-windows-forms.md)
