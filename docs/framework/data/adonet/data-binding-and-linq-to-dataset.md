---
title: Associação e LINQ to DataSet de dados
ms.date: 03/30/2017
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
ms.openlocfilehash: 563d57249daa3aa720da1d9654866727f770afb3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786680"
---
# <a name="data-binding-and-linq-to-dataset"></a>Associação e LINQ to DataSet de dados
A *vinculação de dados* é o processo que estabelece uma conexão entre a interface do usuário do aplicativo e a lógica de negócios. Se a associação possui configurações corretas e os dados fornecem notificações adequadas, quando os dados mudam de valor, os elementos que são associados a dados refletem as mudanças automaticamente. <xref:System.Data.DataSet> é uma representação em memória dos dados que fornecem um modelo relacional consistente de programação, independentemente da fonte de dados que contém. O ADO.NET 2.0 <xref:System.Data.DataView> permite que você classificar e filtrar os dados armazenados em <xref:System.Data.DataTable>. Essa funcionalidade é freqüentemente usada em aplicativos de associação de dados. Usando <xref:System.Data.DataView>, você pode expor os dados em uma tabela com ordem de classificação diferentes, e você pode filtrar os dados pelo estado de linha ou baseados em uma expressão de filtro. Para obter mais informações sobre <xref:System.Data.DataView> o objeto, consulte [DataViews](./dataset-datatable-dataview/dataviews.md).  
  
 LINQ to DataSet permite que os desenvolvedores criem consultas complexas e poderosas <xref:System.Data.DataSet> em um [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]usando o. No entanto, uma consulta LINQ to DataSet retorna uma <xref:System.Data.DataRow> enumeração de objetos, que não é facilmente usada em um cenário de ligação. Para facilitar a ligação, você pode criar um <xref:System.Data.DataView> de uma consulta de LINQ to DataSet. Isso <xref:System.Data.DataView> usa a filtragem e a classificação especificadas na consulta, mas é mais adequada para a vinculação de dados. LINQ to DataSet estende a funcionalidade do <xref:System.Data.DataView> fornecendo [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] filtragem e classificação baseadas em expressão, o que permite operações de filtragem e classificação muito mais complexas e poderosas do que a filtragem e classificação baseadas em cadeia de caracteres.  
  
 Observe que <xref:System.Data.DataView> representa a consulta própria e não é uma visualização sobre a consulta. <xref:System.Data.DataView> é associado a um controle de interface do usuário, como <xref:System.Windows.Forms.DataGrid> ou <xref:System.Windows.Forms.DataGridView>, fornecendo um modelo de associação de dados simples. <xref:System.Data.DataView> também pode ser criado de <xref:System.Data.DataTable>, fornecendo uma visualização padrão da tabela.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Criando um objeto de DataView](creating-a-dataview-object-linq-to-dataset.md)  
 Fornece informações sobre a criação de <xref:System.Data.DataView>.  
  
 [Filtrando com DataView](filtering-with-dataview-linq-to-dataset.md)  
 Descreve como filtragem com <xref:System.Data.DataView>.  
  
 [Classificando com DataView](sorting-with-dataview-linq-to-dataset.md)  
 Descreve como classificar com <xref:System.Data.DataView>.  
  
 [Consultando a coleção DataRowView em um DataView](querying-the-datarowview-collection-in-a-dataview.md)  
 Fornece informações sobre consulte a coleção de <xref:System.Data.DataRowView> expostos por <xref:System.Data.DataView>.  
  
 [Desempenho de DataView](dataview-performance.md)  
 Fornece informações sobre <xref:System.Data.DataView> e desempenho.  
  
 [Como: Associar um objeto DataView a um controle Windows Forms DataGridView](how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 Descreve como associar um objeto de <xref:System.Data.DataView> a <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação](programming-guide-linq-to-dataset.md)
