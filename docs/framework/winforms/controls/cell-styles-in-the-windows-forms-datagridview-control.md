---
title: Estilos de célula no controle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
ms.openlocfilehash: fe56033a5adbe7719c64695c8f9ebc4f3644fc65
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746160"
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Estilos de célula no controle DataGridView dos Windows Forms
Cada célula dentro do controle de <xref:System.Windows.Forms.DataGridView> pode ter seu próprio estilo, como formato de texto, cor de plano de fundo, cor de primeiro plano e fonte. Normalmente, no entanto, várias células compartilharão características de determinado estilo.  
  
 Os grupos de células que compartilham estilos podem incluir todas as células em determinadas linhas ou colunas, todas as células que contêm valores específicos ou todas as células no controle. Como esses grupos se sobrepõem, cada célula pode obter as informações de estilo de mais de um lugar. Por exemplo, você pode desejar que cada célula em um controle de <xref:System.Windows.Forms.DataGridView> use a mesma fonte, mas apenas células em colunas de moedas para usar o formato de moeda e apenas células de moeda com números negativos para usar uma cor de primeiro plano vermelha.  
  
## <a name="the-datagridviewcellstyle-class"></a>A classe DataGridViewCellStyle  
 A classe <xref:System.Windows.Forms.DataGridViewCellStyle> contém as seguintes propriedades relacionadas ao estilo visual:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> e <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> e <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 Essa classe também contém as seguintes propriedades relacionadas à formatação:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> e <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> e <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 Para obter mais informações sobre essas propriedades e outras propriedades de estilo de célula, consulte a documentação de referência do <xref:System.Windows.Forms.DataGridViewCellStyle> e os tópicos listados na seção Consulte também abaixo.  
  
## <a name="using-datagridviewcellstyle-objects"></a>Usando objetos DataGridViewCellStyle  
 Você pode recuperar <xref:System.Windows.Forms.DataGridViewCellStyle> objetos de várias propriedades das classes <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>e <xref:System.Windows.Forms.DataGridViewCell> e suas classes derivadas. Se uma dessas propriedades ainda não tiver sido definida, recuperar seu valor criará um novo objeto <xref:System.Windows.Forms.DataGridViewCellStyle>. Você também pode instanciar seus próprios objetos <xref:System.Windows.Forms.DataGridViewCellStyle> e atribuí-los a essas propriedades.  
  
 Você pode evitar a duplicação desnecessária de informações de estilo compartilhando <xref:System.Windows.Forms.DataGridViewCellStyle> objetos entre vários elementos <xref:System.Windows.Forms.DataGridView>. Como o conjunto de estilos nos níveis de controle, coluna e linha filtram através de cada nível até o nível da célula, você também pode evitar a duplicação de estilos, configurando somente as propriedades de estilo em cada nível, que são diferentes dos níveis acima. Isso é descrito mais detalhadamente na seção de Herança de estilo que se segue.  
  
 A tabela a seguir lista as propriedades primárias que Obtém ou define <xref:System.Windows.Forms.DataGridViewCellStyle> objetos.  
  
