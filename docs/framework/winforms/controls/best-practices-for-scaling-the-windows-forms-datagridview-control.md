---
title: Práticas recomendadas para dimensionar o controle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sharing
- data grids [Windows Forms], best practices
- DataGridView control [Windows Forms], shared rows
- DataGridView control [Windows Forms], best practices
- best practices [Windows Forms], dataGridView control
- DataGridView control [Windows Forms], scaling
ms.assetid: 8321a8a6-6340-4fd1-b475-fa090b905aaf
ms.openlocfilehash: 63500a79def89510b4bc7a436abc4620a7265a79
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744131"
---
# <a name="best-practices-for-scaling-the-windows-forms-datagridview-control"></a>Práticas recomendadas para dimensionamento do controle DataGridView dos Windows Forms

O controle <xref:System.Windows.Forms.DataGridView> foi projetado para fornecer a escalabilidade máxima. Se você precisa exibir grandes quantidades de dados, siga as diretrizes descritas neste tópico para evitar o consumo de grandes quantidades de memória ou prejudicar a capacidade de resposta da UI (interface do usuário). Este tópico discute os seguintes problemas:

- Usando estilos de célula com eficiência

- Usando menus de atalho com eficiência

- Usando o redimensionamento automático com eficiência

- Usando as coleções de células, linhas e colunas selecionadas com eficiência

- Usando linhas compartilhadas

- Impedindo as linhas de se tornarem não compartilhadas

Se você tiver necessidades de desempenho especiais, implemente o modo virtual e forneça suas próprias operações de gerenciamento de dados. Para obter mais informações, consulte [Modos de exibição dos dados no controle DataGridView dos Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md).

## <a name="using-cell-styles-efficiently"></a>Usando Estilos de Célula com Eficiência

Cada célula, linha e coluna pode ter suas próprias informações de estilo. As informações de estilo são armazenadas em objetos <xref:System.Windows.Forms.DataGridViewCellStyle>. A criação de objetos de estilo de célula para muitos elementos de <xref:System.Windows.Forms.DataGridView> individuais pode ser ineficiente, especialmente ao trabalhar com grandes quantidades de dados. Para evitar um impacto no desempenho, use as seguintes diretrizes:

- Evite definir propriedades de estilo de célula para objetos <xref:System.Windows.Forms.DataGridViewCell> individuais ou <xref:System.Windows.Forms.DataGridViewRow>. Isso inclui o objeto Row especificado pela propriedade <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>. Cada nova linha que é clonada do modelo de linha receberá sua própria cópia do objeto de estilo de célula do modelo. Para obter a escalabilidade máxima, defina as propriedades de estilo de célula no nível de <xref:System.Windows.Forms.DataGridView>. Por exemplo, defina a propriedade <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> em vez da propriedade <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>.

- Se algumas células exigirem formatação diferente da formatação padrão, use a mesma <xref:System.Windows.Forms.DataGridViewCellStyle> instância em grupos de células, linhas ou colunas. Evite definir diretamente as propriedades do tipo <xref:System.Windows.Forms.DataGridViewCellStyle> em células, linhas e colunas individuais. Para obter um exemplo de compartilhamento de estilo de célula, consulte [Instruções: definir estilos de célula padrão para o controle DataGridView dos Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md). Você também pode evitar uma penalidade de desempenho ao definir estilos de célula individualmente manipulando o manipulador de eventos <xref:System.Windows.Forms.DataGridView.CellFormatting>. Para obter um exemplo, consulte [Instruções: personalizar a formatação de dados no controle DataGridView dos Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).

- Ao determinar o estilo de uma célula, use a propriedade <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType> em vez da propriedade <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>. O acesso à propriedade <xref:System.Windows.Forms.DataGridViewCell.Style%2A> cria uma nova instância da classe <xref:System.Windows.Forms.DataGridViewCellStyle> se a propriedade ainda não tiver sido usada. Além disso, esse objeto poderá não conter as informações de estilo completas para a célula se alguns estilos forem herdados da linha, da coluna ou do controle. Para obter mais informações sobre herança de estilo de célula, consulte [Estilos de célula no controle DataGridView dos Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).

## <a name="using-shortcut-menus-efficiently"></a>Usando Menus de Atalho com Eficiência

Cada célula, linha e coluna pode ter seu próprio menu de atalho. Os menus de atalho no controle de <xref:System.Windows.Forms.DataGridView> são representados por <xref:System.Windows.Forms.ContextMenuStrip> controles. Assim como ocorre com objetos de estilo de célula, a criação de menus de atalho para muitos elementos de <xref:System.Windows.Forms.DataGridView> individuais afetará negativamente o desempenho. Para evitar essa penalidade, use as seguintes diretrizes:

