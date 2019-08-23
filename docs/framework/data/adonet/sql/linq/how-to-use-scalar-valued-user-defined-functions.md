---
title: 'Como: usar funções definidas pelo usuário com valor escalar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: 0d757e3c37f347014eb2ef90b4e61ddd205dd012
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938661"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>Como: usar funções definidas pelo usuário com valor escalar
Você pode mapear um método de cliente definido em uma classe a uma função definida pelo usuário usando o atributo <xref:System.Data.Linq.Mapping.FunctionAttribute> . Observe que o corpo do método constrói uma expressão que captura a intenção da chamada de método, e passa essa expressão a <xref:System.Data.Linq.DataContext> para a tradução e a execução.  
  
> [!NOTE]
> A execução direta ocorre somente se a função é chamada fora de uma consulta. Para obter mais informações, confira [Como: Chame funções definidas pelo usuário em](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)linha.  
  
## <a name="example"></a>Exemplo  
 O código a seguir SQL apresenta uma função definida pelo usuário escalar- avaliada `ReverseCustName()`.  
  
```  
CREATE FUNCTION ReverseCustName(@string varchar(100))  
RETURNS varchar(100)  
AS  
BEGIN  
    DECLARE @custName varchar(100)  
    -- Implementation left as exercise for users.  
    RETURN @custName  
END  
```  
  
 Você mapearia um método do cliente como o seguinte para este código:  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- [Funções definidas pelo usuário](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
