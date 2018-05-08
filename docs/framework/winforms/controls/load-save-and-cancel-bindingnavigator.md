---
title: Como adicionar botões Carregar, Salvar e Cancelar ao controle BindingNavigator dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: 8f331c67dd22a6a9e2382ecc11d23c67cd2a5cbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>Como adicionar botões Carregar, Salvar e Cancelar ao controle BindingNavigator dos Windows Forms
O <xref:System.Windows.Forms.BindingNavigator> controle é uma finalidade especial <xref:System.Windows.Forms.ToolStrip> controle que é destinado para navegar e manipular os controles no formulário que estão associados a dados.  
  
 Porque ele é um <xref:System.Windows.Forms.ToolStrip> controle, o <xref:System.Windows.Forms.BindingNavigator> componente pode ser facilmente modificado para incluir comandos adicionais ou alternativos para o usuário.  
  
 No procedimento a seguir, uma <xref:System.Windows.Forms.TextBox> controle está associado a dados e o <xref:System.Windows.Forms.ToolStrip> controle que é adicionado ao formulário é modificado para incluir carregar, salvar e Cancelar botões.  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>Para adicionar botões carregar, salvar e cancelar ao componente do BindingNavigator  
  
1.  Adicione um controle <xref:System.Windows.Forms.TextBox> ao seu formulário.  
  
2.  Associa um <xref:System.Windows.Forms.BindingSource>, que está associada a uma fonte de dados. Neste exemplo, o <xref:System.Windows.Forms.BindingSource> está associado a um banco de dados.  
  
3.  Depois que o adaptador de conjunto de dados e tabela são geradas, arraste um <xref:System.Windows.Forms.BindingNavigator> controle no formulário.  
  
4.  Definir o <xref:System.Windows.Forms.BindingNavigator> do controle <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> propriedade para o <xref:System.Windows.Forms.BindingSource> no formulário que está associado aos controles.  
  
5.  Selecione o <xref:System.Windows.Forms.BindingNavigator> controle.  
  
6.  Clique no glifo de smart tag (![glifo de smart tag](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) para que a caixa de diálogo **Tarefas BindingNavigator** seja exibida e selecione **Editar Itens**.  
  
     O **Editor de Coleção de Itens** aparece.  
  
7.  No **Editor de Coleção de Itens**, faça o seguinte:  
  
    1.  Adicionar um <xref:System.Windows.Forms.ToolStripSeparator> e três <xref:System.Windows.Forms.ToolStripButton> itens selecionando o tipo apropriado de <xref:System.Windows.Forms.ToolStripItem> e clicando o **adicionar** botão.  
  
    2.  Definir o <xref:System.Windows.Forms.ToolStripItem.Name%2A> propriedade dos botões para**LoadButton**,**SaveButton**, e**CancelButton**, respectivamente.  
  
    3.  Definir o <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedade dos botões para**carga** `,` **salvar**, e**Cancelar**.  
  
    4.  Definir o <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriedade para cada um dos botões para**texto**. Como alternativa, você pode definir essa propriedade**imagem**ou**ImageAndText**e definir a imagem a ser exibida no <xref:System.Windows.Forms.ToolStripItem.Image%2A> propriedade.  
  
    5.  Clique em **Okey** para fechar a caixa de diálogo. Os botões são adicionados para o <xref:System.Windows.Forms.ToolStrip>.  
  
8.  Clique com o botão direito do mouse no formulário e escolha **Exibir Código**.  
  
9. No Editor de Códigos, localize a linha de código que carrega dados no adaptador de tabela. Esse código foi gerado quando você configura a vinculação de dados na etapa 2. O código deve ser semelhante ao seguinte: `TableAdapterName.Fill(DataSetName.TableName)`. Ele será mais provavelmente estará do formulário <xref:System.Windows.Forms.Form.Load> eventos.  
  
10. Criar um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripItem.Click> evento o**carga** <xref:System.Windows.Forms.ToolStripButton> criado anteriormente e mova este código de carregamento de dados para ela.  
  
     Agora, seu código deve ser semelhante ao seguinte:  
  
    ```vb  
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click  
        TableAdapterName.Fill(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Fill(DataSetName.TableName);  
    }  
    ```  
  
11. Criar um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripItem.Click> eventos do **salvar** <xref:System.Windows.Forms.ToolStripButton> criado anteriormente e escrever um código para atualizar os dados dentro da tabela, o controle está vinculado a.  
  
    ```vb  
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click  
        TableAdapterName.Update(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void SaveButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Update(DataSetName.TableName);  
    }  
    ```  
  
    > [!NOTE]
    >  Em alguns casos, o <xref:System.Windows.Forms.BindingNavigator> componente já terá um**salvar** botão, mas nenhum código será foram geradas pelo Designer de formulários do Windows. Nesse caso, você pode colocar o código acima no <xref:System.Windows.Forms.ToolStripItem.Click> manipulador de eventos para esse botão, em vez de criar um botão inteiramente novo no <xref:System.Windows.Forms.ToolStrip>. No entanto, o botão está desabilitado por padrão, portanto, você deve definir o <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> propriedade do botão para `true` para que a função de botão corretamente.  
  
12. Criar um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripItem.Click> eventos do**Cancelar** <xref:System.Windows.Forms.ToolStripButton> criado anteriormente e escrever código para cancelar as alterações para o registro de dados que é exibido.  
  
    ```vb  
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click  
        BindingSourceName.CancelEdit()  
    End Sub  
    ```  
  
    ```csharp  
    private void CancelButton_Click(System.Object sender, System.EventArgs e)  
    {  
        BindingSourceName.CancelEdit();  
    }  
    ```  
  
    > [!NOTE]
    >  O <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> método voltado para a linha de dados. Salve as alterações feitas ao exibir um registro individual antes de navegar até o próximo registro.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.ToolStrip>  
 [Controle BindingNavigator](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [Visão geral do componente BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)
