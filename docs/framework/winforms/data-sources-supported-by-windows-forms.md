---
title: Fontes de dados com suporte
ms.date: 03/30/2017
helpviewer_keywords:
- collections [Windows Forms], binding to
- OLE DB providers [Windows Forms], Windows Forms
- DataTable class [Windows Forms], binding and Windows Forms
- Windows Forms, data binding
- DataView class [Windows Forms], binding and Windows Forms
- DataViewManager class [Windows Forms], binding and Windows Forms
- Windows Forms, source data
- arrays [Windows Forms]
- data sources [Windows Forms]
- data providers [Windows Forms]
- DataSet class [Windows Forms], binding and Windows Forms
- data [Windows Forms], data providers
ms.assetid: 3d2c43f6-462b-4d35-9c86-13e9afe012e1
ms.openlocfilehash: 83ce4bb0d6f0bf81bcad4e38af212dccc3483ca5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742306"
---
# <a name="data-sources-supported-by-windows-forms"></a>Fontes de dados com suporte do Windows Forms
Tradicionalmente, a associação de dados era usada nos aplicativos para tirar proveito dos dados armazenados em bancos de dados. Com a associação de dados do Windows Forms, você pode acessar dados de bancos de dados, bem como dados em outras estruturas, como matrizes e coleções, desde que certos requisitos mínimos sejam atendidos.  
  
