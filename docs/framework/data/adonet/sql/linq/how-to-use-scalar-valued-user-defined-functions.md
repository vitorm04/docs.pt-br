---
title: 'Como: usar funções definidas pelo usuário com valor escalar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: faf8d6e94c88575f6cb73003fa5bed87650d7d54
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196930"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>Como: usar funções definidas pelo usuário com valor escalar

Você pode mapear um método de cliente definido em uma classe a uma função definida pelo usuário usando o atributo <xref:System.Data.Linq.Mapping.FunctionAttribute> . Observe que o corpo do método constrói uma expressão que captura a intenção da chamada de método, e passa essa expressão a <xref:System.Data.Linq.DataContext> para a tradução e a execução.  
  
> [!NOTE]
> A execução direta ocorre somente se a função é chamada fora de uma consulta. Para obter mais informações, consulte [como: chamar funções definidas pelo usuário em linha](how-to-call-user-defined-functions-inline.md).  
  
## <a name="example"></a>Exemplo  

 O código a seguir SQL apresenta uma função definida pelo usuário escalar- avaliada `ReverseCustName()`.  
  
```sql  
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
  
## <a name="see-also"></a>Veja também

- [Funções definidas pelo usuário](user-defined-functions.md)
