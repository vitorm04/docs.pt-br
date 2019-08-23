---
title: Estilos de célula no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
ms.openlocfilehash: be4c47db5c56685a84153a9ae4a9a2fe14c6adad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917765"
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Estilos de célula no controle DataGridView dos Windows Forms
Cada célula dentro do <xref:System.Windows.Forms.DataGridView> controle pode ter seu próprio estilo, como formato de texto, cor de plano de fundo, cor de primeiro plano e fonte. Normalmente, no entanto, várias células compartilharão características de determinado estilo.  
  
 Os grupos de células que compartilham estilos podem incluir todas as células em determinadas linhas ou colunas, todas as células que contêm valores específicos ou todas as células no controle. Como esses grupos se sobrepõem, cada célula pode obter as informações de estilo de mais de um lugar. Por exemplo, você pode desejar que cada célula em <xref:System.Windows.Forms.DataGridView> um controle use a mesma fonte, mas apenas células em colunas de moedas para usar o formato de moeda, e apenas células de moeda com números negativos para usar uma cor de primeiro plano vermelha.  
  
## <a name="the-datagridviewcellstyle-class"></a>A classe DataGridViewCellStyle  
 A <xref:System.Windows.Forms.DataGridViewCellStyle> classe contém as seguintes propriedades relacionadas ao estilo visual:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> e <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> e <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 Essa classe também contém as seguintes propriedades relacionadas à formatação:  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> e <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> e <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 Para obter mais informações sobre essas propriedades e outras propriedades de estilo de célula, <xref:System.Windows.Forms.DataGridViewCellStyle> consulte a documentação de referência e os tópicos listados na seção Consulte também abaixo.  
  
## <a name="using-datagridviewcellstyle-objects"></a>Usando objetos DataGridViewCellStyle  
 Você pode recuperar <xref:System.Windows.Forms.DataGridViewCellStyle> objetos de várias propriedades <xref:System.Windows.Forms.DataGridView>das <xref:System.Windows.Forms.DataGridViewCell> classes, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>e e suas classes derivadas. Se uma dessas propriedades ainda não tiver sido definida, recuperar seu valor criará um novo <xref:System.Windows.Forms.DataGridViewCellStyle> objeto. Você também pode instanciar seus <xref:System.Windows.Forms.DataGridViewCellStyle> próprios objetos e atribuí-los a essas propriedades.  
  
 Você pode evitar a duplicação desnecessária de informações <xref:System.Windows.Forms.DataGridViewCellStyle> de estilo compartilhando objetos entre vários <xref:System.Windows.Forms.DataGridView> elementos. Como o conjunto de estilos nos níveis de controle, coluna e linha filtram através de cada nível até o nível da célula, você também pode evitar a duplicação de estilos, configurando somente as propriedades de estilo em cada nível, que são diferentes dos níveis acima. Isso é descrito mais detalhadamente na seção de Herança de estilo que se segue.  
  
 A tabela a seguir lista as propriedades primárias que obtêm ou definem <xref:System.Windows.Forms.DataGridViewCellStyle> objetos.  
  