- Evite criar menus de atalho para células e linhas individuais. Isso inclui o modelo de linha, que é clonado juntamente com o menu de atalho quando novas linhas são adicionadas ao controle. Para obter a escalabilidade máxima, use apenas a propriedade <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> do controle para especificar um único menu de atalho para o controle inteiro.

- Se você precisar de vários menus de atalho para várias linhas ou células, manipule os eventos <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> ou <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>. Esses eventos permitem gerenciar os objetos do menu de atalho por conta própria, possibilitando ajustar o desempenho.

## <a name="using-automatic-resizing-efficiently"></a>Usando o Redimensionamento Automático com Eficiência

Cabeçalhos, colunas e linhas podem ser redimensionados automaticamente como alterações de conteúdo da célula para que todo o conteúdo das células seja exibido sem recorte. Alterar os modos de dimensionamento também pode redimensionar linhas, colunas e cabeçalhos. Para determinar o tamanho correto, o controle de <xref:System.Windows.Forms.DataGridView> deve examinar o valor de cada célula que ele deve acomodar. Ao trabalhar com grandes conjuntos de dados, essa análise poderá afetar negativamente o desempenho do controle quando o redimensionamento automático ocorrer. Para evitar penalidades de desempenho, use as seguintes diretrizes:

- Evite usar o dimensionamento automático em um controle de <xref:System.Windows.Forms.DataGridView> com um grande conjunto de linhas. Se você usar o dimensionamento automático, redimensione apenas com base nas linhas exibidas. Além disso, use apenas as linhas exibidas no modo virtual.

  - Para linhas e colunas, use o campo `DisplayedCells` ou `DisplayedCellsExceptHeaders` das enumerações <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>, <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>e <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>.

  - Para cabeçalhos de linha, use o campo <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToDisplayedHeaders> ou <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToFirstHeader> da enumeração <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>.

- Para obter escalabilidade máxima, desligue o dimensionamento automático e use o redimensionamento programático.

Para obter mais informações, consulte [Sizing Options in the Windows Forms DataGridView Control](sizing-options-in-the-windows-forms-datagridview-control.md) (Opções de dimensionamento no controle DataGridView dos Windows Forms).

## <a name="using-the-selected-cells-rows-and-columns-collections-efficiently"></a>Usando as Coleções de Células, Linhas e Colunas Selecionadas com Eficiência

A coleção de <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> não é executada com eficiência com seleções grandes. As coleções <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> e <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> também podem ser ineficientes, embora haja menos linhas do que células em um controle de <xref:System.Windows.Forms.DataGridView> típico e muitas colunas menores que linhas. Para evitar penalidades de desempenho ao trabalhar com essas coleções, use as seguintes diretrizes:

- Para determinar se todas as células na <xref:System.Windows.Forms.DataGridView> foram selecionadas antes de acessar o conteúdo da coleção de <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, verifique o valor de retorno do método <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>. No entanto, observe que esse método pode fazer com que as linhas se tornem não compartilhadas. Para obter mais informações, consulte a próxima seção.

- Evite usar a propriedade <xref:System.Collections.ICollection.Count%2A> da <xref:System.Windows.Forms.DataGridViewSelectedCellCollection?displayProperty=nameWithType> para determinar o número de células selecionadas. Em vez disso, use o método <xref:System.Windows.Forms.DataGridView.GetCellCount%2A?displayProperty=nameWithType> e passe o valor <xref:System.Windows.Forms.DataGridViewElementStates.Selected?displayProperty=nameWithType>. Da mesma forma, use os métodos <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A?displayProperty=nameWithType> e <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A?displayProperty=nameWithType> para determinar o número de elementos selecionados, em vez de acessar as coleções de linhas e colunas selecionadas.

- Evite modos de seleção com base em célula. Em vez disso, defina a propriedade <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> como <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.

## <a name="using-shared-rows"></a>Usando Linhas Compartilhadas

O uso eficiente de memória é obtido no controle de <xref:System.Windows.Forms.DataGridView> por meio de linhas compartilhadas. As linhas compartilharão o máximo possível de informações sobre sua aparência e comportamento ao compartilhar instâncias da classe <xref:System.Windows.Forms.DataGridViewRow>.

