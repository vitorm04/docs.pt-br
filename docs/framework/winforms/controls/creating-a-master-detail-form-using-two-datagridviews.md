---
title: 'Walkthrough: criar um formulário de detalhes mestre usando dois controles DataGridView'
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
ms.openlocfilehash: bb3da36430c7493b941f3711cb584b4517d5bd54
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740575"
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Instruções passo a passo: criando um formulário mestre/detalhes usando dois controles DataGridView dos Windows Forms

Um dos cenários mais comuns para usar o controle de <xref:System.Windows.Forms.DataGridView> é o formulário *mestre/detalhado* , no qual uma relação pai/filho entre duas tabelas de banco de dados é exibida. Seleção de linhas na tabela mestra faz com que a tabela de detalhes sejam atualizadas com os dados filho correspondentes.

A implementação de um formulário mestre/detalhado é fácil usando a interação entre o controle de <xref:System.Windows.Forms.DataGridView> e o componente <xref:System.Windows.Forms.BindingSource>. Neste tutorial, você criará o formulário usando dois controles de <xref:System.Windows.Forms.DataGridView> e dois componentes de <xref:System.Windows.Forms.BindingSource>. O formulário mostrará duas tabelas relacionadas no banco de dados de exemplo SQL Server Northwind: `Customers` e `Orders`. Quando terminar, você terá um formulário que mostra todos os clientes no banco de dados no <xref:System.Windows.Forms.DataGridView> mestre e todos os pedidos do cliente selecionado no <xref:System.Windows.Forms.DataGridView>de detalhes.

Para copiar o código neste tópico como uma única listagem, consulte [Como criar um formulário mestre/detalhes usando dois controles DataGridView dos Windows Forms](create-a-master-detail-form-using-two-datagridviews.md).

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}

Para concluir este passo a passo, você precisará de:

- Acesso a um servidor que tem o banco de dados de exemplo SQL Server Northwind.

## <a name="creating-the-form"></a>Criando o formulário

#### <a name="to-create-a-masterdetail-form"></a>Para criar um formulário mestre/detalhes

1. Crie uma classe que derive de <xref:System.Windows.Forms.Form> e contenha dois controles <xref:System.Windows.Forms.DataGridView> e dois componentes <xref:System.Windows.Forms.BindingSource>. O código a seguir fornece inicialização de formulário básica e inclui um método `Main`. Se você usar o designer do Visual Studio para criar seu formulário, poderá usar o código gerado pelo designer em vez desse código, mas certifique-se de usar os nomes mostrados nas declarações de variável aqui.

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]

2. Implemente um método na sua definição de classe do formulário para manipular os detalhes da conexão ao banco de dados. Este exemplo usa um método `GetData` que popula um objeto <xref:System.Data.DataSet>, adiciona um objeto <xref:System.Data.DataRelation> ao conjunto de dados e associa os componentes <xref:System.Windows.Forms.BindingSource>. Certifique-se de definir a variável de `connectionString` como um valor que seja apropriada para o base de dados.

    > [!IMPORTANT]
    > O armazenamento das informações confidenciais, como uma senha, dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]

3. Implemente um manipulador para o evento <xref:System.Windows.Forms.Form.Load> do seu formulário que associa os controles de <xref:System.Windows.Forms.DataGridView> aos componentes <xref:System.Windows.Forms.BindingSource> e chama o método `GetData`. O exemplo a seguir inclui um código que redimensiona <xref:System.Windows.Forms.DataGridView> colunas para ajustar os dados exibidos.

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]

## <a name="testing-the-application"></a>Testando o aplicativo

Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.

#### <a name="to-test-the-form"></a>Para testar o formulário

- Compile e execute o aplicativo.

  Você verá dois controles de <xref:System.Windows.Forms.DataGridView>, um acima do outro. Na parte superior estão os clientes da tabela `Customers` Northwind e na parte inferior estão os `Orders` correspondentes ao cliente selecionado. À medida que você seleciona linhas diferentes no <xref:System.Windows.Forms.DataGridView>superior, o conteúdo do <xref:System.Windows.Forms.DataGridView> menor é alterado de acordo.

## <a name="next-steps"></a>Próximas etapas

Esse aplicativo oferece uma compreensão básica dos recursos do controle de <xref:System.Windows.Forms.DataGridView>. Você pode personalizar a aparência e o comportamento do controle de <xref:System.Windows.Forms.DataGridView> de várias maneiras:

- Alterar estilos de borda e cabeçalho. Para obter mais informações, consulte [Como alterar os estilos de borda e linha de grade no controle DataGridView dos Windows Forms](change-the-border-and-gridline-styles-in-the-datagrid.md).

- Habilitar ou restringir a entrada do usuário para o controle de <xref:System.Windows.Forms.DataGridView>. Para obter mais informações, consulte [Como evitar a adição e a exclusão de linhas no controle DataGridView do Windows Forms](prevent-row-addition-and-deletion-datagridview.md) e [Como tornar colunas somente leitura no controle DataGridView do Windows Forms](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).

- Valide a entrada do usuário para o controle de <xref:System.Windows.Forms.DataGridView>. Para obter mais informações, consulte [Passo a passo: validando dados no controle DataGridView dos Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).

- Manipule grandes conjuntos de dados usando o modo virtual. Para obter mais informações, consulte [Passo a passo: implementando o modo virtual no controle DataGridView dos Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).

- Personalize a aparência das células. Para obter mais informações, consulte [Como personalizar a aparência de células no controle DataGridView dos Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md) e [Como definir estilos de célula padrão no controle DataGridView dos Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Exibindo dados no controle DataGridView dos Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Como criar um formulário mestre/detalhado usando dois controles DataGridView dos Windows Forms](create-a-master-detail-form-using-two-datagridviews.md)
- [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md)
