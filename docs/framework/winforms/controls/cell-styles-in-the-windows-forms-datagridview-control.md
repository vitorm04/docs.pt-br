---
title: Estilos de célula no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
ms.openlocfilehash: ec2a34deb25cd5f4cf492d92129ffc61d14001ab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171516"
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Estilos de célula no controle DataGridView dos Windows Forms
Cada célula no <xref:System.Windows.Forms.DataGridView> controle pode ter seu próprio estilo, como o formato de texto, cor de plano de fundo, cor de primeiro plano e fonte. Normalmente, no entanto, várias células compartilharão características de determinado estilo.  
  
 Os grupos de células que compartilham estilos podem incluir todas as células em determinadas linhas ou colunas, todas as células que contêm valores específicos ou todas as células no controle. Como esses grupos se sobrepõem, cada célula pode obter as informações de estilo de mais de um lugar. Por exemplo, você pode querer todas as células uma <xref:System.Windows.Forms.DataGridView> controle para usar a mesma fonte, mas apenas as células nas colunas de moeda para usar o formato de moeda e apenas as células de moeda com números negativos para usar uma cor de primeiro plano vermelha.  
  
## <a name="the-datagridviewcellstyle-class"></a>A classe DataGridViewCellStyle  
 O <xref:System.Windows.Forms.DataGridViewCellStyle> classe contém as seguintes propriedades relacionadas a estilo visual:  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> e <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> e <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 Essa classe também contém as seguintes propriedades relacionadas à formatação:  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> e <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> e <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 Para obter mais informações sobre essas propriedades e outras propriedades de estilo de célula, consulte o <xref:System.Windows.Forms.DataGridViewCellStyle> documentação de referência e os tópicos listados na seção Consulte também abaixo.  
  
## <a name="using-datagridviewcellstyle-objects"></a>Usando objetos DataGridViewCellStyle  
 Você pode recuperar <xref:System.Windows.Forms.DataGridViewCellStyle> objetos de várias propriedades do <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>, e <xref:System.Windows.Forms.DataGridViewCell> classes e suas classes derivadas. Se uma dessas propriedades ainda não foi definida, recuperar seu valor criará um novo <xref:System.Windows.Forms.DataGridViewCellStyle> objeto. Você também pode instanciar seu próprio <xref:System.Windows.Forms.DataGridViewCellStyle> objetos e atribuí-los a essas propriedades.  
  
 Você pode evitar a duplicação desnecessária de informações de estilo, compartilhando <xref:System.Windows.Forms.DataGridViewCellStyle> objetos entre vários <xref:System.Windows.Forms.DataGridView> elementos. Como o conjunto de estilos nos níveis de controle, coluna e linha filtram através de cada nível até o nível da célula, você também pode evitar a duplicação de estilos, configurando somente as propriedades de estilo em cada nível, que são diferentes dos níveis acima. Isso é descrito mais detalhadamente na seção de Herança de estilo que se segue.  
  
 A tabela a seguir lista as propriedades principais que obtêm ou definem <xref:System.Windows.Forms.DataGridViewCellStyle> objetos.  
  
