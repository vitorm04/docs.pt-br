---
title: Arquitetura do controle DataGridView (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: 892168ec282fbf168c43515e0718fe5486a345a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130254"
---
# <a name="datagridview-control-architecture-windows-forms"></a>Arquitetura do controle DataGridView (Windows Forms)
O <xref:System.Windows.Forms.DataGridView> controle e suas classes relacionadas foram projetados para ser um sistema flexível e extensível para exibir e editar dados tabulares. Essas classes estão contidas no <xref:System.Windows.Forms?displayProperty=nameWithType> namespace e eles são nomeados com o prefixo "DataGridView".  
  
## <a name="architecture-elements"></a>Elementos de arquitetura  
 O principal <xref:System.Windows.Forms.DataGridView> derivam de classes complementares <xref:System.Windows.Forms.DataGridViewElement>. O modelo de objeto a seguir ilustra o <xref:System.Windows.Forms.DataGridViewElement> hierarquia de herança.  
  
 ![Diagrama que mostra a hierarquia do objeto Datagridviewelement.](./media/datagridview-control-architecture-windows-forms/datagridviewelement-object-model.gif)  
  
 O <xref:System.Windows.Forms.DataGridViewElement> classe fornece uma referência ao pai <xref:System.Windows.Forms.DataGridView> controlar e tem um <xref:System.Windows.Forms.DataGridViewElement.State%2A> propriedade, que contém um valor que representa uma combinação de valores da <xref:System.Windows.Forms.DataGridViewElementStates> enumeração.  
  
 As seções a seguir descrevem o <xref:System.Windows.Forms.DataGridView> complementar classes mais detalhadamente.  
  
### <a name="datagridviewelementstates"></a>DataGridViewElementStates  
 O <xref:System.Windows.Forms.DataGridViewElementStates> enumeração contém os seguintes valores:  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 Os valores dessa enumeração podem ser combinados com os operadores lógicos bit a bit, portanto, o <xref:System.Windows.Forms.DataGridViewElement.State%2A> propriedade pode expressar mais de um estado de uma só vez. Por exemplo, uma <xref:System.Windows.Forms.DataGridViewElement> podem ser simultaneamente <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, e <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.  
  
### <a name="cells-and-bands"></a>Células e faixas  
 O <xref:System.Windows.Forms.DataGridView> controle consiste em dois tipos de objetos fundamentais: células e faixas. Todas as células derivam o <xref:System.Windows.Forms.DataGridViewCell> classe base. Os dois tipos de faixas, <xref:System.Windows.Forms.DataGridViewColumn> e <xref:System.Windows.Forms.DataGridViewRow>, ambos derivam o <xref:System.Windows.Forms.DataGridViewBand> classe base.  
  
 O <xref:System.Windows.Forms.DataGridView> controle interopera com várias classes, mas são mais comumente encontrados <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, e <xref:System.Windows.Forms.DataGridViewRow>.  
  
### <a name="datagridviewcell"></a>DataGridViewCell  
 A célula é a unidade fundamental de interação para o <xref:System.Windows.Forms.DataGridView>. A exibição é centralizada das células e entrada de dados geralmente é realizada por meio das células. Você pode acessar as células usando o <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> coleção do <xref:System.Windows.Forms.DataGridViewRow> classe e você pode acessar as células selecionadas usando a <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> coleção do <xref:System.Windows.Forms.DataGridView> controle. O modelo de objeto a seguir ilustra esse uso e mostra o <xref:System.Windows.Forms.DataGridViewCell> hierarquia de herança.  
  
 ![Diagrama que mostra a hierarquia de modelo do objeto DataGridViewCell.](./media/datagridview-control-architecture-windows-forms/datagridviewcell-object-model.gif)  
  
 O <xref:System.Windows.Forms.DataGridViewCell> tipo é uma classe base abstrata da qual derivam todos os tipos de célula. <xref:System.Windows.Forms.DataGridViewCell> e seus tipos derivados não são controles dos Windows Forms, mas alguns controles de formulários do Windows do host. Qualquer funcionalidade de edição com suporte de uma célula normalmente é manipulada por um controle hospedado.  
  
 <xref:System.Windows.Forms.DataGridViewCell> objetos não controlam sua aparência e seus recursos de pintura da mesma forma que os controles de formulários do Windows. Em vez disso, o <xref:System.Windows.Forms.DataGridView> é responsável pela aparência de seu <xref:System.Windows.Forms.DataGridViewCell> objetos. Você pode afetar significativamente a aparência e comportamento das células interagindo com o <xref:System.Windows.Forms.DataGridView> propriedades e eventos do controle. Quando você tiver requisitos especiais para personalizações que estão além dos recursos do <xref:System.Windows.Forms.DataGridView> controle, você pode implementar sua própria classe que deriva de <xref:System.Windows.Forms.DataGridViewCell> ou uma de suas classes filho.  
  
 A lista a seguir mostra as classes derivadas de <xref:System.Windows.Forms.DataGridViewCell>:  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewImageCell>  
  
-   <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
-   Seus tipos de célula personalizados  
  
### <a name="datagridviewcolumn"></a>DataGridViewColumn  
 O esquema do <xref:System.Windows.Forms.DataGridView> repositório de dados anexados do controle é expresso no <xref:System.Windows.Forms.DataGridView> colunas do controle. Você pode acessar o <xref:System.Windows.Forms.DataGridView> colunas do controle usando o <xref:System.Windows.Forms.DataGridView.Columns%2A> coleção. Você pode acessar as colunas selecionadas usando a <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> coleção. O modelo de objeto a seguir ilustra esse uso e mostra o <xref:System.Windows.Forms.DataGridViewColumn> hierarquia de herança.  
  
 ![Diagrama que mostra a hierarquia de modelo do objeto DataGridViewColumn.](./media/datagridview-control-architecture-windows-forms/datagridviewcolumn-object-model.gif)  
  
 Alguns dos principais tipos de células têm tipos de colunas correspondentes. Eles derivam o <xref:System.Windows.Forms.DataGridViewColumn> classe base.  
  
 A lista a seguir mostra as classes derivadas de <xref:System.Windows.Forms.DataGridViewColumn>:  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   Seus tipos de colunas personalizadas  
  
### <a name="datagridview-editing-controls"></a>Controles de edição de DataGridView  
 Células que dão suporte a recursos de edição avançados normalmente usam um controle hospedado que é derivado de um controle dos Windows Forms. Esses controles também implementam a <xref:System.Windows.Forms.IDataGridViewEditingControl> interface. O modelo de objeto a seguir ilustra o uso desses controles.  
  
 ![Diagrama mostrando a hierarquia de modelo de objeto de controle de edição de DataGridView.](./media/datagridview-control-architecture-windows-forms/datagridviewediting-object-model.gif)  
  
 Os controles de edição a seguir são fornecidos com o <xref:System.Windows.Forms.DataGridView> controle:  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 Para obter informações sobre como criar suas própria edição de controles, consulte [como: Hospedar controles em Windows Forms células DataGridView](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
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
 O <xref:System.Windows.Forms.DataGridViewRow> exibe classe campos de dados de um registro dos dados da loja para o qual o <xref:System.Windows.Forms.DataGridView> controle está anexado. Você pode acessar o <xref:System.Windows.Forms.DataGridView> linhas do controle usando o <xref:System.Windows.Forms.DataGridView.Rows%2A> coleção. Você pode acessar as linhas selecionadas usando a <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> coleção. O modelo de objeto a seguir ilustra esse uso e mostra o <xref:System.Windows.Forms.DataGridViewRow> hierarquia de herança.  
  
 ![Diagrama que mostra a hierarquia de modelo do objeto DataGridViewRow.](./media/datagridview-control-architecture-windows-forms/datagridviewrow-object-model.gif)
  
 Você pode derivar seus próprios tipos da <xref:System.Windows.Forms.DataGridViewRow> classe, embora isso normalmente não será necessário. O <xref:System.Windows.Forms.DataGridView> controle tem vários eventos relacionados à linha e propriedades para personalizar o comportamento do seu <xref:System.Windows.Forms.DataGridViewRow> objetos.  
  
 Se você habilitar a <xref:System.Windows.Forms.DataGridView> do controle <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> propriedade, uma linha especial para adicionar novas linhas aparecerá como a última linha. Esta linha é parte do <xref:System.Windows.Forms.DataGridView.Rows%2A> coleção, mas ele tem uma funcionalidade especial que pode exigir sua atenção. Para obter mais informações, consulte [Usando a linha para novos registros no controle DataGridView dos Windows Forms](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Consulte também

- [Visão geral do controle DataGridView](datagridview-control-overview-windows-forms.md)
- [Personalizando o controle DataGridView dos Windows Forms](customizing-the-windows-forms-datagridview-control.md)
- [Usando a linha para novos registros no controle DataGridView dos Windows Forms](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
