---
title: Modos de classificação da coluna no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: d0d743ccae38d101eda5bb9780b33ae18dfb608a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918457"
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Modos de classificação da coluna no controle DataGridView dos Windows Forms
<xref:System.Windows.Forms.DataGridView>as colunas têm três modos de classificação. O modo de classificação para cada coluna é especificado por <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> meio da propriedade da coluna, que pode ser definida como um dos valores <xref:System.Windows.Forms.DataGridViewColumnSortMode> de enumeração a seguir.  
  
|Valor `DataGridViewColumnSortMode`|Descrição|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|Padrão para colunas de caixa de texto. A menos que os cabeçalhos de coluna sejam usados para seleção, clicar no cabeçalho <xref:System.Windows.Forms.DataGridView> da coluna classifica automaticamente a por esta coluna e exibe um glifo que indica a ordem de classificação.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|Padrão para colunas sem caixa de texto. Você pode classificar essa coluna programaticamente. No entanto, ela não se destina à classificação, então nenhum espaço é reservado para o glifo de classificação.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|Você pode classificar essa coluna programaticamente e o espaço é reservado para o glifo de classificação.|  
  
 Talvez você queira alterar o modo de classificação de uma coluna que usa como padrão <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> se ela contém valores que podem ser ordenados de forma significativa. Por exemplo, se tiver uma coluna de banco de dados que contêm números que representam os estados de item, você poderá exibir esses números como ícones correspondentes ao associar uma coluna de imagem para a coluna de banco de dados. Em seguida, você pode alterar os valores numéricos de célula em valores de exibição de imagem <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> em um manipulador para o evento. Nesse caso, definir a <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> Propriedade como <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic> permitirá que os usuários classifiquem a coluna. A classificação automática permitirá que os usuários agrupem itens que tenham o mesmo estado, mesmo se os estados correspondentes aos números não tiverem uma sequência natural. As colunas da caixa de seleção são outro exemplo no qual a classificação automática é útil para agrupar itens no mesmo estado.  
  
 Você pode classificar um <xref:System.Windows.Forms.DataGridView> programaticamente pelos valores em qualquer coluna ou em várias colunas, independentemente <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> das configurações. A classificação programática é útil quando você deseja fornecer sua própria interface do usuário para classificação ou quando você deseja implementar a classificação personalizada. Fornecer sua própria interface do usuário de classificação é útil, por exemplo, quando <xref:System.Windows.Forms.DataGridView> você define o modo de seleção para habilitar a seleção de cabeçalho de coluna. Nesse caso, embora os cabeçalhos de coluna não possam ser usados para classificação, você ainda deseja que os cabeçalhos exibam o glifo de classificação apropriado, portanto, <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> você definiria a propriedade como. <xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>  
  
 As colunas definidas como modo de classificação programática não exibem um glifo de classificação automaticamente. Para essas colunas, você mesmo deve exibir o glifo definindo a <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> propriedade. Isso é necessário se você quiser flexibilidade na classificação personalizada. Por exemplo, se você classificar o <xref:System.Windows.Forms.DataGridView> por várias colunas, talvez queira exibir vários glifos de classificação ou nenhum glifo de classificação.  
  
 Embora você possa classificar programaticamente uma <xref:System.Windows.Forms.DataGridView> por qualquer coluna, algumas colunas, como colunas de botão, podem não conter valores que possam ser ordenados de forma significativa. Para essas colunas, uma <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> configuração de <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> propriedade indica que ela nunca será usada para classificação, portanto, não há necessidade de reservar espaço no cabeçalho para o glifo de classificação.  
  
 Quando um <xref:System.Windows.Forms.DataGridView> é classificado, você pode determinar a coluna de classificação e a ordem de classificação verificando os valores <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> das propriedades <xref:System.Windows.Forms.DataGridView.SortOrder%2A> e. Esses valores não são significativos após uma operação de classificação personalizada. Para obter mais informações sobre classificação personalizada, consulte a seção Classificação Personalizada neste tópico.  
  
 Quando um <xref:System.Windows.Forms.DataGridView> controle que contém colunas vinculadas e desassociadas é classificado, os valores nas colunas não associadas não podem ser mantidos automaticamente. Para manter esses valores, você deve implementar o modo virtual definindo a <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> Propriedade como `true` e manipulando <xref:System.Windows.Forms.DataGridView.CellValueNeeded> os <xref:System.Windows.Forms.DataGridView.CellValuePushed> eventos e. Para obter mais informações, confira [Como: Implemente o modo virtual no controle](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)Windows Forms DataGridView. Não há suporte para a classificação por colunas não associadas no modo associado.  
  
