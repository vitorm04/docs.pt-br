---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 911a45dad3d5d82ab5e5752b1c12f7d8a6ab1563
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202312"
---
# <a name="datatablereaders"></a>DataTableReaders

O <xref:System.Data.DataTableReader> apresenta o conteúdo de um <xref:System.Data.DataTable> ou de um <xref:System.Data.DataSet> no formato de um ou mais conjuntos de resultados somente de encaminhamento e somente leitura.  
  
 Quando você cria um **DataTableReader** a partir de uma **DataTable**, o objeto **DataTableReader** resultante contém um conjunto de resultados com os mesmos dados que a **DataTable** da qual ele foi criado, exceto para todas as linhas que foram marcadas como excluídas. As colunas aparecem na mesma ordem que na **DataTable**original.  
  
 Um **DataTableReader** pode conter vários conjuntos de resultados se ele foi criado chamando <xref:System.Data.DataSet.CreateDataReader%2A> . Os resultados estão na mesma ordem que as **tabelas de tabela** na coleção do objeto **DataSet** <xref:System.Data.DataSet.Tables%2A> .  
  
## <a name="in-this-section"></a>Nesta seção  

 [Criar um DataReader](creating-a-datareader.md)  
 Discute como criar um objeto **DataTableReader** .  
  
 [Navegar DataTables](navigating-datatables.md)  
 Descreve o uso do método **Read** para percorrer o conteúdo de um **DataTableReader**.  
  
## <a name="see-also"></a>Veja também

- [Recuperando e modificando dados no ADO.NET](../retrieving-and-modifying-data.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)
