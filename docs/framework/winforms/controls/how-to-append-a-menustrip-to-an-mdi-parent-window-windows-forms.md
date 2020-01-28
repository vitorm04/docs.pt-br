---
title: Como acrescentar um MenuStrip a uma janela pai MDI
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], appending
- MDI [Windows Forms], merging menu items
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
ms.openlocfilehash: 06e5c9daab8b7eb72024fff27d661c0eb3bf84c6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747163"
---
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a>Como acrescentar um MenuStrip a uma janela pai MDI (Windows Forms)
Em alguns aplicativos, o tipo de uma janela filho MDI (interface de vários documentos) pode ser diferente da janela MDI pai. Por exemplo, a MDI pai pode ser uma planilha e a MDI filho pode ser um gráfico. Nesse caso, é recomendável atualizar o conteúdo do menu do MDI pai com o conteúdo do menu do MDI filho, visto que janelas MDI filho de tipos diferentes são ativadas.  
  
 O procedimento a seguir usa as propriedades <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>e <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> para acrescentar o menu filho MDI ao menu pai MDI. Fechar a janela filho MDI remove o menu acrescentado do MDI pai.  
  
 Consulte também [Aplicativos MDI (Interface de Vários Documentos)](../advanced/multiple-document-interface-mdi-applications.md).  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a>Acrescentar um item de menu a um pai MDI  
  
1. Crie um formulário e defina sua propriedade <xref:System.Windows.Forms.Form.IsMdiContainer%2A> como `true`.  
  
2. Adicione um <xref:System.Windows.Forms.MenuStrip> a `Form1` e defina a propriedade <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> do <xref:System.Windows.Forms.MenuStrip> como `true`.  
  
3. Defina a propriedade <xref:System.Windows.Forms.ToolStripItem.Visible%2A> do <xref:System.Windows.Forms.MenuStrip> de `Form1`como `false`.  
  
4. Adicione um item de menu de nível superior ao `Form1`<xref:System.Windows.Forms.MenuStrip> e defina sua propriedade <xref:System.Windows.Forms.Control.Text%2A> como `&File`.  
  
5. Adicione um item de submenu ao item de menu `&File` e defina sua propriedade <xref:System.Windows.Forms.Form.Text%2A> como `&Open`.  
  
6. Adicione um formulário ao projeto, adicione um <xref:System.Windows.Forms.MenuStrip> ao formulário e defina a propriedade <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> do `Form2`<xref:System.Windows.Forms.MenuStrip> como `true`.  
  
7. Adicione um item de menu de nível superior ao `Form2`<xref:System.Windows.Forms.MenuStrip> e defina sua propriedade <xref:System.Windows.Forms.Form.Text%2A> como `&Special`.  
  
8. Adicione dois itens de submenu ao item de menu `&Special` e defina suas propriedades <xref:System.Windows.Forms.Form.Text%2A> como `Command&1` e `Command&2`, respectivamente.  
  
9. Defina a propriedade <xref:System.Windows.Forms.MergeAction> dos itens de menu `&Special`, `Command&1`e `Command&2` como <xref:System.Windows.Forms.MergeAction.Append>.  
  
10. Crie um manipulador de eventos para o evento <xref:System.Windows.Forms.Control.Click> do <xref:System.Windows.Forms.ToolStripMenuItem>de `&Open`.  
  
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
  
12. Coloque um código semelhante ao exemplo de código a seguir no `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> para registrar o manipulador de eventos.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Dois controles de <xref:System.Windows.Forms.Form> chamados `Form1` e `Form2`.  
  
- Um controle <xref:System.Windows.Forms.MenuStrip> em `Form1` chamado `menuStrip1`e um controle <xref:System.Windows.Forms.MenuStrip> em `Form2` chamado `menuStrip2`.  
  
- Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.
