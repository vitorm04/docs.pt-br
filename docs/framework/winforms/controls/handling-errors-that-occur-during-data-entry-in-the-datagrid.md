---
title: 'Passo a passo: Identificando Erros que Ocorrem Durante a Entrada de Dados no Controle DataGridView do Windows Forms'
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
ms.openlocfilehash: cee6fe3b049378fa7bbe2585a3607049eaf231bc
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046085"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>Passo a passo: Identificando Erros que Ocorrem Durante a Entrada de Dados no Controle DataGridView do Windows Forms

O tratamento de erros do armazenamento de dados subjacente é um recurso necessário para um aplicativo de entrada de dados. O controle <xref:System.Windows.Forms.DataGridView> de Windows Forms facilita esse processo expondo o <xref:System.Windows.Forms.DataGridView.DataError> evento, que é gerado quando o armazenamento de dados detecta uma violação de restrição ou uma regra de negócio quebrada.

Neste tutorial, você irá recuperar linhas da `Customers` tabela no banco de dados de exemplo Northwind e exibi-las em um <xref:System.Windows.Forms.DataGridView> controle. Quando um valor `CustomerID` duplicado for detectado em uma nova linha ou em uma linha existente editada, o <xref:System.Windows.Forms.DataGridView.DataError> evento ocorrerá, que será manipulado <xref:System.Windows.Forms.MessageBox> exibindo um que descreve a exceção.

Para copiar o código deste tópico como uma única listagem, confira [Como: Manipule erros que ocorrem durante a entrada de dados no controle](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)DataGridView Windows Forms.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este passo a passo, você precisará de:

- Acesso a um servidor com o banco de dados de exemplo Northwind do SQL Server.

## <a name="creating-the-form"></a>Criando o formulário

#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>Tratar erros de entrada de dados no controle DataGridView

1. Crie uma classe que deriva de <xref:System.Windows.Forms.Form> e contém um <xref:System.Windows.Forms.DataGridView> controle e um <xref:System.Windows.Forms.BindingSource> componente.

    O exemplo de código a seguir fornece inicialização básica e inclui um método `Main`.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]

2. Implemente um método na definição de classe do formulário para manipular os detalhes de conexão ao banco de dados.

    Este exemplo de código usa `GetData` um método que retorna um <xref:System.Data.DataTable> objeto populado. Verifique se a variável `connectionString` é definida como um valor apropriado para o banco de dados.

    > [!IMPORTANT]
    > O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]

3. Implemente um manipulador para o evento <xref:System.Windows.Forms.Form.Load> do formulário que inicializa <xref:System.Windows.Forms.DataGridView> o <xref:System.Windows.Forms.BindingSource> e e define a associação de dados.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]

4. Manipule o <xref:System.Windows.Forms.DataGridView.DataError> evento <xref:System.Windows.Forms.DataGridView>no.

    Se o contexto do erro for uma operação de confirmação, exiba o erro em um <xref:System.Windows.Forms.MessageBox>.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]

## <a name="testing-the-application"></a>Testando o aplicativo

Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.

#### <a name="to-test-the-form"></a>Para testar o formulário

- Pressione F5 para executar o aplicativo.

  Você verá um <xref:System.Windows.Forms.DataGridView> controle preenchido com dados da tabela Customers. Se você inserir um valor duplicado `CustomerID` para e confirmar a edição, o valor da célula será revertido automaticamente e você <xref:System.Windows.Forms.MessageBox> verá um que exibe o erro de entrada de dados.

## <a name="next-steps"></a>Próximas etapas

Esse aplicativo oferece uma compreensão básica dos <xref:System.Windows.Forms.DataGridView> recursos do controle. Você pode personalizar a aparência e o comportamento do <xref:System.Windows.Forms.DataGridView> controle de várias maneiras:

- Alterar estilos de borda e cabeçalho. Para obter mais informações, confira [Como: Altere os estilos da borda e da linha de grade no](change-the-border-and-gridline-styles-in-the-datagrid.md)controle Windows Forms DataGridView.

- Habilitar ou restringir a entrada do usuário <xref:System.Windows.Forms.DataGridView> para o controle. Para obter mais informações, confira [Como: Impeça a adição e exclusão de linhas no controle](prevent-row-addition-and-deletion-datagridview.md)Windows Forms DataGridView e [como: Tornar as colunas somente leitura no controle](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)Windows Forms DataGridView.

- Valide a entrada do usuário <xref:System.Windows.Forms.DataGridView> para o controle. Para obter mais informações, confira [Passo a passo: Validação de dados no controle](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)Windows Forms DataGridView.

- Manipule grandes conjuntos de dados usando o modo virtual. Para obter mais informações, confira [Passo a passo: Implementando o modo virtual no controle](implementing-virtual-mode-wf-datagridview-control.md)Windows Forms DataGridView.

- Personalize a aparência das células. Para obter mais informações, confira [Como: Personalize a aparência das células no controle](customize-the-appearance-of-cells-in-the-datagrid.md) Windows Forms DataGridView e [como: Defina os estilos de célula padrão para o controle](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)Windows Forms DataGridView.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Entrada de Dados no controle DataGridView dos Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Como: Manipular erros que ocorrem durante a entrada de dados no controle DataGridView Windows Forms](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Passo a passo: Validando dados no controle Windows Forms DataGridView](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md)
