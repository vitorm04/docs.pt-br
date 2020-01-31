---
title: Modos de exibição de dados no controle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], display modes
- data grids [Windows Forms], display modes
- DataGridView control [Windows Forms], display modes
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
ms.openlocfilehash: ad6be647e3a36904b055fd6771f539df28938fab
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744011"
---
# <a name="data-display-modes-in-the-windows-forms-datagridview-control"></a>Modos de exibição dos dados no controle DataGridView dos Windows Forms
O controle de <xref:System.Windows.Forms.DataGridView> pode exibir dados em três modos distintos: ligado, não associado e virtual. Escolha o modo mais adequado com base em suas necessidades.  
  
## <a name="unbound"></a>Não Associado  
 O modo não associado é adequado para exibir quantidades de dados relativamente pequenas que você gerencia programaticamente. Você não anexa o controle de <xref:System.Windows.Forms.DataGridView> diretamente a uma fonte de dados como no modo ligado. Em vez disso, você deve preencher o controle por conta própria, normalmente usando o método <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType>.  
  
 O modo não associado pode ser particularmente útil para dados estáticos, somente leitura ou quando você desejar fornecer seu próprio código que interage com um armazenamento de dados externo. Quando quiser que os usuários interajam com uma fonte de dados externa, no entanto, você normalmente usará o modo associado.  
  
 Para obter um exemplo que usa um <xref:System.Windows.Forms.DataGridView>desassociado somente leitura, consulte [como criar um controle DataGridView de Windows Forms não associado](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="bound"></a>Associado  
 O modo associado é adequado para gerenciar dados usando a interação automática com o armazenamento de dados. Você pode anexar o controle de <xref:System.Windows.Forms.DataGridView> diretamente à sua fonte de dados definindo a propriedade <xref:System.Windows.Forms.DataGridView.DataSource%2A>. Quando o controle for associado aos dados, as linhas de dados serão enviadas e recebidas sem a necessidade de gerenciamento explícito da sua parte. Quando a propriedade <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> for `true`, cada coluna em sua fonte de dados fará com que uma coluna correspondente seja criada no controle. Se preferir criar suas próprias colunas, você poderá definir essa propriedade como `false` e usar a propriedade <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> para associar cada coluna ao configurá-la. Isso é útil quando você deseja usar um tipo de coluna diferente dos tipos que são gerados por padrão. Para obter mais informações, consulte [Tipos de coluna no controle DataGridView dos Windows Forms](column-types-in-the-windows-forms-datagridview-control.md).  
  
 Para obter um exemplo que usa um controle de <xref:System.Windows.Forms.DataGridView> associado, consulte [Walkthrough: Validando dados no controle DataGridView Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
 Você também pode adicionar colunas desassociadas a um controle de <xref:System.Windows.Forms.DataGridView> no modo ligado. Isso é útil quando você deseja exibir uma coluna de botões ou links que permitem aos usuários executar ações em linhas específicas. Também é útil exibir as colunas com valores calculados de colunas associadas. Você pode preencher os valores de célula para colunas calculadas em um manipulador para o evento <xref:System.Windows.Forms.DataGridView.CellFormatting>. Se você estiver usando um <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> como a fonte de dados, no entanto, talvez queira usar a propriedade <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType> para criar uma coluna calculada. Nesse caso, o controle de <xref:System.Windows.Forms.DataGridView> tratará a coluna calculada, assim como qualquer outra coluna na fonte de dados.  
  
 Não há suporte para a classificação por colunas não associadas no modo associado. Se criar uma coluna não associada no modo associado que contenha os valores editáveis pelo usuário, você deverá implementar o modo virtual para manter esses valores quando o controle for classificado por uma coluna associada.  
  
## <a name="virtual"></a>Virtual  
 Com o modo virtual, você pode implementar suas próprias operações de gerenciamento de dados. Isso é necessário para manter os valores das colunas não associadas no modo associado quando o controle for classificado por colunas associadas. No entanto, o uso principal do modo virtual é otimizar o desempenho ao interagir com grandes quantidades de dados.  
  
 Você anexa o controle de <xref:System.Windows.Forms.DataGridView> a um cache que você gerencia e seus controles de código quando as linhas de dados são enviadas por push e puxadas. Para manter o volume de memória pequeno, o cache deve ser semelhante em tamanho ao número de linhas exibidas atualmente. Quando o usuário rola novas linhas no modo de exibição, seu código solicita novos dados do cache e, como alternativa, libera os dados antigos da memória.  
  
 Quando estiver implementando o modo virtual, você precisará controlar quando uma nova linha for necessária no modelo de dados e o momento para reverter a adição da nova linha. A implementação dessa funcionalidade exata dependerá da implementação do modelo de dados e da semântica de transação do modelo de dados; se o escopo de confirmação está no nível da célula ou da linha.  
  
 Para obter mais informações sobre o modo virtual, consulte [Como implementar o modo virtual no controle DataGridView dos Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md). Para obter um exemplo que mostra como usar os eventos de modo virtual, consulte [Instruções passo a passo: implementando o modo virtual no controle DataGridView dos Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=nameWithType>
- [Exibindo dados no controle DataGridView dos Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Tipos de coluna no controle DataGridView dos Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
- [Instruções passo a passo: criando um controle DataGridView não associado do Windows Forms](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [Como associar dados ao controle DataGridView do Windows Forms](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
- [Modo virtual no controle DataGridView dos Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Passo a passo: implementando o modo virtual no controle DataGridView dos Windows Forms](implementing-virtual-mode-wf-datagridview-control.md)
