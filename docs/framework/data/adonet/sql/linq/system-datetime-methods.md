---
title: Métodos de System.DateTime
ms.date: 03/30/2017
ms.assetid: 4f80700c-e83f-4ab6-af0f-1c9a606e1133
ms.openlocfilehash: fba695975645ecb86a06b17f0664fdf37f8866a0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792423"
---
# <a name="systemdatetime-methods"></a><span data-ttu-id="091e8-102">Métodos de System.DateTime</span><span class="sxs-lookup"><span data-stu-id="091e8-102">System.DateTime Methods</span></span>
<span data-ttu-id="091e8-103">Seguinte LINQ para os métodos suportados SQL-, operadores, e propriedades estão disponíveis para usar em consultas LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="091e8-103">The following LINQ to SQL-supported methods, operators, and properties are available to use in LINQ to SQL queries.</span></span> <span data-ttu-id="091e8-104">Quando um método, um operador ou uma propriedade são sem suporte, LINQ to SQL não pode converter o membro para execução no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="091e8-104">When a method, operator or property is unsupported, LINQ to SQL cannot translate the member for execution on the SQL Server.</span></span> <span data-ttu-id="091e8-105">Você pode usar esses membros em seu código, no entanto, devem ser avaliado antes que a consulta seja convertida a Transact-SQL ou após os resultados foram recuperados de base de dados.</span><span class="sxs-lookup"><span data-stu-id="091e8-105">You may use these members in your code, however, they must be evaluated before the query is translated to Transact-SQL or after the results have been retrieved from the database.</span></span>  
  
## <a name="supported-systemdatetime-members"></a><span data-ttu-id="091e8-106">Membros de System.DateTime suportados</span><span class="sxs-lookup"><span data-stu-id="091e8-106">Supported System.DateTime Members</span></span>  
 <span data-ttu-id="091e8-107">Mapeado uma vez no modelo de objeto ou no arquivo de mapeamento externo, LINQ to SQL permite que você chame os seguintes membros de <xref:System.DateTime?displayProperty=nameWithType> dentro das consultas LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="091e8-107">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call the following <xref:System.DateTime?displayProperty=nameWithType> members inside LINQ to SQL queries.</span></span>  
  
|<span data-ttu-id="091e8-108">Métodos suportados de <xref:System.DateTime></span><span class="sxs-lookup"><span data-stu-id="091e8-108">Supported <xref:System.DateTime> Methods</span></span>|<span data-ttu-id="091e8-109">Operadores de <xref:System.DateTime> suportados</span><span class="sxs-lookup"><span data-stu-id="091e8-109">Supported <xref:System.DateTime> Operators</span></span>|<span data-ttu-id="091e8-110">Propriedades suportadas de <xref:System.DateTime></span><span class="sxs-lookup"><span data-stu-id="091e8-110">Supported <xref:System.DateTime> Properties</span></span>|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Add%2A>|<xref:System.DateTime.op_Addition%2A>|<xref:System.DateTime.Date%2A>|  
|<xref:System.DateTime.AddDays%2A>|<xref:System.DateTime.op_Equality%2A>|<xref:System.DateTime.Day%2A>|  
|<xref:System.DateTime.AddHours%2A>|<xref:System.DateTime.op_GreaterThan%2A>|<xref:System.DateTime.DayOfWeek%2A>|  
|<xref:System.DateTime.AddMilliseconds%2A>|<xref:System.DateTime.op_GreaterThanOrEqual%2A>|<xref:System.DateTime.DayOfYear%2A>|  
|<xref:System.DateTime.AddMinutes%2A>|<xref:System.DateTime.op_Inequality%2A>|<xref:System.DateTime.Hour%2A>|  
|<xref:System.DateTime.AddMonths%2A>|<xref:System.DateTime.op_LessThan%2A>|<xref:System.DateTime.Millisecond%2A>|  
|<xref:System.DateTime.AddSeconds%2A>|<xref:System.DateTime.op_LessThanOrEqual%2A>|<xref:System.DateTime.Minute%2A>|  
|<xref:System.DateTime.AddTicks%2A>|<xref:System.DateTime.op_Subtraction%2A>|<xref:System.DateTime.Month%2A>|  
|<xref:System.DateTime.AddYears%2A>||<xref:System.DateTime.Now%2A>|  
|<xref:System.DateTime.Compare%2A>||<xref:System.DateTime.Second%2A>|  
|<xref:System.DateTime.CompareTo%28System.DateTime%29>||<xref:System.DateTime.TimeOfDay%2A>|  
|<xref:System.DateTime.Equals%28System.DateTime%29>||<xref:System.DateTime.Today%2A>|  
|||<xref:System.DateTime.Year%2A>|  
  
