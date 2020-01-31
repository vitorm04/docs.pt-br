---
title: Tipos de coluna no controle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], types
- DataGridView control [Windows Forms], column types
- data grids [Windows Forms], columns
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
ms.openlocfilehash: e918394cca6350854074d4c1567890138b2a1462
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743858"
---
# <a name="column-types-in-the-windows-forms-datagridview-control"></a>Tipos de coluna no controle DataGridView dos Windows Forms
O controle de <xref:System.Windows.Forms.DataGridView> usa vários tipos de coluna para exibir suas informações e permitir que os usuários modifiquem ou adicionem informações.  
  
 Quando você associa um controle de <xref:System.Windows.Forms.DataGridView> e define a propriedade <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> como `true`, as colunas são geradas automaticamente usando tipos de coluna padrão apropriados para os tipos de dados contidos na fonte de dados ligada.  
  
 Você também pode criar instâncias de qualquer uma das classes de coluna e adicioná-las à coleção retornada pela propriedade <xref:System.Windows.Forms.DataGridView.Columns%2A>. Você pode criar essas instâncias para uso como colunas não associadas ou você pode associá-las manualmente. As colunas associadas manualmente são úteis, por exemplo, quando você quiser substituir uma coluna gerada automaticamente de um tipo com uma coluna de outro tipo.  
  
 A tabela a seguir descreve as várias classes de coluna disponíveis para uso no controle de <xref:System.Windows.Forms.DataGridView>.  
  
|Classe|Descrição|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|Usado com valores baseados em texto. Gerado automaticamente ao associar a números e cadeias de caracteres.|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|Usado com valores de <xref:System.Boolean> e <xref:System.Windows.Forms.CheckState>. Gerado automaticamente ao associar a valores desses tipos.|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|Usado para exibir imagens. Gerado automaticamente ao associar a matrizes de bytes, <xref:System.Drawing.Image> objetos ou <xref:System.Drawing.Icon> objetos.|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|Usado para exibir os botões nas células. Não gerado automaticamente durante a associação. Normalmente usado como colunas não associadas.|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|Usado para exibir listas suspensas nas células. Não gerado automaticamente durante a associação. Normalmente, associação manual de dados.|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|Usado para exibir links nas células. Não gerado automaticamente durante a associação. Normalmente, associação manual de dados.|  
|Seu tipo de coluna personalizada|Você pode criar sua própria classe de coluna herdando a classe <xref:System.Windows.Forms.DataGridViewColumn> ou qualquer uma de suas classes derivadas para fornecer aparência personalizada, comportamento ou controles hospedados. Para mais informações, consulte [Como personalizar células e colunas no controle DataGridView dos Windows Forms estendendo o comportamento e a aparência](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)|  
  
 Esses tipos de colunas são descritos mais detalhadamente nas seções a seguir.  
  
## <a name="datagridviewtextboxcolumn"></a>DataGridViewTextBoxColumn  
 O <xref:System.Windows.Forms.DataGridViewTextBoxColumn> é um tipo de coluna de finalidade geral para uso com valores baseados em texto, como números e cadeias de caracteres. No modo de edição, um controle de <xref:System.Windows.Forms.TextBox> é exibido na célula ativa, permitindo que os usuários modifiquem o valor da célula.  
  
 Os valores da célula são convertidos automaticamente em cadeiras de caracteres para exibição. Os valores inseridos ou modificados pelo usuário são automaticamente analisados para criar um valor de célula do tipo de dados apropriado. Você pode personalizar essas conversões manipulando os eventos de <xref:System.Windows.Forms.DataGridView.CellFormatting> e <xref:System.Windows.Forms.DataGridView.CellParsing> do controle de <xref:System.Windows.Forms.DataGridView>.  
  
 O tipo de dados de valor de célula de uma coluna é especificado na propriedade <xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A> da coluna.  
  
## <a name="datagridviewcheckboxcolumn"></a>DataGridViewCheckBoxColumn  
 O <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> é usado com valores de <xref:System.Boolean> e <xref:System.Windows.Forms.CheckState>. <xref:System.Boolean> valores são exibidos como caixas de seleção de dois Estados ou de três Estados, dependendo do valor da propriedade <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A>. Quando a coluna é associada a valores de <xref:System.Windows.Forms.CheckState>, o valor da propriedade <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> é `true` por padrão.  
  
 Normalmente, os valores de célula da caixa de seleção destinam-se para armazenamento, como qualquer outro dado ou para executar operações em massa. Se você quiser responder imediatamente quando os usuários clicarem em uma célula de caixa de seleção, poderá manipular o evento <xref:System.Windows.Forms.DataGridView.CellClick>, mas esse evento ocorrerá antes que o valor da célula seja atualizado. Se você precisar do novo valor no momento do clique, uma opção será calcular qual será o valor esperado com base no valor atual. Outra abordagem é confirmar a alteração imediatamente e manipular o evento <xref:System.Windows.Forms.DataGridView.CellValueChanged> para responder a ela. Para confirmar a alteração quando a célula é clicada, você deve manipular o evento <xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged>. No manipulador, se a célula atual for uma célula da caixa de seleção, chame o método <xref:System.Windows.Forms.DataGridView.CommitEdit%2A> e passe o valor <xref:System.Windows.Forms.DataGridViewDataErrorContexts.Commit>.  
  
