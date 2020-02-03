---
title: 'Walkthrough: validar dados no controle DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating data [Windows Forms], Windows Forms
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: a4f1d015-2969-430c-8ea2-b612d179c290
ms.openlocfilehash: 45753fb206ad58616c9a727bd81bd2458db6053e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740097"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>Instruções passo a passo: validando dados no controle DataGridView dos Windows Forms

Ao exibir a funcionalidade de entrada de dados para usuários, frequentemente é necessário validar os dados inseridos no formulário. A classe <xref:System.Windows.Forms.DataGridView> fornece uma maneira conveniente de executar a validação antes que os dados sejam confirmados no armazenamento de dados. Você pode validar os dados manipulando o evento <xref:System.Windows.Forms.DataGridView.CellValidating>, que é gerado pelo <xref:System.Windows.Forms.DataGridView> quando a célula atual é alterada.

Neste tutorial, você irá recuperar linhas da tabela `Customers` no banco de dados de exemplo Northwind e exibi-las em um controle de <xref:System.Windows.Forms.DataGridView>. Quando um usuário edita uma célula na coluna `CompanyName` e tenta sair da célula, o manipulador de eventos <xref:System.Windows.Forms.DataGridView.CellValidating> examina a nova cadeia de caracteres do nome da empresa para certificar-se de que ela não está vazia; Se o novo valor for uma cadeia de caracteres vazia, o <xref:System.Windows.Forms.DataGridView> impedirá que o cursor do usuário saia da célula até que uma cadeia de caracteres não vazia seja inserida.

Para copiar o código deste tópico como uma única lista, consulte [Como Validar Dados no Controle DataGridView do Windows Forms](how-to-validate-data-in-the-windows-forms-datagridview-control.md).

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}

Para concluir este passo a passo, você precisará de:

- Acesso a um servidor que tem o banco de dados de exemplo SQL Server Northwind.

## <a name="creating-the-form"></a>Criando o formulário

#### <a name="to-validate-data-entered-in-a-datagridview"></a>Validar dados inseridos em um DataGridView

1. Crie uma classe que derive de <xref:System.Windows.Forms.Form> e contenha um controle de <xref:System.Windows.Forms.DataGridView> e um componente de <xref:System.Windows.Forms.BindingSource>.

    O exemplo de código a seguir fornece inicialização básica e inclui um método `Main`.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]

2. Implemente um método na definição de classe do formulário para manipular os detalhes de conexão ao banco de dados.

    Este exemplo de código usa um método `GetData` que retorna um objeto <xref:System.Data.DataTable> populado. Verifique se a variável `connectionString` é definida como um valor apropriado para o banco de dados.

    > [!IMPORTANT]
    > O armazenamento das informações confidenciais, como uma senha, dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows, também conhecida como segurança integrada, é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]

3. Implemente um manipulador para o evento <xref:System.Windows.Forms.Form.Load> do seu formulário que inicializa o <xref:System.Windows.Forms.DataGridView> e <xref:System.Windows.Forms.BindingSource> e configura a associação de dados.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]

4. Implemente manipuladores para os eventos <xref:System.Windows.Forms.DataGridView.CellValidating> e <xref:System.Windows.Forms.DataGridView.CellEndEdit> do controle de <xref:System.Windows.Forms.DataGridView>.

    O manipulador de eventos <xref:System.Windows.Forms.DataGridView.CellValidating> é onde você determina se o valor de uma célula na coluna `CompanyName` está vazio. Se o valor da célula falhar na validação, defina a propriedade <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> da classe <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType> como `true`. Isso faz com que o controle de <xref:System.Windows.Forms.DataGridView> impeça que o cursor saia da célula. Defina a propriedade <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> na linha como uma cadeia de caracteres explicativa. Isso exibirá um ícone de erro com uma ToolTip que contém o texto de erro. No manipulador de eventos <xref:System.Windows.Forms.DataGridView.CellEndEdit>, defina a propriedade <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> na linha como a cadeia de caracteres vazia. O evento <xref:System.Windows.Forms.DataGridView.CellEndEdit> ocorre somente quando a célula sai do modo de edição, o que não pode ser feito se falhar na validação.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]

## <a name="testing-the-application"></a>Testando o aplicativo

Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.

#### <a name="to-test-the-form"></a>Para testar o formulário

- Compile e execute o aplicativo.

  Você verá uma <xref:System.Windows.Forms.DataGridView> preenchida com dados da tabela `Customers`. Ao clicar duas vezes em uma célula da coluna `CompanyName`, é possível editar o valor. Se você excluir todos os caracteres e pressionar a tecla TAB para sair da célula, a <xref:System.Windows.Forms.DataGridView> impedirá que você saia. Quando você digita uma cadeia de caracteres não vazia na célula, o controle de <xref:System.Windows.Forms.DataGridView> permite sair da célula.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Esse aplicativo oferece uma compreensão básica dos recursos do controle de <xref:System.Windows.Forms.DataGridView>. Você pode personalizar a aparência e o comportamento do controle de <xref:System.Windows.Forms.DataGridView> de várias maneiras:

- Alterar estilos de borda e cabeçalho. Para obter mais informações, consulte [Como alterar os estilos de borda e linha de grade no controle DataGridView dos Windows Forms](change-the-border-and-gridline-styles-in-the-datagrid.md).

- Habilitar ou restringir a entrada do usuário para o controle de <xref:System.Windows.Forms.DataGridView>. Para obter mais informações, consulte [Como evitar a adição e a exclusão de linhas no controle DataGridView do Windows Forms](prevent-row-addition-and-deletion-datagridview.md) e [Como tornar colunas somente leitura no controle DataGridView do Windows Forms](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).

- Verifique a entrada do usuário para erros relacionados ao banco de dados. Para obter mais informações, consulte [Instruções passo a passo: identificando erros que ocorrem durante a entrada de dados no controle DataGridView do Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).

- Manipule conjuntos de dados muito grandes usando o modo virtual. Para obter mais informações, consulte [Passo a passo: implementando o modo virtual no controle DataGridView dos Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).

- Personalize a aparência das células. Para obter mais informações, consulte [Como Personalizar a Aparência de Células no Controle DataGridView do Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md) e [Como Definir Estilos de Fonte e Cor no Controle DataGridView do Windows Forms](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Entrada de dados no controle DataGridView do Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Como validar dados no controle DataGridView dos Windows Forms](how-to-validate-data-in-the-windows-forms-datagridview-control.md)
- [Passo a passo: manipulando erros que ocorrem durante a entrada de dados no controle DataGridView dos Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md)