|Propriedade|Classes|Descrição|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>e classes derivadas|Obtém ou define estilos padrão usados por todas as células em todo o controle (incluindo células de cabeçalho), em uma coluna ou em uma linha.|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtém ou define os estilos de célula padrão usados por todas as linhas no controle. Isso não inclui as células de cabeçalho.|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtém ou define os estilos de célula padrão, alternando as linhas no controle. Usado para criar um efeito semelhante a livro-razão.|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtém ou define os estilos de célula padrão usados por cabeçalhos de linha do controle. Substituídos pelo tema atual se os estilos visuais estiverem habilitados.|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtém ou define os estilos de célula padrão usados por cabeçalhos de coluna do controle. Substituídos pelo tema atual se os estilos visuais estiverem habilitados.|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell> e classes derivadas|Obtém ou define estilos especificados no nível da célula. Esses estilos substituem aqueles herdados de níveis superiores.|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewRow>, <xref:System.Windows.Forms.DataGridViewColumn>e classes derivadas|Obtém todos os estilos atualmente aplicados à célula, linha ou coluna, inclusive estilos herdados de níveis superiores.|  
  
 Como mencionado acima, obter o valor de uma propriedade Style instancia automaticamente um novo objeto <xref:System.Windows.Forms.DataGridViewCellStyle> se a propriedade não tiver sido definida anteriormente. Para evitar a criação desses objetos desnecessariamente, as classes Row e Column têm uma propriedade <xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A> que você pode verificar para determinar se a propriedade <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A> foi definida. Da mesma forma, as classes de célula têm uma propriedade <xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A> que indica se a propriedade <xref:System.Windows.Forms.DataGridViewCell.Style%2A> foi definida.  
  
 Cada uma das propriedades de estilo tem um evento *PropertyName*`Changed` correspondente no controle de <xref:System.Windows.Forms.DataGridView>. Para propriedades de linha, coluna e célula, o nome do evento começa com "`Row`", "`Column`" ou "`Cell`" (por exemplo, <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>). Cada um desses eventos ocorre quando a propriedade Style correspondente é definida como um objeto <xref:System.Windows.Forms.DataGridViewCellStyle> diferente. Esses eventos não ocorrem quando você recupera um objeto <xref:System.Windows.Forms.DataGridViewCellStyle> de uma propriedade Style e modifica seus valores de propriedade. Para responder às alterações nos próprios objetos de estilo de célula, manipule o evento <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged>.  
  
## <a name="style-inheritance"></a>Herança de estilo  
 Cada <xref:System.Windows.Forms.DataGridViewCell> obtém sua aparência de sua propriedade <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>. O objeto <xref:System.Windows.Forms.DataGridViewCellStyle> retornado por essa propriedade herda seus valores de uma hierarquia de propriedades do tipo <xref:System.Windows.Forms.DataGridViewCellStyle>. Essas propriedades são listadas abaixo na ordem em que as <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> para células sem cabeçalho obtêm seus valores.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (somente para células em linhas com números de índice ímpar)  
  
4. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Para células de cabeçalho de linha e coluna, a propriedade <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> é populada por valores da seguinte lista de propriedades de origem na ordem especificada.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 O diagrama a seguir ilustra esse processo.  
  
 ![Propriedades do tipo DataGridViewCellStyle](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-inheritance-diagram.gif "Diagrama de herança DataGridViewCells")  
  
 Você também pode acessar os estilos herdados por colunas e linhas específicas. A propriedade <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A> da coluna herda seus valores das propriedades a seguir.  
  
1. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 A linha <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> propriedade herda seus valores das propriedades a seguir.  
  
1. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (somente para células em linhas com números de índice ímpar)  
  
3. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Para cada propriedade em um objeto <xref:System.Windows.Forms.DataGridViewCellStyle> retornado por uma propriedade `InheritedStyle`, o valor da propriedade é obtido do primeiro estilo de célula na lista apropriada que tem a propriedade correspondente definida com um valor diferente dos padrões da classe <xref:System.Windows.Forms.DataGridViewCellStyle>.  
  
 A tabela a seguir ilustra como o valor da propriedade <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> para uma célula de exemplo é herdado de sua coluna que a contém.  
  
