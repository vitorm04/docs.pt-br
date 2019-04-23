---
title: Fontes de dados com suporte do Windows Forms
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
ms.openlocfilehash: b648d62c9128f0864d60ace1ca56700f594b78c5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124612"
---
# <a name="data-sources-supported-by-windows-forms"></a>Fontes de dados com suporte do Windows Forms
Tradicionalmente, a associação de dados era usada nos aplicativos para tirar proveito dos dados armazenados em bancos de dados. Com a associação de dados do Windows Forms, você pode acessar dados de bancos de dados, bem como dados em outras estruturas, como matrizes e coleções, desde que certos requisitos mínimos sejam atendidos.  
  
## <a name="structures-to-bind-to"></a>Estruturas às quais associar  
 No Windows Forms, é possível associar a uma grande variedade de estruturas, desde objetos simples (associação simples) a listas complexas como tabelas de dados do ADO.NET (associação complexa). Para a associação simples, o Windows Forms dá suporte à associação às propriedades públicas no objeto simples. Associação baseada em lista do Windows Forms geralmente requer que o objeto dá suporte a <xref:System.Collections.IList> interface ou o <xref:System.ComponentModel.IListSource> interface. Além disso, se você estiver associando com por meio de um <xref:System.Windows.Forms.BindingSource> componente, você pode associar a um objeto que dá suporte a <xref:System.Collections.IEnumerable> interface. Para obter mais informações sobre interfaces relacionadas à associação de dados, consulte [Interfaces relacionadas à associação de dados](interfaces-related-to-data-binding.md).  
  
 A lista a seguir mostra as estruturas a que você pode associar no Windows Forms.  
  
 <xref:System.Windows.Forms.BindingSource>  
 Um <xref:System.Windows.Forms.BindingSource> é a fonte de dados mais comuns do Windows Forms e atua como um proxy entre uma fonte de dados e controles de formulários do Windows. Em geral <xref:System.Windows.Forms.BindingSource> padrão de uso é associar os controles para o <xref:System.Windows.Forms.BindingSource> e vincular o <xref:System.Windows.Forms.BindingSource> à fonte de dados (por exemplo, uma tabela de dados do ADO.NET ou um objeto de negócios). O <xref:System.Windows.Forms.BindingSource> fornece serviços que habilitam e aumentam o nível de suporte à associação de dados. Por exemplo, lista de formulários do Windows com base em controles, como o <xref:System.Windows.Forms.DataGridView> e <xref:System.Windows.Forms.ComboBox> não suportam diretamente associação à <xref:System.Collections.IEnumerable> fontes de dados, no entanto, você pode habilitar esse cenário por associação por meio de um <xref:System.Windows.Forms.BindingSource>. Nesse caso, o <xref:System.Windows.Forms.BindingSource> converterá a fonte de dados para um <xref:System.Collections.IList>.  
  
 Objetos simples  
 Windows Forms dá suporte a propriedades de controle de associação de dados a propriedades públicas na instância de um objeto usando o <xref:System.Windows.Forms.Binding> tipo. Windows Forms também oferece suporte a controles de lista com base de associação, como um <xref:System.Windows.Forms.ListControl> a um objeto de instância quando um <xref:System.Windows.Forms.BindingSource> é usado.  
  
 Matriz ou coleção  
 Para atuar como uma fonte de dados, uma lista deve implementar o <xref:System.Collections.IList> interface, um exemplo seria uma matriz que é uma instância do <xref:System.Array> classe. Para obter mais informações sobre matrizes, consulte [como: Criar uma matriz de objetos (Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/487y7874(v=vs.100)).  
  
 Em geral, você deve usar <xref:System.ComponentModel.BindingList%601> quando você cria listas de objetos para associação de dados. <xref:System.ComponentModel.BindingList%601> é uma versão genérica de <xref:System.ComponentModel.IBindingList> interface. O <xref:System.ComponentModel.IBindingList> interface estende o <xref:System.Collections.IList> interface Adicionando propriedades, métodos e eventos necessários para a associação de dados bidirecional.  
  
 <xref:System.Collections.IEnumerable>  
 Controles dos Windows Forms podem ser vinculados a fontes de dados que oferecem suporte apenas a <xref:System.Collections.IEnumerable> se eles estiverem associados por meio da interface um <xref:System.Windows.Forms.BindingSource> componente.  
  
 Objetos de dados [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] fornece um número de estruturas de dados adequadas para associação. Cada uma delas varia em termos de sofisticação e complexidade.  
  
-   <xref:System.Data.DataColumn>. Um <xref:System.Data.DataColumn> é o bloco de construção essencial de um <xref:System.Data.DataTable>, em que um número de colunas compõem uma tabela. Cada <xref:System.Data.DataColumn> tem um <xref:System.Data.DataColumn.DataType%2A> propriedade que determina o tipo de dados, a coluna contém (por exemplo, a marca de um automóvel em uma tabela que descreve carros). Você pode associar de maneira simples um controle (como uma <xref:System.Windows.Forms.TextBox> do controle <xref:System.Windows.Forms.Control.Text%2A> propriedade) para uma coluna dentro de uma tabela de dados.  
  
-   <xref:System.Data.DataTable>. Um <xref:System.Data.DataTable> é a representação de uma tabela, com linhas e colunas, em [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]. Uma tabela de dados contém duas coleções: <xref:System.Data.DataColumn>, que representam as colunas de dados em uma determinada tabela (que determina os tipos de dados que podem ser inseridos na tabela), e <xref:System.Data.DataRow>, que representa as linhas de dados em uma determinada tabela. Você pode complexo associar um controle às informações contidas em uma tabela de dados (como a associação a <xref:System.Windows.Forms.DataGridView> controle para uma tabela de dados). No entanto, quando você associa a um <xref:System.Data.DataTable>, você está na verdade está associando à exibição padrão da tabela.  
  
-   <xref:System.Data.DataView>. Um <xref:System.Data.DataView> é uma exibição personalizada de uma única tabela de dados que pode ser filtrada ou classificada. Uma exibição de dados é o "instantâneo" dos dados usado por controles associados de forma complexa. Você pode associar de forma simples ou complexa aos dados em uma exibição de dados, mas lembre-se de que você está associando a uma "imagem" fixa dos dados em vez de uma fonte de dados limpa e atualizada.  
  
-   <xref:System.Data.DataSet>. Um <xref:System.Data.DataSet> é uma coleção de tabelas, relações e restrições de dados em um banco de dados. Você pode associar de maneira simples ou complexa aos dados dentro de um conjunto de dados, mas lembre-se de que você está associando ao padrão <xref:System.Data.DataViewManager> para o <xref:System.Data.DataSet> (consulte o próximo marcador).  
  
-   <xref:System.Data.DataViewManager>. Um <xref:System.Data.DataViewManager> é uma exibição personalizada de todo o <xref:System.Data.DataSet>, análogo a um <xref:System.Data.DataView>, mas com relações incluídas. Com uma <xref:System.Data.DataViewManager.DataViewSettings%2A> coleção, você pode definir opções de classificação para todas as exibições e filtros padrão que o <xref:System.Data.DataViewManager> tem para uma determinada tabela.  
  
## <a name="see-also"></a>Consulte também

- [Notificação de alteração na vinculação de dados dos Windows Forms](change-notification-in-windows-forms-data-binding.md)
- [Vinculação de dados e os Windows Forms](data-binding-and-windows-forms.md)
- [Associação de dados do Windows Forms](windows-forms-data-binding.md)
