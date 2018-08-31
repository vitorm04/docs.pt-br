---
title: Como formatar o controle DataGrid dos Windows Forms usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], DataGrid controls
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: 533b9814-6124-49dc-9fda-085f1502609f
ms.openlocfilehash: 9d2abdb7025c861df4efe1b662cf4cc91de5bbf8
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43255890"
---
# <a name="how-to-format-the-windows-forms-datagrid-control-using-the-designer"></a>Como formatar o controle DataGrid dos Windows Forms usando o designer
> [!NOTE]
>  O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Aplicando cores diferentes a várias partes de um <xref:System.Windows.Forms.DataGrid> controle pode ajudar a tornar as informações nele mais fáceis de ler e interpretar. É possível aplicar cores às linhas e colunas. Linhas e colunas também podem ser ocultadas ou exibidas como você desejar.  
  
 Há três aspectos básicos de formatação a <xref:System.Windows.Forms.DataGrid> controle:  
  
-   Você pode definir as propriedades para estabelecer um estilo padrão no qual os dados são exibidos.  
  
-   Com base nisso, você pode então personalizar a maneira como determinadas tabelas são exibidas no tempo de execução.  
  
-   Por fim, você pode modificar quais colunas são exibidas na grade de dados, bem como as cores e outras formatações mostradas.  
  
 Como etapa inicial em uma grade de dados de formatação, você pode definir as propriedades do <xref:System.Windows.Forms.DataGrid> em si. Essas opções de cor e formato formam a base da qual você pode fazer alterações dependendo das tabelas de dados e colunas exibidas.  
  
 O procedimento a seguir exige um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.DataGrid> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). Na [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], o <xref:System.Windows.Forms.DataGrid> controle não está na **caixa de ferramentas** por padrão. Para obter mais informações, consulte [Como adicionar itens à Caixa de ferramentas](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Estabelecer um estilo padrão para o controle DataGrid  
  
1.  Selecione o <xref:System.Windows.Forms.DataGrid> controle.  
  
2.  Na janela **Propriedades**, defina as seguintes propriedades, conforme adequado.  
  
    |Propriedade|Descrição|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|A propriedade `BackColor` define a cor das linhas de numeração par da grade. Quando você define o <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> propriedade para uma cor diferente, todas as outras linhas é definida para essa nova cor (linhas 1, 3, 5 e assim por diante).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|A cor da tela de fundo das linhas de numeração par da grade (linhas 0, 2, 4, 6 e assim por diante).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Enquanto o <xref:System.Windows.Forms.DataGrid.BackColor%2A> e <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> propriedades determina a cor das linhas na grade, o <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> propriedade determina a cor da área de fora da área de linha, que fica visível somente quando a grade é rolada para baixo, ou se apenas algumas linhas são contido na grade.|  
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
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|A cor de primeiro plano dos cabeçalhos de coluna da grade, incluindo o texto do cabeçalho de coluna e os glifos de sinal de mais (+) e sinal de menos (-) que expandem e recolhem as linhas quando várias tabelas relacionadas são exibidas.|  
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
    >  Quando você está personalizando as cores dos controles, é possível tornar o controle inacessível devido à escolha incorreta de cor (por exemplo, vermelho e verde). Use as cores disponíveis na paleta de **Cores do Sistema** para evitar esse problema.  
  
     O procedimento a seguir exige um <xref:System.Windows.Forms.DataGrid> controle associado a uma tabela de dados. Para obter mais informações, consulte [Como associar o controle DataGrid dos Windows Forms a uma fonte de dados](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-at-design-time"></a>Para definir o estilo de tabela e de coluna de uma tabela de dados em tempo de design  
  
1.  Selecione o <xref:System.Windows.Forms.DataGrid> controle no formulário.  
  
2.  No **propriedades** janela, selecione a <xref:System.Windows.Forms.DataGrid.TableStyles%2A> propriedade e clique no **reticências** (![captura de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) botão.  
  
3.  Na caixa de diálogo **Editor de Coleção DataGridTableStyle**, clique em **Adicionar** para adicionar um estilo de tabela à coleção.  
  
     Com o **Editor de Coleção DataGridTableStyle**, você pode adicionar e remover estilos de tabela, definir propriedades de layout e exibição e definir o nome de mapeamento para os estilos de tabela.  
  
4.  Defina o <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> propriedade para o nome do mapeamento para cada estilo de tabela.  
  
     O nome do mapeamento é usado para especificar qual estilo de tabela deve ser usado com cada tabela.  
  
5.  No **Editor de coleção DataGridTableStyle**, selecione o <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> propriedade e clique no botão de reticências (![captura de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton ")).  
  
6.  Na caixa de diálogo **Editor de Coleção DataGridColumnStyle**, adicione estilos de coluna ao estilo de tabela que você criou.  
  
     Com o **Editor de Coleção DataGridColumnStyle**, você pode adicionar e remover estilos de coluna, definir propriedades de layout e exibição e definir o nome de mapeamento e cadeias de caracteres de formatação para as colunas de dados.  
  
    > [!NOTE]
    >  Para obter mais informações sobre as cadeias de caracteres de formatação, consulte [Tipos de formatação](../../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.GridTableStylesCollection>  
 <xref:System.Windows.Forms.GridColumnStylesCollection>  
 <xref:System.Windows.Forms.DataGrid>  
 [Como excluir ou ocultar colunas no controle DataGrid do Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [Controle DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
