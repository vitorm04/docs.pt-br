---
title: 'Como: Determinar qual nó TreeView foi clicado (Windows Forms)'
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
ms.openlocfilehash: ab93158daf987e2f19516b8fb3abf80bfe79a12c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967340"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>Como: Determinar qual nó TreeView foi clicado (Windows Forms)
Ao trabalhar com o controle <xref:System.Windows.Forms.TreeView> de Windows Forms, uma tarefa comum é determinar qual nó foi clicado e responder adequadamente.  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>Para determinar qual nó TreeView foi clicado  
  
1. Use o <xref:System.EventArgs> objeto para retornar uma referência ao objeto de nó clicado.  
  
2. Determine qual nó foi clicado verificando <xref:System.Windows.Forms.TreeViewEventArgs> a classe, que contém dados relacionados ao evento.  
  
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
    > Como alternativa, você pode <xref:System.Windows.Forms.MouseEventArgs> usar o <xref:System.Windows.Forms.Control.MouseDown> do evento ou <xref:System.Drawing.Point.Y%2A> <xref:System.Windows.Forms.Control.MouseUp> <xref:System.Drawing.Point.X%2A> para obter os valores de coordenada e de ondeocorreuoclique.<xref:System.Drawing.Point> Em seguida, use <xref:System.Windows.Forms.TreeView> o método <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> do controle para determinar qual nó foi clicado.  
  
## <a name="see-also"></a>Consulte também

- [Controle TreeView](treeview-control-windows-forms.md)
