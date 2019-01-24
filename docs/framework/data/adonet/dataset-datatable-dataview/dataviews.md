---
title: DataViews
ms.date: 03/30/2017
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
ms.openlocfilehash: 4731b0c94f9ecd03dc3d1229f27cb8ede7e0e203
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592894"
---
# <a name="dataviews"></a>DataViews
Um <xref:System.Data.DataView> permite que você crie diferentes exibições dos dados armazenados em um <xref:System.Data.DataTable>, um recurso que é geralmente usado em aplicativos de vinculação de dados. Usando um **DataView**, você pode expor os dados em uma tabela com diferentes ordens de classificação, e você pode filtrar os dados por estado de linha ou com base em uma expressão de filtro.  
  
 Um **DataView** fornece uma exibição dinâmica de dados subjacente **DataTable**: o conteúdo, ordenação e associação refletem as alterações conforme elas ocorrem. Esse comportamento difere do **selecionar** método da **DataTable**, que retorna um <xref:System.Data.DataRow> matriz de uma tabela com base em uma ordem específica de filtro e/ou classificação: este conteúdo reflete as alterações a subjacente da tabela, mas sua associação e ordenação permanecem estáticas. Os recursos dinâmicos do **DataView** o tornam ideal para aplicativos de vinculação de dados.  
  
 Um **DataView** fornece uma exibição dinâmica de um único conjunto de dados, como um modo de exibição de banco de dados ao qual você pode aplicar diferentes de classificação e critérios de filtragem. Ao contrário de uma exibição de banco de dados, no entanto, uma **DataView** não pode ser tratado como uma tabela e não pode fornecer uma exibição de tabelas unidas. Você também não pode excluir as colunas que existem na tabela de origem nem pode acrescentar colunas, como as colunas computacionais, que não existem na tabela de origem.  
  
 Você pode usar um <xref:System.Data.DataView.DataViewManager%2A> para gerenciar as configurações de exibição para todas as tabelas em um **conjunto de dados**. O **DataViewManager** lhe oferece uma maneira conveniente de gerenciar as configurações de exibição padrão para cada tabela. Ao associar um controle a mais de uma tabela de uma **DataSet**, associar a um **DataViewManager** é a opção ideal.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Criando um DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataview.md)  
 Descreve como criar uma **DataView** para um **DataTable**.  
  
 [Classificando e filtrando dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 Descreve como definir as propriedades de um **DataView** para retornar subconjuntos de linhas de dados atendem a critérios específicos de filtro, ou para retornar dados em uma ordem de classificação específica.  
  
 [DataRows e DataRowViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarows-and-datarowviews.md)  
 Descreve como acessar os dados apresentados pela **DataView**.  
  
 [Localizando linhas](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)  
 Descreve como localizar uma linha específica em um **DataView**.  
  
 [ChildViews e relações](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/childviews-and-relations.md)  
 Descreve como criar modos de exibição de dados de uma relação de pai-filho usando um **DataView**.  
  
 [Modificando DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/modifying-dataviews.md)  
 Descreve como modificar os dados subjacentes **DataTable** por meio de **DataView**, incluindo ativar ou desativar atualizações.  
  
 [Manipulação de eventos de exibição de dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataview-events.md)  
 Descreve como usar o **ListChanged** evento para receber notificação quando o conteúdo ou a ordem de uma **DataView** está sendo atualizado.  
  
 [Gerenciando DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/managing-dataviews.md)  
 Descreve como usar um **DataViewManager** gerenciem **DataView** configurações para cada tabela em um **conjunto de dados**.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Aplicativos Web ASP.NET](https://msdn.microsoft.com/library/a812d7b7-049e-4234-a4c2-6acf690301f6)  
 Fornece visões gerais e detalhadas, procedimentos passo a passo para criar aplicativos ASP.NET, Web Forms e serviços Web.  
  
 [Aplicativos do Windows](https://msdn.microsoft.com/library/a6bb2180-09b1-4738-b9fd-7fb05fc92f23)  
 Fornece informações detalhadas sobre como trabalhar com Windows Forms e aplicativos de console.  
  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 Descreve o **conjunto de dados** objeto e como você pode usá-lo para gerenciar dados de aplicativo.  
  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 Descreve o **DataTable** objeto e como você pode usá-lo para gerenciar dados de aplicativo por si só ou como parte de uma **conjunto de dados**.  
  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 Descreve a arquitetura e os componentes do ADO.NET, e como usar o ADO.NET para acessar fontes de dados existentes e gerenciar dados de aplicativo.  
  
## <a name="see-also"></a>Consulte também
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
