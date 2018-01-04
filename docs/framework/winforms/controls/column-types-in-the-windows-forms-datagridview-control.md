---
title: Tipos de coluna no controle DataGridView dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [Windows Forms], types
- DataGridView control [Windows Forms], column types
- data grids [Windows Forms], columns
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 92c6881fe876bba3fe0224a358a9b12767d53f0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="column-types-in-the-windows-forms-datagridview-control"></a>Tipos de coluna no controle DataGridView dos Windows Forms
O <xref:System.Windows.Forms.DataGridView> controle usa vários tipos de coluna para exibir as informações e permitir que os usuários modificar ou adicionar informações.  
  
 Quando você associa um <xref:System.Windows.Forms.DataGridView> controle e defina o <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> propriedade `true`, colunas são geradas automaticamente para usar tipos de coluna padrão apropriados para os tipos de dados contidos na fonte de dados associados.  
  
 Você também pode criar instâncias de qualquer uma das classes de coluna por conta própria e adicioná-los à coleção retornada pelo <xref:System.Windows.Forms.DataGridView.Columns%2A> propriedade. Você pode criar essas instâncias para uso como colunas não associadas ou você pode associá-las manualmente. As colunas associadas manualmente são úteis, por exemplo, quando você quiser substituir uma coluna gerada automaticamente de um tipo com uma coluna de outro tipo.  
  
 A tabela a seguir descreve as várias classes de coluna disponíveis para uso no <xref:System.Windows.Forms.DataGridView> controle.  
  
|Classe|Descrição|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|Usado com valores baseados em texto. Gerado automaticamente ao associar a números e cadeias de caracteres.|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|Usado com <xref:System.Boolean> e <xref:System.Windows.Forms.CheckState> valores. Gerado automaticamente ao associar a valores desses tipos.|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|Usado para exibir imagens. Gerado automaticamente quando a associação para matrizes de bytes, <xref:System.Drawing.Image> objetos, ou <xref:System.Drawing.Icon> objetos.|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|Usado para exibir os botões nas células. Não gerado automaticamente durante a associação. Normalmente usado como colunas não associadas.|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|Usado para exibir listas suspensas nas células. Não gerado automaticamente durante a associação. Normalmente, associação manual de dados.|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|Usado para exibir links nas células. Não gerado automaticamente durante a associação. Normalmente, associação manual de dados.|  
|Seu tipo de coluna personalizada|Você pode criar sua própria classe de coluna herdando a <xref:System.Windows.Forms.DataGridViewColumn> classe ou uma de suas classes derivadas para fornecer personalizada aparência, comportamento ou controles hospedados. Para mais informações, consulte [Como personalizar células e colunas no controle DataGridView dos Windows Forms estendendo o comportamento e a aparência](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)|  
  
 Esses tipos de colunas são descritos mais detalhadamente nas seções a seguir.  
  
## <a name="datagridviewtextboxcolumn"></a>DataGridViewTextBoxColumn  
 O <xref:System.Windows.Forms.DataGridViewTextBoxColumn> é um tipo de coluna para fins gerais para uso com valores com base em texto, como números e cadeias de caracteres. No modo de edição, um <xref:System.Windows.Forms.TextBox> controle é exibido na célula ativa, permitindo que os usuários de modificar o valor da célula.  
  
 Os valores da célula são convertidos automaticamente em cadeiras de caracteres para exibição. Os valores inseridos ou modificados pelo usuário são automaticamente analisados para criar um valor de célula do tipo de dados apropriado. Você pode personalizar essas conversões manipulando o <xref:System.Windows.Forms.DataGridView.CellFormatting> e <xref:System.Windows.Forms.DataGridView.CellParsing> eventos do <xref:System.Windows.Forms.DataGridView> controle.  
  
 O tipo de dados de valor de célula de uma coluna é especificado no <xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A> propriedade da coluna.  
  
## <a name="datagridviewcheckboxcolumn"></a>DataGridViewCheckBoxColumn  
 O <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> é usado com <xref:System.Boolean> e <xref:System.Windows.Forms.CheckState> valores. <xref:System.Boolean>os valores exibidos como caixas de seleção de dois ou três estados, dependendo do valor da <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> propriedade. Quando a coluna é associada a <xref:System.Windows.Forms.CheckState> valores, o <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> é o valor da propriedade `true` por padrão.  
  
 Normalmente, os valores de célula da caixa de seleção destinam-se para armazenamento, como qualquer outro dado ou para executar operações em massa. Se você deseja responder imediatamente quando os usuários em uma célula de caixa de seleção, você pode manipular o <xref:System.Windows.Forms.DataGridView.CellClick> evento, mas esse evento ocorre antes de atualizar o valor da célula. Se você precisar do novo valor no momento do clique, uma opção será calcular qual será o valor esperado com base no valor atual. Outra abordagem é confirmar a alteração imediatamente e manipular o <xref:System.Windows.Forms.DataGridView.CellValueChanged> evento responder a ele. Para confirmar a alteração, quando a célula é clicada, você deve tratar o <xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged> evento. No manipulador, se a célula atual for uma célula de caixa de seleção, chame o <xref:System.Windows.Forms.DataGridView.CommitEdit%2A> método e passar o <xref:System.Windows.Forms.DataGridViewDataErrorContexts.Commit> valor.  
  
