---
title: 'Como: retornar conjuntos de linhas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: b853a6f2175009cbcbc01c14a6732b98e37e1a7f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003066"
---
# <a name="how-to-return-rowsets"></a>Como: retornar conjuntos de linhas
Este exemplo retorna um conjunto de linhas do banco de dados e inclui um parâmetro de entrada para filtrar o resultado.  
  
 Ao executar um procedimento armazenado que retorna um conjunto de linhas, você usa uma classe *Result* que armazena os retornos do procedimento armazenado. Para obter mais informações, consulte [analisando LINQ to SQL código-fonte](analyzing-linq-to-sql-source-code.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir representa um procedimento armazenado que retorna linhas de clientes e usa um parâmetro de entrada para retornar somente as linhas que listam "London" como a cidade do cliente. O exemplo supõe uma classe `CustomersByCityResult` enumerável.  
  
```sql  
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

- [Procedimentos armazenados](stored-procedures.md)
- [Downloading Sample Databases](downloading-sample-databases.md) (Baixando bancos de dados de amostra)
