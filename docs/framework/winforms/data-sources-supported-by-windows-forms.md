---
title: Fontes de dados com suporte do Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a0a4c2bca136377b9c6812008189dae009e195f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="data-sources-supported-by-windows-forms"></a>Fontes de dados com suporte do Windows Forms
Tradicionalmente, a associação de dados era usada nos aplicativos para tirar proveito dos dados armazenados em bancos de dados. Com a associação de dados do Windows Forms, você pode acessar dados de bancos de dados, bem como dados em outras estruturas, como matrizes e coleções, desde que certos requisitos mínimos sejam atendidos.  
  
## <a name="structures-to-bind-to"></a>Estruturas às quais associar  
 No Windows Forms, é possível associar a uma grande variedade de estruturas, desde objetos simples (associação simples) a listas complexas como tabelas de dados do ADO.NET (associação complexa). Para a associação simples, o Windows Forms dá suporte à associação às propriedades públicas no objeto simples. Associação da lista com base em Windows Forms geralmente requer que o objeto oferece suporte a <xref:System.Collections.IList> interface ou <xref:System.ComponentModel.IListSource> interface. Além disso, se você estiver associando com por meio de um <xref:System.Windows.Forms.BindingSource> componente, você pode vincular a um objeto que oferece suporte a <xref:System.Collections.IEnumerable> interface. Para obter mais informações sobre interfaces relacionadas à associação de dados, consulte [Interfaces relacionadas à associação de dados](../../../docs/framework/winforms/interfaces-related-to-data-binding.md).  
  
 A lista a seguir mostra as estruturas a que você pode associar no Windows Forms.  
  
 <xref:System.Windows.Forms.BindingSource>  
 A <xref:System.Windows.Forms.BindingSource> é a fonte de dados mais comuns do Windows Forms e atua um proxy entre uma fonte de dados e controles de formulários do Windows. O geral <xref:System.Windows.Forms.BindingSource> padrão de uso é vincular os controles para o <xref:System.Windows.Forms.BindingSource> e associar o <xref:System.Windows.Forms.BindingSource> à fonte de dados (por exemplo, uma tabela de dados do ADO.NET ou um objeto comercial). O <xref:System.Windows.Forms.BindingSource> fornece serviços que habilitam e aumentar o nível de suporte de associação de dados. Por exemplo, lista de formulários do Windows com base em controles, como o <xref:System.Windows.Forms.DataGridView> e <xref:System.Windows.Forms.ComboBox> diretamente, não oferecem suporte à associação para <xref:System.Collections.IEnumerable> fontes de dados, no entanto, você pode habilitar esse cenário por associação por meio de um <xref:System.Windows.Forms.BindingSource>. Nesse caso, o <xref:System.Windows.Forms.BindingSource> converterá a fonte de dados para um <xref:System.Collections.IList>.  
  
 Objetos simples  
 Windows Forms que dá suporte a propriedades de controle de associação de dados para as propriedades públicas na instância de um objeto usando o <xref:System.Windows.Forms.Binding> tipo. Windows Forms também oferece suporte a controles de lista com base de associação, como um <xref:System.Windows.Forms.ListControl> a um objeto de instância quando um <xref:System.Windows.Forms.BindingSource> é usado.  
  
 Matriz ou coleção  
 Para atuar como uma fonte de dados, uma lista deve implementar o <xref:System.Collections.IList> interface; um exemplo seria uma matriz que é uma instância do <xref:System.Array> classe. Para obter mais informações sobre matrizes, consulte [Como criar uma matriz de objetos (Visual Basic)](http://msdn.microsoft.com/library/6b64e069-0387-400c-9081-3bdc581020c3).  
  
 Em geral, você deve usar <xref:System.ComponentModel.BindingList%601> quando você cria a lista de objetos para associação de dados. <xref:System.ComponentModel.BindingList%601>é uma versão genérica do <xref:System.ComponentModel.IBindingList> interface. O <xref:System.ComponentModel.IBindingList> interface estende o <xref:System.Collections.IList> interface Adicionando propriedades, métodos e eventos necessários para a associação de dados bidirecional.  
  
 <xref:System.Collections.IEnumerable>  
 Controles de formulários do Windows podem ser associados a fontes de dados que oferecem suporte apenas a <xref:System.Collections.IEnumerable> interface se eles são vinculados por meio de um <xref:System.Windows.Forms.BindingSource> componente.  
  
 Objetos de dados [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] fornece um número de estruturas de dados adequadas para associação. Cada uma delas varia em termos de sofisticação e complexidade.  
  
-   <xref:System.Data.DataColumn>. Um <xref:System.Data.DataColumn> é o bloco de construção essencial de um <xref:System.Data.DataTable>, em que um número de colunas compõem uma tabela. Cada <xref:System.Data.DataColumn> tem um <xref:System.Data.DataColumn.DataType%2A> propriedade que determina o tipo de dados mantém a coluna (por exemplo, a marca do exemplo um automóvel em uma tabela que descreve os carros). Você pode simples vincular um controle (como uma <xref:System.Windows.Forms.TextBox> do controle <xref:System.Windows.Forms.Control.Text%2A> propriedade) para uma coluna em uma tabela de dados.  
  
-   <xref:System.Data.DataTable>. Um <xref:System.Data.DataTable> é a representação de uma tabela, com linhas e colunas, em [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]. Uma tabela de dados contém duas coleções: <xref:System.Data.DataColumn>, que representa as colunas de dados em uma determinada tabela (que, por fim, determinar os tipos de dados que podem ser inseridos na tabela), e <xref:System.Data.DataRow>, que representa as linhas de dados em uma determinada tabela. Você pode complexo vincular um controle para as informações contidas em uma tabela de dados (como associação a <xref:System.Windows.Forms.DataGridView> controle a uma tabela de dados). No entanto, quando você associa a um <xref:System.Data.DataTable>, você está realmente associação para o modo de exibição da tabela padrão.  
  
-   <xref:System.Data.DataView>. A <xref:System.Data.DataView> é uma exibição personalizada de uma única tabela de dados que pode ser filtrada ou classificada. Uma exibição de dados é o "instantâneo" dos dados usado por controles associados de forma complexa. Você pode associar de forma simples ou complexa aos dados em uma exibição de dados, mas lembre-se de que você está associando a uma "imagem" fixa dos dados em vez de uma fonte de dados limpa e atualizada.  
  
-   <xref:System.Data.DataSet>. A <xref:System.Data.DataSet> é uma coleção de tabelas, relações e restrições dos dados em um banco de dados. Você pode ligação simples ou complexo associar aos dados em um conjunto de dados, mas lembre-se de que você está associando padrão <xref:System.Data.DataViewManager> para o <xref:System.Data.DataSet> (consulte o próximo marcador de ponto).  
  
-   <xref:System.Data.DataViewManager>. Um <xref:System.Data.DataViewManager> é uma exibição personalizada de todo o <xref:System.Data.DataSet>, análogo a um <xref:System.Data.DataView>, mas com relações incluídas. Com um <xref:System.Data.DataViewManager.DataViewSettings%2A> coleção, você pode definir filtros padrão e opções de classificação para todas as exibições que o <xref:System.Data.DataViewManager> tem para uma determinada tabela.  
  
## <a name="see-also"></a>Consulte também  
 [Notificação de alteração na vinculação de dados dos Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [Vinculação de dados e os Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Associação de dados do Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)
