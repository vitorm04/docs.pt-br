---
title: 'Passo a passo: Criando um formulário mestre-de detalhes usando dois Windows Forms controles DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], displaying on Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: c5fa29e8-47f7-4691-829b-0e697a691f36
ms.openlocfilehash: 4212c7223aca6a5e7de3189d5f6b2757453cc438
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046090"
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Passo a passo: Criar um formulário mestre/de detalhes usando dois controles DataGridView do Windows Forms

Um dos cenários mais comuns para usar o <xref:System.Windows.Forms.DataGridView> controle é o formulário *mestre/detalhado* , no qual uma relação pai/filho entre duas tabelas de banco de dados é exibida. Seleção de linhas na tabela mestra faz com que a tabela de detalhes sejam atualizadas com os dados filho correspondentes.

A implementação de um formulário mestre/detalhado é fácil usando a interação <xref:System.Windows.Forms.DataGridView> entre o controle <xref:System.Windows.Forms.BindingSource> e o componente. Neste tutorial, você criará o formulário usando dois <xref:System.Windows.Forms.DataGridView> controles e dois <xref:System.Windows.Forms.BindingSource> componentes. O formulário mostrará duas tabelas relacionadas no banco de dados de exemplo SQL Server Northwind: `Customers` e `Orders`. Quando terminar, você terá um formulário que mostra todos os clientes no banco de dados no mestre <xref:System.Windows.Forms.DataGridView> e todos os pedidos para o cliente selecionado nos detalhes. <xref:System.Windows.Forms.DataGridView>

Para copiar o código deste tópico como uma única listagem, confira [Como: Crie um formulário mestre/detalhado usando dois Windows Forms controles](create-a-master-detail-form-using-two-datagridviews.md)DataGridView.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este passo a passo, você precisará de:

- Acesso a um servidor que tem o banco de dados de exemplo SQL Server Northwind.

## <a name="creating-the-form"></a>Criando o formulário

#### <a name="to-create-a-masterdetail-form"></a>Para criar um formulário mestre/detalhes

1. Crie uma classe que derive de <xref:System.Windows.Forms.Form> e contenha <xref:System.Windows.Forms.DataGridView> dois controles e <xref:System.Windows.Forms.BindingSource> dois componentes. O código a seguir fornece inicialização de formulário básica e inclui um método `Main`. Se você usar o designer do Visual Studio para criar seu formulário, poderá usar o código gerado pelo designer em vez desse código, mas certifique-se de usar os nomes mostrados nas declarações de variável aqui.

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]

2. Implemente um método na sua definição de classe do formulário para manipular os detalhes da conexão ao banco de dados. Este exemplo usa um `GetData` método que popula um <xref:System.Data.DataSet> objeto, adiciona um <xref:System.Data.DataRelation> objeto ao conjunto de dados e associa os <xref:System.Windows.Forms.BindingSource> componentes. Certifique-se de definir a variável de `connectionString` como um valor que seja apropriada para o base de dados.

    > [!IMPORTANT]
    > O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]

3. Implemente um manipulador para o evento <xref:System.Windows.Forms.Form.Load> do formulário que associa os <xref:System.Windows.Forms.DataGridView> controles aos <xref:System.Windows.Forms.BindingSource> componentes e chama o `GetData` método. O exemplo a seguir inclui um código que redimensiona <xref:System.Windows.Forms.DataGridView> as colunas para ajustar os dados exibidos.

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]

## <a name="testing-the-application"></a>Testando o aplicativo

Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.

#### <a name="to-test-the-form"></a>Para testar o formulário

- Compile e execute o aplicativo.

  Você verá dois <xref:System.Windows.Forms.DataGridView> controles, um acima do outro. Na parte superior estão os clientes da tabela `Customers` Northwind e na parte inferior estão os `Orders` correspondentes ao cliente selecionado. À medida que você seleciona linhas diferentes na <xref:System.Windows.Forms.DataGridView>parte superior, o conteúdo da <xref:System.Windows.Forms.DataGridView> alteração mais baixa é adequado.

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
- [Exibindo dados no controle DataGridView do Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Como: Criar um formulário mestre/detalhado usando dois Windows Forms controles DataGridView](create-a-master-detail-form-using-two-datagridviews.md)
- [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md)