|Propriedade|Classes|Descrição|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.DataGridViewColumn>, <xref:System.Windows.Forms.DataGridViewRow>e as classes derivadas|Obtém ou define estilos padrão usados por todas as células em todo o controle (incluindo células de cabeçalho), em uma coluna ou em uma linha.|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtém ou define os estilos de célula padrão usados por todas as linhas no controle. Isso não inclui as células de cabeçalho.|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtém ou define os estilos de célula padrão, alternando as linhas no controle. Usado para criar um efeito semelhante a livro-razão.|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtém ou define os estilos de célula padrão usados por cabeçalhos de linha do controle. Substituídos pelo tema atual se os estilos visuais estiverem habilitados.|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|Obtém ou define os estilos de célula padrão usados por cabeçalhos de coluna do controle. Substituídos pelo tema atual se os estilos visuais estiverem habilitados.|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell> e classes derivadas|Obtém ou define estilos especificados no nível da célula. Esses estilos substituem aqueles herdados de níveis superiores.|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewRow>, <xref:System.Windows.Forms.DataGridViewColumn>e as classes derivadas|Obtém todos os estilos atualmente aplicados à célula, linha ou coluna, inclusive estilos herdados de níveis superiores.|  
  
 Conforme mencionado acima, a obtenção do valor de uma propriedade de estilo automaticamente cria uma nova <xref:System.Windows.Forms.DataGridViewCellStyle> objeto se a propriedade não foi definida anteriormente. Para evitar a criação desnecessária desses objetos, as classes de linha e coluna têm uma <xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A> propriedade que você pode verificar para determinar se o <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A> propriedade foi definida. Da mesma forma, as classes de célula têm uma <xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A> propriedade que indica se o <xref:System.Windows.Forms.DataGridViewCell.Style%2A> propriedade foi definida.  
  
 Cada uma das propriedades de estilo tem um correspondente *PropertyName* `Changed` eventos sobre o <xref:System.Windows.Forms.DataGridView> controle. Para propriedades de célula, coluna e linha, o nome do evento começa com "`Row`","`Column`", ou "`Cell`" (por exemplo, <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>). Cada um desses eventos ocorre quando a propriedade de estilo correspondente é definida em outro <xref:System.Windows.Forms.DataGridViewCellStyle> objeto. Esses eventos não ocorrem quando você recupera um <xref:System.Windows.Forms.DataGridViewCellStyle> do objeto de uma propriedade de estilo e modificar seus valores de propriedade. Para responder a alterações para os próprios objetos de estilo de célula, lidar com o <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged> eventos.  
  
## <a name="style-inheritance"></a>Herança de estilo  
 Cada <xref:System.Windows.Forms.DataGridViewCell> obtém sua aparência de seu <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> propriedade. O <xref:System.Windows.Forms.DataGridViewCellStyle> objeto retornado por essa propriedade herda seus valores de uma hierarquia de propriedades do tipo <xref:System.Windows.Forms.DataGridViewCellStyle>. Essas propriedades são listadas abaixo na ordem em que o <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> para células de cabeçalho não obtém seus valores.  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (somente para células em linhas com números de índice ímpares)  
  
4.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Para células de cabeçalho de linha e coluna, o <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> propriedade é preenchida com os valores da seguinte lista de propriedades de origem na ordem fornecida.  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 O diagrama a seguir ilustra esse processo.  
  
 ![Propriedades do tipo DataGridViewCellStyle](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-inheritance-diagram.gif "DataGridViewCells diagrama de herança")  
  
 Você também pode acessar os estilos herdados por colunas e linhas específicas. A coluna <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A> propriedade herda seus valores das propriedades a seguir.  
  
1.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 A linha <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> propriedade herda seus valores das propriedades a seguir.  
  
1.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (somente para células em linhas com números de índice ímpares)  
  
3.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Para cada propriedade em uma <xref:System.Windows.Forms.DataGridViewCellStyle> objeto retornado por um `InheritedStyle` propriedade, o valor da propriedade é obtido de estilo da primeira célula na lista apropriada que tenha a propriedade correspondente definida como um valor diferente de <xref:System.Windows.Forms.DataGridViewCellStyle> padrões de classe.  
  
 A tabela a seguir ilustra como o <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> valor da propriedade de uma célula de exemplo é herdado da coluna que a contém.  
  
