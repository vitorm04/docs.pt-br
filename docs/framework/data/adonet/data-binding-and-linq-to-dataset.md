---
title: Associação e LINQ to DataSet de dados
ms.date: 03/30/2017
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
ms.openlocfilehash: b081a648023aa21eea3a20ec409600d3bcbe9878
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607371"
---
# <a name="data-binding-and-linq-to-dataset"></a>Associação e LINQ to DataSet de dados
*Associação de dados* é o processo que estabelece uma conexão entre o aplicativo da interface do usuário e a lógica de negócios. Se a associação possui configurações corretas e os dados fornecem notificações adequadas, quando os dados mudam de valor, os elementos que são associados a dados refletem as mudanças automaticamente. <xref:System.Data.DataSet> é uma representação em memória dos dados que fornecem um modelo relacional consistente de programação, independentemente da fonte de dados que contém. O ADO.NET 2.0 <xref:System.Data.DataView> permite que você classificar e filtrar os dados armazenados em <xref:System.Data.DataTable>. Essa funcionalidade é freqüentemente usada em aplicativos de associação de dados. Usando <xref:System.Data.DataView>, você pode expor os dados em uma tabela com ordem de classificação diferentes, e você pode filtrar os dados pelo estado de linha ou baseados em uma expressão de filtro. Para obter mais informações sobre o <xref:System.Data.DataView> do objeto, consulte [DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] permite aos desenvolvedores criar consultas complexas, avançadas sobre um <xref:System.Data.DataSet> usando [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]. No entanto, uma [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] consulta retorna uma enumeração de <xref:System.Data.DataRow> objetos, que não é usada facilmente em um cenário de associação. Para facilitar a associação, você pode criar uma <xref:System.Data.DataView> de um [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] consulta. Isso <xref:System.Data.DataView> usa a filtragem e classificação especificada na consulta, mas é mais adequado para associação de dados. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] estende a funcionalidade dos <xref:System.Data.DataView> fornecendo [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] baseadas em expressão de filtragem e classificação, que permite muito mais poderosa e complexa filtragem e classificação de operações que baseada em cadeia de caracteres de filtragem e classificação.  
  
 Observe que <xref:System.Data.DataView> representa a consulta própria e não é uma visualização sobre a consulta. <xref:System.Data.DataView> é associado a um controle de interface do usuário, como <xref:System.Windows.Forms.DataGrid> ou <xref:System.Windows.Forms.DataGridView>, fornecendo um modelo de associação de dados simples. <xref:System.Data.DataView> também pode ser criado de <xref:System.Data.DataTable>, fornecendo uma visualização padrão da tabela.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Criando um objeto de DataView](../../../../docs/framework/data/adonet/creating-a-dataview-object-linq-to-dataset.md)  
 Fornece informações sobre a criação de <xref:System.Data.DataView>.  
  
 [Filtrando com DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 Descreve como filtragem com <xref:System.Data.DataView>.  
  
 [Classificando com DataView](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)  
 Descreve como classificar com <xref:System.Data.DataView>.  
  
 [Consultando a coleção DataRowView em um DataView](../../../../docs/framework/data/adonet/querying-the-datarowview-collection-in-a-dataview.md)  
 Fornece informações sobre consulte a coleção de <xref:System.Data.DataRowView> expostos por <xref:System.Data.DataView>.  
  
 [Desempenho de DataView](../../../../docs/framework/data/adonet/dataview-performance.md)  
 Fornece informações sobre <xref:System.Data.DataView> e desempenho.  
  
 [Como: Associar um objeto de DataView a um controle de DataGridView dos Windows Forms](../../../../docs/framework/data/adonet/how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 Descreve como associar um objeto de <xref:System.Data.DataView> a <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