|Propriedade|Classes|Descrição|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>classes derivadas, <xref:System.Windows.Forms.DataGridViewColumn>,e <xref:System.Windows.Forms.DataGridViewRow>|Obtém ou define estilos padrão usados por todas as células em todo o controle (incluindo células de cabeçalho), em uma coluna ou em uma linha.|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtém ou define os estilos de célula padrão usados por todas as linhas no controle. Isso não inclui as células de cabeçalho.|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtém ou define os estilos de célula padrão, alternando as linhas no controle. Usado para criar um efeito semelhante a livro-razão.|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtém ou define os estilos de célula padrão usados por cabeçalhos de linha do controle. Substituídos pelo tema atual se os estilos visuais estiverem habilitados.|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtém ou define os estilos de célula padrão usados por cabeçalhos de coluna do controle. Substituídos pelo tema atual se os estilos visuais estiverem habilitados.|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell>classes derivadas e|Obtém ou define estilos especificados no nível da célula. Esses estilos substituem aqueles herdados de níveis superiores.|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>classes derivadas, <xref:System.Windows.Forms.DataGridViewRow>,e <xref:System.Windows.Forms.DataGridViewColumn>|Obtém todos os estilos atualmente aplicados à célula, linha ou coluna, inclusive estilos herdados de níveis superiores.|  
  
 Como mencionado acima, obter o valor de uma propriedade Style instancia automaticamente um novo <xref:System.Windows.Forms.DataGridViewCellStyle> objeto se a propriedade não tiver sido definida anteriormente. Para evitar a criação desses objetos desnecessariamente, as classes Row e Column têm <xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A> uma propriedade que você pode verificar para determinar se <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A> a propriedade foi definida. Da mesma forma, as classes de <xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A> célula têm uma propriedade que <xref:System.Windows.Forms.DataGridViewCell.Style%2A> indica se a propriedade foi definida.  
  
 Cada uma das propriedades de estilo tem um evento *PropertyName* `Changed` correspondente no <xref:System.Windows.Forms.DataGridView> controle. Para propriedades de linha, coluna e célula, o nome do`Row`evento começa com "", "`Column`" ou "`Cell`" (por exemplo, <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>). Cada um desses eventos ocorre quando a propriedade Style correspondente é definida como um objeto <xref:System.Windows.Forms.DataGridViewCellStyle> diferente. Esses eventos não ocorrem quando você recupera um <xref:System.Windows.Forms.DataGridViewCellStyle> objeto de uma propriedade de estilo e modifica seus valores de propriedade. Para responder às alterações nos próprios objetos de estilo de célula, manipule <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged> o evento.  
  
## <a name="style-inheritance"></a>Herança de estilo  
 Cada <xref:System.Windows.Forms.DataGridViewCell> um obtém sua aparência de <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> sua propriedade. O <xref:System.Windows.Forms.DataGridViewCellStyle> objeto retornado por essa propriedade herda seus valores de uma hierarquia de propriedades do tipo <xref:System.Windows.Forms.DataGridViewCellStyle>. Essas propriedades são listadas abaixo na ordem em que as <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> células para não cabeçalho obtêm seus valores.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>(somente para células em linhas com números de índice ímpares)  
  
4. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Para células de cabeçalho de linha e coluna <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> , a propriedade é preenchida por valores da lista de propriedades de origem a seguir na ordem especificada.  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 O diagrama a seguir ilustra esse processo.  
  
 ![Propriedades do tipo DataGridViewCellStyle](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-inheritance-diagram.gif "Diagrama de herança dataGridViewCells")  
  
 Você também pode acessar os estilos herdados por colunas e linhas específicas. A propriedade <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A> Column herda seus valores das propriedades a seguir.  
  
1. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 A propriedade <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> Row herda seus valores das propriedades a seguir.  
  
1. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>(somente para células em linhas com números de índice ímpares)  
  
3. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Para cada propriedade em um <xref:System.Windows.Forms.DataGridViewCellStyle> objeto retornado por uma `InheritedStyle` Propriedade, o valor da propriedade é obtido do primeiro estilo de célula na lista apropriada que tem a propriedade correspondente definida com um valor diferente dos <xref:System.Windows.Forms.DataGridViewCellStyle> padrões de classe.  
  
 A tabela a seguir ilustra como <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> o valor da propriedade para uma célula de exemplo é herdado de sua coluna que a contém.  
  
