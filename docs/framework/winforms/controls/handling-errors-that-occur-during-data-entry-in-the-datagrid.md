---
title: 'Walkthrough: Manipulando erros que ocorrem durante a entrada de dados no controle DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
ms.openlocfilehash: 77a4dcd9cf069ed8bbee6c49aa41db619c8e12ff
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738729"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>Instruções passo a passo: identificando erros que ocorram durante a entrada de dados no controle DataGridView dos Windows Forms

O tratamento de erros do armazenamento de dados subjacente é um recurso necessário para um aplicativo de entrada de dados. O controle de <xref:System.Windows.Forms.DataGridView> de Windows Forms facilita isso expondo o evento de <xref:System.Windows.Forms.DataGridView.DataError>, que é gerado quando o repositório de dados detecta uma violação de restrição ou uma regra de negócio quebrada.

Neste tutorial, você irá recuperar linhas da tabela `Customers` no banco de dados de exemplo Northwind e exibi-las em um controle de <xref:System.Windows.Forms.DataGridView>. Quando um valor de `CustomerID` duplicado for detectado em uma nova linha ou em uma linha existente editada, o evento de <xref:System.Windows.Forms.DataGridView.DataError> ocorrerá, o qual será tratado exibindo uma <xref:System.Windows.Forms.MessageBox> que descreve a exceção.

Para copiar o código deste tópico como uma única lista, consulte [Como tratar erros que ocorrem durante a entrada de dados no controle DataGridView do Windows Forms](handle-errors-that-occur-during-data-entry-in-the-datagrid.md).

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}

Para concluir este passo a passo, você precisará de:

- Acesso a um servidor que tem o banco de dados de exemplo SQL Server Northwind.

## <a name="creating-the-form"></a>Criando o formulário

#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>Tratar erros de entrada de dados no controle DataGridView

1. Crie uma classe que derive de <xref:System.Windows.Forms.Form> e contenha um controle de <xref:System.Windows.Forms.DataGridView> e um componente de <xref:System.Windows.Forms.BindingSource>.

    O exemplo de código a seguir fornece inicialização básica e inclui um método `Main`.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]

2. Implemente um método na definição de classe do formulário para manipular os detalhes de conexão ao banco de dados.

    Este exemplo de código usa um método `GetData` que retorna um objeto <xref:System.Data.DataTable> populado. Verifique se a variável `connectionString` é definida como um valor apropriado para o banco de dados.

    > [!IMPORTANT]
    > O armazenamento das informações confidenciais, como uma senha, dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]

3. Implemente um manipulador para o evento <xref:System.Windows.Forms.Form.Load> do seu formulário que inicializa o <xref:System.Windows.Forms.DataGridView> e <xref:System.Windows.Forms.BindingSource> e configura a associação de dados.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]

4. Manipule o evento de <xref:System.Windows.Forms.DataGridView.DataError> no <xref:System.Windows.Forms.DataGridView>.

    Se o contexto do erro for uma operação de confirmação, exiba o erro em um <xref:System.Windows.Forms.MessageBox>.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]

## <a name="testing-the-application"></a>Testando o aplicativo

Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.

#### <a name="to-test-the-form"></a>Para testar o formulário

- Pressione F5 para executar o aplicativo.

  Você verá um controle <xref:System.Windows.Forms.DataGridView> preenchido com dados da tabela Customers. Se você inserir um valor duplicado para `CustomerID` e confirmar a edição, o valor da célula será revertido automaticamente e você verá um <xref:System.Windows.Forms.MessageBox> que exibe o erro de entrada de dados.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Esse aplicativo oferece uma compreensão básica dos recursos do controle de <xref:System.Windows.Forms.DataGridView>. Você pode personalizar a aparência e o comportamento do controle de <xref:System.Windows.Forms.DataGridView> de várias maneiras:

- Alterar estilos de borda e cabeçalho. Para obter mais informações, consulte [Como alterar os estilos de borda e linha de grade no controle DataGridView dos Windows Forms](change-the-border-and-gridline-styles-in-the-datagrid.md).

- Habilitar ou restringir a entrada do usuário para o controle de <xref:System.Windows.Forms.DataGridView>. Para obter mais informações, consulte [Como evitar a adição e a exclusão de linhas no controle DataGridView do Windows Forms](prevent-row-addition-and-deletion-datagridview.md) e [Como tornar colunas somente leitura no controle DataGridView do Windows Forms](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).

- Valide a entrada do usuário para o controle de <xref:System.Windows.Forms.DataGridView>. Para obter mais informações, consulte [Passo a passo: validando dados no controle DataGridView dos Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).

- Manipule conjuntos de dados muito grandes usando o modo virtual. Para obter mais informações, consulte [Passo a passo: implementando o modo virtual no controle DataGridView dos Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).

- Personalize a aparência das células. Para obter mais informações, consulte [Como personalizar a aparência de células no controle DataGridView dos Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md) e [Como definir estilos de célula padrão no controle DataGridView dos Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Entrada de dados no controle DataGridView do Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Como manipular erros ocorridos durante a entrada de dados no controle DataGridView dos Windows Forms](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Passo a passo: validando dados no controle DataGridView dos Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md)