## <a name="datagridviewimagecolumn"></a>DataGridViewImageColumn  
 O <xref:System.Windows.Forms.DataGridViewImageColumn> é usado para exibir imagens. As colunas de imagem podem ser preenchidas automaticamente de uma fonte de dados, preenchida manualmente para colunas não associadas ou preenchidas dinamicamente em um manipulador para o evento <xref:System.Windows.Forms.DataGridView.CellFormatting>.  
  
 A população automática de uma coluna de imagem de uma fonte de dados funciona com matrizes de bytes em uma variedade de formatos de imagem, incluindo todos os formatos suportados pela classe <xref:System.Drawing.Image> e o formato de imagem OLE usado pelo Microsoft® Access e o banco de dados de exemplo Northwind.  
  
 Preencher uma coluna de imagem manualmente é útil quando você deseja fornecer a funcionalidade de um <xref:System.Windows.Forms.DataGridViewButtonColumn>, mas com uma aparência personalizada. Você pode manipular o evento <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> para responder a cliques em uma célula de imagem.  
  
 Preencher as células de uma coluna de imagem em um manipulador para o evento <xref:System.Windows.Forms.DataGridView.CellFormatting> é útil quando você deseja fornecer imagens para valores calculados ou valores em formatos que não são de imagem. Por exemplo, você pode ter uma coluna “Risco” com valores de cadeia de caracteres como `"high"`, `"middle"` e `"low"` que você deseja exibir como ícones. Como alternativa, você pode ter uma coluna "Imagem" que contém os locais de imagens que devem ser carregados em vez do conteúdo binário das imagens.  
  
## <a name="datagridviewbuttoncolumn"></a>DataGridViewButtonColumn  
 Com o <xref:System.Windows.Forms.DataGridViewButtonColumn>, você pode exibir uma coluna de células que contêm botões. Isso é útil quando você deseja fornecer uma maneira fácil para os usuários de executar ações em registros específicos, como fazer um pedido ou exibir registros filho em uma janela separada.  
  
 Colunas de botão não são geradas automaticamente ao vincular dados a um controle de <xref:System.Windows.Forms.DataGridView>. Para usar colunas de botão, você deve criá-las manualmente e adicioná-las à coleção retornada pela propriedade <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>.  
  
 Você pode responder a cliques de usuário em células de botão manipulando o evento <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>.  
  
## <a name="datagridviewcomboboxcolumn"></a>DataGridViewComboBoxColumn  
 Com o <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, você pode exibir uma coluna de células que contêm caixas de listagem suspensas. Isso é útil para entrada de dados em campos que podem conter apenas valores específicos, como a coluna Categoria da tabela Produtos no banco de dados de exemplo Northwind.  
  
 Você pode preencher a lista suspensa usada para todas as células da mesma maneira que preencheria uma lista suspensa <xref:System.Windows.Forms.ComboBox>, manualmente por meio da coleção retornada pela propriedade <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A>, ou ligando-a a uma fonte de dados por meio das propriedades <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>e <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>. Para saber mais, consulte [Controle ComboBox](combobox-control-windows-forms.md).  
  
 Você pode associar os valores reais da célula à fonte de dados usada pelo controle de <xref:System.Windows.Forms.DataGridView> definindo a propriedade <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> do <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>.  
  
 As colunas da caixa de combinação não são geradas automaticamente ao vincular dados a um controle <xref:System.Windows.Forms.DataGridView>. Para usar colunas da caixa de combinação, você deve criá-las manualmente e adicioná-las à coleção retornada pela propriedade <xref:System.Windows.Forms.DataGridView.Columns%2A>.  
  
## <a name="datagridviewlinkcolumn"></a>DataGridViewLinkColumn  
 Com o <xref:System.Windows.Forms.DataGridViewLinkColumn>, você pode exibir uma coluna de células que contêm hiperlinks. Isso é útil para valores de URL na fonte de dados ou como uma alternativa para a coluna de botão para comportamentos especiais, como abrir uma janela com registros filho.  
  
 Colunas de link não são geradas automaticamente ao vincular dados a um controle de <xref:System.Windows.Forms.DataGridView>. Para usar colunas de link, você deve criá-las manualmente e adicioná-las à coleção retornada pela propriedade <xref:System.Windows.Forms.DataGridView.Columns%2A>.  
  
 Você pode responder a cliques do usuário em links manipulando o evento <xref:System.Windows.Forms.DataGridView.CellContentClick>. Esse evento é diferente dos eventos <xref:System.Windows.Forms.DataGridView.CellClick> e <xref:System.Windows.Forms.DataGridView.CellMouseClick>, que ocorrem quando um usuário clica em qualquer lugar em uma célula.  
  
 A classe <xref:System.Windows.Forms.DataGridViewLinkColumn> fornece várias propriedades para modificar a aparência dos links antes, durante e depois que eles são clicados.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewButtonColumn>
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>
- <xref:System.Windows.Forms.DataGridViewImageColumn>
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>
- <xref:System.Windows.Forms.DataGridViewLinkColumn>
- [Controle DataGridView](datagridview-control-windows-forms.md)
- [Como exibir imagens em células do controle DataGridView do Windows Forms](how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)
- [Como trabalhar com colunas de imagem no controle DataGridView dos Windows Forms](how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)
- [Personalizando o controle DataGridView do Windows Forms](customizing-the-windows-forms-datagridview-control.md)
