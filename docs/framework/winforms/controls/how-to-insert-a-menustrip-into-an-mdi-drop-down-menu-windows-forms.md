---
title: Como inserir um MenuStrip um menu suspenso MDI
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], inserting
- MenuStrip control [Windows Forms], merging
- MDI [Windows Forms], merging menu items
ms.assetid: 0fad444e-26d9-49af-8860-044d9c10d608
ms.openlocfilehash: 6e189dd159c48b5779679d0563fab85e9b848992
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736407"
---
# <a name="how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms"></a>Como inserir um MenuStrip um menu suspenso MDI (Windows Forms)
Em alguns aplicativos, o tipo de uma janela MDI (interface de vários documentos) filho pode ser diferente da janela MDI pai. Por exemplo, a MDI pai pode ser uma planilha e a MDI filho pode ser um gráfico. Nesse caso, é recomendável atualizar o conteúdo do menu da MDI pai com o conteúdo do menu da MDI filho, visto que janelas MDI filho de tipos diferentes são ativadas.  
  
 O procedimento a seguir usa as propriedades <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>e <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> para inserir um grupo de itens de menu do menu filho MDI na parte suspensa do menu pai MDI. Fechar a janela MDI filho remove os itens de menu inseridos do MDI pai.  
  
### <a name="to-insert-a-menustrip-into-an-mdi-drop-down-menu"></a>Como inserir um MenuStrip em um menu suspenso MDI  
  
1. Crie um formulário e defina sua propriedade <xref:System.Windows.Forms.Form.IsMdiContainer%2A> como `true`.  
  
2. Adicione um <xref:System.Windows.Forms.MenuStrip> a `Form1` e defina a propriedade <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> do <xref:System.Windows.Forms.MenuStrip> como `true`.  
  
3. Adicione um item de menu de nível superior ao `Form1`<xref:System.Windows.Forms.MenuStrip> e defina sua propriedade <xref:System.Windows.Forms.Control.Text%2A> como `&File`.  
  
4. Adicione três itens de submenu ao item de menu `&File` e defina suas propriedades <xref:System.Windows.Forms.ToolStripItem.Text%2A> como `&Open`, `&Import from`e `E&xit`.  
  
5. Adicione dois itens de submenu ao item de submenu `&Import from` e defina suas propriedades <xref:System.Windows.Forms.ToolStripItem.Text%2A> como `&Word` e `&Excel`.  
  
6. Adicione um formulário ao projeto, adicione um <xref:System.Windows.Forms.MenuStrip> ao formulário e defina a propriedade <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> do `Form2`<xref:System.Windows.Forms.MenuStrip> como `true`.  
  
7. Adicione um item de menu de nível superior ao `Form2`<xref:System.Windows.Forms.MenuStrip> e defina sua propriedade <xref:System.Windows.Forms.ToolStripItem.Text%2A> como `&File`.  
  
8. Adicione itens de submenu ao menu de `&File` de `Form2` na seguinte ordem: uma <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `Save and &Close`e outra <xref:System.Windows.Forms.ToolStripSeparator>.  
  
9. Defina as propriedades <xref:System.Windows.Forms.MergeAction> e <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> dos itens de menu `Form2`, conforme mostrado na tabela a seguir.  
  
    |Item de menu Form2|Valor de MergeAction|Valor de MergeIndex|  
    |---------------------|-----------------------|----------------------|  
    |Arquivo|MatchOnly|-1|  
    |Separador|Inserir|2|  
    |Salvar|Inserir|3|  
    |Salvar e Fechar|Inserir|4|  
    |Separador|Inserir|5|  
  
10. Crie um manipulador de eventos para o evento <xref:System.Windows.Forms.Control.Click> do <xref:System.Windows.Forms.ToolStripMenuItem>de `&Open`.  
  
11. No manipulador de eventos, insira um código semelhante ao exemplo de código a seguir para criar e exibir novas instâncias de `Form2` como filhos MDI de `Form1`.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
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
  
## <a name="see-also"></a>Consulte também

- [Como criar formulários pai MDI](../advanced/how-to-create-mdi-parent-forms.md)
- [Como criar formulários filho MDI](../advanced/how-to-create-mdi-child-forms.md)
- [Visão geral do controle MenuStrip](menustrip-control-overview-windows-forms.md)
