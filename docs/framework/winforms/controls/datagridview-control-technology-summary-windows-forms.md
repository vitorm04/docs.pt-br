---
title: Resumo de tecnologia do controle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- data grids [Windows Forms], about data grids
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
ms.openlocfilehash: 18eebd067df9768e14cc81258184551d00dd1402
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742484"
---
# <a name="datagridview-control-technology-summary-windows-forms"></a>Resumo de tecnologia do controle DataGridView (Windows Forms)
Este tópico resume as informações sobre o controle `DataGridView` e as classes que dão suporte ao seu uso.  
  
 Exibir dados em um formato tabular é uma tarefa que provavelmente será executada com frequência. O controle `DataGridView` foi projetado para ser uma solução completa para apresentar dados em uma grade.  
  
## <a name="keywords"></a>Palavras-chave  
 DataGridView, BindingSource, tabela, célula, vinculação de dados, modo virtual  
  
## <a name="namespaces"></a>{1&gt;Namespaces&lt;1}  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
 <xref:System.Data?displayProperty=nameWithType>  
  
## <a name="related-technologies"></a>Tecnologias Relacionadas  
 `BindingSource`  
  
## <a name="background"></a>Segundo Plano  
 Designers de interface do usuário com frequência consideram necessário exibir dados tabulares para os usuários. O .NET Framework fornece várias maneiras de mostrar dados em uma tabela ou grade. O controle `DataGridView` representa a mais recente evolução dessa tecnologia para aplicativos dos Windows Forms.  
  
 O controle `DataGridView` pode exibir linhas de dados de um armazenamento de dados. Há suporte para muitos tipos de armazenamentos de dados. O armazenamento de dados pode conter dados simples e não tipados, como uma matriz unidimensional, ou pode conter dados digitados, como um <xref:System.Data.DataSet>. Para obter mais informações, consulte [Como associar dados ao controle DataGridView dos Windows Forms](how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 O controle de `DataGridView` fornece uma maneira poderosa e flexível para exibir dados em um formato de tabela. Você pode usar o controle para mostrar exibições editáveis ou somente leitura de conjuntos de dados pequenos a muito grandes.  
  
 Você pode estender o controle `DataGridView` de várias maneiras para integrar comportamento personalizado em seus aplicativos. Por exemplo, você pode especificar seus próprios algoritmos de classificação com programação, podendo também criar seus próprios tipos de células. É possível personalizar facilmente a aparência do controle `DataGridView` escolhendo dentre várias propriedades. Muitos tipos de armazenamentos de dados podem ser usados como uma fonte de dados ou o controle `DataGridView` pode operar sem nenhuma fonte de dados associada.  
  
## <a name="implementing-datagridview-classes"></a>Implementando classes de DataGridView  
 Há várias maneiras de aproveitar os recursos de extensibilidade do controle `DataGridView`. Você pode personalizar vários aspectos do controle por meio de propriedades e eventos, mas algumas personalizações requerem a criação de novas classes derivadas de classes `DataGridView` existentes.  
  
 Em geral, as classes base mais usadas são `DataGridViewCell` e `DataGridViewColumn`. Você pode derivar sua própria classe de célula de `DataGridViewCell` ou qualquer uma das suas classes filho. Embora você possa adicionar qualquer tipo de célula a qualquer coluna, normalmente também derivará uma classe de coluna complementar da `DataGridViewColumn` que hospeda as células do seu tipo de célula personalizado por padrão.  
  
 Você pode implementar a interface `IDataGridViewEditingCell` em sua classe de célula derivada para criar um tipo de célula que tenha a funcionalidade de edição, mas que não hospede um controle no modo de edição. Para criar um controle que você pode hospedar em uma célula no modo de edição, você pode implementar a interface `IDataGridViewEditingControl` em uma classe derivada de <xref:System.Windows.Forms.Control>.  
  
 Para obter mais informações, consulte [Como personalizar células e colunas no controle DataGridView dos Windows Forms estendendo o comportamento e aparência](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md) e [Como hospedar controles em células DataGridView dos Windows Forms](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="datagridview-classes-at-a-glance"></a>Visão geral das classes DataGridView  
 <xref:System.Windows.Forms>  
  
|Área de Tecnologia|Elementos de classes/interfaces/configuração|  
|---------------------|-------------------------------------------------|  
|Associação de dados|<xref:System.Windows.Forms.BindingSource>|  
|Apresentação de dados|<xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DataGridViewCell> e classes derivadas<br /><br /> <xref:System.Windows.Forms.DataGridViewRow> e classes derivadas<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> e classes derivadas<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|Extensibilidade de <xref:System.Windows.Forms.DataGridView>|<xref:System.Windows.Forms.DataGridViewCell> e classes derivadas<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> e classes derivadas<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## <a name="whats-new"></a>O Que Há de Novo  
 O controle <xref:System.Windows.Forms.DataGridView> foi projetado para ser uma solução completa para exibir dados tabulares com Windows Forms. Você deve considerar o uso do controle de <xref:System.Windows.Forms.DataGridView> antes de outras soluções, como <xref:System.Windows.Forms.DataGrid>, quando você estiver criando um novo aplicativo. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 O controle de <xref:System.Windows.Forms.DataGridView> pode funcionar em conjunto próximo com o componente <xref:System.Windows.Forms.BindingSource>. Esse componente é projetado para ser a fonte de dados principal de um formulário. Ele pode gerenciar a interação entre um controle de <xref:System.Windows.Forms.DataGridView> e sua fonte de dados, independentemente do tipo de fonte de dados.  
  
## <a name="see-also"></a>Veja também

- [Visão geral do controle DataGridView](datagridview-control-overview-windows-forms.md)
- [Arquitetura de controle DataGridView](datagridview-control-architecture-windows-forms.md)
- [Protegendo informações de conexão](../../data/adonet/protecting-connection-information.md)