|propriedade de tipo `DataGridViewCellStyle`|Valor `ForeColor` de exemplo de objeto recuperado|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 Nesse caso, o <xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType> valor da linha da célula é o primeiro valor real da lista. Isso se torna a <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> valor da propriedade de célula do <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>.  
  
 O diagrama a seguir ilustra como diferentes <xref:System.Windows.Forms.DataGridViewCellStyle> propriedades podem herdar seus valores de diferentes locais.  
  
 ![Propriedade DataGridView&#45;herança do valor](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-value-inheritance-diagram.gif "DataGridViewCells diagrama de herança de valor")  
  
 Ao tirar proveito da herança de estilo, você pode fornecer estilos apropriados para todo o controle sem ter que especificar as mesmas informações em vários locais.  
  
 Embora as células de cabeçalho participem da herança de estilo, conforme descrito, os objetos retornados pela <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> e <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> propriedades do <xref:System.Windows.Forms.DataGridView> controle têm valores de propriedade inicial que substituem os valores de propriedade do objeto retornado por o <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> propriedade. Se você quiser que as propriedades definidas para o objeto retornado pela <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> propriedade a ser aplicado aos cabeçalhos de linha e coluna, você deve definir as propriedades correspondentes dos objetos retornados pela <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> e <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> indicado de propriedades para os padrões para o <xref:System.Windows.Forms.DataGridViewCellStyle> classe.  
  
> [!NOTE]
>  Se os estilos visuais estiverem habilitados, os cabeçalhos de linha e coluna (exceto para o <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) serão automaticamente estilizados pelo tema atual, substituindo qualquer estilo especificado por essas propriedades.  
  
 O <xref:System.Windows.Forms.DataGridViewButtonColumn>, <xref:System.Windows.Forms.DataGridViewImageColumn>, e <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> tipos também inicializam alguns valores do objeto retornado pela coluna <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> propriedade. Para obter mais informações, consulte a documentação de referência para esses tipos.  
  
## <a name="setting-styles-dynamically"></a>Configurando estilos dinamicamente  
 Para personalizar os estilos de células com valores específicos, implemente um manipulador para o <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> eventos. Manipuladores para este evento recebem um argumento do <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> tipo. Este objeto contém propriedades que permitem que você determine o valor da célula que está sendo formatada, junto com seu local no <xref:System.Windows.Forms.DataGridView> controle. Esse objeto também contém um <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A> que é inicializada com o valor da propriedade a <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> propriedade da célula que está sendo formatada. Você pode modificar as propriedades de estilo da célula para especificar as informações de estilo apropriadas para o valor e o local da célula.  
  
> [!NOTE]
>  O <xref:System.Windows.Forms.DataGridView.RowPrePaint> e <xref:System.Windows.Forms.DataGridView.RowPostPaint> eventos também recebem um <xref:System.Windows.Forms.DataGridViewCellStyle> dados de eventos do objeto, mas no seu caso, é uma cópia da linha <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> propriedade para propósitos de somente leitura e as alterações não afetam o controle.  
  
 Você também pode modificar dinamicamente os estilos de células individuais em resposta a eventos, como o <xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType> e <xref:System.Windows.Forms.DataGridView.CellMouseLeave> eventos. Por exemplo, em um manipulador para o <xref:System.Windows.Forms.DataGridView.CellMouseEnter> evento, você poderia armazenar o valor atual da cor de fundo de célula (recuperado por meio da célula <xref:System.Windows.Forms.DataGridViewCell.Style%2A> propriedade), em seguida, defina-o como uma nova cor que destacará a célula quando o mouse passa sobre ele. Em um manipulador para o <xref:System.Windows.Forms.DataGridView.CellMouseLeave> evento, em seguida, você pode restaurar a cor do plano de fundo para o valor original.  
  
> [!NOTE]
>  Armazenamento em cache os valores armazenados na célula de <xref:System.Windows.Forms.DataGridViewCell.Style%2A> propriedade é importante, independentemente se um determinado valor de estilo está definido. Se você substituir temporariamente uma configuração de estilo, restaurá-la ao seu estado original de "não definido" garantirá que a célula voltará a herdar a configuração de estilo de um nível mais alto. Se você precisar determinar o estilo real em vigor para uma célula, independentemente se o estilo é herdado, use a célula <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> propriedade.  
  
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
- [Formatação básica e estilos no controle DataGridView dos Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Como: Definir estilos de célula padrão para o controle DataGridView do Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Formatação de dados no controle DataGridView dos Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md)
