---
title: Diferenças entre os controles DataGridView e DataGrid dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: 6802ef375d8d15826725e68f5065317192523178
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59095666"
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Diferenças entre os controles DataGridView e DataGrid dos Windows Forms
O <xref:System.Windows.Forms.DataGridView> controle é um novo controle que substitui o <xref:System.Windows.Forms.DataGrid> controle. O <xref:System.Windows.Forms.DataGridView> controle fornece vários recursos básicos e avançados que estão faltando no <xref:System.Windows.Forms.DataGrid> controle. Além disso, a arquitetura do <xref:System.Windows.Forms.DataGridView> controle torna muito mais fácil de estender e personalizar que o <xref:System.Windows.Forms.DataGrid> controle.  
  
 A tabela a seguir descreve alguns dos principais recursos disponíveis na <xref:System.Windows.Forms.DataGridView> que estão faltando do controle a <xref:System.Windows.Forms.DataGrid> controle.  
  
|Recurso de controle DataGridView|Descrição|  
|----------------------------------|-----------------|  
|Vários tipos de coluna|O <xref:System.Windows.Forms.DataGridView> controle fornece tipos de coluna mais internos que o <xref:System.Windows.Forms.DataGrid> controle. Esses tipos de coluna atender às necessidades dos cenários mais comuns, mas também são mais fáceis de estender ou substituir que os tipos de coluna no <xref:System.Windows.Forms.DataGrid> controle. Para obter mais informações, consulte [Tipos de coluna no controle DataGridView dos Windows Forms](column-types-in-the-windows-forms-datagridview-control.md).|  
|Várias maneiras de exibir dados|O <xref:System.Windows.Forms.DataGrid> controle está limitado a exibir dados de uma fonte de dados externa. O <xref:System.Windows.Forms.DataGridView> controle, no entanto, pode exibir os dados não associados armazenados no controle, dados de uma fonte de dados associada ou dados associados e não associados juntos. Você também pode implementar o modo virtual no <xref:System.Windows.Forms.DataGridView> controle para fornecer gerenciamento de dados personalizado. Para obter mais informações, consulte [Modos de exibição dos dados no controle DataGridView dos Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md).|  
|Várias maneiras de personalizar a exibição de dados|O <xref:System.Windows.Forms.DataGridView> controle fornece muitas propriedades e eventos que permitem que você especifique como os dados são formatados e exibidos. Por exemplo, você pode alterar a aparência de células, linhas e colunas dependendo dos dados que elas contêm ou pode substituir os dados de um tipo de dados por dados equivalente de outro tipo. Para obter mais informações, consulte [Formatação de dados no controle DataGridView dos Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md).|  
|Várias opções para alterar o comportamento e a aparência de célula, linha, coluna e cabeçalho|O <xref:System.Windows.Forms.DataGridView> controle permite que você trabalhe com componentes de grade individuais de várias maneiras. Por exemplo, você pode congelar linhas e colunas para evitar que elas rolem; ocultar linhas, colunas e cabeçalhos; alterar o modo como os tamanhos de linha, coluna e cabeçalho são ajustados; alterar a maneira como os usuários fazem seleções; e fornecer Dicas de Ferramentas e menus de atalho para células, linhas e colunas individuais.|  
  
 O <xref:System.Windows.Forms.DataGrid> controle é mantido para compatibilidade com versões anteriores e para necessidades especiais. Para quase todas as finalidades, você deve usar o <xref:System.Windows.Forms.DataGridView> controle. O único recurso que está disponível na <xref:System.Windows.Forms.DataGrid> controle que não está disponível no <xref:System.Windows.Forms.DataGridView> controle é a exibição hierárquica de informações de duas tabelas relacionadas em um único controle. Você deve usar dois <xref:System.Windows.Forms.DataGridView> controles para exibir informações de duas tabelas que estão em uma relação mestre/detalhes.  
  
## <a name="upgrading-to-the-datagridview-control"></a>Atualizando para o controle DataGridView  
 Se você tiver aplicativos existentes que usam o <xref:System.Windows.Forms.DataGrid> controle em um cenário de associação de dados simples sem personalizações, você pode simplesmente substituir o antigo controle com o novo controle. Ambos os controles usam a arquitetura de vinculação de dados padrão do Windows Forms, portanto, o <xref:System.Windows.Forms.DataGridView> controle exibirá os dados associados sem nenhuma configuração adicional necessária. Você talvez queira considerar aproveitar os aprimoramentos de associação de dados, no entanto, associando os dados para um <xref:System.Windows.Forms.BindingSource> componente, que, em seguida, você pode associar ao <xref:System.Windows.Forms.DataGridView> controle. Para obter mais informações, consulte [Componente BindingSource](bindingsource-component.md).  
  
 Porque o <xref:System.Windows.Forms.DataGridView> controle tem uma arquitetura totalmente nova, não há nenhum caminho simples de conversão que permite que você use <xref:System.Windows.Forms.DataGrid> personalizações com o <xref:System.Windows.Forms.DataGridView> controle. Muitas <xref:System.Windows.Forms.DataGrid> personalizações são desnecessárias com o <xref:System.Windows.Forms.DataGridView> controlar, no entanto, devido a recursos internos disponíveis no novo controle. Se você tiver criado tipos de coluna personalizados para o <xref:System.Windows.Forms.DataGrid> controle que você deseja usar com o <xref:System.Windows.Forms.DataGridView> controle, você precisará implementá-los novamente usando a nova arquitetura. Para obter mais informações, consulte [Personalizando o controle DataGridView dos Windows Forms](customizing-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.BindingSource>
- [Controle DataGridView](datagridview-control-windows-forms.md)
- [Controle DataGrid](datagrid-control-windows-forms.md)
- [Componente BindingSource](bindingsource-component.md)
- [Tipos de coluna no controle DataGridView dos Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
- [Estilos de célula no controle DataGridView do Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Modos de exibição dos dados no controle DataGridView do Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Formatação de dados no controle DataGridView dos Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md)
- [Sizing Options in the Windows Forms DataGridView Control](sizing-options-in-the-windows-forms-datagridview-control.md) (Opções de dimensionamento no controle DataGridView dos Windows Forms)
- [Modos de classificação da coluna no controle DataGridView dos Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Modos de seleção no controle DataGridView dos Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md)
- [Personalizando o controle DataGridView dos Windows Forms](customizing-the-windows-forms-datagridview-control.md)