|Propriedade do tipo `DataGridViewCellStyle`|Valor `ForeColor` de exemplo de objeto recuperado|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 Nesse caso, o valor <xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType> da linha da célula é o primeiro valor real na lista. Isso se torna o <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> valor da propriedade da <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>da célula.  
  
 O diagrama a seguir ilustra como diferentes propriedades de <xref:System.Windows.Forms.DataGridViewCellStyle> podem herdar seus valores de locais diferentes.  
  
 ![Herança de&#45;valor da propriedade DataGridView](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-value-inheritance-diagram.gif "Diagrama de herança de valor DataGridViewCells")  
  
 Ao tirar proveito da herança de estilo, você pode fornecer estilos apropriados para todo o controle sem ter que especificar as mesmas informações em vários locais.  
  
 Embora as células de cabeçalho participem da herança de estilo conforme descrito, os objetos retornados pelas propriedades <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> e <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> do controle de <xref:System.Windows.Forms.DataGridView> têm valores de propriedade iniciais que substituem os valores de Propriedade do objeto retornado pela propriedade <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>. Se desejar que as propriedades definidas para o objeto retornado pela propriedade <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> sejam aplicadas aos cabeçalhos de linha e de coluna, você deverá definir as propriedades correspondentes dos objetos retornados pela <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> e <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> Propriedades para os padrões indicados para a classe <xref:System.Windows.Forms.DataGridViewCellStyle>.  
  
> [!NOTE]
> Se os estilos visuais estiverem habilitados, os cabeçalhos de linha e coluna (exceto para o <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) serão automaticamente estilizados pelo tema atual, substituindo todos os estilos especificados por essas propriedades.  
  
 Os tipos <xref:System.Windows.Forms.DataGridViewButtonColumn>, <xref:System.Windows.Forms.DataGridViewImageColumn>e <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> também inicializam alguns valores do objeto retornado pela propriedade <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> de coluna. Para obter mais informações, consulte a documentação de referência para esses tipos.  
  
## <a name="setting-styles-dynamically"></a>Configurando estilos dinamicamente  
 Para personalizar os estilos de células com valores específicos, implemente um manipulador para o evento <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>. Os manipuladores para esse evento recebem um argumento do tipo <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs>. Este objeto contém propriedades que permitem determinar o valor da célula que está sendo formatada junto com seu local no controle de <xref:System.Windows.Forms.DataGridView>. Esse objeto também contém uma propriedade <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A> que é inicializada para o valor da propriedade <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> da célula que está sendo formatada. Você pode modificar as propriedades de estilo da célula para especificar as informações de estilo apropriadas para o valor e o local da célula.  
  
> [!NOTE]
> Os eventos <xref:System.Windows.Forms.DataGridView.RowPrePaint> e <xref:System.Windows.Forms.DataGridView.RowPostPaint> também recebem um objeto <xref:System.Windows.Forms.DataGridViewCellStyle> nos dados do evento, mas, em seu caso, é uma cópia da linha <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> propriedade para fins somente leitura, e as alterações feitas nele não afetam o controle.  
  
 Você também pode modificar dinamicamente os estilos de células individuais em resposta a eventos como os eventos <xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType> e <xref:System.Windows.Forms.DataGridView.CellMouseLeave>. Por exemplo, em um manipulador para o evento <xref:System.Windows.Forms.DataGridView.CellMouseEnter>, você pode armazenar o valor atual da cor de plano de fundo da célula (recuperada por meio da propriedade <xref:System.Windows.Forms.DataGridViewCell.Style%2A> da célula) e, em seguida, defini-la como uma nova cor que realçará a célula quando o mouse passar sobre ela. Em um manipulador para o evento <xref:System.Windows.Forms.DataGridView.CellMouseLeave>, você pode restaurar a cor do plano de fundo para o valor original.  
  
> [!NOTE]
> Armazenar em cache os valores armazenados na propriedade <xref:System.Windows.Forms.DataGridViewCell.Style%2A> da célula é importante, independentemente de um determinado valor de estilo ser definido. Se você substituir temporariamente uma configuração de estilo, restaurá-la ao seu estado original de "não definido" garantirá que a célula voltará a herdar a configuração de estilo de um nível mais alto. Se você precisar determinar o estilo real em vigor para uma célula, independentemente de o estilo ser herdado, use a propriedade de <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> da célula.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [Formatação e definição de estilos básicas no controle DataGridView dos Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Como definir estilos de célula padrão para o controle DataGridView do Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Formatação de dados no controle DataGridView do Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md)
