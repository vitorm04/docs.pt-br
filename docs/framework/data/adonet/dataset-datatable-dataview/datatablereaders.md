---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 1559cde9cb786ccb2baf920347064b8b28d472c3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785347"
---
# <a name="datatablereaders"></a>DataTableReaders
O <xref:System.Data.DataTableReader> apresenta o conteúdo de um <xref:System.Data.DataTable> ou <xref:System.Data.DataSet> de um no formato de um ou mais conjuntos de resultados somente de encaminhamento e somente leitura.  
  
 Quando você cria um **DataTableReader** a partir de uma **DataTable**, o objeto **DataTableReader** resultante contém um conjunto de resultados com os mesmos dados que a **DataTable** da qual foi criado, exceto para todas as linhas que foram marcadas como excluí. As colunas aparecem na mesma ordem que na **DataTable**original.  
  
 Um **DataTableReader** pode conter vários conjuntos de resultados se ele foi criado chamando <xref:System.Data.DataSet.CreateDataReader%2A>. Os resultados estão na mesma ordem que as **tabelas de tabela** na coleção do <xref:System.Data.DataSet.Tables%2A> objeto DataSet.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Criando um DataReader](creating-a-datareader.md)  
 Discute como criar um objeto **DataTableReader** .  
  
 [Navegando DataTables](navigating-datatables.md)  
 Descreve o uso do método **Read** para percorrer o conteúdo de um **DataTableReader**.  
  
## <a name="see-also"></a>Consulte também

- [Retrieving and Modifying Data in ADO.NET](../retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
