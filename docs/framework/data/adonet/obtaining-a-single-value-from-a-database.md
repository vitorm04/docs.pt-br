---
title: Obter um único valor de um banco de dados
description: Saiba como retornar um único valor em ADO.NET. Este exemplo de código retorna o valor da coluna de identidade para um registro inserido.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: a6f268f72f8b8a09ae48ba3cad6254323cb95a20
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286696"
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="0859c-104">Obter um único valor de um banco de dados</span><span class="sxs-lookup"><span data-stu-id="0859c-104">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="0859c-105">Talvez seja necessário retornar informações do banco de dados que seja simplesmente um único valor em vez de na forma de um fluxo de tabela ou data.</span><span class="sxs-lookup"><span data-stu-id="0859c-105">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="0859c-106">Por exemplo, talvez você queira retornar o resultado de uma função de agregação, como COUNT ( \* ), Sum (Price) ou AVG (quantity).</span><span class="sxs-lookup"><span data-stu-id="0859c-106">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="0859c-107">O objeto **Command** fornece a capacidade de retornar valores únicos usando o método **ExecuteScalar** .</span><span class="sxs-lookup"><span data-stu-id="0859c-107">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="0859c-108">O método **ExecuteScalar** retorna, como um valor escalar, o valor da primeira coluna da primeira linha do conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="0859c-108">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="0859c-109">O exemplo de código a seguir insere um novo valor no banco de dados usando um <xref:System.Data.SqlClient.SqlCommand> .</span><span class="sxs-lookup"><span data-stu-id="0859c-109">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="0859c-110">O <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> método é usado para retornar o valor da coluna de identidade para o registro inserido.</span><span class="sxs-lookup"><span data-stu-id="0859c-110">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0859c-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="0859c-111">See also</span></span>

- [<span data-ttu-id="0859c-112">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="0859c-112">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="0859c-113">Executando um comando</span><span class="sxs-lookup"><span data-stu-id="0859c-113">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="0859c-114">DbConnection, DbCommand e DbException</span><span class="sxs-lookup"><span data-stu-id="0859c-114">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="0859c-115">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0859c-115">ADO.NET Overview</span></span>](ado-net-overview.md)
