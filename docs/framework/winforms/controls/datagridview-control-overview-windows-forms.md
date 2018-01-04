---
title: "Visão geral do controle DataGridView (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DataGridView
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- grid controls [Windows Forms]
- tables [Windows Forms], displaying in DataGridView control
- tables [Windows Forms], binding to DataGridView control
- columns [Windows Forms], DataGridView control
- bound controls [Windows Forms], dataGridView control
- datasets [Windows Forms], binding to DataGridView control
- data grids [Windows Forms], about data grids
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- grids [Windows Forms]
- data binding [Windows Forms], DataGridView control
- data sources [Windows Forms], binding to DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6d9cc6568813af866acaf20696b870bedc3099be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="datagridview-control-overview-windows-forms"></a>Visão geral do controle DataGridView (Windows Forms)
> [!NOTE]
>  O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Com o <xref:System.Windows.Forms.DataGridView> controle, você pode exibir e editar dados tabulares de muitos tipos diferentes de fontes de dados.  
  
 Associação de dados para o <xref:System.Windows.Forms.DataGridView> controle é simples e intuitiva e, em muitos casos, ele é tão simple quanto a configuração do <xref:System.Windows.Forms.DataGridView.DataSource%2A> propriedade. Quando você associa a uma fonte de dados que contém várias listas ou tabelas, defina o <xref:System.Windows.Forms.DataGridView.DataMember%2A> uma cadeia de caracteres que especifica a lista ou tabela para associar à propriedade.  
  
 O <xref:System.Windows.Forms.DataGridView> controle oferece suporte para o modelo de associação de dados formulários do Windows padrão, portanto ele associará a instâncias das classes descritas na lista a seguir:  
  
-   Qualquer classe que implementa o <xref:System.Collections.IList> interface, inclusive matrizes unidimensionais.  
  
-   Qualquer classe que implementa o <xref:System.ComponentModel.IListSource> interface, como o <xref:System.Data.DataTable> e <xref:System.Data.DataSet> classes.  
  
-   Qualquer classe que implementa o <xref:System.ComponentModel.IBindingList> interface, como o <xref:System.ComponentModel.BindingList%601> classe.  
  
-   Qualquer classe que implementa o <xref:System.ComponentModel.IBindingListView> interface, como o <xref:System.Windows.Forms.BindingSource> classe.  
  
 O <xref:System.Windows.Forms.DataGridView> controle oferece suporte à associação de dados para as propriedades públicas de objetos retornados por essas interfaces ou à coleção de propriedades retornado por um <xref:System.ComponentModel.ICustomTypeDescriptor> interface, se implementado em objetos retornados.  
  
 Normalmente, você associará a uma <xref:System.Windows.Forms.BindingSource> componente e vincular o <xref:System.Windows.Forms.BindingSource> componente para outra fonte de dados ou preenchê-la com objetos de negócios. O <xref:System.Windows.Forms.BindingSource> componente é a fonte de dados preferencial porque ele pode ser associado a uma ampla variedade de fontes de dados e pode resolver vários problemas de associação de dados automaticamente. Para obter mais informações, consulte [Componente BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md).  
  
 O <xref:System.Windows.Forms.DataGridView> controle também pode ser usado em *desassociado* modo, com nenhum armazenamento de dados subjacente. Para obter um exemplo de código que usa um desassociado <xref:System.Windows.Forms.DataGridView> , consulte [passo a passo: Criando um controle DataGridView do Windows Forms não associados](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
 O <xref:System.Windows.Forms.DataGridView> controle é altamente configurável e extensível, e fornece muitas propriedades, métodos e eventos para personalizar sua aparência e comportamento. Quando você quiser que seu aplicativo do Windows Forms para exibir dados de tabela, considere o uso de <xref:System.Windows.Forms.DataGridView> controle antes de outros (por exemplo, <xref:System.Windows.Forms.DataGrid>). Se você estiver exibindo uma pequena grade valores somente leitura, ou se você estiver habilitando um usuário editar uma tabela com milhões de registros, o <xref:System.Windows.Forms.DataGridView> controle fornece uma solução eficiente de memória prontamente programável.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Resumo de tecnologia do controle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-technology-summary-windows-forms.md)  
 Resume <xref:System.Windows.Forms.DataGridView> controlar o uso de classes relacionadas e conceitos.  
  
 [Arquitetura de controle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 Descreve a arquitetura do <xref:System.Windows.Forms.DataGridView> controle, explicando sua estrutura de hierarquia e herança de tipo.  
  
 [Cenários do controle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-scenarios-windows-forms.md)  
 Descreve os cenários mais comuns no qual <xref:System.Windows.Forms.DataGridView> controles são usados.  
  
 [Diretório de código do controle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-code-directory-windows-forms.md)  
 Fornece links para exemplos de código na documentação para vários <xref:System.Windows.Forms.DataGridView> tarefas. Esses exemplos são categorizados por tipo de tarefa.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Tipos de coluna no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 Descreve os tipos de coluna em Windows Forms <xref:System.Windows.Forms.DataGridView> usado para exibir informações e permitir que os usuários modificar ou adicionar informações de controle.  
  
 [Exibindo dados no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 Fornece tópicos que descrevem como preencher o controle com os dados manualmente ou de uma fonte de dados externa.  
  
 [Personalizando o controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 Fornece tópicos que descrevem a pintura personalizada de células e linhas <xref:System.Windows.Forms.DataGridView>, bem como a criação de tipos de célula, coluna e linha derivados.  
  
 [Ajuste de desempenho no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Apresenta tópicos que descrevem como usar o controle com eficiência para evitar problemas de desempenho ao trabalhar com grandes volumes de dados.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Controle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Funcionalidade padrão no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 [Tratamento de teclado e mouse padrão no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
