---
title: Opções de dimensionamento no controle DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid control [WPF], sizing
- size [WPF], DataGrid
- automatically size DataGrid [WPF]
ms.assetid: 96a0e47e-b010-4302-98ef-2daac446d8db
ms.openlocfilehash: 6d100fb17b1ee3e652985a637d333d9f65e20d36
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219194"
---
# <a name="sizing-options-in-the-datagrid-control"></a>Opções de dimensionamento no controle DataGrid
Várias opções estão disponíveis para controlar como o <xref:System.Windows.Controls.DataGrid> se dimensiona. O <xref:System.Windows.Controls.DataGrid>e linhas e colunas individuais no <xref:System.Windows.Controls.DataGrid>, pode ser definido para dimensionar automaticamente a seu conteúdo ou podem ser definidas com valores específicos. Por padrão, o <xref:System.Windows.Controls.DataGrid> aumentará ou reduzirá para ajustar o tamanho de seu conteúdo.  
  
## <a name="sizing-the-datagrid"></a>Dimensionamento de DataGrid  
  
### <a name="cautions-when-using-automatic-sizing"></a>Cuidados ao usar o dimensionamento automático  
 Por padrão, o <xref:System.Windows.FrameworkElement.Height%2A> e <xref:System.Windows.FrameworkElement.Width%2A> propriedades da <xref:System.Windows.Controls.DataGrid> são definidos como <xref:System.Double.NaN?displayProperty=nameWithType> ("`Auto`" em XAML) e o <xref:System.Windows.Controls.DataGrid> irá se ajustar ao tamanho do seu conteúdo.  
  
 Quando colocado dentro de um contêiner que não restringe o tamanho de seus filhos, como um <xref:System.Windows.Controls.Canvas> ou <xref:System.Windows.Controls.StackPanel>, o <xref:System.Windows.Controls.DataGrid> será alongado para além dos limites visíveis do contêiner e barras de rolagem não serão mostradas. Esta condição tem implicações de desempenho e usabilidade.  
  
 Quando associado a um conjunto de dados, se o <xref:System.Windows.FrameworkElement.Height%2A> do <xref:System.Windows.Controls.DataGrid> não é restrito, ele continuará a adicionar uma linha para cada item de dados no conjunto de dados associados. Isso pode causar a <xref:System.Windows.Controls.DataGrid> aumente para fora dos limites visíveis do seu aplicativo conforme as linhas são adicionadas. O <xref:System.Windows.Controls.DataGrid> não mostrará as barras de rolagem nesse caso porque seu <xref:System.Windows.FrameworkElement.Height%2A> continuará a crescer para acomodar as novas linhas.  
  
 Um objeto é criado para cada linha a <xref:System.Windows.Controls.DataGrid>. Se você estiver trabalhando com um grande conjunto de dados e você permitir que o <xref:System.Windows.Controls.DataGrid> para dimensionar automaticamente em si, a criação de um grande número de objetos pode afetar o desempenho do seu aplicativo.  
  
 Para evitar esses problemas ao trabalhar com grandes conjuntos de dados, é recomendável que você defina especificamente o <xref:System.Windows.FrameworkElement.Height%2A> do <xref:System.Windows.Controls.DataGrid> ou colocá-lo em um contêiner que restringirá seus <xref:System.Windows.FrameworkElement.Height%2A>, como um <xref:System.Windows.Controls.Grid>. Quando o <xref:System.Windows.FrameworkElement.Height%2A> é restrito, o <xref:System.Windows.Controls.DataGrid> criará somente as linhas que se ajustarão dentro de seu especificado <xref:System.Windows.FrameworkElement.Height%2A>e reciclará as linhas conforme necessário para exibir os novos dados.  
  
