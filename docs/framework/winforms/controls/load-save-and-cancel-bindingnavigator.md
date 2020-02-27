---
title: Adicionar botões carregar, salvar e cancelar ao controle BindingNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: 0305df5e7566f9441ce09fa3346a8b2dc67c8943
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627962"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>Como adicionar botões Carregar, Salvar e Cancelar ao controle BindingNavigator dos Windows Forms

O controle de <xref:System.Windows.Forms.BindingNavigator> é um controle de <xref:System.Windows.Forms.ToolStrip> de finalidade especial que se destina a navegar e manipular controles no formulário que estão associados a dados.

Como é um controle <xref:System.Windows.Forms.ToolStrip>, o componente <xref:System.Windows.Forms.BindingNavigator> pode ser facilmente modificado para incluir comandos adicionais ou alternativos para o usuário.

No procedimento a seguir, um controle de <xref:System.Windows.Forms.TextBox> está associado a dados e o controle de <xref:System.Windows.Forms.ToolStrip> que é adicionado ao formulário é modificado para incluir os botões carregar, salvar e cancelar.

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>Adicionar os botões carregar, salvar e cancelar ao componente BindingNavigator

1. No Visual Studio, adicione um controle de <xref:System.Windows.Forms.TextBox> ao formulário.

2. Associá-lo a um <xref:System.Windows.Forms.BindingSource>, que está associado a uma fonte de dados. Para este exemplo, o <xref:System.Windows.Forms.BindingSource> está associado a um banco de dados.

3. Após a geração do conjunto de tabelas e do adaptador de tabela, arraste um controle de <xref:System.Windows.Forms.BindingNavigator> para o formulário.

4. Defina a propriedade <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> do controle de <xref:System.Windows.Forms.BindingNavigator> como a <xref:System.Windows.Forms.BindingSource> no formulário que está associado aos controles.

5. Selecione o controle <xref:System.Windows.Forms.BindingNavigator>.

6. Clique no glifo ações do designer (![seta preta pequena](./media/designer-actions-glyph.gif)) para que a caixa de diálogo **tarefas do BindingNavigator** seja exibida e selecione **Editar itens**.

     O **Editor de Coleção de Itens** aparece.

7. No **Editor de Coleção de Itens**, faça o seguinte:

    1. Adicione um <xref:System.Windows.Forms.ToolStripSeparator> e três itens de <xref:System.Windows.Forms.ToolStripButton> selecionando o tipo apropriado de <xref:System.Windows.Forms.ToolStripItem> e clicando no botão **Adicionar** .

    2. Defina a propriedade <xref:System.Windows.Forms.ToolStripItem.Name%2A> dos botões como **loadButton**, **SaveButton**e **CancelButton**, respectivamente.

    3. Defina a propriedade <xref:System.Windows.Forms.ToolStripItem.Text%2A> dos botões para **carregar**, **salvar**e **Cancelar**.

    4. Defina a propriedade <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> para cada um dos botões em **texto**. Como alternativa, você pode definir essa propriedade como **Image** ou **ImageAndText**e definir a imagem a ser exibida na propriedade <xref:System.Windows.Forms.ToolStripItem.Image%2A>.

    5. Clique em **OK** para fechar a caixa de diálogo. Os botões são adicionados à <xref:System.Windows.Forms.ToolStrip>.

8. Clique com o botão direito do mouse do formulário e escolha **Exibir código**.

9. No Editor de Códigos, localize a linha de código que carrega dados no adaptador de tabela. Esse código foi gerado quando você configura a vinculação de dados na etapa 2. O código deve ser semelhante ao seguinte: `TableAdapterName.Fill(DataSetName.TableName)`. Isso provavelmente estará no evento de <xref:System.Windows.Forms.Form.Load> do formulário.

10. Crie um manipulador de eventos para o evento <xref:System.Windows.Forms.ToolStripItem.Click> da **carga** <xref:System.Windows.Forms.ToolStripButton> criada anteriormente e mova esse código de carregamento de dados para ele.

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

11. Crie um manipulador de eventos para o evento <xref:System.Windows.Forms.ToolStripItem.Click> do<xref:System.Windows.Forms.ToolStripButton> **salvar** que você criou anteriormente e escreva o código para atualizar os dados dentro da tabela à qual o controle está vinculado.

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
    > Em alguns casos, o componente de <xref:System.Windows.Forms.BindingNavigator> já tem um botão **salvar** , mas nenhum código foi gerado pelo designer de formulários do Windows. Nesse caso, você pode posicionar o código anterior no manipulador de eventos <xref:System.Windows.Forms.ToolStripItem.Click> para esse botão, em vez de criar um botão totalmente novo na <xref:System.Windows.Forms.ToolStrip>. No entanto, o botão é desabilitado por padrão, portanto, você deve definir a propriedade <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> do botão como `true` para que o botão funcione corretamente.

12. Crie um manipulador de eventos para o evento <xref:System.Windows.Forms.ToolStripItem.Click> do **Cancelamento** <xref:System.Windows.Forms.ToolStripButton> criado anteriormente e escreva o código para cancelar as alterações no registro de dados exibido.

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
    > O método de <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> tem como escopo a linha de dados. Salve as alterações feitas ao exibir um registro individual antes de navegar até o próximo registro.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [Controle BindingNavigator](bindingnavigator-control-windows-forms.md)
- [Visão geral do componente BindingSource](bindingsource-component-overview.md)
