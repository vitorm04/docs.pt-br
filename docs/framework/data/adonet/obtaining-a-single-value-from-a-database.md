---
title: Obter um único valor de um banco de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: 5eb81fd2a64f06f1252f71e251e58df568e7407c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120673"
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="b27fa-102">Obter um único valor de um banco de dados</span><span class="sxs-lookup"><span data-stu-id="b27fa-102">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="b27fa-103">Você pode precisar de informações de banco de dados de retorno que é simplesmente um único valor, em vez de na forma de um fluxo de dados ou tabela.</span><span class="sxs-lookup"><span data-stu-id="b27fa-103">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="b27fa-104">Por exemplo, você talvez queira retornar o resultado de uma função de agregação, como contagem (\*), Sum, ou AVG(Quantity).</span><span class="sxs-lookup"><span data-stu-id="b27fa-104">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="b27fa-105">O **comando** objeto fornece a capacidade de retornar valores únicos usando o **ExecuteScalar** método.</span><span class="sxs-lookup"><span data-stu-id="b27fa-105">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="b27fa-106">O **ExecuteScalar** método retorna, como um valor escalar, o valor da primeira coluna da primeira linha do conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="b27fa-106">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="b27fa-107">O exemplo de código a seguir insere um novo valor no banco de dados usando um <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="b27fa-107">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="b27fa-108">O <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> método é usado para retornar o valor da coluna de identidade para o registro inserido.</span><span class="sxs-lookup"><span data-stu-id="b27fa-108">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b27fa-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b27fa-109">See also</span></span>

- [<span data-ttu-id="b27fa-110">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="b27fa-110">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="b27fa-111">Executando um comando</span><span class="sxs-lookup"><span data-stu-id="b27fa-111">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)
- [<span data-ttu-id="b27fa-112">DbConnection, DbCommand e DbException</span><span class="sxs-lookup"><span data-stu-id="b27fa-112">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="b27fa-113">Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet</span><span class="sxs-lookup"><span data-stu-id="b27fa-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
