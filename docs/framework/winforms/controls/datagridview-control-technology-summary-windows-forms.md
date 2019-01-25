---
title: Resumo de tecnologia do controle DataGridView (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- data grids [Windows Forms], about data grids
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
ms.openlocfilehash: efa567e6f8a91b40d2710b4cef0d1a56d38650c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737826"
---
# <a name="datagridview-control-technology-summary-windows-forms"></a>Resumo de tecnologia do controle DataGridView (Windows Forms)
Este tópico resume as informações sobre o controle `DataGridView` e as classes que dão suporte ao seu uso.  
  
 Exibir dados em um formato tabular é uma tarefa que provavelmente será executada com frequência. O controle `DataGridView` foi projetado para ser uma solução completa para apresentar dados em uma grade.  
  
## <a name="keywords"></a>Palavras-chave  
 DataGridView, BindingSource, tabela, célula, vinculação de dados, modo virtual  
  
## <a name="namespaces"></a>Namespaces  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
 <xref:System.Data?displayProperty=nameWithType>  
  
## <a name="related-technologies"></a>Tecnologias Relacionadas  
 `BindingSource`  
  
## <a name="background"></a>Informações preliminares  
 Designers de interface do usuário com frequência consideram necessário exibir dados tabulares para os usuários. O [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] fornece várias maneiras de exibir dados em uma tabela ou grade. O controle `DataGridView` representa a mais recente evolução dessa tecnologia para aplicativos dos Windows Forms.  
  
 O controle `DataGridView` pode exibir linhas de dados de um armazenamento de dados. Há suporte para muitos tipos de armazenamentos de dados. O armazenamento de dados pode conter dados simples, sem tipo, como uma matriz unidimensional, ou ele pode conter dados tipados, como um <xref:System.Data.DataSet>. Para obter mais informações, confira [Como: Associar dados para o Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 O controle de `DataGridView` fornece uma maneira poderosa e flexível para exibir dados em um formato de tabela. Você pode usar o controle para mostrar exibições editáveis ou somente leitura de conjuntos de dados pequenos a muito grandes.  
  
 Você pode estender o controle `DataGridView` de várias maneiras para integrar comportamento personalizado em seus aplicativos. Por exemplo, você pode especificar programaticamente seus próprios algoritmos de classificação e criar seus próprios tipos de células. É possível personalizar facilmente a aparência do controle `DataGridView` escolhendo entre várias propriedades. Muitos tipos de armazenamentos de dados podem ser usados como uma fonte de dados ou o controle `DataGridView` pode operar sem nenhuma fonte de dados associada.  
  
## <a name="implementing-datagridview-classes"></a>Implementando classes de DataGridView  
 Há várias maneiras de aproveitar os recursos de extensibilidade do controle `DataGridView`. Você pode personalizar vários aspectos do controle por meio de propriedades e eventos, mas algumas personalizações requerem a criação de novas classes derivadas de classes `DataGridView` existentes.  
  
 Em geral, as classes base mais usadas são `DataGridViewCell` e `DataGridViewColumn`. Você pode derivar sua própria classe de célula de `DataGridViewCell` ou qualquer uma das suas classes filho. Embora você possa adicionar qualquer tipo de célula a qualquer coluna, normalmente também derivará uma classe de coluna complementar da `DataGridViewColumn` que hospeda as células do seu tipo de célula personalizado por padrão.  
  
 Você pode implementar a interface `IDataGridViewEditingCell` em sua classe de célula derivada para criar um tipo de célula que tenha a funcionalidade de edição, mas que não hospede um controle no modo de edição. Para criar um controle que podem ser hospedados em uma célula no modo de edição, você pode implementar o `IDataGridViewEditingControl` interface em uma classe derivada de <xref:System.Windows.Forms.Control>.  
  
 Para obter mais informações, confira [Como: Personalizar células e colunas no Windows Forms DataGridView Control estendendo o comportamento e aparência](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md) e [como: Hospedar controles em Windows Forms células DataGridView](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="datagridview-classes-at-a-glance"></a>Visão geral das classes DataGridView  
 <xref:System.Windows.Forms>  
  
|Área de Tecnologia|Elementos de classes/interfaces/configuração|  
|---------------------|-------------------------------------------------|  
|Associação de dados|<xref:System.Windows.Forms.BindingSource>|  
|Apresentação de dados|<xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DataGridViewCell> e classes derivadas<br /><br /> <xref:System.Windows.Forms.DataGridViewRow> e classes derivadas<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> e classes derivadas<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|<xref:System.Windows.Forms.DataGridView> Extensibilidade|<xref:System.Windows.Forms.DataGridViewCell> e classes derivadas<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> e classes derivadas<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## <a name="whats-new"></a>O Que Há de Novo  
 O <xref:System.Windows.Forms.DataGridView> controle foi projetado para ser uma solução completa para exibir dados tabulares com Windows Forms. Você deve considerar usar o <xref:System.Windows.Forms.DataGridView> controlar antes de outras soluções, tais como <xref:System.Windows.Forms.DataGrid>, quando você estiver criando um novo aplicativo. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 O <xref:System.Windows.Forms.DataGridView> controle pode trabalhar em conjunto com o <xref:System.Windows.Forms.BindingSource> componente. Esse componente é projetado para ser a fonte de dados principal de um formulário. Ele pode gerenciar a interação entre um <xref:System.Windows.Forms.DataGridView> tipo de fonte de controle e sua fonte de dados, independentemente dos dados.  
  
## <a name="see-also"></a>Consulte também
- [Visão geral do controle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)
- [Arquitetura de controle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)
- [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md)
