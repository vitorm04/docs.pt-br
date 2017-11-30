---
title: "Como determinar qual nó TreeView foi clicado (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords: TreeNode
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- tree nodes in TreeView control [Windows Forms], determining node clicked
- TreeView control [Windows Forms], determining node clicked
ms.assetid: 06a4a191-d918-42af-9f49-956c93eff261
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c59b09f6df7fdc6a7bb237ff6eafcad99329256
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>Como determinar qual nó TreeView foi clicado (Windows Forms)
Ao trabalhar com o Windows Forms <xref:System.Windows.Forms.TreeView> controle, uma tarefa comum é determinar qual nó foi clicado e responder adequadamente.  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>Para determinar qual nó TreeView foi clicado  
  
1.  Use o <xref:System.EventArgs> objeto para retornar uma referência ao objeto de nó clicado.  
  
2.  Determinar qual nó foi clicado, verificando o <xref:System.Windows.Forms.TreeViewEventArgs> classe, que contém dados relacionados ao evento.  
  
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
    >  Como alternativa, você pode usar o <xref:System.Windows.Forms.MouseEventArgs> do <xref:System.Windows.Forms.Control.MouseDown> ou <xref:System.Windows.Forms.Control.MouseUp> evento para obter o <xref:System.Drawing.Point.X%2A> e <xref:System.Drawing.Point.Y%2A> coordenar os valores da <xref:System.Drawing.Point> onde ocorreu o clique. Em seguida, use o <xref:System.Windows.Forms.TreeView> do controle <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> método para determinar qual nó foi clicado.  
  
## <a name="see-also"></a>Consulte também  
 [Controle TreeView](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
