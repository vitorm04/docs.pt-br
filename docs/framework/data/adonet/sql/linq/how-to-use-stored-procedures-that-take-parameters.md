---
title: "Como: Use os procedimentos armazenados que têm parâmetros"
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
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fbd4e0b7534a213f56c5c6ba60208d3024535bd7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a>Como: Use os procedimentos armazenados que têm parâmetros
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapeia parâmetros de saída para definições de referência, e para tipos de valor declara o parâmetro como anulável.  
  
 Para obter um exemplo de como usar um parâmetro de entrada em uma consulta que retorna um conjunto de linhas, consulte [como: retornar conjuntos de linhas](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir utiliza um único parâmetro de entrada (a identificação do cliente) e retorna um parâmetro de saída (o total de vendas para aquele cliente.)  
  
```  
CREATE PROCEDURE [dbo].[CustOrderTotal]   
@CustomerID nchar(5),  
@TotalSales money OUTPUT  
AS  
SELECT @TotalSales = SUM(OD.UNITPRICE*(1-OD.DISCOUNT) * OD.QUANTITY)  
FROM ORDERS O, "ORDER DETAILS" OD  
where O.CUSTOMERID = @CustomerID AND O.ORDERID = OD.ORDERID  
```  
  
 [!code-csharp[DLinqSprox#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#2)]
 [!code-vb[DLinqSprox#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#2)]  
  
## <a name="example"></a>Exemplo  
 Você poderia chamar esse procedimento armazenado como segue:  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos armazenados](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md) (Baixando bancos de dados de amostra)  
 [Usando tipos que permitem valor nulo](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md)  
 [Tipos de Valor Anulável](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