## <a name="programmatic-sorting"></a>Classificação programática  
 Você pode classificar um <xref:System.Windows.Forms.DataGridView> programaticamente chamando <xref:System.Windows.Forms.DataGridView.Sort%2A> seu método.  
  
 A `Sort(DataGridViewColumn,ListSortDirection)` sobrecarga <xref:System.Windows.Forms.DataGridViewColumn> <xref:System.ComponentModel.ListSortDirection> do método usa um e um valor de enumeração como parâmetros. <xref:System.Windows.Forms.DataGridView.Sort%2A> Essa sobrecarga é útil ao classificar por colunas com valores que podem ser ordenados significativamente, mas que você não deseja configurar para a classificação automática. Quando você chama essa sobrecarga e passa uma coluna com <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> um valor de propriedade de <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>, as <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> Propriedades e <xref:System.Windows.Forms.DataGridView.SortOrder%2A> são definidas automaticamente e o glifo de classificação apropriado é exibido no cabeçalho da coluna.  
  
> [!NOTE]
> Quando o <xref:System.Windows.Forms.DataGridView> controle está associado a uma fonte de dados externa definindo a <xref:System.Windows.Forms.DataGridView.DataSource%2A> Propriedade, a `Sort(DataGridViewColumn,ListSortDirection)` sobrecarga do método não funciona para colunas desassociadas. Além disso, quando <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> a propriedade `true`é, você pode chamar essa sobrecarga somente para colunas associadas. Para determinar se uma coluna é associada a dados, verifique o <xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A> valor da propriedade. Não há suporte para a classificação por colunas não associadas no modo associado.  
  
## <a name="custom-sorting"></a>Classificação personalizada  
 Você pode personalizar <xref:System.Windows.Forms.DataGridView> usando a `Sort(IComparer)` sobrecarga do <xref:System.Windows.Forms.DataGridView.Sort%2A> método ou manipulando o <xref:System.Windows.Forms.DataGridView.SortCompare> evento.  
  
 A `Sort(IComparer)` sobrecarga do método usa uma instância de uma classe que implementa <xref:System.Collections.IComparer> a interface como um parâmetro. Essa sobrecarga é útil quando você deseja fornecer classificação personalizada. Por exemplo, quando os valores em uma coluna não têm uma ordem de classificação natural ou quando a ordem de classificação natural é inadequada. Nesse caso, você não pode usar a classificação automática, mas talvez ainda queira que os usuários classifiquem clicando em cabeçalhos de coluna. Você pode chamar essa sobrecarga em um manipulador para o <xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick> evento se não usar cabeçalhos de coluna para seleção.  
  
> [!NOTE]
> A `Sort(IComparer)` sobrecarga do método só funciona quando <xref:System.Windows.Forms.DataGridView> o controle não está associado a uma fonte de dados externa <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> e o valor `false`da propriedade é. Para personalizar a classificação para colunas associadas a uma fonte de dados externa, você deve usar as operações de classificação fornecidas pela fonte de dados. No modo virtual, você deve fornecer suas próprias operações de classificação para colunas não associadas.  
  
 Para usar a `Sort(IComparer)` sobrecarga do método, você deve criar sua própria classe que implementa <xref:System.Collections.IComparer> a interface. Essa interface requer que sua classe implemente <xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType> o método, ao qual <xref:System.Windows.Forms.DataGridView> o <xref:System.Windows.Forms.DataGridViewRow> passa objetos como entrada quando `Sort(IComparer)` a sobrecarga do método é chamada. Com isso, você pode calcular a ordem correta da linha com base nos valores em qualquer coluna.  
  
 A `Sort(IComparer)` sobrecarga do método não define as <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> propriedades <xref:System.Windows.Forms.DataGridView.SortOrder%2A> e, portanto, você deve sempre definir <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> a propriedade para exibir o glifo de classificação.  
  
 Como alternativa à sobrecarga do `Sort(IComparer)` método, você pode fornecer classificação personalizada implementando um manipulador para o <xref:System.Windows.Forms.DataGridView.SortCompare> evento. Esse evento ocorre quando os usuários clicam nos cabeçalhos das colunas configuradas para classificação automática ou `Sort(DataGridViewColumn,ListSortDirection)` quando você chama <xref:System.Windows.Forms.DataGridView.Sort%2A> a sobrecarga do método. O evento ocorre para cada par de linhas no controle, permitindo que você calcule a ordem correta.  
  
> [!NOTE]
> O <xref:System.Windows.Forms.DataGridView.SortCompare> evento não ocorre quando a <xref:System.Windows.Forms.DataGridView.DataSource%2A> propriedade é definida ou quando o valor <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> da propriedade é `true`.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>
- [Classificando dados no controle DataGridView dos Windows Forms](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Como: Definir os modos de classificação para colunas no controle Windows Forms DataGridView](set-the-sort-modes-for-columns-wf-datagridview-control.md)
- [Como: Personalizar a classificação no controle Windows Forms DataGridView](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
