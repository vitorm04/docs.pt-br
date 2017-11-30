---
title: Como retornar conjuntos de linhas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 24211e82633e41256a8c801000c4d3e17d9d8612
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-return-rowsets"></a>Como retornar conjuntos de linhas
Este exemplo retorna um conjunto de linhas do banco de dados e inclui um parâmetro de entrada para filtrar o resultado.  
  
 Quando você executar um procedimento armazenado que retorna um conjunto de linhas, você usar um *resultados* classe que armazena a retornar do procedimento armazenado. Para obter mais informações, consulte [Analisando código do LINQ to SQL fonte](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir representa um procedimento armazenado que retorna linhas de clientes e usa um parâmetro de entrada para retornar somente as linhas que listam "London" como a cidade do cliente. O exemplo supõe uma classe `CustomersByCityResult` enumerável.  
  
```  
CREATE PROCEDURE [dbo].[Customers By City]  
    (@param1 NVARCHAR(20))  
AS  
BEGIN  
    -- SET NOCOUNT ON added to prevent extra result sets from  
    -- interfering with SELECT statements.  
    SET NOCOUNT ON;  
    SELECT CustomerID, ContactName, CompanyName, City from Customers  
        as c where c.City=@param1  
END  
```  
  
 [!code-csharp[DLinqSprox#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#1)]
 [!code-vb[DLinqSprox#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos armazenados](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md) (Baixando bancos de dados de amostra)
