---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 8a16e3fe0cea04813be50a83f906170199e78e3e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764847"
---
# <a name="linq-to-dataset"></a>LINQ to DataSet
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] torna mais fácil e rápido a consulta sobre os dados armazenados em cache uma <xref:System.Data.DataSet> objeto. Especificamente, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] simplifica a consulta, permitindo que os desenvolvedores a escrever consultas de linguagem de programação em si, em vez de usando uma linguagem de consulta separada. Isso é especialmente útil para desenvolvedores do Visual Studio, que agora podem se beneficiar da verificação de sintaxe de tempo de compilação, digitação estática e suporte do IntelliSense fornecidos pelo Visual Studio em suas consultas.  
  
 O [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] também pode ser usado para efetuar consultas a dados que foram consolidados de uma ou mais fontes de dados. Isso permite vários cenários que requerem flexibilidade na representação e na manipulação de dados, como consultas a dados localmente agregados e a cache de camada intermediária em aplicativos Web. Em particular, relatórios genéricos, análise e aplicativos de business intelligence exigem esse método de manipulação.  
  
 O [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] funcionalidade é exposta principalmente por meio dos métodos de extensão no <xref:System.Data.DataRowExtensions> e <xref:System.Data.DataTableExtensions> classes. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] amplia e usa existente [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] arquitetura e não se destina a substituir [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] no código do aplicativo. Código do ADO.NET 2.0 existente continuarão a funcionar em um [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] aplicativo. A relação de [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] para [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] e o repositório de dados é ilustrado no diagrama a seguir.  
  
 ![O LINQ to DataSet é baseado no provedor ADO.NET](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")  
  
## <a name="in-this-section"></a>Nesta seção  
 [Introdução](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [Guia de Programação](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>Referência  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>Consulte também  
 [LINQ (Consulta Integrada à Linguagem)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [LINQ e ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)
