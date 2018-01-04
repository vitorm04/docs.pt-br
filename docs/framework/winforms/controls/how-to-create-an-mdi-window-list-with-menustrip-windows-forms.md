---
title: Como criar uma lista de janelas MDI com MenuStrip (Windows Forms)
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
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8bf09170b4def3f041e34942a968fdf41fcdf66
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a>Como criar uma lista de janelas MDI com MenuStrip (Windows Forms)
Use a interface MDI para criar aplicativos que podem abrir vários documentos no mesmo momento e copie e cole o conteúdo de um documento para outro.  
  
 Este procedimento mostra como criar uma lista de todos os formulários filho ativos no menu Janela do pai.  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a>Para criar uma lista de janelas MDI em um MenuStrip  
  
1.  Criar um formulário e defina seu <xref:System.Windows.Forms.Form.IsMdiContainer%2A> propriedade `true`.  
  
2.  Adicionar uma <xref:System.Windows.Forms.MenuStrip> ao formulário.  
  
3.  Adicionar dois itens de menu de nível superior para o <xref:System.Windows.Forms.MenuStrip> e defina seus <xref:System.Windows.Forms.Control.Text%2A> propriedades `&File` e `&Window`.  
  
4.  Adicionar um item de submenu a `&File` item de menu e defina seu <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedade `&Open`.  
  
5.  Definir o <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> propriedade o <xref:System.Windows.Forms.MenuStrip> para o `&Window` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
6.  Adicione um formulário para o projeto e adicione o controle que você deseja a ele, como outro <xref:System.Windows.Forms.MenuStrip>.  
  
7.  Criar um manipulador de eventos para o <xref:System.Windows.Forms.Control.Click> evento o `&New` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
8.  No manipulador de eventos, insira um código semelhante ao seguinte para criar e exibir novas instâncias de `Form2` como filhos MDI de `Form1`.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As _  
    System.Object, ByVal e As System.EventArgs) Handles _  
    openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void newToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
9. Coloque o código como o seguinte o `&New` <xref:System.Windows.Forms.ToolStripMenuItem> para registrar o manipulador de eventos.  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Dois <xref:System.Windows.Forms.Form> controles denominados `Form1` e `Form2`.  
  
-   Um <xref:System.Windows.Forms.MenuStrip> control em `Form1` chamado `menuStrip1`e um <xref:System.Windows.Forms.MenuStrip> control em `Form2` chamado `menuStrip2`.  
  
-   Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também  
 [Como criar formulários pai MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Como criar formulários filho MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Controle MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
