---
title: Métodos de System.DateTimeOffset
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: 46b1622cdc8a38544f1c8a8104abb935c9ff1269
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637197"
---
# <a name="systemdatetimeoffset-methods"></a><span data-ttu-id="9c454-102">Métodos de System.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="9c454-102">System.DateTimeOffset Methods</span></span>
<span data-ttu-id="9c454-103">Mapeado uma vez no modelo de objeto ou no arquivo de mapeamento externo, LINQ to SQL permite que você chame a maioria dos métodos de <xref:System.DateTimeOffset?displayProperty=nameWithType> , operadores, e as propriedades do seu consulte LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="9c454-103">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call most of the <xref:System.DateTimeOffset?displayProperty=nameWithType> methods, operators, and properties from within your LINQ to SQL queries.</span></span>  
  
 <span data-ttu-id="9c454-104">Somente os métodos suportados não são aqueles herdados de <xref:System.Object?displayProperty=nameWithType> que não fazem sentido no contexto de consultas LINQ to SQL, como: `Finalize`, `GetHashCode`, `GetType`, e `MemberwiseClone`.</span><span class="sxs-lookup"><span data-stu-id="9c454-104">The only methods not supported are those inherited from <xref:System.Object?displayProperty=nameWithType> that do not make sense in the context of LINQ to SQL queries, such as: `Finalize`, `GetHashCode`, `GetType`, and `MemberwiseClone`.</span></span> <span data-ttu-id="9c454-105">Esses métodos não são suportados porque LINQ to SQL não pode converter os para execução no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9c454-105">These methods are not supported because LINQ to SQL cannot translate them for execution on the SQL Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c454-106">A estrutura do Common Language Runtime (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> , e a capacidade mapear-lo para uma coluna do SQL `DATETIMEOFFSET` com LINQ to SQL, requerem o .NET Framework 3.5 SP1 ou além.</span><span class="sxs-lookup"><span data-stu-id="9c454-106">The common language runtime (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> structure, and the ability to map it to a SQL `DATETIMEOFFSET` column with LINQ to SQL, requires the .NET Framework 3.5 SP1 or beyond.</span></span> <span data-ttu-id="9c454-107">A coluna SQL `DATETIMEOFFSET` só está disponível no Microsoft SQL Server 2008 e além.</span><span class="sxs-lookup"><span data-stu-id="9c454-107">The SQL `DATETIMEOFFSET` column is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="9c454-108">Métodos de data e hora de SQLMethods</span><span class="sxs-lookup"><span data-stu-id="9c454-108">SQLMethods Date and Time Methods</span></span>  
 <span data-ttu-id="9c454-109">Além dos métodos oferecidos pela estrutura de <xref:System.DateTimeOffset> , LINQ to SQL oferece métodos listados na tabela de classes de <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> para trabalhar com data e hora.</span><span class="sxs-lookup"><span data-stu-id="9c454-109">In addition to the methods offered by the <xref:System.DateTimeOffset> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="9c454-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c454-110">See also</span></span>
- [<span data-ttu-id="9c454-111">Conceitos de consulta</span><span class="sxs-lookup"><span data-stu-id="9c454-111">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="9c454-112">Criando o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="9c454-112">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [<span data-ttu-id="9c454-113">Mapeamento de tipo CLR do SQL</span><span class="sxs-lookup"><span data-stu-id="9c454-113">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