### <a name="setting-the-datagrid-size"></a>Configurando o tamanho de DataGrid  
 O <xref:System.Windows.Controls.DataGrid> pode ser definido para ser dimensionado automaticamente dentro dos limites especificados, ou o <xref:System.Windows.Controls.DataGrid> pode ser definido para um tamanho específico. A tabela a seguir mostra as propriedades que podem ser definidas para controlar o <xref:System.Windows.Controls.DataGrid> tamanho.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|<xref:System.Windows.FrameworkElement.Height%2A>|Define uma altura específica para o <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.FrameworkElement.MaxHeight%2A>|Define o limite superior para a altura do <xref:System.Windows.Controls.DataGrid>. O <xref:System.Windows.Controls.DataGrid> crescerá verticalmente até atingir essa altura.|  
|<xref:System.Windows.FrameworkElement.MinHeight%2A>|Define o limite inferior para a altura do <xref:System.Windows.Controls.DataGrid>. O <xref:System.Windows.Controls.DataGrid> será reduzido verticalmente até atingir essa altura.|  
|<xref:System.Windows.FrameworkElement.Width%2A>|Define uma largura específica para o <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.FrameworkElement.MaxWidth%2A>|Define o limite superior para a largura do <xref:System.Windows.Controls.DataGrid>. O <xref:System.Windows.Controls.DataGrid> crescerá horizontalmente até atingir essa largura.|  
|<xref:System.Windows.FrameworkElement.MinWidth%2A>|Define o limite inferior para a largura do <xref:System.Windows.Controls.DataGrid>. O <xref:System.Windows.Controls.DataGrid> será reduzido horizontalmente até atingir essa largura.|  
  
## <a name="sizing-rows-and-row-headers"></a>Dimensionando linhas e cabeçalhos de linha  
  
### <a name="datagrid-rows"></a>Linhas DataGrid  
 Por padrão, uma <xref:System.Windows.Controls.DataGrid> da linha <xref:System.Windows.FrameworkElement.Height%2A> estiver definida como <xref:System.Double.NaN?displayProperty=nameWithType> ("`Auto`" em XAML), e a altura da linha se expandirá para o tamanho de seu conteúdo. A altura de todas as linhas as <xref:System.Windows.Controls.DataGrid> pode ser especificada definindo o <xref:System.Windows.Controls.DataGrid.RowHeight%2A?displayProperty=nameWithType> propriedade. Os usuários podem alterar a altura da linha arrastando os divisores de cabeçalho de linha.  
  
### <a name="datagrid-row-headers"></a>Cabeçalhos de linha DataGrid  
 Para exibir cabeçalhos de linha, o <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> propriedade deve ser definida como <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> ou <xref:System.Windows.Controls.DataGridHeadersVisibility.All?displayProperty=nameWithType>. Por padrão, os cabeçalhos de linha são exibidos e são dimensionados automaticamente para ajustar seu conteúdo. Os cabeçalhos de linha podem ser fornecidos a uma largura específica configurando a <xref:System.Windows.Controls.DataGrid.RowHeaderWidth%2A?displayProperty=nameWithType> propriedade.  
  
## <a name="sizing-columns-and-column-headers"></a>Dimensionamento de colunas e cabeçalhos de coluna  
  
### <a name="datagrid-columns"></a>Colunas DataGrid  
 O <xref:System.Windows.Controls.DataGrid> usa valores da <xref:System.Windows.Controls.DataGridLength> e o <xref:System.Windows.Controls.DataGridLengthUnitType> estrutura para especificar os modos de dimensionamento automático ou absoluto.  
  
 A tabela a seguir mostra os valores fornecidos pelo <xref:System.Windows.Controls.DataGridLengthUnitType> estrutura.  
  
