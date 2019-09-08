---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 4995512336ee9eb6e33df011757ed533db57e76e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783792"
---
# <a name="linq-to-dataset"></a>LINQ to DataSet
LINQ to DataSet torna mais fácil e rápido a consulta sobre dados armazenados em cache em <xref:System.Data.DataSet> um objeto. Especificamente, LINQ to DataSet simplifica a consulta, permitindo que os desenvolvedores gravem consultas a partir da própria linguagem de programação, em vez de usar uma linguagem de consulta separada. Isso é especialmente útil para desenvolvedores do Visual Studio, que agora podem aproveitar a verificação de sintaxe de tempo de compilação, digitação estática e suporte do IntelliSense fornecidos pelo Visual Studio em suas consultas.  
  
 LINQ to DataSet também pode ser usado para consultar dados que foram consolidados de uma ou mais fontes de dados. Isso permite vários cenários que requerem flexibilidade na representação e na manipulação de dados, como consultas a dados localmente agregados e a cache de camada intermediária em aplicativos Web. Em particular, relatórios genéricos, análises e business intelligence aplicativos exigem esse método de manipulação.  
  
 A funcionalidade de LINQ to DataSet é exposta principalmente por meio dos métodos de <xref:System.Data.DataRowExtensions> extensão <xref:System.Data.DataTableExtensions> nas classes e. LINQ to DataSet baseia-se no e usa a arquitetura ADO.NET existente e não se destina a substituir o ADO.NET no código do aplicativo. O código ADO.NET existente continuará a funcionar em um aplicativo LINQ to DataSet. A relação de LINQ to DataSet para ADO.NET e o armazenamento de dados é ilustrada no diagrama a seguir.  
  
 ![Diagrama mostrando que LINQ to DataSet se baseia no provedor ADO.NET.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a>Nesta seção  
 [Introdução](getting-started-linq-to-dataset.md)  
  
 [Guia de Programação](programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>Referência  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>Consulte também

- [LINQ (consulta integrada à linguagem) – C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ (consulta integrada à linguagem) – Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ e ADO.NET](linq-and-ado-net.md)
- [ADO.NET](index.md)
