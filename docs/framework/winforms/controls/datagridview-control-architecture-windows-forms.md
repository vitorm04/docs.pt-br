---
title: Arquitetura de controle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: 2e1884383cca87f8d4ff84f486e2b29761a0c55d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742535"
---
# <a name="datagridview-control-architecture-windows-forms"></a>Arquitetura do controle DataGridView (Windows Forms)
O controle de <xref:System.Windows.Forms.DataGridView> e suas classes relacionadas são projetados para ser um sistema flexível e extensível para exibir e editar dados tabulares. Essas classes estão todas contidas no namespace <xref:System.Windows.Forms?displayProperty=nameWithType>, e elas são todas nomeadas com o prefixo "DataGridView".  
  
## <a name="architecture-elements"></a>Elementos de arquitetura  
 As classes principais do <xref:System.Windows.Forms.DataGridView> Companion derivam de <xref:System.Windows.Forms.DataGridViewElement>. O modelo de objeto a seguir ilustra a hierarquia de herança do <xref:System.Windows.Forms.DataGridViewElement>.  
  
 ![Diagrama que mostra a hierarquia de modelo de objeto DataGridViewelement.](./media/datagridview-control-architecture-windows-forms/datagridviewelement-object-model.gif)  
  
 A classe <xref:System.Windows.Forms.DataGridViewElement> fornece uma referência ao controle de <xref:System.Windows.Forms.DataGridView> pai e tem uma propriedade <xref:System.Windows.Forms.DataGridViewElement.State%2A>, que contém um valor que representa uma combinação de valores da enumeração <xref:System.Windows.Forms.DataGridViewElementStates>.  
  
 As seções a seguir descrevem as classes <xref:System.Windows.Forms.DataGridView> complementares mais detalhadamente.  
  
### <a name="datagridviewelementstates"></a>DataGridViewElementStates  
 A enumeração <xref:System.Windows.Forms.DataGridViewElementStates> contém os seguintes valores:  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 Os valores dessa enumeração podem ser combinados com os operadores lógicos de bit-a, para que a propriedade <xref:System.Windows.Forms.DataGridViewElement.State%2A> possa expressar mais de um estado de uma vez. Por exemplo, um <xref:System.Windows.Forms.DataGridViewElement> pode ser <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>e <xref:System.Windows.Forms.DataGridViewElementStates.Visible>simultaneamente.  
  
### <a name="cells-and-bands"></a>Células e faixas  
 O controle <xref:System.Windows.Forms.DataGridView> consiste em dois tipos fundamentais de objetos: células e faixas. Todas as células derivam da classe base <xref:System.Windows.Forms.DataGridViewCell>. Os dois tipos de bandas, <xref:System.Windows.Forms.DataGridViewColumn> e <xref:System.Windows.Forms.DataGridViewRow>derivam da classe base <xref:System.Windows.Forms.DataGridViewBand>.  
  
 O controle de <xref:System.Windows.Forms.DataGridView> interopera com várias classes, mas as mais comumente encontradas são <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>e <xref:System.Windows.Forms.DataGridViewRow>.  
  
### <a name="datagridviewcell"></a>DataGridViewCell  
 A célula é a unidade fundamental de interação para o <xref:System.Windows.Forms.DataGridView>. A exibição é centralizada das células e entrada de dados geralmente é realizada por meio das células. Você pode acessar células usando a coleção de <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> da classe <xref:System.Windows.Forms.DataGridViewRow> e pode acessar as células selecionadas usando a coleção <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> do controle <xref:System.Windows.Forms.DataGridView>. O modelo de objeto a seguir ilustra esse uso e mostra a hierarquia de herança do <xref:System.Windows.Forms.DataGridViewCell>.  
  
 ![Diagrama que mostra a hierarquia de modelo de objeto DataGridViewCell.](./media/datagridview-control-architecture-windows-forms/datagridviewcell-object-model.gif)  
  
 O tipo de <xref:System.Windows.Forms.DataGridViewCell> é uma classe base abstrata, da qual todos os tipos de célula derivam. <xref:System.Windows.Forms.DataGridViewCell> e seus tipos derivados não são Windows Forms controles, mas alguns controles de Windows Forms do host. Qualquer funcionalidade de edição com suporte de uma célula normalmente é manipulada por um controle hospedado.  
  
 <xref:System.Windows.Forms.DataGridViewCell> objetos não controlam seus próprios recursos de aparência e pintura da mesma maneira que Windows Forms controles. Em vez disso, o <xref:System.Windows.Forms.DataGridView> é responsável pela aparência de seus objetos <xref:System.Windows.Forms.DataGridViewCell>. Você pode afetar significativamente a aparência e o comportamento das células interagindo com as propriedades e os eventos do controle de <xref:System.Windows.Forms.DataGridView>. Quando você tem requisitos especiais para personalizações que estão além dos recursos do controle de <xref:System.Windows.Forms.DataGridView>, você pode implementar sua própria classe que deriva de <xref:System.Windows.Forms.DataGridViewCell> ou de uma de suas classes filhas.  
  
 A lista a seguir mostra as classes derivadas de <xref:System.Windows.Forms.DataGridViewCell>:  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
