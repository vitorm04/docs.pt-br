---
title: Usando a linha para novos registros no controle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], adding rows for new records
- rows [Windows Forms], new records
- DataGridView control [Windows Forms], data entry
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
ms.openlocfilehash: 2fcd35f8c4d04909cdbc26f6a4293fdd570385b8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728338"
---
# <a name="using-the-row-for-new-records-in-the-windows-forms-datagridview-control"></a>Usando a linha para novos registros no controle DataGridView dos Windows Forms
Quando você usa um <xref:System.Windows.Forms.DataGridView> para editar dados em seu aplicativo, muitas vezes você desejará dar aos usuários a capacidade de adicionar novas linhas de dados ao armazenamento de dados. O controle de <xref:System.Windows.Forms.DataGridView> dá suporte a essa funcionalidade, fornecendo uma linha para novos registros, que é sempre mostrada como a última linha. Ela é marcada com um símbolo de asterisco (*) em seu cabeçalho de linha. As seções a seguir tratam de algumas coisas que você deve considerar quando programar com a linha de novos registros habilitada.  
  
## <a name="displaying-the-row-for-new-records"></a>Exibindo a linha de novos registros  
 Use a propriedade <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> para indicar se a linha de novos registros é exibida. O valor padrão dessa propriedade é `true`.  
  
 Para o caso associado a dados, a linha de novos registros será mostrada se a propriedade <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> do controle e a propriedade <xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=nameWithType> da fonte de dados forem `true`. Se uma delas for `false`, a linha não será exibida.  
  
## <a name="populating-the-row-for-new-records-with-default-data"></a>Preenchendo a linha de novos registros com os dados padrão  
 Quando o usuário seleciona a linha para novos registros como a linha atual, o controle de <xref:System.Windows.Forms.DataGridView> gera o evento <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>.  
  
 Esse evento fornece acesso ao novo <xref:System.Windows.Forms.DataGridViewRow> e permite que você preencha a nova linha com dados padrão. Para obter mais informações, consulte [Como especificar valores padrão para novas linhas no controle DataGridView dos Windows Forms](specify-default-values-for-new-rows-in-the-datagrid.md)  
  
## <a name="the-rows-collection"></a>A coleção de linhas  
 A linha de novos registros está contida na coleção de <xref:System.Windows.Forms.DataGridView.Rows%2A> do controle de <xref:System.Windows.Forms.DataGridView>, mas se comporta de forma diferente em dois aspectos:  
  
- A linha de novos registros não pode ser removida da coleção de <xref:System.Windows.Forms.DataGridView.Rows%2A> programaticamente. Um <xref:System.InvalidOperationException> será gerado se isso for tentado. O usuário também não pode excluir a linha de novos registros. O método <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=nameWithType> não remove essa linha da coleção <xref:System.Windows.Forms.DataGridView.Rows%2A>.  
  
- Nenhuma linha pode ser adicionada após a linha de novos registros. Um <xref:System.InvalidOperationException> será gerado se isso for tentado. Como resultado, a linha de novos registros é sempre a última linha no controle de <xref:System.Windows.Forms.DataGridView>. Os métodos em <xref:System.Windows.Forms.DataGridViewRowCollection> que adicionam linhas –<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>e <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>– todos os métodos de inserção de chamada internamente quando a linha de novos registros está presente.  
  
## <a name="visual-customization-of-the-row-for-new-records"></a>Personalização visual da linha de novos registros  
 Quando a linha de novos registros é criada, ela é baseada na linha especificada pela propriedade <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>. Qualquer estilo de célula que não for especificado para essa linha será herdado de outras propriedades. Para obter mais informações sobre herança de estilo de célula, consulte [Estilos de célula no controle DataGridView dos Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Os valores iniciais exibidos pelas células na linha para novos registros são recuperados da propriedade <xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A> de cada célula. Para células do tipo <xref:System.Windows.Forms.DataGridViewImageCell>, essa propriedade retorna uma imagem de espaço reservado. Caso contrário, essa propriedade retornará `null`. Você pode substituir essa propriedade para retornar um valor personalizado. No entanto, esses valores iniciais podem ser substituídos por um manipulador de eventos <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> quando o foco entra na linha para novos registros.  
  
 Os ícones padrão do cabeçalho dessa linha, que são uma seta ou um asterisco, não são expostos publicamente. Se você quiser personalizar os ícones, será necessário criar uma classe de <xref:System.Windows.Forms.DataGridViewRowHeaderCell> personalizada.  
  
 Os ícones padrão usam a propriedade <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> da <xref:System.Windows.Forms.DataGridViewCellStyle> em uso pela célula de cabeçalho de linha. Os ícones padrão não serão renderizados se não houver espaço suficiente para exibi-los completamente.  
  
 Se a célula do cabeçalho de linha tiver um valor de cadeia de caracteres definido e, se não houver espaço suficiente para o texto e o ícone, o ícone será descartado primeiro.  
  
## <a name="sorting"></a>Classificação  
 No modo não associado, os novos registros serão sempre adicionados ao final do <xref:System.Windows.Forms.DataGridView> mesmo que o usuário tenha classificado o conteúdo do <xref:System.Windows.Forms.DataGridView>. O usuário precisará aplicar a classificação novamente para classificar a linha para a posição correta; Esse comportamento é semelhante ao do controle de <xref:System.Windows.Forms.ListView>.  
  
 Em modos virtuais ou com associação de dados, o comportamento de inserção quando uma classificação for aplicada dependerá da implementação do modelo de dados. Para ADO.NET, a linha é imediatamente classificada na posição correta.  
  
## <a name="other-notes-on-the-row-for-new-records"></a>Outras observações sobre a linha de novos registros  
 Não é possível definir a propriedade <xref:System.Windows.Forms.DataGridViewRow.Visible%2A> dessa linha como `false`. Um <xref:System.InvalidOperationException> será gerado se isso for tentado.  
  
 A linha de novos registros sempre é criada no estado desmarcado.  
  
## <a name="virtual-mode"></a>Modo virtual  
 Se estiver implementando o modo virtual, você precisará monitorar quando uma linha de novos registros é necessária no modelo de dados e o momento para reverter a adição da linha. A implementação exata dessa funcionalidade depende da implementação do modelo de dados e de sua semântica de transação, por exemplo, se o escopo de confirmação está no nível da célula ou da linha. Para obter mais informações, consulte [Modo virtual no controle DataGridView dos Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Entrada de Dados no controle DataGridView dos Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Como especificar valores padrão para novas linhas no controle DataGridView dos Windows Forms](specify-default-values-for-new-rows-in-the-datagrid.md)
