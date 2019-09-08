---
title: DataViews
ms.date: 03/30/2017
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
ms.openlocfilehash: 8a06accb11631f2dce6b0d39587d7274223c0e68
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786352"
---
# <a name="dataviews"></a>DataViews
Um <xref:System.Data.DataView> permite que você crie diferentes exibições dos dados armazenados em um <xref:System.Data.DataTable>, um recurso que é geralmente usado em aplicativos de vinculação de dados. Usando um **DataView**, você pode expor os dados em uma tabela com diferentes ordens de classificação e pode filtrar os dados por estado de linha ou com base em uma expressão de filtro.  
  
 Um **DataView** fornece uma exibição dinâmica dos dados na **DataTable**subjacente: o conteúdo, a ordenação e a associação refletem as alterações conforme elas ocorrem. Esse comportamento é diferente do método **Select** da **DataTable**, que retorna uma <xref:System.Data.DataRow> matriz de uma tabela com base em um filtro específico e/ou ordem de classificação: esse conteúdo reflete as alterações na tabela subjacente, mas sua associação e a ordenação permanece estática. Os recursos dinâmicos do **DataView** o tornam ideal para aplicativos de vinculação de dados.  
  
 Um **DataView** fornece uma exibição dinâmica de um único conjunto de dados, de forma semelhante a uma exibição de banco de dado, à qual você pode aplicar diferentes critérios de classificação e filtragem. Ao contrário de uma exibição de banco de dados, no entanto, um **DataView** não pode ser tratado como uma tabela e não pode fornecer uma exibição de tabelas unidas. Você também não pode excluir as colunas que existem na tabela de origem nem pode acrescentar colunas, como as colunas computacionais, que não existem na tabela de origem.  
  
 Você pode usar um <xref:System.Data.DataView.DataViewManager%2A> para gerenciar as configurações de exibição para todas as tabelas em um **conjunto**de um. O **DataViewManager** fornece uma maneira conveniente de gerenciar as configurações de exibição padrão para cada tabela. Ao associar um controle a mais de uma tabela de um **conjunto**de informações, a associação a um **DataViewManager** é a opção ideal.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Criando um DataView](creating-a-dataview.md)  
 Descreve como criar um **DataView** para uma **DataTable**.  
  
 [Classificando e filtrando dados](sorting-and-filtering-data.md)  
 Descreve como definir as propriedades de um **DataView** para retornar subconjuntos de linhas de dados que atendem a critérios de filtro específicos ou para retornar dados em uma ordem de classificação específica.  
  
 [DataRows e DataRowViews](datarows-and-datarowviews.md)  
 Descreve como acessar os dados expostos pelo **DataView**.  
  
 [Localizando linhas](finding-rows.md)  
 Descreve como localizar uma linha específica em um **DataView**.  
  
 [ChildViews e relações](childviews-and-relations.md)  
 Descreve como criar exibições de dados de uma relação pai-filho usando um **DataView**.  
  
 [Modificando DataViews](modifying-dataviews.md)  
 Descreve como modificar os dados na **DataTable** subjacente por meio do **DataView**, incluindo a habilitação ou desabilitação de atualizações.  
  
 [Manipulação de eventos de exibição de dados](handling-dataview-events.md)  
 Descreve como usar o evento **ListChanged** para receber notificações quando o conteúdo ou a ordem de um **DataView** está sendo atualizado.  
  
 [Gerenciando DataViews](managing-dataviews.md)  
 Descreve como usar o **DataViewManager** para gerenciar as configurações de **DataView** para cada tabela em um **conjunto**de uma.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Aplicativos Web ASP.NET](https://docs.microsoft.com/previous-versions/655cec97(v=vs.100))  
 Fornece visões gerais e detalhadas, procedimentos passo a passo para criar aplicativos ASP.NET, Web Forms e serviços Web.  
  
 [Aplicativos do Windows](https://docs.microsoft.com/previous-versions/ms184421(v=vs.100))  
 Fornece informações detalhadas sobre como trabalhar com Windows Forms e aplicativos de console.  
  
 [DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)  
 Descreve o objeto **DataSet** e como você pode usá-lo para gerenciar dados de aplicativo.  
  
 [DataTables](datatables.md)  
 Descreve o objeto **DataTable** e como você pode usá-lo para gerenciar dados de aplicativo por si só ou como parte de um **DataSet**.  
  
 [ADO.NET](../index.md)  
 Descreve a arquitetura e os componentes do ADO.NET, e como usar o ADO.NET para acessar fontes de dados existentes e gerenciar dados de aplicativo.  
  
## <a name="see-also"></a>Consulte também

- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