- <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewImageCell>  
  
- <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
- Seus tipos de célula personalizados  
  
### <a name="datagridviewcolumn"></a>DataGridViewColumn  
 O esquema do armazenamento de dados anexado do controle de <xref:System.Windows.Forms.DataGridView> é expresso nas colunas do controle de <xref:System.Windows.Forms.DataGridView>. Você pode acessar as colunas do controle de <xref:System.Windows.Forms.DataGridView> usando a coleção <xref:System.Windows.Forms.DataGridView.Columns%2A>. Você pode acessar as colunas selecionadas usando a coleção de <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>. O modelo de objeto a seguir ilustra esse uso e mostra a hierarquia de herança do <xref:System.Windows.Forms.DataGridViewColumn>.  
  
 ![Diagrama que mostra a hierarquia do modelo de objeto DataGridViewColumn.](./media/datagridview-control-architecture-windows-forms/datagridviewcolumn-object-model.gif)  
  
 Alguns dos principais tipos de células têm tipos de colunas correspondentes. Eles são derivados da classe base <xref:System.Windows.Forms.DataGridViewColumn>.  
  
 A lista a seguir mostra as classes derivadas de <xref:System.Windows.Forms.DataGridViewColumn>:  
  
- <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
- Seus tipos de colunas personalizadas  
  
### <a name="datagridview-editing-controls"></a>Controles de edição de DataGridView  
 Células que dão suporte a recursos de edição avançados normalmente usam um controle hospedado que é derivado de um controle dos Windows Forms. Esses controles também implementam a interface <xref:System.Windows.Forms.IDataGridViewEditingControl>. O modelo de objeto a seguir ilustra o uso desses controles.  
  
 ![Diagrama que mostra a hierarquia de modelo de objeto do controle de edição do DataGridView.](./media/datagridview-control-architecture-windows-forms/datagridviewediting-object-model.gif)  
  
 Os seguintes controles de edição são fornecidos com o controle de <xref:System.Windows.Forms.DataGridView>:  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 Para obter informações sobre como criar seus próprios controles de edição, consulte [Como hospedar controles em células DataGridView dos Windows Forms](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
 A tabela a seguir ilustra o relacionamento entre tipos de células, tipos de colunas e controles de edição.  
  
|Tipo de célula|Controle hospedado|Tipo de coluna|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|N/D|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|N/D|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|N/D|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|N/D|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a>DataGridViewRow  
 A classe <xref:System.Windows.Forms.DataGridViewRow> exibe os campos de dados de um registro do armazenamento de dados ao qual o controle de <xref:System.Windows.Forms.DataGridView> está anexado. Você pode acessar as linhas do controle de <xref:System.Windows.Forms.DataGridView> usando a coleção <xref:System.Windows.Forms.DataGridView.Rows%2A>. Você pode acessar as linhas selecionadas usando a coleção de <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>. O modelo de objeto a seguir ilustra esse uso e mostra a hierarquia de herança do <xref:System.Windows.Forms.DataGridViewRow>.  
  
 ![Diagrama que mostra a hierarquia do modelo de objeto DataGridViewRow.](./media/datagridview-control-architecture-windows-forms/datagridviewrow-object-model.gif)
  
 Você pode derivar seus próprios tipos da classe <xref:System.Windows.Forms.DataGridViewRow>, embora isso normalmente não será necessário. O controle <xref:System.Windows.Forms.DataGridView> tem vários eventos e propriedades relacionados à linha para personalizar o comportamento de seus objetos <xref:System.Windows.Forms.DataGridViewRow>.  
  
 Se você habilitar a propriedade <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> do controle de <xref:System.Windows.Forms.DataGridView>, uma linha especial para adicionar novas linhas será exibida como a última linha. Essa linha faz parte da coleção de <xref:System.Windows.Forms.DataGridView.Rows%2A>, mas tem uma funcionalidade especial que pode exigir sua atenção. Para obter mais informações, consulte [Usando a linha para novos registros no controle DataGridView dos Windows Forms](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Veja também

- [Visão geral do controle DataGridView](datagridview-control-overview-windows-forms.md)
- [Personalizando o controle DataGridView do Windows Forms](customizing-the-windows-forms-datagridview-control.md)
- [Usando a linha para novos registros no controle DataGridView dos Windows Forms](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
