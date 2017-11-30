---
title: "Práticas recomendadas para dimensionamento do controle DataGridView dos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], row sharing
- data grids [Windows Forms], best practices
- DataGridView control [Windows Forms], shared rows
- DataGridView control [Windows Forms], best practices
- best practices [Windows Forms], dataGridView control
- DataGridView control [Windows Forms], scaling
ms.assetid: 8321a8a6-6340-4fd1-b475-fa090b905aaf
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bfefd41a4773c81757f73e725095057f988cef2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="best-practices-for-scaling-the-windows-forms-datagridview-control"></a>Práticas recomendadas para dimensionamento do controle DataGridView dos Windows Forms
O <xref:System.Windows.Forms.DataGridView> controle foi projetado para fornecer escalabilidade máxima. Se você precisa exibir grandes quantidades de dados, siga as diretrizes descritas neste tópico para evitar o consumo de grandes quantidades de memória ou prejudicar a capacidade de resposta da UI (interface do usuário). Este tópico discute os seguintes problemas:  
  
-   Usando estilos de célula com eficiência  
  
-   Usando menus de atalho com eficiência  
  
-   Usando o redimensionamento automático com eficiência  
  
-   Usando as coleções de células, linhas e colunas selecionadas com eficiência  
  
-   Usando linhas compartilhadas  
  
-   Impedindo as linhas de se tornarem não compartilhadas  
  
 Se você tiver necessidades de desempenho especiais, implemente o modo virtual e forneça suas próprias operações de gerenciamento de dados. Para obter mais informações, consulte [Modos de exibição dos dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md).  
  
## <a name="using-cell-styles-efficiently"></a>Usando Estilos de Célula com Eficiência  
 Cada célula, linha e coluna pode ter suas próprias informações de estilo. Informações de estilo são armazenadas em <xref:System.Windows.Forms.DataGridViewCellStyle> objetos. Criando objetos de estilo de célula para muitos individuais <xref:System.Windows.Forms.DataGridView> elementos podem ser ineficientes, especialmente ao trabalhar com grandes quantidades de dados. Para evitar um impacto no desempenho, use as seguintes diretrizes:  
  
-   Evite configurar propriedades de estilo de célula para individuais <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewRow> objetos. Isso inclui o objeto de linha especificado pelo <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> propriedade. Cada nova linha que é clonada do modelo de linha receberá sua própria cópia do objeto de estilo de célula do modelo. Para dimensionamento máximo, definir propriedades de estilo de célula no <xref:System.Windows.Forms.DataGridView> nível. Por exemplo, definir a <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> propriedade em vez de <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType> propriedade.  
  
