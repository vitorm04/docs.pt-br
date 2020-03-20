---
title: Controle de DataGrid de formato
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], DataGrid control
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- columns [Windows Forms], formatting in DataGrid control
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: a50fcc3b-8abf-47ec-9029-7f268af4ddb1
ms.openlocfilehash: 180f837c7d60f49af880faefc05da262be061d12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182144"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>Como formatar o controle DataGrid dos Windows Forms
> [!NOTE]
> O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças entre os formulários do Windows DataGridView e controles datagrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Aplicar cores diferentes a <xref:System.Windows.Forms.DataGrid> várias partes de um controle pode ajudar a tornar as informações mais fáceis de ler e interpretar. É possível aplicar cores às linhas e colunas. Linhas e colunas também podem ser ocultadas ou exibidas como você desejar.  
  
 Há três aspectos básicos da <xref:System.Windows.Forms.DataGrid> formatação do controle. Você pode definir as propriedades para estabelecer um estilo padrão no qual os dados são exibidos. Com base nisso, você pode então personalizar a maneira como determinadas tabelas são exibidas no tempo de execução. Por fim, você pode modificar quais colunas são exibidas na grade de dados, bem como as cores e outras formatações mostradas.  
  
 Como um passo inicial na formatação de uma grade <xref:System.Windows.Forms.DataGrid> de dados, você pode definir as propriedades da própria. Essas opções de cor e formato formam a base da qual você pode fazer alterações dependendo das tabelas de dados e colunas exibidas.  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Estabelecer um estilo padrão para o controle DataGrid  
  