Embora o compartilhamento de instâncias de linha poupe memória, as linhas podem facilmente se tornar não compartilhadas. Por exemplo, sempre que um usuário interage diretamente com uma célula, sua linha se torna não compartilhada. Como isso não pode ser evitado, as diretrizes neste tópico são úteis somente ao trabalhar com grandes quantidades de dados e somente quando os usuários forem interagir com uma parte relativamente pequena dos dados sempre que o programa for executado.

Uma linha não poderá ser compartilhada em um controle de <xref:System.Windows.Forms.DataGridView> não associado se qualquer uma de suas células contiver valores. Quando o controle de <xref:System.Windows.Forms.DataGridView> está associado a uma fonte de dados externa ou quando você implementa o modo virtual e fornece sua própria fonte de dados, os valores de célula são armazenados fora do controle em vez de objetos de célula, permitindo que as linhas sejam compartilhadas.

Um objeto de linha poderá ser compartilhado apenas se o estado de todas as suas células puder ser determinado por meio do estado da linha e dos estados das colunas que contêm as células. Se você alterar o estado de uma célula para que ela não possa mais ser deduzida por meio do estado de sua linha e coluna, a linha não poderá ser compartilhada.

Por exemplo, uma linha não pode ser compartilhada em nenhuma das seguintes situações:

- A linha contém uma única célula selecionada que não está em uma coluna selecionada.

- A linha contém uma célula com suas propriedades <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> ou <xref:System.Windows.Forms.DataGridViewCell.ContextMenuStrip%2A> definidas.

- A linha contém um <xref:System.Windows.Forms.DataGridViewComboBoxCell> com sua propriedade <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A> definida.

No modo ligado ou virtual, você pode fornecer dicas de ferramenta e menus de atalho para células individuais manipulando os eventos <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> e <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded>.

O controle de <xref:System.Windows.Forms.DataGridView> tentará automaticamente usar linhas compartilhadas sempre que linhas forem adicionadas à <xref:System.Windows.Forms.DataGridViewRowCollection>. Use as diretrizes a seguir para garantir que as linhas sejam compartilhadas:

- Evite chamar a sobrecarga de `Add(Object[])` do método <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> e a sobrecarga `Insert(Object[])` do método <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> da coleção de <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>. Essas sobrecargas criam linhas não compartilhadas automaticamente.

- Certifique-se de que a linha especificada na propriedade <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> possa ser compartilhada nos seguintes casos:

  - Ao chamar o `Add()` ou `Add(Int32)` sobrecargas do método <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> ou a sobrecarga `Insert(Int32,Int32)` do método <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> da coleção de <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>.

  - Ao aumentar o valor da propriedade <xref:System.Windows.Forms.DataGridView.RowCount%2A?displayProperty=nameWithType>.

  - Ao definir a propriedade <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>.

- Certifique-se de que a linha indicada pelo parâmetro `indexSource` possa ser compartilhada ao chamar os métodos <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopy%2A>e <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopies%2A> da coleção <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>.

- Certifique-se de que a linha ou as linhas especificadas possam ser compartilhadas ao chamar a sobrecarga de `Add(DataGridViewRow)` do método <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>, o método <xref:System.Windows.Forms.DataGridViewRowCollection.AddRange%2A>, a sobrecarga `Insert(Int32,DataGridViewRow)` do método <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> e o método <xref:System.Windows.Forms.DataGridViewRowCollection.InsertRange%2A> da coleção de <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>.

Para determinar se uma linha é compartilhada, use o método <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> para recuperar o objeto Row e, em seguida, verifique a propriedade <xref:System.Windows.Forms.DataGridViewBand.Index%2A> do objeto. As linhas compartilhadas sempre têm um valor de propriedade <xref:System.Windows.Forms.DataGridViewBand.Index%2A> de – 1.

## <a name="preventing-rows-from-becoming-unshared"></a>Impedindo as Linhas de se Tornarem Não Compartilhadas

As linhas compartilhadas podem se tornar não compartilhadas como resultado da ação de usuário ou de código. Para evitar um impacto no desempenho, evite fazer com que as linhas se tornem não compartilhadas. Durante o desenvolvimento de aplicativos, você pode manipular o evento <xref:System.Windows.Forms.DataGridView.RowUnshared> para determinar quando as linhas se tornam descompartilhadas. Isso é útil ao depurar problemas de compartilhamento de linhas.

Para impedir que as linhas se tornem não compartilhadas, use as seguintes diretrizes:

