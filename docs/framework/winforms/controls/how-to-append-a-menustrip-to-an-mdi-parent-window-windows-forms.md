---
title: 'Como: Acrescentar um MenuStrip a uma janela pai do MDI (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], appending
- MDI [Windows Forms], merging menu items
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
ms.openlocfilehash: d70418c6d8a626fd3ef54161086b24655037b086
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64612834"
---
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a>Como: Acrescentar um MenuStrip a uma janela pai do MDI (Windows Forms)
Em alguns aplicativos, o tipo de uma janela MDI (interface de vários documentos) filho pode ser diferente da janela MDI pai. Por exemplo, a MDI pai pode ser uma planilha e a MDI filho pode ser um gráfico. Nesse caso, é recomendável atualizar o conteúdo do menu da MDI pai com o conteúdo do menu da MDI filho, visto que janelas MDI filho de tipos diferentes são ativadas.  
  
 O procedimento a seguir usa o <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, e <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> propriedades para acrescentar o menu filho MDI ao menu MDI pai. Fechar a janela filho MDI remove o menu acrescentado do MDI pai.  
  
 Consulte também [Aplicativos MDI (Interface de Vários Documentos)](../advanced/multiple-document-interface-mdi-applications.md).  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a>Acrescentar um item de menu a um pai MDI  
  
1. Criar um formulário e defina suas <xref:System.Windows.Forms.Form.IsMdiContainer%2A> propriedade para `true`.  
  
2. Adicionar um <xref:System.Windows.Forms.MenuStrip> para `Form1` e defina o <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> propriedade o <xref:System.Windows.Forms.MenuStrip> para `true`.  
  
3. Defina as <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriedade do `Form1` <xref:System.Windows.Forms.MenuStrip> para `false`.  
  
4. Adicionar um item de menu de nível superior para o `Form1` <xref:System.Windows.Forms.MenuStrip> e defina seu <xref:System.Windows.Forms.Control.Text%2A> propriedade `&File`.  
  
5. Adicionar um item de submenu para o `&File` item de menu e defina seu <xref:System.Windows.Forms.Form.Text%2A> propriedade para `&Open`.  
  
6. Adicionar um formulário ao projeto, adicione uma <xref:System.Windows.Forms.MenuStrip> para o formulário e defina o <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> propriedade da `Form2` <xref:System.Windows.Forms.MenuStrip> para `true`.  
  
7. Adicionar um item de menu de nível superior para o `Form2` <xref:System.Windows.Forms.MenuStrip> e defina seu <xref:System.Windows.Forms.Form.Text%2A> propriedade `&Special`.  
  
8. Adicionar dois itens de submenu para o `&Special` item de menu e defina seus <xref:System.Windows.Forms.Form.Text%2A> propriedades a serem `Command&1` e `Command&2`, respectivamente.  
  
9. Defina a <xref:System.Windows.Forms.MergeAction> propriedade do `&Special`, `Command&1`, e `Command&2` itens de menu <xref:System.Windows.Forms.MergeAction.Append>.  
  
10. Crie um manipulador de eventos para o <xref:System.Windows.Forms.Control.Click> eventos do `&New` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
11. No manipulador de eventos, insira um código semelhante ao exemplo de código a seguir para criar e exibir novas instâncias de `Form2` como filhos MDI de `Form1`.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void openToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
12. Coloque um código semelhante ao seguinte exemplo de código na `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> para registrar o manipulador de eventos.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Duas <xref:System.Windows.Forms.Form> controles denominados `Form1` e `Form2`.  
  
- Um <xref:System.Windows.Forms.MenuStrip> control em `Form1` denominado `menuStrip1`e uma <xref:System.Windows.Forms.MenuStrip> control em `Form2` chamado `menuStrip2`.  
  
- Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.