1. Defina as seguintes propriedades conforme necessário:  
  
    |Propriedade|Descrição|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|A propriedade <xref:System.Windows.Forms.DataGrid.BackColor%2A> define a cor das linhas de numeração par da grade. Quando você <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> define a propriedade para uma cor diferente, todas as outras linhas são definidas para esta nova cor (linhas 1, 3, 5 e assim por diante).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|A cor da tela de fundo das linhas de numeração par da grade (linhas 0, 2, 4, 6 e assim por diante).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Considerando que <xref:System.Windows.Forms.DataGrid.BackColor%2A> <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> as propriedades e as propriedades determinam <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> a cor das linhas na grade, a propriedade determina a cor da área não-row, que só é visível quando a grade é rolada para o fundo, ou se apenas algumas linhas estão contidas na grade.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|O estilo de borda da <xref:System.Windows.Forms.BorderStyle> grade, um dos valores de enumeração.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|A cor da tela de fundo da legenda da janela da grade que aparece logo acima da grade.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|A fonte da legenda na parte superior da grade.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|A cor da tela de fundo da legenda da janela da grade.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|A fonte usada para exibir o texto na grade.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|A cor da fonte exibida pelos dados nas linhas da grade de dados.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|A cor das linhas da grade dos dados.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|O estilo das linhas que separam as células da grade, um dos valores de <xref:System.Windows.Forms.DataGridLineStyle> enumeração.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|A cor da tela de fundo dos cabeçalhos de linha e de coluna.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|A fonte usada para os cabeçalhos de coluna.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|A cor de primeiro plano dos cabeçalhos de coluna da grade, incluindo o texto do cabeçalho de coluna e os glifos mais/menos (para expandir linhas quando várias tabelas relacionadas são exibidas).|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|A cor do texto de todos os links na grade de dados, incluindo links para tabelas filho, o nome da relação e assim por diante.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|Na tabela filho, indica a cor da tela de fundo das linhas pai.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|Na tabela filho, indica a cor de primeiro plano das linhas pai.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Determina se os nomes da tabela e da coluna são <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> exibidos na linha pai, por meio da enumeração.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|A largura padrão (em pixels) das colunas na grade. Defina essa propriedade <xref:System.Windows.Forms.DataGrid.DataSource%2A> antes <xref:System.Windows.Forms.DataGrid.DataMember%2A> de redefinir as propriedades <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> (separadamente, ou através do método), ou a propriedade não terá efeito.<br /><br /> Não é possível definir a propriedade para um valor inferior a 0.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|A altura (em pixels) das linhas na grade. Defina essa propriedade <xref:System.Windows.Forms.DataGrid.DataSource%2A> antes <xref:System.Windows.Forms.DataGrid.DataMember%2A> de redefinir as propriedades <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> (separadamente, ou através do método), ou a propriedade não terá efeito.<br /><br /> Não é possível definir a propriedade para um valor inferior a 0.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|A largura dos cabeçalhos de linha da grade.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Quando uma linha ou célula é selecionada, essa é a cor da tela de fundo.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Quando uma linha ou célula é selecionada, essa é a cor de primeiro plano.|  
  
    > [!NOTE]
    > Lembre-se que, ao personalizar as cores dos controles, é possível tornar o controle inacessível devido a opção incorreta de cor (por exemplo, vermelho e verde). Use as cores disponíveis na paleta de **Cores do Sistema** para evitar esse problema.  
  
     Os procedimentos a seguir <xref:System.Windows.Forms.DataGrid> assumem que seu formulário tem um controle vinculado a uma tabela de dados. Para obter mais informações, consulte [Associando o controle DataGrid do Windows Forms a uma fonte de dados](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>Definir o estilo de tabela e coluna de uma tabela de dados com programação  
  
1. Crie um novo estilo de tabela e defina suas propriedades.  
  
2. Crie um estilo de coluna e defina suas propriedades.  
  
3. Adicione o estilo de coluna à coleção de estilos de coluna do estilo de tabela.  
  
4. Adicione o estilo de tabela à coleção de estilos de tabela da grade de dados.  
  
5. No exemplo abaixo, crie uma <xref:System.Windows.Forms.DataGridTableStyle> instância de <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> um novo e defina sua propriedade.  
  
6. Crie uma nova instância de um **GridColumnStyle** e defina seu **MappingName** (e algumas outras propriedades de layout e exibição).  
  
7. Repita as etapas 2 a 6 para cada estilo de coluna que você deseja criar.  
  
     O exemplo a seguir <xref:System.Windows.Forms.DataGridTextBoxColumn> ilustra como um é criado, porque um nome deve ser exibido na coluna. Além disso, você adiciona o <xref:System.Windows.Forms.GridColumnStylesCollection> estilo de coluna ao estilo da <xref:System.Windows.Forms.GridTableStylesCollection> tabela e adiciona o estilo de tabela à grade de dados.  
  
    ```vb  
    Private Sub CreateAuthorFirstNameColumn()  
       ' Add a GridTableStyle and set the MappingName
       ' to the name of the DataTable.  
       Dim TSAuthors As New DataGridTableStyle()  
       TSAuthors.MappingName = "Authors"  
  
       ' Add a GridColumnStyle and set the MappingName
       ' to the name of a DataColumn in the DataTable.
       ' Set the HeaderText and Width properties.
       Dim TCFirstName As New DataGridTextBoxColumn()  
       TCFirstName.MappingName = "AV_FName"  
       TCFirstName.HeaderText = "First Name"  
       TCFirstName.Width = 75  
       TSAuthors.GridColumnStyles.Add(TCFirstName)  
  
       ' Add the DataGridTableStyle instance to
       ' the GridTableStylesCollection.
       myDataGrid.TableStyles.Add(TSAuthors)  
    End Sub  
    ```  
  
    ```csharp  
    private void addCustomDataTableStyle()  
    {  
       // Add a GridTableStyle and set the MappingName
       // to the name of the DataTable.  
       DataGridTableStyle TSAuthors = new DataGridTableStyle();  
       TSAuthors.MappingName = "Authors";  
  
       // Add a GridColumnStyle and set the MappingName
       // to the name of a DataColumn in the DataTable.
       // Set the HeaderText and Width properties.
       DataGridColumnStyle TCFirstName = new DataGridTextBoxColumn();  
       TCFirstName.MappingName = " AV_FName";  
       TCFirstName.HeaderText = "First Name";  
       TCFirstName.Width = 75;  
       TSAuthors.GridColumnStyles.Add(TCFirstName);  
  
       // Add the DataGridTableStyle instance to
       // the GridTableStylesCollection.
       dataGrid1.TableStyles.Add(TSAuthors);  
    }  
    ```  
  
    ```cpp  
    private:  
       void addCustomDataTableStyle()  
       {  
          // Add a GridTableStyle and set the MappingName
          // to the name of the DataTable.  
          DataGridTableStyle^ TSAuthors = new DataGridTableStyle();  
          TSAuthors->MappingName = "Authors";  
  
          // Add a GridColumnStyle and set the MappingName
          // to the name of a DataColumn in the DataTable.
          // Set the HeaderText and Width properties.
          DataGridColumnStyle^ TCFirstName = gcnew DataGridTextBoxColumn();  
          TCFirstName->MappingName = "AV_FName";  
          TCFirstName->HeaderText = "First Name";  
          TCFirstName->Width = 75;  
          TSAuthors->GridColumnStyles->Add(TCFirstName);  
  
          // Add the DataGridTableStyle instance to
          // the GridTableStylesCollection.
          dataGrid1->TableStyles->Add(TSAuthors);  
       }  
    ```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [Como excluir ou ocultar colunas no controle DataGrid do Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Controle DataGrid](datagrid-control-windows-forms.md)
