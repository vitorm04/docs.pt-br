---
title: 'Como: Retornar conjuntos de linhas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: b9fcbd8aa74740a66fa6caca18067ac473891f4e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587210"
---
# <a name="how-to-return-rowsets"></a>Como: Retornar conjuntos de linhas
Este exemplo retorna um conjunto de linhas do banco de dados e inclui um parâmetro de entrada para filtrar o resultado.  
  
 Quando você executar um procedimento armazenado que retorna um conjunto de linhas, você usar um *resultado* classe que armazena os valores retornados pelo procedimento armazenado. Para obter mais informações, consulte [Analisando código LINQ to SQL fonte](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).  
  
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
- [Procedimentos armazenados](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
- [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md) (Baixando bancos de dados de amostra)
