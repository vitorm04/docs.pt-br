---
title: Associar dados ao controle DataGridView usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, binding to a data source
- data sources [Windows Forms], binding to Windows Forms controls
- DataGridView control [Windows Forms], data binding
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
ms.openlocfilehash: d5fab6acc53e5b8be247e958bdba78f0d3647fdc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744122"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control-using-the-designer"></a>Como associar dados ao controle DataGridView dos Windows Forms usando o designer
Você pode usar o designer para conectar um controle de <xref:System.Windows.Forms.DataGridView> a fontes de dados de várias variedades diferentes, incluindo bancos de dados, objetos comerciais ou Web Services. Quando você associa o controle a uma fonte de dados usando o designer, o controle é associado automaticamente a um componente <xref:System.Windows.Forms.BindingSource> que representa a fonte de dados. Além disso, as colunas são automaticamente geradas no controle para coincidir com as informações de esquema fornecidas pela fonte de dados.

 Depois que as colunas tiverem sido geradas, você poderá modificá-las para atender às suas necessidades. Por exemplo, você pode remover ou ocultar colunas que você não queira exibir, pode reorganizar as colunas ou pode modificar os tipos de coluna. Para obter mais informações sobre como modificar colunas, consulte os tópicos listados na seção Consulte também.

 Você também pode associar vários controles de <xref:System.Windows.Forms.DataGridView> a tabelas relacionadas para criar relações mestre/detalhes. Nessa configuração, um controle exibe uma tabela pai e outro controle exibe somente as linhas de uma tabela filho que estão relacionadas à linha atual na tabela pai. Para obter mais informações, consulte [Como exibir dados relacionados em um aplicativo dos Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120)).

 O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contenha um controle de <xref:System.Windows.Forms.DataGridView> ou dois controles para uma relação de mestre/detalhes. Para obter informações sobre como iniciar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles a Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-bind-the-control-to-a-data-source"></a>Para associar o controle a uma fonte de dados

1. Clique no glifo de marca inteligente (![glifo de marca inteligente](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no canto superior direito do controle de <xref:System.Windows.Forms.DataGridView>.

2. Clique na seta suspensa para a opção **Escolher Fonte de Dados**.

3. Se seu projeto ainda não tiver uma fonte de dados, clique em **Adicionar Fonte de Dados do Projeto** e siga as etapas indicadas pelo assistente.

     Para obter mais informações, consulte [Assistente de Configuração da Fonte de Dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/w4dd7z6t(v=vs.120)). A nova fonte de dados aparecerá na janela suspensa **Escolher Fonte de Dados**. Se a nova fonte de dados contiver apenas um membro, como uma única tabela de banco de dados, o controle será associado automaticamente a esse membro. Do contrário, continue para a próxima etapa.

4. Expanda os nós **Outras Fontes de Dados** e **Fontes de Dados do Projeto** se eles ainda não tiverem sido expandidos e, em seguida, selecione a fonte de dados à qual associar o controle.

5. Se sua fonte de dados contiver mais de um membro, como se você tiver criado um <xref:System.Data.DataSet?displayProperty=nameWithType> que contém várias tabelas, expanda a fonte de dados e selecione o membro específico ao qual associar.

6. Para criar uma relação mestre/detalhes, na janela suspensa **escolher fonte de dados** para um segundo controle de <xref:System.Windows.Forms.DataGridView>, expanda a <xref:System.Windows.Forms.BindingSource> criada para a tabela pai e, em seguida, selecione a tabela filho relacionada na lista mostrada.

    > [!NOTE]
    > Se o projeto já tiver uma fonte de dados, você também poderá usar a janela **Fontes de Dados** para criar um formulário de dados. Para obter mais informações, consulte [Janela de Fontes de Dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120)).

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- [Como conectar-se a dados em um banco de dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120))
- [Como adicionar e remover colunas no controle DataGridView dos Windows Forms usando o designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Como alterar a ordem das colunas no controle DataGridView dos Windows Forms usando o designer](change-the-order-of-columns-in-the-datagrid-using-the-designer.md)
- [Como alterar o tipo de uma coluna DataGridView dos Windows Forms usando o designer](change-the-type-of-a-wf-datagridview-column-using-the-designer.md)
- [Como congelar colunas no controle DataGridView dos Windows Forms usando o designer](freeze-columns-in-the-datagrid-using-the-designer.md)
- [Como ocultar colunas no controle DataGridView dos Windows Forms usando o designer](hide-columns-in-the-datagrid-using-the-designer.md)
- [Como tornar as colunas somente leitura no controle DataGridView dos Windows Forms usando o designer](make-columns-read-only-in-the-datagrid-using-the-designer.md)
- [Como criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Como Adicionar Controles ao Windows Forms](how-to-add-controls-to-windows-forms.md)
- [Janela Fontes de Dados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))
- [Como exibir dados relacionados em um Aplicativo do Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))