## <a name="structures-to-bind-to"></a>Estruturas às quais associar  
 No Windows Forms, é possível associar a uma grande variedade de estruturas, desde objetos simples (associação simples) a listas complexas como tabelas de dados do ADO.NET (associação complexa). Para a associação simples, o Windows Forms dá suporte à associação às propriedades públicas no objeto simples. Windows Forms associação baseada em lista geralmente requer que o objeto dê suporte à interface <xref:System.Collections.IList> ou à interface <xref:System.ComponentModel.IListSource>. Além disso, se você estiver ligando com um componente <xref:System.Windows.Forms.BindingSource>, você poderá associar a um objeto que dá suporte à interface <xref:System.Collections.IEnumerable>. Para obter mais informações sobre interfaces relacionadas à associação de dados, consulte [Interfaces relacionadas à associação de dados](interfaces-related-to-data-binding.md).  
  
 A lista a seguir mostra as estruturas a que você pode associar no Windows Forms.  
  
 <xref:System.Windows.Forms.BindingSource>  
 Uma <xref:System.Windows.Forms.BindingSource> é a fonte de dados Windows Forms mais comum e atua como um proxy entre uma fonte de dados e os controles de Windows Forms. O padrão de uso geral de <xref:System.Windows.Forms.BindingSource> é associar os controles ao <xref:System.Windows.Forms.BindingSource> e associar os <xref:System.Windows.Forms.BindingSource> à fonte de dados (por exemplo, uma tabela de dados ADO.NET ou um objeto comercial). O <xref:System.Windows.Forms.BindingSource> fornece serviços que habilitam e melhoram o nível de suporte de vinculação de dados. Por exemplo, Windows Forms controles baseados em lista, como o <xref:System.Windows.Forms.DataGridView> e <xref:System.Windows.Forms.ComboBox>, não dão suporte diretamente à associação para <xref:System.Collections.IEnumerable> fontes de dados no entanto, você pode habilitar esse cenário ligando-se por meio de um <xref:System.Windows.Forms.BindingSource>. Nesse caso, o <xref:System.Windows.Forms.BindingSource> converterá a fonte de dados em um <xref:System.Collections.IList>.  
  
 Objetos simples  
 Windows Forms dá suporte a propriedades de controle de ligação de dados para propriedades públicas na instância de um objeto usando o tipo <xref:System.Windows.Forms.Binding>. Windows Forms também dá suporte a controles baseados em lista de associação, como um <xref:System.Windows.Forms.ListControl> a uma instância de objeto quando um <xref:System.Windows.Forms.BindingSource> é usado.  
  
 Matriz ou coleção  
 Para atuar como uma fonte de dados, uma lista deve implementar a interface <xref:System.Collections.IList>; um exemplo seria uma matriz que é uma instância da classe <xref:System.Array>. Para obter mais informações sobre matrizes, consulte [Como criar uma matriz de objetos (Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/487y7874(v=vs.100)).  
  
 Em geral, você deve usar <xref:System.ComponentModel.BindingList%601> ao criar listas de objetos para associação de dados. <xref:System.ComponentModel.BindingList%601> é uma versão genérica da interface <xref:System.ComponentModel.IBindingList>. A interface <xref:System.ComponentModel.IBindingList> estende a interface <xref:System.Collections.IList> adicionando Propriedades, métodos e eventos necessários para a ligação de dados bidirecional.  
  
 <xref:System.Collections.IEnumerable>  
 Windows Forms controles podem ser vinculados a fontes de dados que só dão suporte à interface <xref:System.Collections.IEnumerable> se estiverem ligados por um componente <xref:System.Windows.Forms.BindingSource>.  
  
 Objetos de dados ADO.NET  
 O ADO.NET fornece várias estruturas de dados adequadas para a associação ao. Cada uma delas varia em termos de sofisticação e complexidade.  
  
- <xref:System.Data.DataColumn>. Uma <xref:System.Data.DataColumn> é o bloco de construção essencial de uma <xref:System.Data.DataTable>, pois várias colunas compõem uma tabela. Cada <xref:System.Data.DataColumn> tem uma propriedade <xref:System.Data.DataColumn.DataType%2A> que determina o tipo de dados que a coluna contém (por exemplo, a marca de um automóvel em uma tabela que descreve carros). Você pode associar simples um controle (como uma propriedade de <xref:System.Windows.Forms.Control.Text%2A> do controle de <xref:System.Windows.Forms.TextBox>) a uma coluna em uma tabela de dados.  
  
- <xref:System.Data.DataTable>. Uma <xref:System.Data.DataTable> é a representação de uma tabela, com linhas e colunas, em ADO.NET. Uma tabela de dados contém duas coleções: <xref:System.Data.DataColumn>, representando as colunas de dados em uma determinada tabela (que, por fim, determina os tipos de dados que podem ser inseridos nessa tabela) e <xref:System.Data.DataRow>, representando as linhas de dados em uma determinada tabela. Você pode associar um controle de forma complexa às informações contidas em uma tabela de dados (como associar o controle de <xref:System.Windows.Forms.DataGridView> a uma tabela de dados). No entanto, ao associar a um <xref:System.Data.DataTable>, você é realmente uma associação à exibição padrão da tabela.  
  
- <xref:System.Data.DataView>. Uma <xref:System.Data.DataView> é uma exibição personalizada de uma única tabela de dados que pode ser filtrada ou classificada. Uma exibição de dados é o "instantâneo" dos dados usado por controles associados de forma complexa. Você pode associar de forma simples ou complexa aos dados em uma exibição de dados, mas lembre-se de que você está associando a uma "imagem" fixa dos dados em vez de uma fonte de dados limpa e atualizada.  
  
- <xref:System.Data.DataSet>. Uma <xref:System.Data.DataSet> é uma coleção de tabelas, relações e restrições dos dados em um banco de dado. Você pode fazer uma associação simples ou uma associação complexa aos dados em um DataSet, mas lembre-se de que você está ligando ao <xref:System.Data.DataViewManager> padrão para o <xref:System.Data.DataSet> (consulte o próximo ponto de marcador).  
  
- <xref:System.Data.DataViewManager>. Uma <xref:System.Data.DataViewManager> é uma exibição personalizada de todo o <xref:System.Data.DataSet>, análogo a uma <xref:System.Data.DataView>, mas com as relações incluídas. Com uma coleção de <xref:System.Data.DataViewManager.DataViewSettings%2A>, você pode definir filtros padrão e opções de classificação para quaisquer exibições que o <xref:System.Data.DataViewManager> tenha para uma determinada tabela.  
  
## <a name="see-also"></a>Veja também

- [Notificação de alteração na associação de dados do Windows Forms](change-notification-in-windows-forms-data-binding.md)
- [Vinculação de dados e os Windows Forms](data-binding-and-windows-forms.md)
- [Vinculação de dados dos Windows Forms](windows-forms-data-binding.md)
