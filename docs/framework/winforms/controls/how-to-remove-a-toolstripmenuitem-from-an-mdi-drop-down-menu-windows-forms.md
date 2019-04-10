---
title: 'Como: Remover um ToolStripMenuItem de um Menu suspenso MDI (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], removing from MDI drop-down menus
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], removing
- MDI [Windows Forms], merging menu items
ms.assetid: bdafe60d-82ee-45bc-97fe-eeefca6e54c1
ms.openlocfilehash: 7c84d260783e3a511b5ef6a651c71f1ee55acffe
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295335"
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a>Como: Remover um ToolStripMenuItem de um Menu suspenso MDI (Windows Forms)
Em alguns aplicativos, o tipo de uma janela MDI (interface de vários documentos) filho pode ser diferente da janela MDI pai. Por exemplo, a MDI pai pode ser uma planilha e a MDI filho pode ser um gráfico. Nesse caso, é recomendável atualizar o conteúdo do menu da MDI pai com o conteúdo do menu da MDI filho, visto que janelas MDI filho de tipos diferentes são ativadas.  
  
 O procedimento a seguir usa o <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, e <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> propriedades para remover um item de menu da parte suspensa do menu MDI pai. Fechando a janela filho MDI restaura os itens de menu removido ao menu MDI pai.  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a>Para remover um MenuStrip um menu suspenso do MDI  
  
1. Criar um formulário e defina suas <xref:System.Windows.Forms.Form.IsMdiContainer%2A> propriedade para `true`.  
  
2. Adicionar um <xref:System.Windows.Forms.MenuStrip> para `Form1` e defina o <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> propriedade o <xref:System.Windows.Forms.MenuStrip> para `true`.  
  
3. Adicionar um item de menu de nível superior para o `Form1`<xref:System.Windows.Forms.MenuStrip> e defina sua <xref:System.Windows.Forms.Control.Text%2A> propriedade `&File`.  
  
4. Adicione três itens de submenu para o `&File` item de menu e defina seus <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedades a serem `&Open`, `&Import from`, e `E&xit`.  
  
5. Adicione dois itens de submenu para o `&Import from` item de submenu e defina seus <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedades a serem `&Word` e `&Excel`.  
  
6. Adicionar um formulário ao projeto, adicione uma <xref:System.Windows.Forms.MenuStrip> para o formulário e defina o <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> propriedade da `Form2`<xref:System.Windows.Forms.MenuStrip> para `true`.  
  
7. Adicionar um item de menu de nível superior para o `Form2`<xref:System.Windows.Forms.MenuStrip> e defina sua <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedade `&File`.  
  
8. Adicionar um `&Import from` item de submenu para o `&File` menu da `Form2`e adicione um `&Word` item de submenu ao `&File` menu.  
  
9. Defina as <xref:System.Windows.Forms.MergeAction> e <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> propriedades do `Form2` itens de menu, conforme mostrado na tabela a seguir.  
  
    |Item de menu Form2|Valor de MergeAction|Valor de MergeIndex|  
    |---------------------|-----------------------|----------------------|  
    |Arquivo|MatchOnly|-1|  
    |Importar do|MatchOnly|-1|  
    |Palavra|Remover|-1|  
  
10. Na `Form1`, crie um manipulador de eventos para o <xref:System.Windows.Forms.Control.Click> evento do `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.  
  
11. No manipulador de eventos, insira um código semelhante ao exemplo de código a seguir para criar e exibir novas instâncias de `Form2` como filhos MDI de `Form1`:  
  
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
  
12. Coloque um código semelhante ao seguinte exemplo de código no `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> para registrar o manipulador de eventos.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Duas <xref:System.Windows.Forms.Form> controles denominados `Form1` e `Form2`.  
  
-   Um <xref:System.Windows.Forms.MenuStrip> control em `Form1` denominado `menuStrip1`e uma <xref:System.Windows.Forms.MenuStrip> control em `Form2` chamado `menuStrip2`.  
  
-   Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também

- [Como: criar formulários pai MDI](../advanced/how-to-create-mdi-parent-forms.md)
- [Como: criar formulários filho MDI](../advanced/how-to-create-mdi-child-forms.md)
- [Visão geral do controle MenuStrip](menustrip-control-overview-windows-forms.md)
