---
title: Modos de classificação de coluna no controle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: d1e2f582c9759332e0ed963cb7f88ee052616c45
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744200"
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Modos de classificação da coluna no controle DataGridView dos Windows Forms
<xref:System.Windows.Forms.DataGridView> colunas têm três modos de classificação. O modo de classificação para cada coluna é especificado por meio da propriedade <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> da coluna, que pode ser definida como um dos valores de enumeração a seguir <xref:System.Windows.Forms.DataGridViewColumnSortMode>.  
  
|`DataGridViewColumnSortMode` valor|Descrição|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|Padrão para colunas de caixa de texto. A menos que os cabeçalhos de coluna sejam usados para seleção, clicar no cabeçalho da coluna classifica automaticamente o <xref:System.Windows.Forms.DataGridView> por essa coluna e exibe um glifo que indica a ordem de classificação.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|Padrão para colunas sem caixa de texto. Você pode classificar essa coluna programaticamente. No entanto, ela não se destina à classificação, então nenhum espaço é reservado para o glifo de classificação.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|Você pode classificar essa coluna programaticamente e o espaço é reservado para o glifo de classificação.|  
  
 Talvez você queira alterar o modo de classificação de uma coluna que usa como padrão <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> se ela contiver valores que possam ser ordenados de forma significativa. Por exemplo, se tiver uma coluna de banco de dados que contêm números que representam os estados de item, você poderá exibir esses números como ícones correspondentes ao associar uma coluna de imagem para a coluna de banco de dados. Em seguida, você pode alterar os valores numéricos de célula em valores de exibição de imagem em um manipulador para o evento <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>. Nesse caso, configurar a propriedade <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> como <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic> permitirá que os usuários classifiquem a coluna. A classificação automática permitirá que os usuários agrupem itens que tenham o mesmo estado, mesmo se os estados correspondentes aos números não tiverem uma sequência natural. As colunas da caixa de seleção são outro exemplo no qual a classificação automática é útil para agrupar itens no mesmo estado.  
  
 Você pode classificar um <xref:System.Windows.Forms.DataGridView> programaticamente pelos valores em qualquer coluna ou em várias colunas, independentemente das configurações de <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>. A classificação programática é útil quando você deseja fornecer sua própria interface do usuário para classificação ou quando você deseja implementar a classificação personalizada. Fornecer sua própria interface do usuário de classificação é útil, por exemplo, quando você define o modo de seleção de <xref:System.Windows.Forms.DataGridView> para habilitar a seleção de cabeçalho de coluna. Nesse caso, embora os cabeçalhos de coluna não possam ser usados para classificação, você ainda deseja que os cabeçalhos exibam o glifo de classificação apropriado, portanto, você definiria a propriedade <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> como <xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>.  
  
 As colunas definidas como modo de classificação programática não exibem um glifo de classificação automaticamente. Para essas colunas, você mesmo deve exibir o glifo definindo a propriedade <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>. Isso é necessário se você quiser flexibilidade na classificação personalizada. Por exemplo, se você classificar o <xref:System.Windows.Forms.DataGridView> por várias colunas, talvez queira exibir vários glifos de classificação ou nenhum glifo de classificação.  
  
 Embora você possa classificar programaticamente um <xref:System.Windows.Forms.DataGridView> por qualquer coluna, algumas colunas, como colunas de botão, podem não conter valores que possam ser ordenados de forma significativa. Para essas colunas, uma configuração de propriedade <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> de <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> indica que ela nunca será usada para classificação, portanto, não há necessidade de reservar espaço no cabeçalho para o glifo de classificação.  
  
 Quando um <xref:System.Windows.Forms.DataGridView> é classificado, você pode determinar a coluna de classificação e a ordem de classificação verificando os valores das propriedades <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> e <xref:System.Windows.Forms.DataGridView.SortOrder%2A>. Esses valores não são significativos após uma operação de classificação personalizada. Para obter mais informações sobre classificação personalizada, consulte a seção Classificação Personalizada neste tópico.  
  
 Quando um controle de <xref:System.Windows.Forms.DataGridView> que contém colunas vinculadas e desassociadas é classificado, os valores nas colunas não associadas não podem ser mantidos automaticamente. Para manter esses valores, você deve implementar o modo virtual definindo a propriedade <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> como `true` e manipulando os eventos <xref:System.Windows.Forms.DataGridView.CellValueNeeded> e <xref:System.Windows.Forms.DataGridView.CellValuePushed>. Para obter mais informações, consulte [Como implementar o modo virtual no controle DataGridView dos Windows Forms](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md). Não há suporte para a classificação por colunas não associadas no modo associado.  
  
