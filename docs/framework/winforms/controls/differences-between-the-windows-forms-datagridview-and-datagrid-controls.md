---
title: Diferenças entre os controles DataGridView e DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: 3552abe55d8e2c1cb4ae372ca64c7ca21f1fed0e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745961"
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Diferenças entre os controles DataGridView e DataGrid dos Windows Forms
O controle de <xref:System.Windows.Forms.DataGridView> é um novo controle que substitui o controle de <xref:System.Windows.Forms.DataGrid>. O controle de <xref:System.Windows.Forms.DataGridView> fornece vários recursos básicos e avançados que estão faltando no controle de <xref:System.Windows.Forms.DataGrid>. Além disso, a arquitetura do controle de <xref:System.Windows.Forms.DataGridView> torna muito mais fácil estender e personalizar do que o controle de <xref:System.Windows.Forms.DataGrid>.  
  
 A tabela a seguir descreve alguns dos principais recursos disponíveis no controle de <xref:System.Windows.Forms.DataGridView> que estão faltando no controle de <xref:System.Windows.Forms.DataGrid>.  
  
|Recurso de controle DataGridView|Descrição|  
|----------------------------------|-----------------|  
|Vários tipos de coluna|O controle de <xref:System.Windows.Forms.DataGridView> fornece mais tipos de coluna internos do que o controle de <xref:System.Windows.Forms.DataGrid>. Esses tipos de coluna atendem às necessidades dos cenários mais comuns, mas também são mais fáceis de estender ou substituir do que os tipos de coluna no controle de <xref:System.Windows.Forms.DataGrid>. Para obter mais informações, consulte [Tipos de coluna no controle DataGridView dos Windows Forms](column-types-in-the-windows-forms-datagridview-control.md).|  
|Várias maneiras de exibir dados|O controle de <xref:System.Windows.Forms.DataGrid> é limitado à exibição de dados de uma fonte de dados externa. O controle de <xref:System.Windows.Forms.DataGridView>, no entanto, pode exibir dados desvinculados armazenados no controle, dados de uma fonte de dados ligada ou dados vinculados e desvinculados juntos. Você também pode implementar o modo virtual no controle de <xref:System.Windows.Forms.DataGridView> para fornecer gerenciamento de dados personalizado. Para obter mais informações, consulte [Modos de exibição dos dados no controle DataGridView dos Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md).|  
|Várias maneiras de personalizar a exibição de dados|O controle <xref:System.Windows.Forms.DataGridView> fornece muitas propriedades e eventos que permitem especificar como os dados são formatados e exibidos. Por exemplo, você pode alterar a aparência de células, linhas e colunas dependendo dos dados que elas contêm ou pode substituir os dados de um tipo de dados por dados equivalente de outro tipo. Para obter mais informações, consulte [Formatação de dados no controle DataGridView dos Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md).|  
|Várias opções para alterar o comportamento e a aparência de célula, linha, coluna e cabeçalho|O controle de <xref:System.Windows.Forms.DataGridView> permite que você trabalhe com componentes individuais de grade de várias maneiras. Por exemplo, você pode congelar linhas e colunas para evitar que elas rolem; ocultar linhas, colunas e cabeçalhos; alterar o modo como os tamanhos de linha, coluna e cabeçalho são ajustados; alterar a maneira como os usuários fazem seleções; e fornecer Dicas de Ferramentas e menus de atalho para células, linhas e colunas individuais.|  
  
 O controle de <xref:System.Windows.Forms.DataGrid> é retido para compatibilidade com versões anteriores e necessidades especiais. Para quase todas as finalidades, você deve usar o controle <xref:System.Windows.Forms.DataGridView>. O único recurso que está disponível no controle de <xref:System.Windows.Forms.DataGrid> que não está disponível no controle de <xref:System.Windows.Forms.DataGridView> é a exibição hierárquica das informações de duas tabelas relacionadas em um único controle. Você deve usar dois controles de <xref:System.Windows.Forms.DataGridView> para exibir informações de duas tabelas que estão em uma relação mestre/detalhes.  
  
## <a name="upgrading-to-the-datagridview-control"></a>Atualizando para o controle DataGridView  
 Se você tiver aplicativos existentes que usam o controle de <xref:System.Windows.Forms.DataGrid> em um cenário simples vinculado a dados sem personalizações, você pode simplesmente substituir o controle antigo pelo novo controle. Ambos os controles usam a arquitetura de ligação de dados do Windows Forms padrão, de modo que o controle de <xref:System.Windows.Forms.DataGridView> exibirá os dados associados sem a necessidade de configuração adicional. No entanto, talvez você queira aproveitar as melhorias de vinculação de dados, ligando seus dados a um componente <xref:System.Windows.Forms.BindingSource>, que você pode associar ao controle <xref:System.Windows.Forms.DataGridView>. Para obter mais informações, consulte [Componente BindingSource](bindingsource-component.md).  
  
 Como o controle de <xref:System.Windows.Forms.DataGridView> tem uma arquitetura totalmente nova, não há nenhum caminho de conversão direto que permitirá que você use <xref:System.Windows.Forms.DataGrid> personalizações com o controle de <xref:System.Windows.Forms.DataGridView>. Muitas <xref:System.Windows.Forms.DataGrid> personalizações são desnecessárias com o controle de <xref:System.Windows.Forms.DataGridView>, no entanto, devido aos recursos internos disponíveis no novo controle. Se você tiver criado tipos de coluna personalizados para o controle de <xref:System.Windows.Forms.DataGrid> que deseja usar com o controle de <xref:System.Windows.Forms.DataGridView>, precisará implementá-los novamente usando a nova arquitetura. Para obter mais informações, consulte [Personalizando o controle DataGridView dos Windows Forms](customizing-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.BindingSource>
- [Controle DataGridView](datagridview-control-windows-forms.md)
- [Controle DataGrid](datagrid-control-windows-forms.md)
- [Componente BindingSource](bindingsource-component.md)
- [Tipos de coluna no controle DataGridView dos Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
- [Estilos de Célula no Controle DataGridView dos Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Modos de exibição de dados no controle DataGridView dos Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Formatação de dados no controle DataGridView dos Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md)
- [Sizing Options in the Windows Forms DataGridView Control](sizing-options-in-the-windows-forms-datagridview-control.md) (Opções de dimensionamento no controle DataGridView dos Windows Forms)
- [Modos de classificação da coluna no controle DataGridView dos Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Modos de seleção no controle DataGridView dos Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md)
- [Personalizando o controle DataGridView do Windows Forms](customizing-the-windows-forms-datagridview-control.md)
