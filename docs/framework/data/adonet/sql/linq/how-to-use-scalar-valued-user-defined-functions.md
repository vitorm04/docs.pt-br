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
# <a name="how-to-use-scalar-valued-user-defined-functions"></a><span data-ttu-id="4c252-102">Como: usar funções definidas pelo usuário com valor escalar</span><span class="sxs-lookup"><span data-stu-id="4c252-102">How to: Use Scalar-Valued User-Defined Functions</span></span>
<span data-ttu-id="4c252-103">Você pode mapear um método de cliente definido em uma classe a uma função definida pelo usuário usando o atributo <xref:System.Data.Linq.Mapping.FunctionAttribute> .</span><span class="sxs-lookup"><span data-stu-id="4c252-103">You can map a client method defined on a class to a user-defined function by using the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute.</span></span> <span data-ttu-id="4c252-104">Observe que o corpo do método constrói uma expressão que captura a intenção da chamada de método, e passa essa expressão a <xref:System.Data.Linq.DataContext> para a tradução e a execução.</span><span class="sxs-lookup"><span data-stu-id="4c252-104">Note that the body of the method constructs an expression that captures the intent of the method call, and passes that expression to the <xref:System.Data.Linq.DataContext> for translation and execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c252-105">A execução direta ocorre somente se a função é chamada fora de uma consulta.</span><span class="sxs-lookup"><span data-stu-id="4c252-105">Direct execution occurs only if the function is called outside a query.</span></span> <span data-ttu-id="4c252-106">Para obter mais informações, confira [Como: Chame funções definidas pelo usuário em](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)linha.</span><span class="sxs-lookup"><span data-stu-id="4c252-106">For more information, see [How to: Call User-Defined Functions Inline](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c252-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4c252-107">Example</span></span>  
 <span data-ttu-id="4c252-108">O código a seguir SQL apresenta uma função definida pelo usuário escalar- avaliada `ReverseCustName()`.</span><span class="sxs-lookup"><span data-stu-id="4c252-108">The following SQL code presents a scalar-valued user-defined function `ReverseCustName()`.</span></span>  
  
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
  
 <span data-ttu-id="4c252-109">Você mapearia um método do cliente como o seguinte para este código:</span><span class="sxs-lookup"><span data-stu-id="4c252-109">You would map a client method such as the following for this code:</span></span>  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="4c252-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c252-110">See also</span></span>

- [<span data-ttu-id="4c252-111">Funções definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="4c252-111">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