|Nome|Descrição|  
|----------|-----------------|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Auto>|O padrão de tamanhos de modo de dimensionamento automático <xref:System.Windows.Controls.DataGrid> colunas com base no conteúdo das células e cabeçalhos de coluna.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToCells>|O automático baseado em célula tamanhos de modo de dimensionamento <xref:System.Windows.Controls.DataGrid> colunas com base no conteúdo das células na coluna, não incluindo os cabeçalhos de coluna.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToHeader>|O automático baseado em cabeçalho tamanhos de modo de dimensionamento <xref:System.Windows.Controls.DataGrid> colunas com base no conteúdo dos cabeçalhos de coluna apenas.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Pixel>|O pixel baseado em tamanhos de modo de dimensionamento <xref:System.Windows.Controls.DataGrid> colunas com base no valor numérico fornecido.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Star>|O modo de dimensionamento em estrela é usado para distribuir o espaço disponível em proporções ponderadas.<br /><br /> No XAML, os valores de estrela são expressos como n*, em que n representa um valor numérico. 1\* equivale a \*. Por exemplo, se duas colunas em uma <xref:System.Windows.Controls.DataGrid> tivessem larguras de \* e 2\*, a primeira coluna receberia uma parte do espaço disponível e a segunda coluna receberia duas partes do espaço disponível.|  
  
 O <xref:System.Windows.Controls.DataGridLengthConverter> classe pode ser usada para converter dados entre os valores numéricos ou de cadeia de caracteres e <xref:System.Windows.Controls.DataGridLength> valores.  
  
 Por padrão, o <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType> estiver definida como <xref:System.Windows.Controls.DataGridLength.SizeToHeader%2A>e o <xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType> estiver definida como <xref:System.Windows.Controls.DataGridLength.Auto%2A>. Quando o modo de dimensionamento é definido como <xref:System.Windows.Controls.DataGridLength.Auto%2A> ou <xref:System.Windows.Controls.DataGridLength.SizeToCells%2A>, as colunas serão aumentadas para a largura do seu conteúdo visível mais amplo. Ao rolar, esses modos de dimensionamento farão as colunas expandirem se o conteúdo que é maior do que o tamanho atual da coluna for colocado na exibição. A coluna não será reduzida depois que o conteúdo estiver fora da exibição.  
  
 Colunas no <xref:System.Windows.Controls.DataGrid> também pode ser definido para ser dimensionado automaticamente apenas dentro dos limites especificados, ou colunas podem ser definidas para um tamanho específico. A tabela a seguir mostra as propriedades que podem ser definidas para controlar o tamanho das colunas.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>|Define o limite superior para todas as colunas a <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.MaxWidth%2A?displayProperty=nameWithType>|Define o limite superior para uma coluna individual. Substitui <xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>|Define o limite inferior de todas as colunas a <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.MinWidth%2A?displayProperty=nameWithType>|Define o limite inferior para uma coluna individual. Substitui <xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>|Define uma largura específica para todas as colunas a <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>|Define uma largura específica para uma coluna individual. Substitui <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>.|  
  
### <a name="datagrid-column-headers"></a>Cabeçalhos da coluna DataGrid  
 Por padrão, <xref:System.Windows.Controls.DataGrid> cabeçalhos de coluna são exibidos. Para ocultar cabeçalhos de coluna, o <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> propriedade deve ser definida como <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> ou <xref:System.Windows.Controls.DataGridHeadersVisibility.None?displayProperty=nameWithType>. Por padrão, quando os cabeçalhos de coluna, eles são dimensionados automaticamente para ajustar seu conteúdo. Os cabeçalhos de coluna podem receber uma altura específica definindo o <xref:System.Windows.Controls.DataGrid.ColumnHeaderHeight%2A?displayProperty=nameWithType> propriedade.  
  
### <a name="resizing-with-the-mouse"></a>Redimensionando com o mouse  
 Os usuários podem redimensionar <xref:System.Windows.Controls.DataGrid> linhas e colunas arrastando os divisores de cabeçalho de linha ou coluna. O <xref:System.Windows.Controls.DataGrid> também dá suporte a redimensionamento automático de linhas e colunas clicando duas vezes no divisor de cabeçalho de linha ou coluna. Para impedir que um usuário redimensione colunas específicas, defina as <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> propriedade para `false` para as colunas individuais. Para impedir que os usuários redimensionem todas as colunas, defina as <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> propriedade para `false`. Para impedir que os usuários redimensionem todas as linhas, defina as <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A?displayProperty=nameWithType> propriedade para `false`.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.DataGrid>
- <xref:System.Windows.Controls.DataGridColumn>
- <xref:System.Windows.Controls.DataGridLength>
- <xref:System.Windows.Controls.DataGridLengthConverter>
