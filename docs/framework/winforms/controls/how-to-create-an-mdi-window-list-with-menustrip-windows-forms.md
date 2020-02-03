---
title: Como criar uma lista de janelas MDI com MenuStrip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
ms.openlocfilehash: f013c3df2ab5783a22fe2c34402dc53a328cafa2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731015"
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a>Como criar uma lista de janelas MDI com MenuStrip (Windows Forms)
Use a interface MDI para criar aplicativos que podem abrir vários documentos no mesmo momento e copie e cole o conteúdo de um documento para outro.  
  
 Este procedimento mostra como criar uma lista de todos os formulários filho ativos no menu Janela do pai.  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a>Para criar uma lista de janelas MDI em um MenuStrip  
  
1. Crie um formulário e defina sua propriedade <xref:System.Windows.Forms.Form.IsMdiContainer%2A> como `true`.  
  
2. Adicione um <xref:System.Windows.Forms.MenuStrip> ao formulário.  
  
3. Adicione dois itens de menu de nível superior à <xref:System.Windows.Forms.MenuStrip> e defina suas propriedades de <xref:System.Windows.Forms.Control.Text%2A> como `&File` e `&Window`.  
  
4. Adicione um item de submenu ao item de menu `&File` e defina sua propriedade <xref:System.Windows.Forms.ToolStripItem.Text%2A> como `&Open`.  
  
5. Defina a propriedade <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> da <xref:System.Windows.Forms.MenuStrip> como a `&Window`<xref:System.Windows.Forms.ToolStripMenuItem>.  
  
6. Adicione um formulário ao projeto e adicione o controle que você deseja, como outro <xref:System.Windows.Forms.MenuStrip>.  
  
7. Crie um manipulador de eventos para o evento <xref:System.Windows.Forms.Control.Click> do <xref:System.Windows.Forms.ToolStripMenuItem>de `&New`.  
  
8. No manipulador de eventos, insira um código semelhante ao seguinte para criar e exibir novas instâncias de `Form2` como filhos MDI de `Form1`.  
  
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
  
9. Coloque um código como o seguinte no `&New`<xref:System.Windows.Forms.ToolStripMenuItem> para registrar o manipulador de eventos.  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Dois controles de <xref:System.Windows.Forms.Form> chamados `Form1` e `Form2`.  
  
- Um controle <xref:System.Windows.Forms.MenuStrip> em `Form1` chamado `menuStrip1`e um controle <xref:System.Windows.Forms.MenuStrip> em `Form2` chamado `menuStrip2`.  
  
- Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também

- [Como criar formulários pai MDI](../advanced/how-to-create-mdi-parent-forms.md)
- [Como criar formulários filho MDI](../advanced/how-to-create-mdi-child-forms.md)
- [Controle MenuStrip](menustrip-control-windows-forms.md)
