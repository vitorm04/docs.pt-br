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
ms.openlocfilehash: f190bfa29af480fa104f30b21b1af517c413b838
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211571"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>Como: Adicionar botões Carregar, Salvar e Cancelar ao controle BindingNavigator do Windows Forms

O <xref:System.Windows.Forms.BindingNavigator> controle é uma finalidade especial <xref:System.Windows.Forms.ToolStrip> controle que é destinado para navegar e manipular controles no formulário que estão associados aos dados.

Porque ele é um <xref:System.Windows.Forms.ToolStrip> controle, o <xref:System.Windows.Forms.BindingNavigator> componente pode ser facilmente modificado para incluir comandos adicionais ou alternativos para o usuário.

No procedimento a seguir, uma <xref:System.Windows.Forms.TextBox> controle é associado a dados e o <xref:System.Windows.Forms.ToolStrip> controle que é adicionado ao formulário é modificado para incluem carregar, salvar e Cancelar botões.

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>Adicione carga, salvar, botões e Cancelar ao componente do BindingNavigator

1. No Visual Studio, adicione um <xref:System.Windows.Forms.TextBox> controle ao seu formulário.

2. Associe-o a um <xref:System.Windows.Forms.BindingSource>, que está associada a uma fonte de dados. Neste exemplo, o <xref:System.Windows.Forms.BindingSource> está associado a um banco de dados.

3. Depois que o adaptador de conjunto de dados e tabela são gerados, arraste um <xref:System.Windows.Forms.BindingNavigator> controle ao formulário.

4. Defina a <xref:System.Windows.Forms.BindingNavigator> do controle <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> propriedade para o <xref:System.Windows.Forms.BindingSource> no formulário que está associado aos controles.

5. Selecione o <xref:System.Windows.Forms.BindingNavigator> controle.

6. Clique no glifo de smart tag (![glifo de smart tag](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) para que a caixa de diálogo **Tarefas BindingNavigator** seja exibida e selecione **Editar Itens**.

     O **Editor de Coleção de Itens** aparece.

7. No **Editor de Coleção de Itens**, faça o seguinte:

    1. Adicionar um <xref:System.Windows.Forms.ToolStripSeparator> e três <xref:System.Windows.Forms.ToolStripButton> itens selecionando o tipo apropriado de <xref:System.Windows.Forms.ToolStripItem> e clicando o **Add** botão.

    2. Defina as <xref:System.Windows.Forms.ToolStripItem.Name%2A> propriedade dos botões como **LoadButton**, **SaveButton**, e **CancelButton**, respectivamente.

    3. Defina as <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedade dos botões como **carga**, **salvar**, e **Cancelar**.

    4. Defina as <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriedade para cada um dos botões para **texto**. Como alternativa, você pode definir essa propriedade **imagem** ou **ImageAndText**e definir a imagem a ser exibido no <xref:System.Windows.Forms.ToolStripItem.Image%2A> propriedade.

    5. Clique em **Okey** para fechar a caixa de diálogo. Os botões são adicionados a <xref:System.Windows.Forms.ToolStrip>.

8. Clique com o botão direito do mouse no formulário e escolha **Exibir Código**.

9. No Editor de Códigos, localize a linha de código que carrega dados no adaptador de tabela. Esse código foi gerado quando você configura a vinculação de dados na etapa 2. O código deve ser semelhante ao seguinte: `TableAdapterName.Fill(DataSetName.TableName)`. Ele estará mais provavelmente, o formulário <xref:System.Windows.Forms.Form.Load> eventos.

10. Crie um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripItem.Click> eventos do **carga** <xref:System.Windows.Forms.ToolStripButton> criado anteriormente e mover esse código de carregamento de dados para ela.

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

11. Crie um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripItem.Click> eventos do **salvar** <xref:System.Windows.Forms.ToolStripButton> criado anteriormente e escreva o código para atualizar os dados dentro da tabela de controle está vinculado a.

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
    > Em alguns casos, o <xref:System.Windows.Forms.BindingNavigator> componente já tem uma **salvar** botão, mas nenhum código foi gerado pelo Designer de formulários do Windows. Nesse caso, você pode colocar o código anterior a <xref:System.Windows.Forms.ToolStripItem.Click> manipulador de eventos para esse botão, em vez de criar um botão totalmente novo no <xref:System.Windows.Forms.ToolStrip>. No entanto, o botão está desabilitado por padrão, portanto, você deve definir a <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> propriedade do botão para `true` para que o botão funcione corretamente.

12. Crie um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripItem.Click> eventos do **Cancelar** <xref:System.Windows.Forms.ToolStripButton> criado anteriormente e escreva código para cancelar as alterações para o registro de dados que é exibida.

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
    > O <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> está no escopo do método para a linha de dados. Salve as alterações feitas ao exibir um registro individual antes de navegar até o próximo registro.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [Controle BindingNavigator](bindingnavigator-control-windows-forms.md)
- [Visão geral do componente BindingSource](bindingsource-component-overview.md)
