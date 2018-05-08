---
title: Como inserir um MenuStrip um menu suspenso MDI (Windows Forms)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], inserting
- MenuStrip control [Windows Forms], merging
- MDI [Windows Forms], merging menu items
ms.assetid: 0fad444e-26d9-49af-8860-044d9c10d608
ms.openlocfilehash: 9f7534720f9be185a176247ce00b0be5e2649bff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms"></a>Como inserir um MenuStrip um menu suspenso MDI (Windows Forms)
Em alguns aplicativos, o tipo de uma janela MDI (interface de vários documentos) filho pode ser diferente da janela MDI pai. Por exemplo, a MDI pai pode ser uma planilha e a MDI filho pode ser um gráfico. Nesse caso, é recomendável atualizar o conteúdo do menu da MDI pai com o conteúdo do menu da MDI filho, visto que janelas MDI filho de tipos diferentes são ativadas.  
  
 O procedimento a seguir usa o <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, e <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> propriedades para inserir um grupo de itens de menu no menu de filho MDI a parte do menu suspenso do menu MDI pai. Fechar a janela MDI filho remove os itens de menu inseridos do MDI pai.  
  
### <a name="to-insert-a-menustrip-into-an-mdi-drop-down-menu"></a>Como inserir um MenuStrip em um menu suspenso MDI  
  
1.  Criar um formulário e defina seu <xref:System.Windows.Forms.Form.IsMdiContainer%2A> propriedade `true`.  
  
2.  Adicionar um <xref:System.Windows.Forms.MenuStrip> para `Form1` e defina o <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> propriedade o <xref:System.Windows.Forms.MenuStrip> para `true`.  
  
3.  Adicionar um item de menu de nível superior para o `Form1` <xref:System.Windows.Forms.MenuStrip> e defina seu <xref:System.Windows.Forms.Control.Text%2A> propriedade `&File`.  
  
4.  Adicionar três itens de submenu para o `&File` item de menu e defina seus <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedades `&Open`, `&Import from`, e `E&xit`.  
  
5.  Adicionar dois itens de submenu para o `&Import from` item de submenu e defina seus <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedades `&Word` e `&Excel`.  
  
6.  Adicionar um formulário para o projeto, adicione um <xref:System.Windows.Forms.MenuStrip> para o formulário e o <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> propriedade do `Form2` <xref:System.Windows.Forms.MenuStrip> para `true`.  
  
7.  Adicionar um item de menu de nível superior para o `Form2` <xref:System.Windows.Forms.MenuStrip> e defina seu <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedade `&File`.  
  
8.  Adicionar itens de submenu para o `&File` menu `Form2` na seguinte ordem: um <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `&Close``and Save`e outro <xref:System.Windows.Forms.ToolStripSeparator>.  
  
9. Definir o <xref:System.Windows.Forms.MergeAction> e <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> propriedades do `Form2` itens de menu, conforme mostrado na tabela a seguir.  
  
    |Item de menu Form2|Valor de MergeAction|Valor de MergeIndex|  
    |---------------------|-----------------------|----------------------|  
    |Arquivo|MatchOnly|-1|  
    |Separador|Inserir|2|  
    |Salvar|Inserir|3|  
    |Salvar e Fechar|Inserir|4|  
    |Separador|Inserir|5|  
  
10. Criar um manipulador de eventos para o <xref:System.Windows.Forms.Control.Click> evento o `&Open` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
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
  
12. Coloque o código semelhante ao exemplo de código a seguir no `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> para registrar o manipulador de eventos.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Dois <xref:System.Windows.Forms.Form> controles denominados `Form1` e `Form2`.  
  
-   Um <xref:System.Windows.Forms.MenuStrip> control em `Form1` chamado `menuStrip1`e um <xref:System.Windows.Forms.MenuStrip> control em `Form2` chamado `menuStrip2`.  
  
-   Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também  
 [Como criar formulários pai MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Como criar formulários filho MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Visão geral do controle MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
