---
title: Obter um único valor de um banco de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: fb43d21546a0e98e87aab23db9213309b62320b9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794742"
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="05d67-102">Obter um único valor de um banco de dados</span><span class="sxs-lookup"><span data-stu-id="05d67-102">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="05d67-103">Talvez seja necessário retornar informações do banco de dados que seja simplesmente um único valor em vez de na forma de um fluxo de tabela ou data.</span><span class="sxs-lookup"><span data-stu-id="05d67-103">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="05d67-104">Por exemplo, talvez você queira retornar o resultado de uma função de agregação, como Count\*(), Sum (Price) ou AVG (quantity).</span><span class="sxs-lookup"><span data-stu-id="05d67-104">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="05d67-105">O objeto **Command** fornece a capacidade de retornar valores únicos usando o método **ExecuteScalar** .</span><span class="sxs-lookup"><span data-stu-id="05d67-105">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="05d67-106">O método **ExecuteScalar** retorna, como um valor escalar, o valor da primeira coluna da primeira linha do conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="05d67-106">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="05d67-107">O exemplo de código a seguir insere um novo valor no banco de <xref:System.Data.SqlClient.SqlCommand>dados usando um.</span><span class="sxs-lookup"><span data-stu-id="05d67-107">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="05d67-108">O <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> método é usado para retornar o valor da coluna de identidade para o registro inserido.</span><span class="sxs-lookup"><span data-stu-id="05d67-108">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="05d67-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05d67-109">See also</span></span>

- [<span data-ttu-id="05d67-110">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="05d67-110">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="05d67-111">Executar um comando</span><span class="sxs-lookup"><span data-stu-id="05d67-111">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="05d67-112">DbConnection, DbCommand e DbException</span><span class="sxs-lookup"><span data-stu-id="05d67-112">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)
- <span data-ttu-id="05d67-113">[ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="05d67-113">[ADO.NET Overview](ado-net-overview.md)</span></span>
