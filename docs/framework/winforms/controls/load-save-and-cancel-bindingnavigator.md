---
title: 'Como: Adicionar botões Carregar, Salvar e Cancelar ao controle BindingNavigator do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: 2d4867c0bc4feb7b43e15614fc56a3c709cef9e7
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991735"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>Como: Adicionar botões Carregar, Salvar e Cancelar ao controle BindingNavigator do Windows Forms

O <xref:System.Windows.Forms.BindingNavigator> controle é um controle de finalidade <xref:System.Windows.Forms.ToolStrip> especial que destina-se a navegar e manipular controles no formulário que estão associados a dados.

Como é um <xref:System.Windows.Forms.ToolStrip> controle, o <xref:System.Windows.Forms.BindingNavigator> componente pode ser facilmente modificado para incluir comandos adicionais ou alternativos para o usuário.

No procedimento a seguir, um <xref:System.Windows.Forms.TextBox> controle é associado a dados e o <xref:System.Windows.Forms.ToolStrip> controle que é adicionado ao formulário é modificado para incluir os botões carregar, salvar e cancelar.

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>Adicionar os botões carregar, salvar e cancelar ao componente BindingNavigator

1. No Visual Studio, adicione um <xref:System.Windows.Forms.TextBox> controle ao formulário.

2. Associe-o a <xref:System.Windows.Forms.BindingSource>um, que está associado a uma fonte de dados. Para este exemplo, o <xref:System.Windows.Forms.BindingSource> está associado a um banco de dados.

3. Após a geração do conjunto de tabelas e do adaptador de <xref:System.Windows.Forms.BindingNavigator> tabela, arraste um controle para o formulário.

4. Defina a <xref:System.Windows.Forms.BindingNavigator> Propriedade do <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> controle como o <xref:System.Windows.Forms.BindingSource> no formulário que está associado aos controles.

5. Selecione o controle <xref:System.Windows.Forms.BindingNavigator>.

6. Clique no glifo de smart tag (![glifo de smart tag](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) para que a caixa de diálogo **Tarefas BindingNavigator** seja exibida e selecione **Editar Itens**.

     O **Editor de Coleção de Itens** aparece.

7. No **Editor de Coleção de Itens**, faça o seguinte:

    1. Adicione um <xref:System.Windows.Forms.ToolStripSeparator> e três <xref:System.Windows.Forms.ToolStripButton> itens <xref:System.Windows.Forms.ToolStripItem> selecionando o tipo apropriado e clicando no botão **Adicionar** .

    2. Defina a <xref:System.Windows.Forms.ToolStripItem.Name%2A> propriedade dos botões como **loadButton**, **SaveButton**e **CancelButton**, respectivamente.

    3. Defina a <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedade dos botões para **carregar**, **salvar**e **Cancelar**.

    4. Defina a <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriedade para cada um dos botões em **texto**. Como alternativa, você pode definir essa propriedade como **Image** ou **ImageAndText**e definir a imagem a ser <xref:System.Windows.Forms.ToolStripItem.Image%2A> exibida na propriedade.

    5. Clique em **OK** para fechar a caixa de diálogo. Os botões são adicionados ao <xref:System.Windows.Forms.ToolStrip>.

8. Clique com o botão direito do mouse no formulário e escolha **Exibir Código**.

9. No Editor de Códigos, localize a linha de código que carrega dados no adaptador de tabela. Esse código foi gerado quando você configura a vinculação de dados na etapa 2. O código deve ser semelhante ao seguinte: `TableAdapterName.Fill(DataSetName.TableName)`. Provavelmente estará no evento do <xref:System.Windows.Forms.Form.Load> formulário.

10. Crie um manipulador de eventos para <xref:System.Windows.Forms.ToolStripItem.Click> o evento da **carga** <xref:System.Windows.Forms.ToolStripButton> que você criou anteriormente e mova esse código de carregamento de dados para ele.

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

11. Crie um manipulador de eventos para <xref:System.Windows.Forms.ToolStripItem.Click> o evento do **salvamento** <xref:System.Windows.Forms.ToolStripButton> criado anteriormente e escreva o código para atualizar os dados dentro da tabela à qual o controle está vinculado.

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
    > Em alguns casos, o <xref:System.Windows.Forms.BindingNavigator> componente já tem um botão **salvar** , mas nenhum código foi gerado pelo designer de formulários do Windows. Nesse caso, você pode posicionar o código anterior no <xref:System.Windows.Forms.ToolStripItem.Click> manipulador de eventos para esse botão, em vez de criar um botão totalmente novo <xref:System.Windows.Forms.ToolStrip>no. No entanto, o botão é desabilitado por padrão, portanto, <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> você deve definir a propriedade `true` do botão como para que o botão funcione corretamente.

12. Crie um manipulador de eventos para <xref:System.Windows.Forms.ToolStripItem.Click> o evento do **cancelamento** <xref:System.Windows.Forms.ToolStripButton> criado anteriormente e escreva o código para cancelar as alterações no registro de dados exibido.

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
    > O <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> método tem como escopo a linha de dados. Salve as alterações feitas ao exibir um registro individual antes de navegar até o próximo registro.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [Controle BindingNavigator](bindingnavigator-control-windows-forms.md)
- [Visão geral do componente BindingSource](bindingsource-component-overview.md)
