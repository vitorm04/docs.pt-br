---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 1ff7868b59c6fdc4e6c443be1b831accc84f36a6
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203823"
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
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
