---
title: 'Como: Definir estilos de célula padrão e formatos de dados para o controle DataGridView do Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
ms.openlocfilehash: 6d7d867b7c9e83b68589e046565bfb0199692f5f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658506"
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>Como: Definir estilos de célula padrão e formatos de dados para o controle DataGridView do Windows Forms usando o designer

O <xref:System.Windows.Forms.DataGridView> controle permite que você especifique estilos de célula padrão e formatos de dados de célula para todo o controle, para colunas específicas, para cabeçalhos de linha e coluna e para linhas alternadas para criar um efeito de razão. Os estilos padrão definidos para todo o controle serão substituídos por estilos padrão definidos para colunas e linhas alternadas. Além disso, os estilos definidos no código para as linhas e células individuais substituem os estilos padrão.

Para obter mais informações sobre estilos de célula, consulte [Estilos de Célula no Controle DataGridView dos Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md). Para definir estilos para linhas alternadas, [consulte Como: Defina os estilos de linha alternados para o controle Windows Forms DataGridView](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)usando o designer.

Você também pode definir estilos usando a <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> propriedade para afetar todas as linhas que serão adicionadas ao controle. Para obter mais informações sobre o modelo de linha [, consulte Como: Use o modelo de linha para personalizar linhas no controle](use-the-row-template-to-customize-rows-in-the-datagrid.md)Windows Forms DataGridView.

Os procedimentos a seguir exigem um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.DataGridView> formulário que contém um controle. Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>Definir estilos padrão para todas as células no controle

1. Selecione o <xref:System.Windows.Forms.DataGridView> controle no designer.

2. Na janela **Propriedades** , clique no botão de reticências![(o botão de reticências (...) na janela Propriedades do Visual](./media/visual-studio-ellipsis-button.png)Studio.) ao <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>lado <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>da propriedade <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> , ou. A caixa de diálogo **Criador de CellStyle** aparecerá.

3. Defina o estilo configurando as propriedades e use o painel **Visualização** para confirmas suas escolhas.

> [!NOTE]
> Se os estilos visuais estiverem habilitados, os cabeçalhos de linha e coluna ( <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>exceto para) serão automaticamente estilizados pelo tema atual, substituindo <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> os valores de <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> Propriedade e.
>
> Você pode definir estilos de célula para vários <xref:System.Windows.Forms.DataGridView> controles selecionados usando o designer, mas somente se eles tiverem valores idênticos para a propriedade de estilo de célula que você deseja modificar. Caso algum estilo de célula seja diferente nessa propriedade, a janela **Propriedades** da caixa de diálogo **Criador de CellStyle** ficará em branco.

### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>Definir estilos padrão para células em colunas individuais

1. Clique com o botão <xref:System.Windows.Forms.DataGridView> direito do mouse no controle no designer e escolha **Editar colunas**.

2. Selecione uma coluna na lista **Colunas Selecionadas**.

3. Na grade **Propriedades da coluna** , clique no botão de reticências (![o botão de reticências (...) na janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> ao lado da propriedade. A caixa de diálogo **Criador de CellStyle** aparecerá.

4. Defina o estilo configurando as propriedades e use o painel **Visualização** para confirmas suas escolhas.

### <a name="to-format-data-in-cells"></a>Formatar dados em células

1. Use um dos procedimentos anteriores para exibir uma caixa de diálogo **Criador de CellStyle** relacionada a uma propriedade de estilo de célula padrão.

2. Na caixa de diálogo **Construtor** de célulastyle, clique no botão de![reticências (o botão de reticências (...) na janela Propriedades](./media/visual-studio-ellipsis-button.png)do Visual Studio. <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> ) ao lado da propriedade. A caixa de diálogo **Editar Cadeia de Caracteres** será exibida.

3. Selecione um tipo de formato e, em seguida, modifique os detalhes do tipo (como o número de casas decimais a serem exibidas), usando a caixa **Exemplo** para confirmar suas escolhas.

4. Se você estiver associando <xref:System.Windows.Forms.DataGridView> o controle a uma fonte de dados que provavelmente conterá valores nulos, preencha a caixa de texto **valor nulo** . Esse valor é exibido quando o valor da célula é igual a uma referência nula`Nothing` (em Visual Basic) <xref:System.DBNull.Value?displayProperty=nameWithType>ou.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>
- [Estilos de célula no controle DataGridView do Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Como: Definir estilos de linha alternados para o controle Windows Forms DataGridView usando o designer](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)
- [Como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Como: Adicionar controles a Windows Forms](how-to-add-controls-to-windows-forms.md)
