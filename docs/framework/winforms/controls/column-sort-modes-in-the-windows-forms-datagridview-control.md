---
title: Modos de classificação da coluna no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: b8f6048946d367dd79b1ce0d23d84446ffdb1115
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59106660"
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Modos de classificação da coluna no controle DataGridView dos Windows Forms
<xref:System.Windows.Forms.DataGridView> colunas têm três modos de classificação. O modo de classificação para cada coluna é especificado por meio de <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> propriedade da coluna, que pode ser definida como um dos seguintes <xref:System.Windows.Forms.DataGridViewColumnSortMode> valores de enumeração.  
  
|Valor `DataGridViewColumnSortMode`|Descrição|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|Padrão para colunas de caixa de texto. A menos que os cabeçalhos de coluna são usados para seleção, clicar no cabeçalho da coluna automaticamente classifica o <xref:System.Windows.Forms.DataGridView> por esta coluna e exibe um glifo indicando a ordem de classificação.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|Padrão para colunas sem caixa de texto. Você pode classificar essa coluna programaticamente. No entanto, ela não se destina à classificação, então nenhum espaço é reservado para o glifo de classificação.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|Você pode classificar essa coluna programaticamente e o espaço é reservado para o glifo de classificação.|  
  
 Você talvez queira alterar o modo de classificação para uma coluna que usa como padrão <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> se ela contiver valores que podem ser ordenados. Por exemplo, se tiver uma coluna de banco de dados que contêm números que representam os estados de item, você poderá exibir esses números como ícones correspondentes ao associar uma coluna de imagem para a coluna de banco de dados. Em seguida, você pode alterar os valores de célula numéricos em valores de exibição de imagem em um manipulador para o <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> eventos. Nesse caso, definindo a <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> propriedade para <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic> permitirá que os usuários classificar a coluna. A classificação automática permitirá que os usuários agrupem itens que tenham o mesmo estado, mesmo se os estados correspondentes aos números não tiverem uma sequência natural. As colunas da caixa de seleção são outro exemplo no qual a classificação automática é útil para agrupar itens no mesmo estado.  
  
 Você pode classificar uma <xref:System.Windows.Forms.DataGridView> programaticamente, os valores em qualquer coluna ou em várias colunas, independentemente do <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> configurações. A classificação programática é útil quando você deseja fornecer sua própria interface do usuário para classificação ou quando você deseja implementar a classificação personalizada. Fornecendo sua própria interface do usuário de classificação é útil, por exemplo, quando você define o <xref:System.Windows.Forms.DataGridView> modo de seleção para habilitar a seleção do cabeçalho de coluna. Nesse caso, embora os cabeçalhos de coluna não podem ser usados para classificação, você ainda deseja que os cabeçalhos para exibir o glifo de classificação apropriado, então você definiria o <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> propriedade para <xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>.  
  
 As colunas definidas como modo de classificação programática não exibem um glifo de classificação automaticamente. Para essas colunas, você deve exibir o glifo por conta própria, configurando o <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> propriedade. Isso é necessário se você quiser flexibilidade na classificação personalizada. Por exemplo, se você classificar o <xref:System.Windows.Forms.DataGridView> por várias colunas, você talvez queira exibir vários glifos de classificação ou nenhum glifo de classificação.  
  
 Embora você possa classificar programaticamente um <xref:System.Windows.Forms.DataGridView> por qualquer coluna, algumas colunas, como colunas de botão, podem não conter valores que podem ser ordenados. Para essas colunas, uma <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> configuração da propriedade de <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> indica que ele nunca será usado para classificação, portanto, não é necessário para reservar espaço no cabeçalho do glifo de classificação.  
  
 Quando um <xref:System.Windows.Forms.DataGridView> é classificada, você pode determinar a coluna de classificação e a ordem de classificação verificando os valores da <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> e <xref:System.Windows.Forms.DataGridView.SortOrder%2A> propriedades. Esses valores não são significativos após uma operação de classificação personalizada. Para obter mais informações sobre classificação personalizada, consulte a seção Classificação Personalizada neste tópico.  
  
 Quando um <xref:System.Windows.Forms.DataGridView> controle contendo colunas associadas e não associadas for classificado, os valores nas colunas não associadas não podem ser mantidos automaticamente. Para manter esses valores, você deve implementar o modo virtual, definindo o <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> propriedade para `true` e manipulando os <xref:System.Windows.Forms.DataGridView.CellValueNeeded> e <xref:System.Windows.Forms.DataGridView.CellValuePushed> eventos. Para obter mais informações, confira [Como: Implementar o modo Virtual no Windows Forms DataGridView Control](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md). Não há suporte para a classificação por colunas não associadas no modo associado.  
  
