---
title: Como remover um ToolStripMenuItem de um menu suspenso MDI
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
ms.openlocfilehash: 3198195cf0991734826508aa65818505bf2038c8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735843"
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a>Como remover um ToolStripMenuItem de um menu suspenso MDI (Windows Forms)
Em alguns aplicativos, o tipo de uma janela filho MDI (interface de vários documentos) pode ser diferente da janela MDI pai. Por exemplo, a MDI pai pode ser uma planilha e a MDI filho pode ser um gráfico. Nesse caso, é recomendável atualizar o conteúdo do menu do MDI pai com o conteúdo do menu do MDI filho, visto que janelas MDI filho de tipos diferentes são ativadas.  
  
 O procedimento a seguir usa as propriedades <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>e <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> para remover um item de menu da parte suspensa do menu pai MDI. Fechar a janela filho MDI restaura os itens de menu removidos para o menu pai MDI.  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a>Para remover um MenuStrip de um menu suspenso MDI  
  
1. Crie um formulário e defina sua propriedade <xref:System.Windows.Forms.Form.IsMdiContainer%2A> como `true`.  
  
2. Adicione um <xref:System.Windows.Forms.MenuStrip> a `Form1` e defina a propriedade <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> do <xref:System.Windows.Forms.MenuStrip> como `true`.  
  
3. Adicione um item de menu de nível superior ao `Form1`<xref:System.Windows.Forms.MenuStrip> e defina sua propriedade <xref:System.Windows.Forms.Control.Text%2A> como `&File`.  
  
4. Adicione três itens de submenu ao item de menu `&File` e defina suas propriedades <xref:System.Windows.Forms.ToolStripItem.Text%2A> como `&Open`, `&Import from`e `E&xit`.  
  
5. Adicione dois itens de submenu ao item de submenu `&Import from` e defina suas propriedades <xref:System.Windows.Forms.ToolStripItem.Text%2A> como `&Word` e `&Excel`.  
  
6. Adicione um formulário ao projeto, adicione um <xref:System.Windows.Forms.MenuStrip> ao formulário e defina a propriedade <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> do `Form2`<xref:System.Windows.Forms.MenuStrip> como `true`.  
  
7. Adicione um item de menu de nível superior ao `Form2`<xref:System.Windows.Forms.MenuStrip> e defina sua propriedade <xref:System.Windows.Forms.ToolStripItem.Text%2A> como `&File`.  
  
8. Adicione um item de submenu `&Import from` ao `&File` menu de `Form2`e adicione um item de submenu `&Word` ao menu `&File`.  
  
9. Defina as propriedades <xref:System.Windows.Forms.MergeAction> e <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> dos itens de menu `Form2`, conforme mostrado na tabela a seguir.  
  
    |Item de menu Form2|Valor de MergeAction|Valor de MergeIndex|  
    |---------------------|-----------------------|----------------------|  
    |File|MatchOnly|-1|  
    |Importar do|MatchOnly|-1|  
    |Word|Remover|-1|  
  
10. Em `Form1`, crie um manipulador de eventos para o evento <xref:System.Windows.Forms.Control.Click> do <xref:System.Windows.Forms.ToolStripMenuItem>de `&Open`.  
  
11. Dentro do manipulador de eventos, insira um código semelhante ao exemplo de código a seguir para criar e exibir novas instâncias de `Form2` como filhos MDI de `Form1`:  
  
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
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Dois controles de <xref:System.Windows.Forms.Form> chamados `Form1` e `Form2`.  
  
- Um controle <xref:System.Windows.Forms.MenuStrip> em `Form1` chamado `menuStrip1`e um controle <xref:System.Windows.Forms.MenuStrip> em `Form2` chamado `menuStrip2`.  
  
- Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Veja também

- [Como criar formulários pai MDI](../advanced/how-to-create-mdi-parent-forms.md)
- [Como criar formulários filho MDI](../advanced/how-to-create-mdi-child-forms.md)
- [Visão geral do controle MenuStrip](menustrip-control-overview-windows-forms.md)
