---
title: Como formatar o controle DataGrid dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8518fdcaca7ebed65d0923b9bc1fe1a6797b97c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>Como formatar o controle DataGrid dos Windows Forms
> [!NOTE]
>  O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Aplicando cores diferentes para várias partes de um <xref:System.Windows.Forms.DataGrid> controle pode ajudar a tornar as informações nela mais fácil de ler e interpretar. É possível aplicar cores às linhas e colunas. Linhas e colunas também podem ser ocultadas ou exibidas como você desejar.  
  
 Há três aspectos básicos de formatação de <xref:System.Windows.Forms.DataGrid> controle. Você pode definir as propriedades para estabelecer um estilo padrão no qual os dados são exibidos. Com base nisso, você pode então personalizar a maneira como determinadas tabelas são exibidas no tempo de execução. Por fim, você pode modificar quais colunas são exibidas na grade de dados, bem como as cores e outras formatações mostradas.  
  
 Como uma etapa inicial em uma grade de dados de formatação, você pode definir as propriedades da <xref:System.Windows.Forms.DataGrid> em si. Essas opções de cor e formato formam a base da qual você pode fazer alterações dependendo das tabelas de dados e colunas exibidas.  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Estabelecer um estilo padrão para o controle DataGrid  
  
1.  Defina as seguintes propriedades conforme necessário:  
  
    |Propriedade|Descrição|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|A propriedade <xref:System.Windows.Forms.DataGrid.BackColor%2A> define a cor das linhas de numeração par da grade. Quando você define o <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> propriedade para uma cor diferente, todas as outras linhas é definida para essa nova cor (linhas 1, 3, 5 e assim por diante).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|A cor da tela de fundo das linhas de numeração par da grade (linhas 0, 2, 4, 6 e assim por diante).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Enquanto o <xref:System.Windows.Forms.DataGrid.BackColor%2A> e <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> propriedades determina a cor das linhas na grade, o <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> propriedade determina a cor da área de nonrow, que só é visível quando a grade é rolada na parte inferior, ou se apenas algumas linhas estão contidas em a grade.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Estilo da borda da grade, uma da <xref:System.Windows.Forms.BorderStyle> valores de enumeração.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|A cor da tela de fundo da legenda da janela da grade que aparece logo acima da grade.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|A fonte da legenda na parte superior da grade.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|A cor da tela de fundo da legenda da janela da grade.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|A fonte usada para exibir o texto na grade.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|A cor da fonte exibida pelos dados nas linhas da grade de dados.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|A cor das linhas da grade dos dados.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|O estilo das linhas que separam as células da grade, uma da <xref:System.Windows.Forms.DataGridLineStyle> valores de enumeração.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|A cor da tela de fundo dos cabeçalhos de linha e de coluna.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|A fonte usada para os cabeçalhos de coluna.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|A cor de primeiro plano dos cabeçalhos de coluna da grade, incluindo o texto do cabeçalho de coluna e os glifos mais/menos (para expandir linhas quando várias tabelas relacionadas são exibidas).|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|A cor do texto de todos os links na grade de dados, incluindo links para tabelas filho, o nome da relação e assim por diante.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|Na tabela filho, indica a cor da tela de fundo das linhas pai.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|Na tabela filho, indica a cor de primeiro plano das linhas pai.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Determina se os nomes de tabela e coluna são exibidos na linha pai, por meio do <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> enumeração.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|A largura padrão (em pixels) das colunas na grade. Defina essa propriedade antes de redefinir o <xref:System.Windows.Forms.DataGrid.DataSource%2A> e <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriedades (tanto separadamente, ou por meio de <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método), ou a propriedade não terá efeito.<br /><br /> Não é possível definir a propriedade para um valor inferior a 0.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|A altura (em pixels) das linhas na grade. Defina essa propriedade antes de redefinir o <xref:System.Windows.Forms.DataGrid.DataSource%2A> e <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriedades (tanto separadamente, ou por meio de <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método), ou a propriedade não terá efeito.<br /><br /> Não é possível definir a propriedade para um valor inferior a 0.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|A largura dos cabeçalhos de linha da grade.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Quando uma linha ou célula é selecionada, essa é a cor da tela de fundo.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Quando uma linha ou célula é selecionada, essa é a cor de primeiro plano.|  
  
    > [!NOTE]
    >  Lembre-se que, ao personalizar as cores dos controles, é possível tornar o controle inacessível devido a opção incorreta de cor (por exemplo, vermelho e verde). Use as cores disponíveis na paleta de **Cores do Sistema** para evitar esse problema.  
  
     Os procedimentos a seguir pressupõem que o formulário tem uma <xref:System.Windows.Forms.DataGrid> controle associada a uma tabela de dados. Para obter mais informações, consulte [Associando o controle DataGrid do Windows Forms a uma fonte de dados](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>Definir o estilo de tabela e coluna de uma tabela de dados com programação  
  
1.  Crie um novo estilo de tabela e defina suas propriedades.  
  
2.  Crie um estilo de coluna e defina suas propriedades.  
  
3.  Adicione o estilo de coluna à coleção de estilos de coluna do estilo de tabela.  
  
4.  Adicione o estilo de tabela à coleção de estilos de tabela da grade de dados.  
  
5.  O exemplo a seguir, cria uma instância de um novo <xref:System.Windows.Forms.DataGridTableStyle> e defina seu <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> propriedade.  
  
6.  Crie uma nova instância de um **GridColumnStyle** e defina seu **MappingName** (e algumas outras propriedades de layout e exibição).  
  
7.  Repita as etapas 2 a 6 para cada estilo de coluna que você deseja criar.  
  
     O exemplo a seguir ilustra como um <xref:System.Windows.Forms.DataGridTextBoxColumn> é criado, porque é um nome a ser exibido na coluna. Além disso, você pode adicionar o estilo de coluna para o <xref:System.Windows.Forms.GridColumnStylesCollection> do estilo de tabela, e adicionar o estilo de tabela para o <xref:System.Windows.Forms.GridTableStylesCollection> da grade de dados.  
  
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
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.GridTableStylesCollection>  
 <xref:System.Windows.Forms.GridColumnStylesCollection>  
 <xref:System.Windows.Forms.DataGrid>  
 [Como excluir ou ocultar colunas no controle DataGrid dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [Controle DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