## <a name="programmatic-sorting"></a>Classificação programática  
 Você pode classificar um <xref:System.Windows.Forms.DataGridView> programaticamente chamando seu método <xref:System.Windows.Forms.DataGridView.Sort%2A>.  
  
 A sobrecarga de `Sort(DataGridViewColumn,ListSortDirection)` do método <xref:System.Windows.Forms.DataGridView.Sort%2A> usa um <xref:System.Windows.Forms.DataGridViewColumn> e um valor de enumeração de <xref:System.ComponentModel.ListSortDirection> como parâmetros. Essa sobrecarga é útil ao classificar por colunas com valores que podem ser ordenados significativamente, mas que você não deseja configurar para a classificação automática. Quando você chama essa sobrecarga e passa uma coluna com um valor de propriedade <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> de <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>, as propriedades <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> e <xref:System.Windows.Forms.DataGridView.SortOrder%2A> são definidas automaticamente e o glifo de classificação apropriado é exibido no cabeçalho da coluna.  
  
> [!NOTE]
> Quando o controle de <xref:System.Windows.Forms.DataGridView> está associado a uma fonte de dados externa, definindo a propriedade <xref:System.Windows.Forms.DataGridView.DataSource%2A>, a sobrecarga do método `Sort(DataGridViewColumn,ListSortDirection)` não funciona para colunas desassociadas. Além disso, quando a propriedade <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> é `true`, você pode chamar essa sobrecarga somente para colunas associadas. Para determinar se uma coluna é associada a dados, verifique o valor da propriedade <xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A>. Não há suporte para a classificação por colunas não associadas no modo associado.  
  
## <a name="custom-sorting"></a>Classificação personalizada  
 Você pode personalizar <xref:System.Windows.Forms.DataGridView> usando a sobrecarga `Sort(IComparer)` do método <xref:System.Windows.Forms.DataGridView.Sort%2A> ou manipulando o evento <xref:System.Windows.Forms.DataGridView.SortCompare>.  
  
 A sobrecarga do método `Sort(IComparer)` usa uma instância de uma classe que implementa a interface <xref:System.Collections.IComparer> como um parâmetro. Essa sobrecarga é útil quando você deseja fornecer classificação personalizada. Por exemplo, quando os valores em uma coluna não têm uma ordem de classificação natural ou quando a ordem de classificação natural é inadequada. Nesse caso, você não pode usar a classificação automática, mas talvez ainda queira que os usuários classifiquem clicando em cabeçalhos de coluna. Você pode chamar essa sobrecarga em um manipulador para o evento <xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick> se não usar cabeçalhos de coluna para seleção.  
  
> [!NOTE]
> A sobrecarga do método de `Sort(IComparer)` só funciona quando o controle de <xref:System.Windows.Forms.DataGridView> não está associado a uma fonte de dados externa e o valor da propriedade <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> é `false`. Para personalizar a classificação para colunas associadas a uma fonte de dados externa, você deve usar as operações de classificação fornecidas pela fonte de dados. No modo virtual, você deve fornecer suas próprias operações de classificação para colunas não associadas.  
  
 Para usar a sobrecarga do método de `Sort(IComparer)`, você deve criar sua própria classe que implementa a interface <xref:System.Collections.IComparer>. Essa interface requer que sua classe implemente o método <xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType>, ao qual o <xref:System.Windows.Forms.DataGridView> passa <xref:System.Windows.Forms.DataGridViewRow> objetos como entrada quando a sobrecarga do método `Sort(IComparer)` é chamada. Com isso, você pode calcular a ordem correta da linha com base nos valores em qualquer coluna.  
  
 A sobrecarga do método de `Sort(IComparer)` não define as propriedades <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> e <xref:System.Windows.Forms.DataGridView.SortOrder%2A>, portanto, você deve sempre definir a propriedade <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> para exibir o glifo de classificação.  
  
 Como alternativa à sobrecarga do método de `Sort(IComparer)`, você pode fornecer classificação personalizada implementando um manipulador para o evento <xref:System.Windows.Forms.DataGridView.SortCompare>. Esse evento ocorre quando os usuários clicam nos cabeçalhos das colunas configuradas para classificação automática ou quando você chama a sobrecarga de `Sort(DataGridViewColumn,ListSortDirection)` do método <xref:System.Windows.Forms.DataGridView.Sort%2A>. O evento ocorre para cada par de linhas no controle, permitindo que você calcule a ordem correta.  
  
> [!NOTE]
> O evento <xref:System.Windows.Forms.DataGridView.SortCompare> não ocorre quando a propriedade <xref:System.Windows.Forms.DataGridView.DataSource%2A> é definida ou quando o valor da propriedade <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> é `true`.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>
- [Classificando dados no controle DataGridView do Windows Forms](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Como definir os modos de classificação para colunas no controle DataGridView dos Windows Forms](set-the-sort-modes-for-columns-wf-datagridview-control.md)
- [Como personalizar a classificação no controle DataGridView dos Windows Forms](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