|Propriedade do tipo `DataGridViewCellStyle`|Valor `ForeColor` de exemplo de objeto recuperado|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 Nesse caso, o <xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType> valor da linha da célula é o primeiro valor real na lista. Isso torna- <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> se o valor da propriedade da <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>célula.  
  
 O diagrama a seguir ilustra como <xref:System.Windows.Forms.DataGridViewCellStyle> diferentes propriedades podem herdar seus valores de locais diferentes.  
  
 ![Herança de&#45;valor da propriedade DataGridView](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-value-inheritance-diagram.gif "Diagrama de herança de valor dataGridViewCells")  
  
 Ao tirar proveito da herança de estilo, você pode fornecer estilos apropriados para todo o controle sem ter que especificar as mesmas informações em vários locais.  
  
 Embora as células de cabeçalho participem da herança de estilo conforme descrito, os <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> objetos <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> retornados pelas propriedades <xref:System.Windows.Forms.DataGridView> e do controle têm valores de propriedade iniciais que substituem os valores de Propriedade do objeto retornado por a <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> propriedade. Se desejar que as propriedades definidas para o objeto retornado pela <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> Propriedade sejam aplicadas a cabeçalhos de linha e coluna, você deverá definir as propriedades correspondentes dos objetos retornados <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> pelas propriedades e <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> para os padrões indicados para a <xref:System.Windows.Forms.DataGridViewCellStyle> classe.  
  
> [!NOTE]
> Se os estilos visuais estiverem habilitados, os cabeçalhos de linha e coluna ( <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>exceto para) serão automaticamente estilizados pelo tema atual, substituindo todos os estilos especificados por essas propriedades.  
  
 Os <xref:System.Windows.Forms.DataGridViewButtonColumn>tipos <xref:System.Windows.Forms.DataGridViewImageColumn>, <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> e <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> também inicializam alguns valores do objeto retornado pela Propriedade Column. Para obter mais informações, consulte a documentação de referência para esses tipos.  
  
## <a name="setting-styles-dynamically"></a>Configurando estilos dinamicamente  
 Para personalizar os estilos de células com valores específicos, implemente um manipulador para <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> o evento. Os <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> manipuladores para esse evento recebem um argumento do tipo. Este objeto contém propriedades que permitem determinar o valor da célula que está sendo formatada junto com seu local no <xref:System.Windows.Forms.DataGridView> controle. Esse objeto também contém uma <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A> propriedade que é inicializada para o valor <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> da propriedade da célula que está sendo formatada. Você pode modificar as propriedades de estilo da célula para especificar as informações de estilo apropriadas para o valor e o local da célula.  
  
> [!NOTE]
> Os <xref:System.Windows.Forms.DataGridView.RowPrePaint> eventos <xref:System.Windows.Forms.DataGridView.RowPostPaint> e também recebem um <xref:System.Windows.Forms.DataGridViewCellStyle> objeto nos dados do evento, mas, em seu caso, é uma cópia da propriedade Row <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> para finalidades somente leitura e as alterações nela não afetam o controle.  
  
 Você também pode modificar dinamicamente os estilos de células individuais em resposta a eventos como os <xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType> eventos e. <xref:System.Windows.Forms.DataGridView.CellMouseLeave> Por exemplo, em um manipulador para o <xref:System.Windows.Forms.DataGridView.CellMouseEnter> evento, você pode armazenar o valor atual da cor de plano de fundo da célula (recuperada <xref:System.Windows.Forms.DataGridViewCell.Style%2A> por meio da propriedade da célula) e, em seguida, defini-la como uma nova cor que realçará a célula quando o mouse passar sobre ela. Em um manipulador para o <xref:System.Windows.Forms.DataGridView.CellMouseLeave> evento, você pode restaurar a cor do plano de fundo para o valor original.  
  
> [!NOTE]
> Armazenar em cache os valores armazenados na propriedade <xref:System.Windows.Forms.DataGridViewCell.Style%2A> da célula é importante, independentemente de um determinado valor de estilo ser definido. Se você substituir temporariamente uma configuração de estilo, restaurá-la ao seu estado original de "não definido" garantirá que a célula voltará a herdar a configuração de estilo de um nível mais alto. Se você precisar determinar o estilo real em vigor para uma célula, independentemente de o estilo ser herdado, use a propriedade da <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> célula.  
  
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
- [Formatação e estilos básicos no controle DataGridView do Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Como: Definir estilos de célula padrão para o controle Windows Forms DataGridView](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Formatação de dados no controle DataGridView dos Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md)
