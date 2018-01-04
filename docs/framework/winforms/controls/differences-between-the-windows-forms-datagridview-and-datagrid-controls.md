---
title: "Diferenças entre os controles DataGridView e DataGrid dos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3bc6d1fa2450d0aba52bd6a5a030c025fede0cb2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Diferenças entre os controles DataGridView e DataGrid dos Windows Forms
O <xref:System.Windows.Forms.DataGridView> o controle é um novo que substitui o <xref:System.Windows.Forms.DataGrid> controle. O <xref:System.Windows.Forms.DataGridView> controle fornece vários recursos básicos e avançados que estão faltando no <xref:System.Windows.Forms.DataGrid> controle. Além disso, a arquitetura do <xref:System.Windows.Forms.DataGridView> controle torna muito mais fácil de estender e personalizar o que o <xref:System.Windows.Forms.DataGrid> controle.  
  
 A tabela a seguir descreve alguns dos principais recursos disponíveis no <xref:System.Windows.Forms.DataGridView> que estão faltando do controle de <xref:System.Windows.Forms.DataGrid> controle.  
  
|Recurso de controle DataGridView|Descrição|  
|----------------------------------|-----------------|  
|Vários tipos de coluna|O <xref:System.Windows.Forms.DataGridView> controle fornece tipos de coluna mais internos que o <xref:System.Windows.Forms.DataGrid> controle. Esses tipos de coluna atende às necessidades da maioria dos cenários comuns, mas também são mais fáceis de estender ou substituir que os tipos de coluna no <xref:System.Windows.Forms.DataGrid> controle. Para obter mais informações, consulte [Tipos de coluna no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md).|  
|Várias maneiras de exibir dados|O <xref:System.Windows.Forms.DataGrid> controle está limitado a exibir dados de uma fonte de dados externa. O <xref:System.Windows.Forms.DataGridView> controle, no entanto, pode exibir dados não associados armazenados no controle, dados de uma fonte de dados associados ou dados acoplados e não acoplados juntos. Você também pode implementar o modo virtual no <xref:System.Windows.Forms.DataGridView> controle para fornecer gerenciamento de dados personalizados. Para obter mais informações, consulte [Modos de exibição dos dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md).|  
|Várias maneiras de personalizar a exibição de dados|O <xref:System.Windows.Forms.DataGridView> controle fornece muitas propriedades e eventos que permitem que você especifique como os dados são formatados e exibidos. Por exemplo, você pode alterar a aparência de células, linhas e colunas dependendo dos dados que elas contêm ou pode substituir os dados de um tipo de dados por dados equivalente de outro tipo. Para obter mais informações, consulte [Formatação de dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md).|  
|Várias opções para alterar o comportamento e a aparência de célula, linha, coluna e cabeçalho|O <xref:System.Windows.Forms.DataGridView> controle permite que você trabalhe com os componentes individuais de grade de várias maneiras. Por exemplo, você pode congelar linhas e colunas para evitar que elas rolem; ocultar linhas, colunas e cabeçalhos; alterar o modo como os tamanhos de linha, coluna e cabeçalho são ajustados; alterar a maneira como os usuários fazem seleções; e fornecer Dicas de Ferramentas e menus de atalho para células, linhas e colunas individuais.|  
  
 O <xref:System.Windows.Forms.DataGrid> controle é mantido para compatibilidade com versões anteriores e para necessidades especiais. Para quase todas as finalidades, você deve usar o <xref:System.Windows.Forms.DataGridView> controle. O recurso só está disponível na <xref:System.Windows.Forms.DataGrid> controle que não está disponível na <xref:System.Windows.Forms.DataGridView> controle é a exibição hierárquica de informações de duas tabelas relacionadas em um único controle. Você deve usar dois <xref:System.Windows.Forms.DataGridView> controles para exibir informações de duas tabelas que estão em uma relação mestre/detalhes.  
  
## <a name="upgrading-to-the-datagridview-control"></a>Atualizando para o controle DataGridView  
 Se você tiver aplicativos existentes que usam o <xref:System.Windows.Forms.DataGrid> controle em um cenário de associação de dados simples sem personalizações, você pode substituir o controle antigo com o novo controle. Ambos os controles usam a arquitetura de associação de dados padrão do Windows Forms, portanto, o <xref:System.Windows.Forms.DataGridView> controle exibirá os dados associados com nenhuma configuração adicional necessária. Você talvez queira considerar a tirar proveito dos aprimoramentos de associação de dados, no entanto, associando os dados para um <xref:System.Windows.Forms.BindingSource> componente, que, em seguida, você pode vincular ao <xref:System.Windows.Forms.DataGridView> controle. Para obter mais informações, consulte [Componente BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md).  
  
 Porque o <xref:System.Windows.Forms.DataGridView> controle tem uma arquitetura totalmente nova, não há nenhum caminho de conversão simples que permite que você use <xref:System.Windows.Forms.DataGrid> personalizações com o <xref:System.Windows.Forms.DataGridView> controle. Muitos <xref:System.Windows.Forms.DataGrid> personalizações são desnecessárias com o <xref:System.Windows.Forms.DataGridView> controlar, no entanto, devido os recursos internos disponíveis no novo controle. Se você tiver criado tipos de coluna personalizada para o <xref:System.Windows.Forms.DataGrid> controle que você deseja usar com o <xref:System.Windows.Forms.DataGridView> controle, você precisará implementá-los novamente usando a nova arquitetura. Para obter mais informações, consulte [Personalizando o controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGrid>  
 <xref:System.Windows.Forms.BindingSource>  
 [Controle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Controle DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Componente BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Tipos de coluna no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 [Estilos de célula no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Modos de exibição dos dados no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)  
 [Formatação de dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)  
 [Sizing Options in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md) (Opções de dimensionamento no controle DataGridView dos Windows Forms)  
 [Modos de classificação da coluna no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [Modos de seleção no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)  
 [Personalizando o controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
