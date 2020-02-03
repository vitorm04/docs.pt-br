---
title: Visão geral do controle DataGridView
ms.date: 03/30/2017
f1_keywords:
- DataGridView
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
ms.openlocfilehash: 74de5b449525be9ff93fcbef0ddabd041470177c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742488"
---
# <a name="datagridview-control-overview-windows-forms"></a>Visão geral do controle DataGridView (Windows Forms)
> [!NOTE]
> O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Com o controle <xref:System.Windows.Forms.DataGridView>, você pode exibir e editar dados tabulares de vários tipos diferentes de fontes de dados.  
  
 Associar dados ao controle de <xref:System.Windows.Forms.DataGridView> é simples e intuitivo e, em muitos casos, é tão simples quanto definir a propriedade <xref:System.Windows.Forms.DataGridView.DataSource%2A>. Quando você se associa a uma fonte de dados que contém várias listas ou tabelas, defina a propriedade <xref:System.Windows.Forms.DataGridView.DataMember%2A> como uma cadeia de caracteres que especifica a lista ou tabela à qual associar.  
  
 O controle <xref:System.Windows.Forms.DataGridView> dá suporte ao modelo de ligação de dados do Windows Forms padrão, portanto, ele se associará a instâncias de classes descritas na lista a seguir:  
  
- Qualquer classe que implemente a interface <xref:System.Collections.IList>, incluindo matrizes unidimensionais.  
  
- Qualquer classe que implemente a interface <xref:System.ComponentModel.IListSource>, como as classes <xref:System.Data.DataTable> e <xref:System.Data.DataSet>.  
  
- Qualquer classe que implemente a interface <xref:System.ComponentModel.IBindingList>, como a classe <xref:System.ComponentModel.BindingList%601>.  
  
- Qualquer classe que implemente a interface <xref:System.ComponentModel.IBindingListView>, como a classe <xref:System.Windows.Forms.BindingSource>.  
  
 O controle <xref:System.Windows.Forms.DataGridView> dá suporte à vinculação de dados para as propriedades públicas dos objetos retornados por essas interfaces ou à coleção Properties retornada por uma interface <xref:System.ComponentModel.ICustomTypeDescriptor>, se implementada nos objetos retornados.  
  
 Normalmente, você se associará a um componente <xref:System.Windows.Forms.BindingSource> e associará o componente <xref:System.Windows.Forms.BindingSource> a outra fonte de dados ou o preencherá com objetos comerciais. O componente de <xref:System.Windows.Forms.BindingSource> é a fonte de dados preferida porque ele pode ser associado a uma ampla variedade de fontes de dados e pode resolver vários problemas de ligação de dados automaticamente. Para obter mais informações, consulte [Componente BindingSource](bindingsource-component.md).  
  
 O controle de <xref:System.Windows.Forms.DataGridView> também pode ser usado no modo não *associado* , sem nenhum armazenamento de dados subjacente. Para obter um exemplo de código que usa um controle de <xref:System.Windows.Forms.DataGridView> não associado, consulte [Walkthrough: Criando um controle DataGridView de Windows Forms não associado](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
 O controle de <xref:System.Windows.Forms.DataGridView> é altamente configurável e extensível e fornece muitas propriedades, métodos e eventos para personalizar sua aparência e comportamento. Quando você quiser que seu aplicativo Windows Forms exiba dados tabulares, considere usar o controle de <xref:System.Windows.Forms.DataGridView> antes de outros (por exemplo, <xref:System.Windows.Forms.DataGrid>). Se você estiver exibindo uma pequena grade de valores somente leitura ou se estiver permitindo que um usuário edite uma tabela com milhões de registros, o controle de <xref:System.Windows.Forms.DataGridView> fornecerá uma solução prontamente programável e com economia de memória.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Resumo de tecnologia do controle DataGridView](datagridview-control-technology-summary-windows-forms.md)  
 Resume <xref:System.Windows.Forms.DataGridView> conceitos de controle e o uso de classes relacionadas.  
  
 [Arquitetura de controle DataGridView](datagridview-control-architecture-windows-forms.md)  
 Descreve a arquitetura do controle de <xref:System.Windows.Forms.DataGridView>, explicando sua hierarquia de tipos e estrutura de herança.  
  
 [Cenários do controle DataGridView](datagridview-control-scenarios-windows-forms.md)  
 Descreve os cenários mais comuns nos quais os controles de <xref:System.Windows.Forms.DataGridView> são usados.  
  
 [Diretório de código do controle DataGridView](datagridview-control-code-directory-windows-forms.md)  
 Fornece links para exemplos de código na documentação para várias tarefas de <xref:System.Windows.Forms.DataGridView>. Esses exemplos são categorizados por tipo de tarefa.  
  
## <a name="related-sections"></a>Seções Relacionadas  
 [Tipos de coluna no controle DataGridView do Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)  
 Discute os tipos de coluna no controle de <xref:System.Windows.Forms.DataGridView> Windows Forms usado para exibir informações e permitir que os usuários modifiquem ou adicionem informações.  
  
 [Exibindo dados no controle DataGridView do Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)  
 Fornece tópicos que descrevem como preencher o controle com os dados manualmente ou de uma fonte de dados externa.  
  
 [Personalizando o controle DataGridView do Windows Forms](customizing-the-windows-forms-datagridview-control.md)  
 Fornece tópicos que descrevem a pintura personalizada de células e linhas <xref:System.Windows.Forms.DataGridView>, bem como a criação de tipos de célula, coluna e linha derivados.  
  
 [Ajuste de desempenho no controle DataGridView do Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Apresenta tópicos que descrevem como usar o controle com eficiência para evitar problemas de desempenho ao trabalhar com grandes volumes de dados.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Controle DataGridView](datagridview-control-windows-forms.md)
- [Funcionalidade padrão no controle DataGridView do Windows Forms](default-functionality-in-the-windows-forms-datagridview-control.md)
- [Tratamento de teclado e mouse padrão no controle DataGridView do Windows Forms](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
