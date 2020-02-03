---
title: Definir estilos de célula padrão e formatos de dados para o controle DataGridView usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
ms.openlocfilehash: ca602fa15e4648550bfa171a9c3abd057e930eca
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731365"
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>Como definir estilos de célula padrão e formatos de dados para o controle DataGridView dos Windows Forms usando o designer

O controle <xref:System.Windows.Forms.DataGridView> permite especificar estilos de célula padrão e formatos de dados de célula para todo o controle, para colunas específicas, para cabeçalhos de linha e coluna, e para linhas alternadas para criar um efeito de razão. Os estilos padrão definidos para todo o controle serão substituídos por estilos padrão definidos para colunas e linhas alternadas. Além disso, os estilos definidos no código para as linhas e células individuais substituem os estilos padrão.

Para obter mais informações sobre estilos de célula, consulte [Estilos de Célula no Controle DataGridView dos Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md). Para definir estilos para linhas alternadas, consulte [Como Definir Estilos de Linha Alternada para o Controle DataGridView dos Windows Forms Usando o Designer](set-alternating-row-styles-for-the-datagrid-using-the-designer.md).

Você também pode definir estilos usando a propriedade <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> para afetar todas as linhas que serão adicionadas ao controle. Para obter mais informações sobre o modelo de linha, consulte [Como Usar o Modelo de Linha para Personalizar Linhas no Controle DataGridView dos Windows Forms](use-the-row-template-to-customize-rows-in-the-datagrid.md).

Os procedimentos a seguir exigem um projeto de **aplicativo do Windows** com um formulário que contém um controle de <xref:System.Windows.Forms.DataGridView>. Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>Definir estilos padrão para todas as células no controle

1. Selecione o controle de <xref:System.Windows.Forms.DataGridView> no designer.

2. Na janela **Propriedades** , clique no botão de reticências (![botão de reticências (...) na janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado da propriedade <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>ou <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>. A caixa de diálogo **Criador de CellStyle** aparecerá.

3. Defina o estilo configurando as propriedades e use o painel **Visualização** para confirmas suas escolhas.

> [!NOTE]
> Se os estilos visuais estiverem habilitados, os cabeçalhos de linha e coluna (exceto para o <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) serão automaticamente estilizados pelo tema atual, substituindo os valores de propriedade <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> e <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>.
>
> Você pode definir estilos de célula para vários controles de <xref:System.Windows.Forms.DataGridView> selecionados usando o designer, mas somente se eles tiverem valores idênticos para a propriedade de estilo de célula que você deseja modificar. Caso algum estilo de célula seja diferente nessa propriedade, a janela **Propriedades** da caixa de diálogo **Criador de CellStyle** ficará em branco.

### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>Definir estilos padrão para células em colunas individuais

1. Clique com o botão direito do mouse no controle <xref:System.Windows.Forms.DataGridView> no designer e escolha **Editar colunas**.

2. Selecione uma coluna na lista **Colunas Selecionadas**.

3. Na grade **Propriedades da coluna** , clique no botão de reticências (![botão de reticências (...) na janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado da propriedade <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>. A caixa de diálogo **Criador de CellStyle** aparecerá.

4. Defina o estilo configurando as propriedades e use o painel **Visualização** para confirmas suas escolhas.

### <a name="to-format-data-in-cells"></a>Formatar dados em células

1. Use um dos procedimentos anteriores para exibir uma caixa de diálogo **Criador de CellStyle** relacionada a uma propriedade de estilo de célula padrão.

2. Na caixa de diálogo **Construtor de célulastyle** , clique no botão de reticências (![botão de reticências (...) na janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado da propriedade <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>. A caixa de diálogo **Editar Cadeia de Caracteres** será exibida.

3. Selecione um tipo de formato e, em seguida, modifique os detalhes do tipo (como o número de casas decimais a serem exibidas), usando a caixa **Exemplo** para confirmar suas escolhas.

4. Se você estiver associando o controle de <xref:System.Windows.Forms.DataGridView> a uma fonte de dados que provavelmente conterá valores nulos, preencha a caixa de texto **valor nulo** . Esse valor é exibido quando o valor da célula é igual a uma referência nula (`Nothing` em Visual Basic) ou <xref:System.DBNull.Value?displayProperty=nameWithType>.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>
- [Estilos de célula no controle DataGridView do Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Como definir estilos de linhas alternados para o controle DataGridView dos Windows Forms usando o designer](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)
- [Como criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Como Adicionar Controles ao Windows Forms](how-to-add-controls-to-windows-forms.md)