## <a name="datagridviewimagecolumn"></a>DataGridViewImageColumn  
 O <xref:System.Windows.Forms.DataGridViewImageColumn> é usado para exibir imagens. Colunas de imagem podem ser preenchidas automaticamente a partir de uma fonte de dados, populadas manualmente para colunas desassociadas ou populadas dinamicamente em um manipulador para o <xref:System.Windows.Forms.DataGridView.CellFormatting> evento.  
  
 O preenchimento automático de uma coluna de imagem de uma fonte de dados funciona com matrizes de bytes em uma variedade de formatos de imagem, incluindo todos os formatos com suporte a <xref:System.Drawing.Image> classe e o formato de imagem OLE usado pelo Microsoft® Access e o banco de dados de exemplo Northwind.  
  
 Preencher uma coluna de imagem manualmente é útil quando você deseja fornecer a funcionalidade de um <xref:System.Windows.Forms.DataGridViewButtonColumn>, mas com uma aparência personalizada. Você pode manipular o <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> evento para responder a cliques dentro de uma célula de imagem.  
  
 Preencher as células de uma coluna de imagem em um manipulador para o <xref:System.Windows.Forms.DataGridView.CellFormatting> evento é útil quando você deseja fornecer imagens para valores calculados ou em formatos de imagem não. Por exemplo, você pode ter uma coluna “Risco” com valores de cadeia de caracteres como `"high"`, `"middle"` e `"low"` que você deseja exibir como ícones. Como alternativa, você pode ter uma coluna "Imagem" que contém os locais de imagens que devem ser carregados em vez do conteúdo binário das imagens.  
  
## <a name="datagridviewbuttoncolumn"></a>DataGridViewButtonColumn  
 Com o <xref:System.Windows.Forms.DataGridViewButtonColumn>, você pode exibir uma coluna de células que contêm botões. Isso é útil quando você deseja fornecer uma maneira fácil para os usuários de executar ações em registros específicos, como fazer um pedido ou exibir registros filho em uma janela separada.  
  
 Colunas de botões não são geradas automaticamente quando a associação de dados um <xref:System.Windows.Forms.DataGridView> controle. Para usar as colunas de botão, você deve criá-los manualmente e adicioná-los à coleção retornada pelo <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType> propriedade.  
  
 Você pode responder a cliques do usuário em células de botão manipulando o <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> evento.  
  
## <a name="datagridviewcomboboxcolumn"></a>DataGridViewComboBoxColumn  
 Com o <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, você pode exibir uma coluna de células que contêm as caixas de listagem suspensa. Isso é útil para entrada de dados em campos que podem conter apenas valores específicos, como a coluna Categoria da tabela Produtos no banco de dados de exemplo Northwind.  
  
 Você pode preencher a lista suspensa usada para todas as células da mesma maneira que você preenche um <xref:System.Windows.Forms.ComboBox> lista suspensa, manualmente por meio da coleção retornada pelo <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> propriedade, ou por associação a uma fonte de dados por meio de <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>, e <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> propriedades. Para saber mais, consulte [Controle ComboBox](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md).  
  
 Você pode vincular os valores de célula reais para a fonte de dados usada pelo <xref:System.Windows.Forms.DataGridView> controle definindo o <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> propriedade o <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>.  
  
 Colunas da caixa de combinação não são geradas automaticamente quando a associação de dados um <xref:System.Windows.Forms.DataGridView> controle. Para usar as colunas de caixa de combinação, você deve criá-los manualmente e adicioná-los à coleção retornada pelo <xref:System.Windows.Forms.DataGridView.Columns%2A> propriedade.  
  
## <a name="datagridviewlinkcolumn"></a>DataGridViewLinkColumn  
 Com o <xref:System.Windows.Forms.DataGridViewLinkColumn>, você pode exibir uma coluna de células que contêm hiperlinks. Isso é útil para valores de URL na fonte de dados ou como uma alternativa para a coluna de botão para comportamentos especiais, como abrir uma janela com registros filho.  
  
 Colunas de link não são geradas automaticamente quando a associação de dados um <xref:System.Windows.Forms.DataGridView> controle. Para usar as colunas de link, você deve criá-los manualmente e adicioná-los à coleção retornada pelo <xref:System.Windows.Forms.DataGridView.Columns%2A> propriedade.  
  
 Você pode responder a cliques do usuário nos links manipulando o <xref:System.Windows.Forms.DataGridView.CellContentClick> evento. Esse evento é diferente de <xref:System.Windows.Forms.DataGridView.CellClick> e <xref:System.Windows.Forms.DataGridView.CellMouseClick> eventos que ocorrem quando um usuário clica em qualquer lugar em uma célula.  
  
 O <xref:System.Windows.Forms.DataGridViewLinkColumn> classe fornece várias propriedades para modificar a aparência de links antes, durante e depois eles são clicados.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewImageColumn>  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewLinkColumn>  
 [Controle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Como exibir imagens em células do controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)  
 [Como trabalhar com colunas de imagem no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)  
 [Personalizando o controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