-   Se algumas células requerem formatação diferente de formatação padrão, use o mesmo <xref:System.Windows.Forms.DataGridViewCellStyle> instância entre grupos de células, linhas ou colunas. Evite diretamente definir propriedades do tipo <xref:System.Windows.Forms.DataGridViewCellStyle> em células individuais, linhas e colunas. Para obter um exemplo de compartilhamento de estilo de célula, consulte [Instruções: definir estilos de célula padrão para o controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md). Você também pode evitar uma penalidade de desempenho ao definir estilos de célula individualmente manipulando o <xref:System.Windows.Forms.DataGridView.CellFormatting> manipulador de eventos. Para obter um exemplo, consulte [Instruções: personalizar a formatação de dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
-   Ao determinar o estilo da célula, use o <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType> propriedade em vez de <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType> propriedade. Acessando o <xref:System.Windows.Forms.DataGridViewCell.Style%2A> propriedade cria uma nova instância do <xref:System.Windows.Forms.DataGridViewCellStyle> classe se a propriedade já não tiver sido usada. Além disso, esse objeto poderá não conter as informações de estilo completas para a célula se alguns estilos forem herdados da linha, da coluna ou do controle. Para obter mais informações sobre herança de estilo de célula, consulte [Estilos de célula no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="using-shortcut-menus-efficiently"></a>Usando Menus de Atalho com Eficiência  
 Cada célula, linha e coluna pode ter seu próprio menu de atalho. Menus de atalho a <xref:System.Windows.Forms.DataGridView> controle são representados por <xref:System.Windows.Forms.ContextMenuStrip> controles. Assim como ocorre com objetos de estilo de célula, Criando menus de atalho para o indivíduo muitos <xref:System.Windows.Forms.DataGridView> elementos afetará negativamente o desempenho. Para evitar essa penalidade, use as seguintes diretrizes:  
  
-   Evite criar menus de atalho para células e linhas individuais. Isso inclui o modelo de linha, que é clonado juntamente com o menu de atalho quando novas linhas são adicionadas ao controle. Para escalabilidade máxima, use somente o controle <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> propriedade para especificar um menu de atalho único para todo o controle.  
  
-   Se você precisar vários menus de atalho para várias linhas ou células, trate o <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> ou <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded> eventos. Esses eventos permitem gerenciar os objetos do menu de atalho por conta própria, possibilitando ajustar o desempenho.  
  
## <a name="using-automatic-resizing-efficiently"></a>Usando o Redimensionamento Automático com Eficiência  
 Cabeçalhos, colunas e linhas podem ser redimensionados automaticamente como alterações de conteúdo da célula para que todo o conteúdo das células seja exibido sem recorte. Alterar os modos de dimensionamento também pode redimensionar linhas, colunas e cabeçalhos. Para determinar o tamanho correto, o <xref:System.Windows.Forms.DataGridView> controle deve examinar o valor de cada célula que ele deve conter. Ao trabalhar com grandes conjuntos de dados, essa análise poderá afetar negativamente o desempenho do controle quando o redimensionamento automático ocorrer. Para evitar penalidades de desempenho, use as seguintes diretrizes:  
  
-   Evite usar o dimensionamento automático em um <xref:System.Windows.Forms.DataGridView> controle com um grande conjunto de linhas. Se você usar o dimensionamento automático, redimensione apenas com base nas linhas exibidas. Além disso, use apenas as linhas exibidas no modo virtual.  
  
    -   Para linhas e colunas, use o `DisplayedCells` ou `DisplayedCellsExceptHeaders` campo o <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>, <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>, e <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> enumerações.  
  
    -   Para cabeçalhos de linha, use o <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToDisplayedHeaders> ou <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToFirstHeader> campo o <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode> enumeração.  
  
-   Para obter escalabilidade máxima, desligue o dimensionamento automático e use o redimensionamento programático.  
  
 Para obter mais informações, consulte [Sizing Options in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md) (Opções de dimensionamento no controle DataGridView dos Windows Forms).  
  
## <a name="using-the-selected-cells-rows-and-columns-collections-efficiently"></a>Usando as Coleções de Células, Linhas e Colunas Selecionadas com Eficiência  
 O <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> coleção não executar com eficiência com grandes seleções. O <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> e <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> coleções também podem ser ineficientes, embora a um grau menor porque há menos linhas do que as células em um típico <xref:System.Windows.Forms.DataGridView> controle e menos colunas do que linhas. Para evitar penalidades de desempenho ao trabalhar com essas coleções, use as seguintes diretrizes:  
  
-   Para determinar se todas as células a <xref:System.Windows.Forms.DataGridView> foi selecionada antes de acessar o conteúdo do <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> coleção, verifique o valor de retorno o <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> método. No entanto, observe que esse método pode fazer com que as linhas se tornem não compartilhadas. Para obter mais informações, consulte a próxima seção.  
  
-   Evite usar o <xref:System.Collections.ICollection.Count%2A> propriedade o <xref:System.Windows.Forms.DataGridViewSelectedCellCollection?displayProperty=nameWithType> para determinar o número de células selecionadas. Em vez disso, use o <xref:System.Windows.Forms.DataGridView.GetCellCount%2A?displayProperty=nameWithType> método e passar o <xref:System.Windows.Forms.DataGridViewElementStates.Selected?displayProperty=nameWithType> valor. Da mesma forma, use o <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A?displayProperty=nameWithType> e <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A?displayProperty=nameWithType> métodos para determinar o número de elementos selecionados, em vez de acessar as coleções selecionadas de linha e coluna.  
  
-   Evite modos de seleção com base em célula. Em vez disso, defina o <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> propriedade <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.  
  
## <a name="using-shared-rows"></a>Usando Linhas Compartilhadas  
 Uso eficiente da memória é obtido no <xref:System.Windows.Forms.DataGridView> controle por meio de linhas compartilhadas. Linhas compartilharão o máximo possível de informações sobre sua aparência e comportamento pelo compartilhamento de instâncias da <xref:System.Windows.Forms.DataGridViewRow> classe.  
  
 Embora o compartilhamento de instâncias de linha poupe memória, as linhas podem facilmente se tornar não compartilhadas. Por exemplo, sempre que um usuário interage diretamente com uma célula, sua linha se torna não compartilhada. Como isso não pode ser evitado, as diretrizes neste tópico são úteis somente ao trabalhar com grandes quantidades de dados e somente quando os usuários forem interagir com uma parte relativamente pequena dos dados sempre que o programa for executado.  
  
 Uma linha não pode ser compartilhada em um desassociado <xref:System.Windows.Forms.DataGridView> controlar se qualquer uma de suas células contêm valores. Quando o <xref:System.Windows.Forms.DataGridView> controle está associado a uma fonte de dados externa ou ao implementar o modo virtual e fornecer sua própria fonte de dados, os valores de célula são armazenados fora do controle, não em objetos de célula, permitindo que as linhas a serem compartilhadas.  
  
 Um objeto de linha poderá ser compartilhado apenas se o estado de todas as suas células puder ser determinado por meio do estado da linha e dos estados das colunas que contêm as células. Se você alterar o estado de uma célula para que ela não possa mais ser deduzida por meio do estado de sua linha e coluna, a linha não poderá ser compartilhada.  
  
 Por exemplo, uma linha não pode ser compartilhada em nenhuma das seguintes situações:  
  
-   A linha contém uma única célula selecionada que não está em uma coluna selecionada.  
  
-   A linha contém uma célula com seu <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> ou <xref:System.Windows.Forms.DataGridViewCell.ContextMenuStrip%2A> conjunto de propriedades.  
  
-   A linha contém uma <xref:System.Windows.Forms.DataGridViewComboBoxCell> com seus <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A> conjunto de propriedades.  
  
 No modo associado ou virtual, você pode fornecer os menus de atalho e dicas de ferramenta para células individuais manipulando o <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> e <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> eventos.  
  
 O <xref:System.Windows.Forms.DataGridView> controle automaticamente tentará usar linhas compartilhadas sempre que linhas são adicionadas para o <xref:System.Windows.Forms.DataGridViewRowCollection>. Use as diretrizes a seguir para garantir que as linhas sejam compartilhadas:  
  
-   Evite chamar o `Add(Object[])` sobrecarga do <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> método e o `Insert(Object[])` sobrecarga do <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> método o <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> coleção. Essas sobrecargas criam linhas não compartilhadas automaticamente.  
  
-   Certifique-se que a linha especificada no <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> propriedade pode ser compartilhada nos seguintes casos:  
  
    -   Ao chamar o `Add()` ou `Add(Int32)` sobrecargas do <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> método ou o `Insert(Int32,Int32)` sobrecarga do <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> método o <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> coleção.  
  
    -   Ao aumentar o valor de <xref:System.Windows.Forms.DataGridView.RowCount%2A?displayProperty=nameWithType> propriedade.  
  
    -   Ao definir o <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType> propriedade.  
  
-   Certifique-se que a linha indicada pelo `indexSource` parâmetro pode ser compartilhado ao chamar o <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopy%2A>, e <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopies%2A> métodos do <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> coleção.  
  
-   Certifique-se de que a linha ou linhas especificadas podem ser compartilhadas ao chamar o `Add(DataGridViewRow)` de sobrecarga do <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> método, o <xref:System.Windows.Forms.DataGridViewRowCollection.AddRange%2A> método, o `Insert(Int32,DataGridViewRow)` de sobrecarga do <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> método e o <xref:System.Windows.Forms.DataGridViewRowCollection.InsertRange%2A> método o <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>coleção.  
  
 Para determinar se uma linha é compartilhada, use o <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> método para recuperar o objeto de linha e, em seguida, verificar o objeto <xref:System.Windows.Forms.DataGridViewBand.Index%2A> propriedade. Linhas compartilhadas sempre têm uma <xref:System.Windows.Forms.DataGridViewBand.Index%2A> valor da propriedade de -1.  
  
## <a name="preventing-rows-from-becoming-unshared"></a>Impedindo as Linhas de se Tornarem Não Compartilhadas  
 As linhas compartilhadas podem se tornar não compartilhadas como resultado da ação de usuário ou de código. Para evitar um impacto no desempenho, evite fazer com que as linhas se tornem não compartilhadas. Durante o desenvolvimento de aplicativos, você pode manipular o <xref:System.Windows.Forms.DataGridView.RowUnshared> evento para determinar quando linhas se tornam não compartilhadas. Isso é útil ao depurar problemas de compartilhamento de linhas.  
  
 Para impedir que as linhas se tornem não compartilhadas, use as seguintes diretrizes:  
  
-   Evitar a indexação de <xref:System.Windows.Forms.DataGridView.Rows%2A> coleção ou iteração com um `foreach` loop. Normalmente não será necessário acessar as linhas diretamente. <xref:System.Windows.Forms.DataGridView>métodos que operam em linhas ter argumentos de índice de linha em vez de instâncias de linha. Além disso, os manipuladores de eventos relacionados à linha recebem objetos de argumento de evento com propriedades de linha que você pode usar para manipular linhas sem fazer com que elas se tornem não compartilhadas.  
  
-   Se você precisar acessar um objeto de linha, use o <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> método e passar em índice real da linha. Observe, entretanto, que modificar um objeto de linha compartilhada recuperado por esse método modificará todas as linhas que compartilham esse objeto. A linha para novos registros não é compartilhada com outras linhas, no entanto, ela não será afetada quando você modificar qualquer outra linha. Observe também que diferentes linhas representadas por uma linha compartilhada podem ter menus de atalho diferentes. Para recuperar o menu de atalho correto da instância de uma linha compartilhada, use o <xref:System.Windows.Forms.DataGridViewRow.GetContextMenuStrip%2A> método e passar em índice real da linha. Se você acessar a linha compartilhada <xref:System.Windows.Forms.DataGridViewRow.ContextMenuStrip%2A> propriedade em vez disso, ele usará o índice de linha compartilhada de -1 e não recuperará o menu de atalho correto.  
  
-   Evitar a indexação de <xref:System.Windows.Forms.DataGridViewRow.Cells%2A?displayProperty=nameWithType> coleção. Acessando uma célula diretamente fará com que a linha pai para se tornar não compartilhado, criando um novo <xref:System.Windows.Forms.DataGridViewRow>. Manipuladores de eventos relacionados à célula recebem objetos de argumento de evento com propriedades de célula que você pode usar para manipular células sem fazer com que as linhas se tornem não compartilhadas. Você também pode usar o <xref:System.Windows.Forms.DataGridView.CurrentCellAddress%2A> propriedade para recuperar os índices de linha e coluna da célula atual sem acessar a célula diretamente.  
  
-   Evite modos de seleção com base em célula. Esses modos fazem com que as linhas se tornem não compartilhadas. Em vez disso, defina o <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> propriedade <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>.  
  
-   Não tratar o <xref:System.Windows.Forms.DataGridViewRowCollection.CollectionChanged?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridView.RowStateChanged?displayProperty=nameWithType> eventos. Esses eventos fazem com que as linhas se tornem não compartilhadas. Além disso, não chame o <xref:System.Windows.Forms.DataGridViewRowCollection.OnCollectionChanged%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridView.OnRowStateChanged%2A?displayProperty=nameWithType> métodos, que geram esses eventos.  
  
-   Não acessam o <xref:System.Windows.Forms.DataGridView.SelectedCells%2A?displayProperty=nameWithType> coleção quando o <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> é o valor da propriedade <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>, ou <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>. Isso faz com que todas as linhas selecionadas se tornem não compartilhadas.  
  
-   Não chame o <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A?displayProperty=nameWithType> método. Esse método pode fazer com que as linhas se tornem não compartilhadas.  
  
-   Não chame o <xref:System.Windows.Forms.DataGridView.SelectAll%2A?displayProperty=nameWithType> método quando o <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> é o valor da propriedade <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>. Isso faz com que todas as linhas se tornem não compartilhadas.  
  
-   Não defina o <xref:System.Windows.Forms.DataGridViewCell.ReadOnly%2A> ou <xref:System.Windows.Forms.DataGridViewCell.Selected%2A> propriedade de uma célula para `false` quando a propriedade correspondente na coluna é definida como `true`. Isso faz com que todas as linhas se tornem não compartilhadas.  
  
-   Não acessam o <xref:System.Windows.Forms.DataGridViewRowCollection.List%2A?displayProperty=nameWithType> propriedade. Isso faz com que todas as linhas se tornem não compartilhadas.  
  
-   Não chame o `Sort(IComparer)` de sobrecarga do <xref:System.Windows.Forms.DataGridView.Sort%2A> método. Classificar com um comparador personalizado faz com que todas as linhas se tornem não compartilhadas.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 [Ajuste de desempenho no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [Modo virtual no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 [Modos de exibição de dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)  
 [Estilos de Célula no Controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Como definir estilos de célula padrão para o controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 [Sizing Options in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md) (Opções de dimensionamento no controle DataGridView dos Windows Forms)