## <a name="programmatic-sorting"></a>Classificação programática  
 Você pode classificar uma <xref:System.Windows.Forms.DataGridView> programaticamente, chamando seu <xref:System.Windows.Forms.DataGridView.Sort%2A> método.  
  
 O `Sort(DataGridViewColumn,ListSortDirection)` sobrecarga da <xref:System.Windows.Forms.DataGridView.Sort%2A> leva um <xref:System.Windows.Forms.DataGridViewColumn> e um <xref:System.ComponentModel.ListSortDirection> valor de enumeração como parâmetros. Essa sobrecarga é útil ao classificar por colunas com valores que podem ser ordenados significativamente, mas que você não deseja configurar para a classificação automática. Quando você chamar essa sobrecarga e passa em uma coluna com um <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> valor da propriedade de <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>, o <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> e <xref:System.Windows.Forms.DataGridView.SortOrder%2A> propriedades são definidas automaticamente e o glifo de classificação apropriado é exibido no cabeçalho da coluna.  
  
> [!NOTE]
>  Quando o <xref:System.Windows.Forms.DataGridView> controle está vinculado a uma fonte de dados externa, definindo o <xref:System.Windows.Forms.DataGridView.DataSource%2A> propriedade, o `Sort(DataGridViewColumn,ListSortDirection)` sobrecarga de método não funciona para colunas não associadas. Além disso, quando o <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> é de propriedade `true`, você pode chamar essa sobrecarga apenas para colunas associadas. Para determinar se uma coluna é associada a dados, verifique o <xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A> valor da propriedade. Não há suporte para a classificação por colunas não associadas no modo associado.  
  
## <a name="custom-sorting"></a>Classificação personalizada  
 Você pode personalizar <xref:System.Windows.Forms.DataGridView> usando o `Sort(IComparer)` sobrecarga da <xref:System.Windows.Forms.DataGridView.Sort%2A> método ou manipulando o <xref:System.Windows.Forms.DataGridView.SortCompare> eventos.  
  
 O `Sort(IComparer)` sobrecarga de método tem uma instância de uma classe que implementa o <xref:System.Collections.IComparer> interface como parâmetro. Essa sobrecarga é útil quando você deseja fornecer classificação personalizada. Por exemplo, quando os valores em uma coluna não têm uma ordem de classificação natural ou quando a ordem de classificação natural é inadequada. Nesse caso, você não pode usar a classificação automática, mas talvez ainda queira que os usuários classifiquem clicando em cabeçalhos de coluna. Você pode chamar essa sobrecarga em um manipulador para o <xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick> se você não usar cabeçalhos de coluna para seleção de eventos.  
  
> [!NOTE]
>  O `Sort(IComparer)` sobrecarga do método funciona somente quando o <xref:System.Windows.Forms.DataGridView> controle não está associado a uma fonte de dados externa e o <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> é o valor da propriedade `false`. Para personalizar a classificação para colunas associadas a uma fonte de dados externa, você deve usar as operações de classificação fornecidas pela fonte de dados. No modo virtual, você deve fornecer suas próprias operações de classificação para colunas não associadas.  
  
 Para usar o `Sort(IComparer)` sobrecarga de método, você deve criar sua própria classe que implementa o <xref:System.Collections.IComparer> interface. Essa interface requer que sua classe implemente a <xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType> método ao qual o <xref:System.Windows.Forms.DataGridView> passa <xref:System.Windows.Forms.DataGridViewRow> objetos como entrada quando o `Sort(IComparer)` sobrecarga do método é chamada. Com isso, você pode calcular a ordem correta da linha com base nos valores em qualquer coluna.  
  
 O `Sort(IComparer)` sobrecarga de método não define o <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> e <xref:System.Windows.Forms.DataGridView.SortOrder%2A> propriedades, portanto, você sempre deve definir o <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> propriedade para exibir o glifo de classificação.  
  
 Como uma alternativa para o `Sort(IComparer)` sobrecarga de método, você pode fornecer classificação personalizada implementando um manipulador para o <xref:System.Windows.Forms.DataGridView.SortCompare> eventos. Esse evento ocorre quando os usuários clicam em cabeçalhos de colunas configuradas para a classificação automática ou quando você chama o `Sort(DataGridViewColumn,ListSortDirection)` sobrecarga da <xref:System.Windows.Forms.DataGridView.Sort%2A> método. O evento ocorre para cada par de linhas no controle, permitindo que você calcule a ordem correta.  
  
> [!NOTE]
>  O <xref:System.Windows.Forms.DataGridView.SortCompare> evento não ocorre quando o <xref:System.Windows.Forms.DataGridView.DataSource%2A> estiver definida ou quando o <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> é o valor da propriedade `true`.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>
- [Classificando dados no controle DataGridView dos Windows Forms](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Como: Definir os modos de classificação para colunas no controle DataGridView dos Windows Forms](set-the-sort-modes-for-columns-wf-datagridview-control.md)
- [Como: Personalizar a classificação no controle DataGridView dos Windows Forms](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
