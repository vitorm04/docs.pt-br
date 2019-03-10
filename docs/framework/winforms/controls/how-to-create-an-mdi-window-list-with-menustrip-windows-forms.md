---
title: 'Como: Criar uma lista de janelas MDI com MenuStrip (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
ms.openlocfilehash: e58f35304f70c82973ebbc9928bae5a7477e9c53
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716121"
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a>Como: Criar uma lista de janelas MDI com MenuStrip (Windows Forms)
Use a interface MDI para criar aplicativos que podem abrir vários documentos no mesmo momento e copie e cole o conteúdo de um documento para outro.  
  
 Este procedimento mostra como criar uma lista de todos os formulários filho ativos no menu Janela do pai.  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a>Para criar uma lista de janelas MDI em um MenuStrip  
  
1.  Criar um formulário e defina suas <xref:System.Windows.Forms.Form.IsMdiContainer%2A> propriedade para `true`.  
  
2.  Adicionar um <xref:System.Windows.Forms.MenuStrip> ao formulário.  
  
3.  Adicione dois itens de menu de nível superior para o <xref:System.Windows.Forms.MenuStrip> e defina seus <xref:System.Windows.Forms.Control.Text%2A> propriedades a serem `&File` e `&Window`.  
  
4.  Adicionar um item de submenu para o `&File` item de menu e defina seu <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedade para `&Open`.  
  
5.  Defina a <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> propriedade do <xref:System.Windows.Forms.MenuStrip> para o `&Window` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
6.  Adicione um formulário ao projeto e adicionar o controle desejado, como outro <xref:System.Windows.Forms.MenuStrip>.  
  
7.  Crie um manipulador de eventos para o <xref:System.Windows.Forms.Control.Click> eventos do `&New` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
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
  
9. Coloque o código semelhante ao seguinte na `&New` <xref:System.Windows.Forms.ToolStripMenuItem> para registrar o manipulador de eventos.  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Duas <xref:System.Windows.Forms.Form> controles denominados `Form1` e `Form2`.  
  
-   Um <xref:System.Windows.Forms.MenuStrip> control em `Form1` denominado `menuStrip1`e uma <xref:System.Windows.Forms.MenuStrip> control em `Form2` chamado `menuStrip2`.  
  
-   Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também
- [Como: Criar formulários pai MDI](../advanced/how-to-create-mdi-parent-forms.md)
- [Como: Criar formulários filho MDI](../advanced/how-to-create-mdi-child-forms.md)
- [Controle MenuStrip](menustrip-control-windows-forms.md)
