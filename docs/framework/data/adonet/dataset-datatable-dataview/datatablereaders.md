---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: a790335a25327563e3dab6093449345b99afd048
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213995"
---
# <a name="datatablereaders"></a>DataTableReaders
O <xref:System.Data.DataTableReader> apresenta o conteúdo de um <xref:System.Data.DataTable> ou um <xref:System.Data.DataSet> na forma de um ou mais resultados de somente leitura, somente encaminhamento define.  
  
 Quando você cria um **DataTableReader** de uma **DataTable**, resultante **DataTableReader** objeto contém um conjunto de resultados com os mesmos dados que o  **DataTable** do qual ele foi criado, exceto para quaisquer linhas que foram marcadas como excluídas. As colunas aparecem na mesma ordem como original **DataTable**.  
  
 Um **DataTableReader** pode conter vários conjuntos de resultados, se ele foi criado chamando <xref:System.Data.DataSet.CreateDataReader%2A>. Os resultados estão na mesma ordem que o **DataTables** na **DataSet** do objeto <xref:System.Data.DataSet.Tables%2A> coleção.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Criar um DataReader](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 Discute como criar uma **DataTableReader** objeto.  
  
 [Navegar DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 Descreve o uso do **leitura** método para mover o conteúdo de um **DataTableReader**.  
  
## <a name="see-also"></a>Consulte também

- [Recuperando e modificando dados no ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
