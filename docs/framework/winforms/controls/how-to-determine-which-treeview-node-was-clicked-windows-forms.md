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
ms.openlocfilehash: d960eaae2aa479e0be74e9a5e4fdbfec8ff411c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182186"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>Como determinar qual nó TreeView foi clicado (Windows Forms)
Ao trabalhar com <xref:System.Windows.Forms.TreeView> o controle do Windows Forms, uma tarefa comum é determinar qual nó foi clicado e responder adequadamente.  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>Para determinar qual nó TreeView foi clicado  
  
1. Use <xref:System.EventArgs> o objeto para retornar uma referência ao objeto nó clicado.  
  
2. Determine qual nó foi clicado <xref:System.Windows.Forms.TreeViewEventArgs> verificando a classe, que contém dados relacionados ao evento.  
  
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
    > Como alternativa, você pode <xref:System.Windows.Forms.MouseEventArgs> usar <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.MouseUp> o do <xref:System.Drawing.Point.X%2A> evento <xref:System.Drawing.Point.Y%2A> ou para <xref:System.Drawing.Point> obter os valores e coordenar o local onde o clique ocorreu. Em seguida, <xref:System.Windows.Forms.TreeView> use <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> o método do controle para determinar qual nó foi clicado.  
  
## <a name="see-also"></a>Confira também

- [Controle TreeView](treeview-control-windows-forms.md)
