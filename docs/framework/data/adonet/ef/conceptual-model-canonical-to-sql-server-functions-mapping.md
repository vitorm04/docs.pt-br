---
title: Modelo conceitual canônico a mapeamento de funções do SQL Server
ms.date: 03/30/2017
ms.assetid: 1a2631bc-a426-4c0a-ba8d-26d9c80d39e2
ms.openlocfilehash: f997fbf39f3dee07cc0d58a39fca779f55236606
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251673"
---
# <a name="conceptual-model-canonical-to-sql-server-functions-mapping"></a>Modelo conceitual canônico a mapeamento de funções do SQL Server
Este tópico descreve como o mapa canônico de funções modelo conceitual ao SQL Server correspondente funciona.  
  
## <a name="date-and-time-functions"></a>Funções de data e hora  
 A tabela a seguir descreve mapeamento de funções de data e hora:  
  
|Funções canônicas|Funções do SQL Server|  
|-------------------------|--------------------------|  
|[AddDays(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(day, number, date)`|  
|[AddHours(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(hour, number, date)`|  
|[AddMicroseconds(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(microsecond, number, date)`|  
|[AddMilliseconds(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(millisecond, number, date)`|  
|[AddMinutes(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(minute, number, date)`|  
|[AddMonths(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(month, number, date)`|  
|[AddNanoseconds(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(nanosecond, number, date)`|  
|[AddSeconds(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(second, number, date)`|  
|[AddYears(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(year, number, date)`|  
|[CreateDateTime (ano, mês, dia, hora, minuto, segundo)](./language-reference/date-and-time-canonical-functions.md)|Para SQL Server 2000 e SQL Server 2005, um valor formatado `datetime` é criado no servidor. Para SQL Server 2008 e versões posteriores, um valor de `datetime2` é criado no servidor.|  
|[CreateDateTimeOffset (ano, mês, dia, hora, minuto, segundo, TZoffset)](./language-reference/date-and-time-canonical-functions.md)|Um valor formatado `datetimeoffset` é criado no servidor.<br /><br /> Não suportado no SQL Server 2000 ou no SQL Server 2005.|  
|[CreateTime (hora, minuto, segundo)](./language-reference/date-and-time-canonical-functions.md)|Um valor formatado `time` é criado no servidor.<br /><br /> Não suportado no SQL Server 2000 ou no SQL Server 2005.|  
|[CurrentDateTime()](./language-reference/date-and-time-canonical-functions.md)|`SysDateTime()` em SQLServer 2008.<br /><br /> `GetDate()` em SQLServer 2000 e em SQLServer 2005.|  
|[CurrentDateTimeOffset()](./language-reference/date-and-time-canonical-functions.md)|`SysDateTimeOffset()` no SQL Server 2008.<br /><br /> Não suportado no SQL Server 2000 ou no SQL Server 2005.|  
|[CurrentUtcDateTime()](./language-reference/date-and-time-canonical-functions.md)|`SysUtcDateTime()` em SQLServer 2008. `GetUtcDate()` no SQL Server 2000 e no SQL Server 2005.|  
|[DayOfYear(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(dayofyear, expression)`|  
|[Day(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(day, expression)`|  
|[DiffDays (StartName, endexpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(day, startdate, enddate)`|  
|[DiffHours (StartName, endexpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(hour, startdate, enddate)`|  
|[DiffMicroseconds(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(microsecond, startdate, enddate)`|  
|[DiffMilliseconds(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(millisecond, startdate, enddate)`|  
|[DiffMinutes (StartName, endexpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(minute, startdate, enddate)`|  
|[DiffNanoseconds(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(nanosecond, startdate, enddate)`|  
|[DiffSeconds(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(second, startdate, enddate)`|  
|[DiffYears(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(year, startdate, enddate)`|  
|[GetTotalOffsetMinutes(DateTimeOffset)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(tzoffset, expression)`|  
|[Hour(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(hour, expression)`|  
|[Millisecond(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(millisecond, expression)`|  
|[Minute(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(minute, expression)`|  
|[Month (expressão)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(month, expression)`|  
|[Second(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(second, expression)`|  
|[Truncate(expression)](./language-reference/date-and-time-canonical-functions.md)|Para SQL Server 2000 e SQL Server 2005, um valor `datetime` formatado truncado é criado no servidor. Para SQL Server 2008 e versões posteriores, um `datetime2` truncado `datetimeoffset` ou valor é criado no servidor.|  
|[Year(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(YEAR, expression)`|  
  
## <a name="aggregate-functions"></a>Funções agregadas  
 A tabela a seguir descreve mapeamento de funções agregadas:  
  
|Funções canônicas|Funções do SQL Server|  
|-------------------------|--------------------------|  
|[Avg(expression)](./language-reference/aggregate-canonical-functions.md)|`AVG(expression)`|  
|[BigCount(expression)](./language-reference/aggregate-canonical-functions.md)|`BIGCOUNT(expression)`|  
|[Count(expression)](./language-reference/aggregate-canonical-functions.md)|`COUNT(expression)`|  
|[Min(expression)](./language-reference/aggregate-canonical-functions.md)|`MIN(expression)`|  
|[Max(expression)](./language-reference/aggregate-canonical-functions.md)|`MAX(expression)`|  
|[StDev(expression)](./language-reference/aggregate-canonical-functions.md)|`STDEV(expression)`|  
|[StDevP(expression)](./language-reference/aggregate-canonical-functions.md)|`STDEVP(expression)`|  
|[Sum(expression)](./language-reference/aggregate-canonical-functions.md)|`SUM(expression)`|  
|[Var(expression)](./language-reference/aggregate-canonical-functions.md)|`VAR(expression)`|  
|[VarP(expression)](./language-reference/aggregate-canonical-functions.md)|`VARP(expression)`|  
  
## <a name="math-functions"></a>Funções matemáticas  
 A tabela a seguir descreve mapeamento de funções matemáticas:  
  
|Funções canônicas|Funções do SQL Server|  
|-------------------------|--------------------------|  
|[ABS (valor)](./language-reference/math-canonical-functions.md)|`ABS(value)`|  
|[Teto (valor)](./language-reference/math-canonical-functions.md)|`CEILING(value)`|  
|[Floor (valor)](./language-reference/math-canonical-functions.md)|`FLOOR(value)`|  
|[Power(value)](./language-reference/math-canonical-functions.md)|`POWER(value, exponent)`|  
|[Round(value)](./language-reference/math-canonical-functions.md)|`ROUND(value, digits, 0)`|  
|[Truncar](./language-reference/math-canonical-functions.md)|`ROUND(value , digits, 1)`|  
  
## <a name="string-functions"></a>Funções da cadeia de caracteres  
 A tabela a seguir descreve mapeamento de funções de cadeia de caracteres:  
  
|Funções canônicas|Funções do SQL Server|  
|-------------------------|--------------------------|  
|[Contains (cadeia de caracteres, destino)](./language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[Concat(string1, string2)](./language-reference/string-canonical-functions.md)|string1 + string2|  
|[EndsWith (cadeia de caracteres, destino)](./language-reference/string-canonical-functions.md)|`CHARINDEX(REVERSE(target), REVERSE(string)) = 1`<br /><br /> **Observação** A `CHARINDEX` função retornará `false` se o `string` for armazenado em uma coluna de cadeia de caracteres `target` de comprimento fixo e for uma constante. Nesse caso, a cadeia de caracteres inteira é pesquisada, incluindo todos os espaço à direita de preenchimento. Uma solução alternativa é possível quebrar dados a cadeia de caracteres fixa de comprimento antes de passar a cadeia de caracteres a função de `EndsWith` , como no exemplo a seguir: `EndsWith(TRIM(string), target)`|  
|[IndexOf (Target, seqüência2)](./language-reference/string-canonical-functions.md)|`CHARINDEX(target, string2)`|  
|[Esquerda (Seqüência1, comprimento)](./language-reference/string-canonical-functions.md)|`LEFT(string1, length)`|  
|[Comprimento (cadeia de caracteres)](./language-reference/string-canonical-functions.md)|`LEN(string)`|  
|[LTrim(string)](./language-reference/string-canonical-functions.md)|`LTRIM(string)`|  
|[Right (Seqüência1, comprimento)](./language-reference/string-canonical-functions.md)|`RIGHT (string1, length)`|  
|[Trim(string)](./language-reference/string-canonical-functions.md)|`LTRIM(RTRIM(string))`|  
|[Replace (Seqüência1, seqüência2, String3)](./language-reference/string-canonical-functions.md)|`REPLACE(string1, string2, string3)`|  
|[Inversa (cadeia de caracteres)](./language-reference/string-canonical-functions.md)|`REVERSE (string)`|  
|[RTrim(string)](./language-reference/string-canonical-functions.md)|`RTRIM(string)`|  
|[StartsWith (cadeia de caracteres, destino)](./language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[Substring (cadeia de caracteres, início, comprimento)](./language-reference/string-canonical-functions.md)|`SUBSTRING(string, start, length)`|  
|[ToLower(string)](./language-reference/string-canonical-functions.md)|`LOWER(string)`|  
|[ToUpper(string)](./language-reference/string-canonical-functions.md)|`UPPER(string)`|  
  
## <a name="bitwise-functions"></a>Funções bit a bit  
 A tabela a seguir descreve mapear bit a bit das funções:  
  
|Funções canônicas|Funções do SQL Server|  
|-------------------------|--------------------------|  
|[BitWiseAnd (value1, value2)](./language-reference/bitwise-canonical-functions.md)|value1 & value2|  
|[BitWiseNot (valor)](./language-reference/bitwise-canonical-functions.md)|~value|  
|[Bit-a (value1, value2)](./language-reference/bitwise-canonical-functions.md)|value1 &#124; value2|  
|[BitWiseXor (value1, value2)](./language-reference/bitwise-canonical-functions.md)|valor2 de ^ de valor1|
