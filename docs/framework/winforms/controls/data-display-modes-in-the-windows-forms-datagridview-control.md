---
title: Modos de exibição dos dados no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], display modes
- data grids [Windows Forms], display modes
- DataGridView control [Windows Forms], display modes
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
ms.openlocfilehash: 673780909f6d66168548893e99d79bbfec70a0e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011392"
---
# <a name="data-display-modes-in-the-windows-forms-datagridview-control"></a>Modos de exibição dos dados no controle DataGridView dos Windows Forms
O <xref:System.Windows.Forms.DataGridView> controle pode exibir dados em três modos diferentes: associado, não associado e virtual. Escolha o modo mais adequado com base em suas necessidades.  
  
## <a name="unbound"></a>Não Associado  
 O modo não associado é adequado para exibir quantidades de dados relativamente pequenas que você gerencia programaticamente. Não anexar o <xref:System.Windows.Forms.DataGridView> controle diretamente a uma fonte de dados como no modo associado. Em vez disso, você deve preencher o controle por conta própria, normalmente usando o <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> método.  
  
 O modo não associado pode ser particularmente útil para dados estáticos, somente leitura ou quando você desejar fornecer seu próprio código que interage com um armazenamento de dados externo. Quando quiser que os usuários interajam com uma fonte de dados externa, no entanto, você normalmente usará o modo associado.  
  
 Para obter um exemplo que usa somente leitura não associado <xref:System.Windows.Forms.DataGridView>, consulte [como: Criar um controle de DataGridView não associado do Windows Forms](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="bound"></a>Associado  
 O modo associado é adequado para gerenciar dados usando a interação automática com o armazenamento de dados. Você pode anexar a <xref:System.Windows.Forms.DataGridView> controle diretamente para sua fonte de dados, definindo o <xref:System.Windows.Forms.DataGridView.DataSource%2A> propriedade. Quando o controle for associado aos dados, as linhas de dados serão enviadas e recebidas sem a necessidade de gerenciamento explícito da sua parte. Quando o <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> é de propriedade `true`, cada coluna na fonte de dados fará com que uma coluna correspondente a ser criado no controle. Se você preferir criar suas próprias colunas, você pode definir essa propriedade `false` e use o <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> propriedade para associar cada coluna quando você configurá-lo. Isso é útil quando você deseja usar um tipo de coluna diferente dos tipos que são gerados por padrão. Para obter mais informações, consulte [Tipos de coluna no controle DataGridView dos Windows Forms](column-types-in-the-windows-forms-datagridview-control.md).  
  
 Para obter um exemplo que usa um limite <xref:System.Windows.Forms.DataGridView> de controle, consulte [passo a passo: Validando dados em que o Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
 Você também pode adicionar colunas não associadas a um <xref:System.Windows.Forms.DataGridView> controle no modo associado. Isso é útil quando você deseja exibir uma coluna de botões ou links que permitem aos usuários executar ações em linhas específicas. Também é útil exibir as colunas com valores calculados de colunas associadas. Você pode preencher os valores de célula para colunas calculadas em um manipulador para o <xref:System.Windows.Forms.DataGridView.CellFormatting> eventos. Se você estiver usando um <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> como fonte de dados, no entanto, você talvez queira usar o <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType> propriedade para criar uma coluna calculada em vez disso. Nesse caso, o <xref:System.Windows.Forms.DataGridView> controle tratará a coluna calculada, assim como qualquer outra coluna na fonte de dados.  
  
 Não há suporte para a classificação por colunas não associadas no modo associado. Se criar uma coluna não associada no modo associado que contenha os valores editáveis pelo usuário, você deverá implementar o modo virtual para manter esses valores quando o controle for classificado por uma coluna associada.  
  
## <a name="virtual"></a>Virtual  
 Com o modo virtual, você pode implementar suas próprias operações de gerenciamento de dados. Isso é necessário para manter os valores das colunas não associadas no modo associado quando o controle for classificado por colunas associadas. No entanto, o uso principal do modo virtual é otimizar o desempenho ao interagir com grandes quantidades de dados.  
  
 Você anexa o <xref:System.Windows.Forms.DataGridView> controle a um cache que você gerencia e seu código controlará quando as linhas de dados forem enviadas e recebidas. Para manter o volume de memória pequeno, o cache deve ser semelhante em tamanho ao número de linhas exibidas atualmente. Quando o usuário rola novas linhas no modo de exibição, seu código solicita novos dados do cache e, como alternativa, libera os dados antigos da memória.  
  
 Quando estiver implementando o modo virtual, você precisará controlar quando uma nova linha for necessária no modelo de dados e o momento para reverter a adição da nova linha. A implementação dessa funcionalidade exata dependerá da implementação do modelo de dados e da semântica de transação do modelo de dados; se o escopo de confirmação está no nível da célula ou da linha.  
  
 Para obter mais informações sobre o modo virtual, consulte [Como implementar o modo virtual no controle DataGridView dos Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md). Para obter um exemplo que mostra como usar eventos de modo virtual, consulte [passo a passo: Implementando o modo Virtual no Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=nameWithType>
- [Exibindo dados no controle DataGridView do Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Tipos de coluna no controle DataGridView dos Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
- [Passo a passo: Criando um Windows não associado Forms o controle DataGridView](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [Como: Associar dados ao controle DataGridView dos Windows Forms](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
- [Modo virtual no controle DataGridView dos Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Passo a passo: Implementando o modo Virtual no controle DataGridView dos Windows Forms](implementing-virtual-mode-wf-datagridview-control.md)