## <a name="members-not-supported-by-linq-to-sql"></a><span data-ttu-id="091e8-111">Membros não suportados por LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="091e8-111">Members Not Supported by LINQ to SQL</span></span>  
 <span data-ttu-id="091e8-112">Os seguintes membros não são suportadas consultas internas LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="091e8-112">The following members are not supported inside LINQ to SQL queries.</span></span>  
  
|||  
|-|-|  
|<xref:System.DateTime.IsDaylightSavingTime%2A>|<xref:System.DateTime.IsLeapYear%2A>|  
|<xref:System.DateTime.DaysInMonth%2A>|<xref:System.DateTime.ToBinary%2A>|  
|<xref:System.DateTime.ToFileTime%2A>|<xref:System.DateTime.ToFileTimeUtc%2A>|  
|<xref:System.DateTime.ToLongDateString%2A>|<xref:System.DateTime.ToLongTimeString%2A>|  
|<xref:System.DateTime.ToOADate%2A>|<xref:System.DateTime.ToShortDateString%2A>|  
|<xref:System.DateTime.ToShortTimeString%2A>|<xref:System.DateTime.ToUniversalTime%2A>|  
|<xref:System.DateTime.FromBinary%2A>|<xref:System.DateTime.UtcNow%2A>|  
|<xref:System.DateTime.FromFileTime%2A>|<xref:System.DateTime.FromFileTimeUtc%2A>|  
|<xref:System.DateTime.FromOADate%2A>|<xref:System.DateTime.GetDateTimeFormats%2A>|  
  
## <a name="method-translation-example"></a><span data-ttu-id="091e8-113">Exemplo de tradução de método</span><span class="sxs-lookup"><span data-stu-id="091e8-113">Method Translation Example</span></span>  
 <span data-ttu-id="091e8-114">Todos os métodos suportados por LINQ to SQL são traduzidas a Transact-SQL antes que eles sejam enviados ao SQL Server.</span><span class="sxs-lookup"><span data-stu-id="091e8-114">All methods supported by LINQ to SQL are translated to Transact-SQL before they are sent to   SQL Server.</span></span> <span data-ttu-id="091e8-115">Por exemplo, considere o seguinte padrão.</span><span class="sxs-lookup"><span data-stu-id="091e8-115">For example, consider the following pattern.</span></span>  
  
 `(dateTime1 – dateTime2).{Days, Hours, Milliseconds, Minutes, Months, Seconds, Years}`  
  
 <span data-ttu-id="091e8-116">Quando se reconhece, ele é convertido em uma chamada direto à função SQL Server `DATEDIFF` , como segue:</span><span class="sxs-lookup"><span data-stu-id="091e8-116">When it is recognized, it is translated into a direct call to the SQL Server `DATEDIFF` function, as follows:</span></span>  
  
 `DATEDIFF({DatePart}, @dateTime1, @dateTime2)`  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="091e8-117">Métodos de data e hora de SQLMethods</span><span class="sxs-lookup"><span data-stu-id="091e8-117">SQLMethods Date and Time Methods</span></span>  
 <span data-ttu-id="091e8-118">Além dos métodos oferecidos pela estrutura de <xref:System.DateTime> , LINQ to SQL oferece métodos listados na tabela de classes de <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> para trabalhar com data e hora.</span><span class="sxs-lookup"><span data-stu-id="091e8-118">In addition to the methods offered by the <xref:System.DateTime> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="091e8-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="091e8-119">See also</span></span>

- [<span data-ttu-id="091e8-120">Conceitos de consulta</span><span class="sxs-lookup"><span data-stu-id="091e8-120">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="091e8-121">Criando o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="091e8-121">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="091e8-122">Mapeamento de tipo CLR do SQL</span><span class="sxs-lookup"><span data-stu-id="091e8-122">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
- [<span data-ttu-id="091e8-123">Funções e tipos de dados</span><span class="sxs-lookup"><span data-stu-id="091e8-123">Data Types and Functions</span></span>](data-types-and-functions.md)
