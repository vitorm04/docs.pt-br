---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 92be418e38039757437e6e673f39a7baef011528
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221776"
---
# <a name="linq-to-dataset"></a>LINQ to DataSet
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] torna mais fácil e mais rápida para consultar dados armazenados em cache em um <xref:System.Data.DataSet> objeto. Especificamente, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] simplifica as consultas, permitindo que os desenvolvedores escrevam consultas de linguagem de programação em si, em vez de por meio de uma linguagem de consulta separada. Isso é especialmente útil para desenvolvedores do Visual Studio, que agora podem aproveitar a vantagem de verificação de sintaxe em tempo de compilação, digitação estática e suporte do IntelliSense fornecidos pelo Visual Studio em suas consultas.  
  
 O [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] também pode ser usado para efetuar consultas a dados que foram consolidados de uma ou mais fontes de dados. Isso permite vários cenários que requerem flexibilidade na representação e na manipulação de dados, como consultas a dados localmente agregados e a cache de camada intermediária em aplicativos Web. Em particular, genéricos de relatório, análise e aplicativos de business intelligence requerem esse método de manipulação.  
  
 O [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] funcionalidade é exposta primeiramente por meio de métodos de extensão em de <xref:System.Data.DataRowExtensions> e <xref:System.Data.DataTableExtensions> classes. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] se baseia no existente e a utiliza [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] arquitetura e não se destina a substituir [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] no código do aplicativo. Código do ADO.NET 2.0 existente continuará a funcionar em um [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] aplicativo. A relação das [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] para [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] e o armazenamento de dados é ilustrado no diagrama a seguir.  
  
 ![Diagrama mostrando que o LINQ to DataSet é baseado em provedor ADO.NET.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a>Nesta seção  
 [Introdução](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [Guia de Programação](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>Referência  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>Consulte também

- [LINQ (consulta integrada à linguagem) – C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ (consulta integrada à linguagem) – Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ e ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