- Evite indexar a coleção de <xref:System.Windows.Forms.DataGridView.Rows%2A> ou iterar através dela com um loop `foreach`. Normalmente não será necessário acessar as linhas diretamente. <xref:System.Windows.Forms.DataGridView> métodos que operam em linhas usam argumentos de índice de linha em vez de instâncias de linha. Além disso, os manipuladores de eventos relacionados à linha recebem objetos de argumento de evento com propriedades de linha que você pode usar para manipular linhas sem fazer com que elas se tornem não compartilhadas.

- Se você precisar acessar um objeto Row, use o método <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> e passe o índice real da linha. Observe, entretanto, que modificar um objeto de linha compartilhada recuperado por esse método modificará todas as linhas que compartilham esse objeto. A linha para novos registros não é compartilhada com outras linhas, no entanto, ela não será afetada quando você modificar qualquer outra linha. Observe também que diferentes linhas representadas por uma linha compartilhada podem ter menus de atalho diferentes. Para recuperar o menu de atalho correto de uma instância de linha compartilhada, use o método <xref:System.Windows.Forms.DataGridViewRow.GetContextMenuStrip%2A> e passe o índice real da linha. Se você acessar a propriedade <xref:System.Windows.Forms.DataGridViewRow.ContextMenuStrip%2A> da linha compartilhada em vez disso, ela usará o índice de linha compartilhado de-1 e não recuperará o menu de atalho correto.

- Evite indexar a coleção de <xref:System.Windows.Forms.DataGridViewRow.Cells%2A?displayProperty=nameWithType>. Acessar uma célula diretamente fará com que sua linha pai fique descompartilhada, instanciando um novo <xref:System.Windows.Forms.DataGridViewRow>. Manipuladores de eventos relacionados à célula recebem objetos de argumento de evento com propriedades de célula que você pode usar para manipular células sem fazer com que as linhas se tornem não compartilhadas. Você também pode usar a propriedade <xref:System.Windows.Forms.DataGridView.CurrentCellAddress%2A> para recuperar os índices de linha e coluna da célula atual sem acessar a célula diretamente.

- Evite modos de seleção com base em célula. Esses modos fazem com que as linhas se tornem não compartilhadas. Em vez disso, defina a propriedade <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> como <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.

- Não manipule os eventos de <xref:System.Windows.Forms.DataGridViewRowCollection.CollectionChanged?displayProperty=nameWithType> ou de <xref:System.Windows.Forms.DataGridView.RowStateChanged?displayProperty=nameWithType>. Esses eventos fazem com que as linhas se tornem não compartilhadas. Além disso, não chame os métodos <xref:System.Windows.Forms.DataGridViewRowCollection.OnCollectionChanged%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridView.OnRowStateChanged%2A?displayProperty=nameWithType>, que geram esses eventos.

- Não acesse a coleção de <xref:System.Windows.Forms.DataGridView.SelectedCells%2A?displayProperty=nameWithType> quando o valor da propriedade <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> for <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>ou <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>. Isso faz com que todas as linhas selecionadas se tornem não compartilhadas.

- Não chame o método <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A?displayProperty=nameWithType>. Esse método pode fazer com que as linhas se tornem não compartilhadas.

- Não chame o método <xref:System.Windows.Forms.DataGridView.SelectAll%2A?displayProperty=nameWithType> quando o valor da propriedade <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> for <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>. Isso faz com que todas as linhas se tornem não compartilhadas.

- Não defina a propriedade <xref:System.Windows.Forms.DataGridViewCell.ReadOnly%2A> ou <xref:System.Windows.Forms.DataGridViewCell.Selected%2A> de uma célula como `false` quando a propriedade correspondente em sua coluna estiver definida como `true`. Isso faz com que todas as linhas se tornem não compartilhadas.

- Não acesse a propriedade <xref:System.Windows.Forms.DataGridViewRowCollection.List%2A?displayProperty=nameWithType>. Isso faz com que todas as linhas se tornem não compartilhadas.

- Não chame a sobrecarga de `Sort(IComparer)` do método <xref:System.Windows.Forms.DataGridView.Sort%2A>. Classificar com um comparador personalizado faz com que todas as linhas se tornem não compartilhadas.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- [Ajuste de desempenho no controle DataGridView do Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Modo virtual no controle DataGridView dos Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Modos de exibição dos dados no controle DataGridView do Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Estilos de célula no controle DataGridView do Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Como definir estilos de célula padrão para o controle DataGridView do Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Sizing Options in the Windows Forms DataGridView Control](sizing-options-in-the-windows-forms-datagridview-control.md) (Opções de dimensionamento no controle DataGridView dos Windows Forms)
