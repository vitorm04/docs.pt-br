---
title: Incompatibilidade de SQL-CLR
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
ms.openlocfilehash: 13d8d68140b68652b5e059ae9fb106f32142f698
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61876857"
---
# <a name="sql-clr-type-mismatches"></a><span data-ttu-id="e6389-102">Incompatibilidade de SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="e6389-102">SQL-CLR Type Mismatches</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e6389-103">automatiza muitas de conversão entre o modelo de objeto e o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e6389-103">automates much of the translation between the object model and SQL Server.</span></span> <span data-ttu-id="e6389-104">Entretanto, algumas situações impedem a conversão exata.</span><span class="sxs-lookup"><span data-stu-id="e6389-104">Nevertheless, some situations prevent exact translation.</span></span> <span data-ttu-id="e6389-105">Essas incompatíveis chave entre os tipos do common language runtime (CLR) e os tipos de banco de dados do SQL Server são resumidas nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="e6389-105">These key mismatches between the common language runtime (CLR) types and the SQL Server database types are summarized in the following sections.</span></span> <span data-ttu-id="e6389-106">Você pode encontrar mais detalhes sobre mapeamentos de tipo específico e tradução de função em [mapeamento de tipo de SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) e [tipos de dados e funções](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md).</span><span class="sxs-lookup"><span data-stu-id="e6389-106">You can find more details about specific type mappings and function translation at [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) and [Data Types and Functions](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md).</span></span>

## <a name="data-types"></a><span data-ttu-id="e6389-107">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="e6389-107">Data Types</span></span>

<span data-ttu-id="e6389-108">A conversão entre CLR SQL Server e ocorre quando uma consulta está sendo enviadas a base de dados, e quando os resultados são novamente enviado ao seu modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="e6389-108">Translation between the CLR and SQL Server occurs when a query is being sent to the database, and when the results are sent back to your object model.</span></span> <span data-ttu-id="e6389-109">Por exemplo, a seguinte consulta de Transact-SQL requer duas conversões de valor:</span><span class="sxs-lookup"><span data-stu-id="e6389-109">For example, the following Transact-SQL query requires two value conversions:</span></span>

```sql
Select DateOfBirth From Customer Where CustomerId = @id
```

<span data-ttu-id="e6389-110">Antes que a consulta pode ser executada no SQL Server, o valor para o parâmetro de Transact-SQL deve ser especificado.</span><span class="sxs-lookup"><span data-stu-id="e6389-110">Before the query can be executed on SQL Server, the value for the Transact-SQL parameter must be specified.</span></span> <span data-ttu-id="e6389-111">Nesse exemplo, o valor do parâmetro de `id` deve primeiro ser convertido de um tipo de CLR <xref:System.Int32?displayProperty=nameWithType> a um tipo SQL Server `INT` de modo que a base de dados pode compreender o que o valor é.</span><span class="sxs-lookup"><span data-stu-id="e6389-111">In this example, the `id` parameter value must first be translated from a CLR <xref:System.Int32?displayProperty=nameWithType> type to a SQL Server `INT` type so that the database can understand what the value is.</span></span> <span data-ttu-id="e6389-112">Para recuperar os resultados, a coluna SQL Server `DateOfBirth` deve ser convertido de um tipo SQL Server `DATETIME` a um tipo de CLR <xref:System.DateTime?displayProperty=nameWithType> para uso no modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="e6389-112">Then to retrieve the results, the SQL Server `DateOfBirth` column must be translated from a SQL Server `DATETIME` type to a CLR <xref:System.DateTime?displayProperty=nameWithType> type for use in the object model.</span></span> <span data-ttu-id="e6389-113">Nesse exemplo, os tipos no modelo de objeto CLR e na base de dados SQL Server têm mapeamentos naturais.</span><span class="sxs-lookup"><span data-stu-id="e6389-113">In this example, the types in the CLR object model and SQL Server database have natural mappings.</span></span> <span data-ttu-id="e6389-114">Mas, isto não é sempre o caso.</span><span class="sxs-lookup"><span data-stu-id="e6389-114">But, this is not always the case.</span></span>

### <a name="missing-counterparts"></a><span data-ttu-id="e6389-115">Contrapartes ausentes</span><span class="sxs-lookup"><span data-stu-id="e6389-115">Missing Counterparts</span></span>

<span data-ttu-id="e6389-116">Os seguintes tipos não têm correspondentes razoáveis.</span><span class="sxs-lookup"><span data-stu-id="e6389-116">The following types do not have reasonable counterparts.</span></span>

- <span data-ttu-id="e6389-117">Incompatíveis no namespace de CLR <xref:System> :</span><span class="sxs-lookup"><span data-stu-id="e6389-117">Mismatches in the CLR <xref:System> namespace:</span></span>

  - <span data-ttu-id="e6389-118">**Inteiros sem sinal**.</span><span class="sxs-lookup"><span data-stu-id="e6389-118">**Unsigned integers**.</span></span> <span data-ttu-id="e6389-119">Esses tipos são mapeados normalmente a suas contrapartes assinados de tamanho maior para evitar estouro.</span><span class="sxs-lookup"><span data-stu-id="e6389-119">These types are typically mapped to their signed counterparts of larger size to avoid overflow.</span></span> <span data-ttu-id="e6389-120">Literais podem ser convertidos em um sinal numérico do mesmo ou de menor tamanho, com base no valor.</span><span class="sxs-lookup"><span data-stu-id="e6389-120">Literals can be converted to a signed numeric of the same or smaller size, based on value.</span></span>

  - <span data-ttu-id="e6389-121">**Booliano**.</span><span class="sxs-lookup"><span data-stu-id="e6389-121">**Boolean**.</span></span> <span data-ttu-id="e6389-122">Esses tipos podem ser mapeados para um bit ou um número maior ou uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e6389-122">These types can be mapped to a bit or larger numeric or string.</span></span> <span data-ttu-id="e6389-123">Um literal pode ser mapeado para uma expressão que avalia para o mesmo valor (por exemplo, `1=1` em SQL para `True` em CLS).</span><span class="sxs-lookup"><span data-stu-id="e6389-123">A literal can be mapped to an expression that evaluates to the same value (for example, `1=1` in SQL for `True` in CLS).</span></span>

  - <span data-ttu-id="e6389-124">**TimeSpan**.</span><span class="sxs-lookup"><span data-stu-id="e6389-124">**TimeSpan**.</span></span> <span data-ttu-id="e6389-125">Este tipo representa a diferença entre dois valores de `DateTime` e não corresponde a `timestamp` SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e6389-125">This type represents the difference between two `DateTime` values and does not correspond to the `timestamp` of SQL Server.</span></span> <span data-ttu-id="e6389-126">CLR <xref:System.TimeSpan?displayProperty=nameWithType> também pode mapear ao SQL Server `TIME` o tipo em alguns casos.</span><span class="sxs-lookup"><span data-stu-id="e6389-126">The CLR <xref:System.TimeSpan?displayProperty=nameWithType> may also map to the SQL Server `TIME` type in some cases.</span></span> <span data-ttu-id="e6389-127">O tipo do SQL Server `TIME` foi pretendido representar somente valores positivos menos de 24 horas.</span><span class="sxs-lookup"><span data-stu-id="e6389-127">The SQL Server `TIME` type was only intended to represent positive values less than 24 hours.</span></span> <span data-ttu-id="e6389-128">CLR <xref:System.TimeSpan> tem um intervalo muito maior.</span><span class="sxs-lookup"><span data-stu-id="e6389-128">The CLR <xref:System.TimeSpan> has a much larger range.</span></span>

  > [!NOTE]
  > <span data-ttu-id="e6389-129">Específicas do SQL Server [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] tipos no <xref:System.Data.SqlTypes> não estão incluídos nessa comparação.</span><span class="sxs-lookup"><span data-stu-id="e6389-129">SQL Server-specific [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] types in <xref:System.Data.SqlTypes> are not included in this comparison.</span></span>

- <span data-ttu-id="e6389-130">Incompatíveis no SQL Server:</span><span class="sxs-lookup"><span data-stu-id="e6389-130">Mismatches in SQL Server:</span></span>

  - <span data-ttu-id="e6389-131">**Tipos de caracteres de comprimento fixo**.</span><span class="sxs-lookup"><span data-stu-id="e6389-131">**Fixed length character types**.</span></span> <span data-ttu-id="e6389-132">Transact-SQL faz distinção entre categorias Unicode e não-Unicode e tem três tipos distintos em cada categoria: comprimento fixo `nchar` / `char`, de comprimento variável `nvarchar` / `varchar`, e tamanho maior `ntext` / `text`.</span><span class="sxs-lookup"><span data-stu-id="e6389-132">Transact-SQL distinguishes between Unicode and non-Unicode categories and has three distinct types in each category: fixed length `nchar`/`char`, variable length `nvarchar`/`varchar`, and larger-sized `ntext`/`text`.</span></span> <span data-ttu-id="e6389-133">Os tipos de caracteres de comprimento fixo podem ser mapeado para o tipo de CLR <xref:System.Char?displayProperty=nameWithType> para recuperar caracteres, mas não correspondem realmente o mesmo tipo em conversões e comportamento.</span><span class="sxs-lookup"><span data-stu-id="e6389-133">The fixed length character types could be mapped to the CLR <xref:System.Char?displayProperty=nameWithType> type for retrieving characters, but they do not really correspond to the same type in conversions and behavior.</span></span>

  - <span data-ttu-id="e6389-134">**Bit**.</span><span class="sxs-lookup"><span data-stu-id="e6389-134">**Bit**.</span></span> <span data-ttu-id="e6389-135">Embora o domínio de `bit` tem o mesmo número de valores que `Nullable<Boolean>`, os dois tipos são diferentes.</span><span class="sxs-lookup"><span data-stu-id="e6389-135">Although the `bit` domain has the same number of values as `Nullable<Boolean>`, the two are different types.</span></span> <span data-ttu-id="e6389-136">`Bit` usa os valores `1` e `0` em vez de `true` / `false`e não pode ser usado como um equivalente para expressões booleanas.</span><span class="sxs-lookup"><span data-stu-id="e6389-136">`Bit` takes values `1` and `0` instead of `true`/`false`, and cannot be used as an equivalent to Boolean expressions.</span></span>

  - <span data-ttu-id="e6389-137">**Carimbo de hora**.</span><span class="sxs-lookup"><span data-stu-id="e6389-137">**Timestamp**.</span></span> <span data-ttu-id="e6389-138">Ao contrário do tipo de CLR <xref:System.TimeSpan?displayProperty=nameWithType> , o tipo do SQL Server `TIMESTAMP` representa um número de 8 bytes gerado pelo base de dados que é exclusivo para cada atualização e não é baseado na diferença entre valores de <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="e6389-138">Unlike the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type, the SQL Server `TIMESTAMP` type represents an 8-byte number generated by the database that is unique for each update and is not based on the difference between <xref:System.DateTime> values.</span></span>

  - <span data-ttu-id="e6389-139">**Dinheiro** e **SmallMoney**.</span><span class="sxs-lookup"><span data-stu-id="e6389-139">**Money** and **SmallMoney**.</span></span> <span data-ttu-id="e6389-140">Esses tipos podem ser mapeados para <xref:System.Decimal> mas são basicamente tipos diferentes e são tratados como esta'n por funções e conversões pelo base.</span><span class="sxs-lookup"><span data-stu-id="e6389-140">These types can be mapped to <xref:System.Decimal> but are basically different types and are treated as such by server-based functions and conversions.</span></span>

### <a name="multiple-mappings"></a><span data-ttu-id="e6389-141">Vários mapeamentos</span><span class="sxs-lookup"><span data-stu-id="e6389-141">Multiple Mappings</span></span>

<span data-ttu-id="e6389-142">Há muitos tipos de dados do SQL Server que você pode mapear a CLR um ou mais tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="e6389-142">There are many SQL Server data types that you can map to one or more CLR data types.</span></span> <span data-ttu-id="e6389-143">Também há muitos tipos de CLR que você pode mapear a um ou mais tipos SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e6389-143">There are also many CLR types that you can map to one or more SQL Server types.</span></span> <span data-ttu-id="e6389-144">Embora um mapeamento pode ser suportados por LINQ to SQL, não significa que os dois tipos mapeadas entre CLR e o SQL Server são uma correspondência perfeita com precisão, intervalo, e semântica.</span><span class="sxs-lookup"><span data-stu-id="e6389-144">Although a mapping may be supported by LINQ to SQL, it does not mean that the two types mapped between the CLR and SQL Server are a perfect match in precision, range, and semantics.</span></span> <span data-ttu-id="e6389-145">Alguns mapeamentos podem incluir diferenças em algumas ou todas essas dimensões.</span><span class="sxs-lookup"><span data-stu-id="e6389-145">Some mappings may include differences in any or all of these dimensions.</span></span> <span data-ttu-id="e6389-146">Você pode encontrar detalhes sobre essas diferenças possíveis para as várias possibilidades de mapeamento no [mapeamento de tipo CLR SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="e6389-146">You can find details about these potential differences for the various mapping possibilities at [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>

### <a name="user-defined-types"></a><span data-ttu-id="e6389-147">Tipos definidos pelo usuário</span><span class="sxs-lookup"><span data-stu-id="e6389-147">User-defined Types</span></span>

<span data-ttu-id="e6389-148">Tipos definidos pelo usuário de CLR são criados para ajudar a ponte entre o intervalo do sistema de tipos.</span><span class="sxs-lookup"><span data-stu-id="e6389-148">User-defined CLR types are designed to help bridge the type system gap.</span></span> <span data-ttu-id="e6389-149">Entretanto problemas surgem interessantes sobre o controle de versão do tipo.</span><span class="sxs-lookup"><span data-stu-id="e6389-149">Nevertheless they surface interesting issues about type versioning.</span></span> <span data-ttu-id="e6389-150">Uma alteração na versão do cliente não pode ser correspondida por uma alteração no tipo armazenado no servidor de base de dados.</span><span class="sxs-lookup"><span data-stu-id="e6389-150">A change in the version on the client might not be matched by a change in the type stored on the database server.</span></span> <span data-ttu-id="e6389-151">Uma alteração causa um outros tipos incompatíveis onde a semântica de tipo pode não corresponder e o intervalo de versão é provável ficar visível.</span><span class="sxs-lookup"><span data-stu-id="e6389-151">Any such change causes another type mismatch where the type semantics might not match and the version gap is likely to become visible.</span></span> <span data-ttu-id="e6389-152">Uma complicações adicionais ocorrem a hierarquias de herança refactored em sucessivas versões.</span><span class="sxs-lookup"><span data-stu-id="e6389-152">Further complications occur as inheritance hierarchies are refactored in successive versions.</span></span>

## <a name="expression-semantics"></a><span data-ttu-id="e6389-153">Semântica de expressão</span><span class="sxs-lookup"><span data-stu-id="e6389-153">Expression Semantics</span></span>

<span data-ttu-id="e6389-154">Além de por pares a incompatibilidade entre CLR e tipos de base de dados, expressões adicionar complexidade a incompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="e6389-154">In addition to the pairwise mismatch between CLR and database types, expressions add complexity to the mismatch.</span></span> <span data-ttu-id="e6389-155">As incompatíveis na semântica de operador, na semântica de função, na conversão implícita de tipos, e as regras de precedência devem ser consideradas.</span><span class="sxs-lookup"><span data-stu-id="e6389-155">Mismatches in operator semantics, function semantics, implicit type conversion, and precedence rules must be considered.</span></span>

<span data-ttu-id="e6389-156">As seguintes subseções ilustram a incompatibilidade entre expressões aparentemente semelhantes.</span><span class="sxs-lookup"><span data-stu-id="e6389-156">The following subsections illustrate the mismatch between apparently similar expressions.</span></span> <span data-ttu-id="e6389-157">Talvez seja possível gerar as expressões SQL que são semanticamente equivalentes a uma expressão fornecida de CLR.</span><span class="sxs-lookup"><span data-stu-id="e6389-157">It might be possible to generate SQL expressions that are semantically equivalent to a given CLR expression.</span></span> <span data-ttu-id="e6389-158">No entanto, não é claro se semânticas as diferenças entre expressões aparentemente semelhantes são evidentes a um usuário de CLR, e portanto se as alterações que são necessárias para equivalências semântica estão se ou não.</span><span class="sxs-lookup"><span data-stu-id="e6389-158">However, it is not clear whether the semantic differences between apparently similar expressions are evident to a CLR user, and therefore whether the changes that are required for semantic equivalence are intended or not.</span></span> <span data-ttu-id="e6389-159">Isso é especialmente importante quando um assunto uma expressão é avaliada para um conjunto de valores.</span><span class="sxs-lookup"><span data-stu-id="e6389-159">This is an especially critical issue when an expression is evaluated for a set of values.</span></span> <span data-ttu-id="e6389-160">A visibilidade da diferença pode depender de dados e ser difícil de identificar durante a codificação e depuração.</span><span class="sxs-lookup"><span data-stu-id="e6389-160">The visibility of the difference might depend on data- and be hard to identify during coding and debugging.</span></span>

### <a name="null-semantics"></a><span data-ttu-id="e6389-161">Semântica nula</span><span class="sxs-lookup"><span data-stu-id="e6389-161">Null Semantics</span></span>

<span data-ttu-id="e6389-162">As expressões SQL fornecem lógica três avaliada para expressões booleanas.</span><span class="sxs-lookup"><span data-stu-id="e6389-162">SQL expressions provide three-valued logic for Boolean expressions.</span></span> <span data-ttu-id="e6389-163">O resultado pode ser true, false, ou zero.</span><span class="sxs-lookup"><span data-stu-id="e6389-163">The result can be true, false, or null.</span></span> <span data-ttu-id="e6389-164">Por outro lado, CLR especifica o resultado booleano duas avaliado para as comparações que envolvem valores nulos.</span><span class="sxs-lookup"><span data-stu-id="e6389-164">By contrast, CLR specifies two-valued Boolean result for comparisons involving null values.</span></span> <span data-ttu-id="e6389-165">Considere o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="e6389-165">Consider the following code:</span></span>

[!code-csharp[DLinqMismatch#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#2)]
[!code-vb[DLinqMismatch#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#2)]

```sql
-- Assume col1 and col2 are integer columns with null values.
-- Assume that ANSI null behavior has not been explicitly
--  turned off.
Select …
From …
Where col1 = col2
-- Evaluates to null, not true and the corresponding row is not
--   selected.
-- To obtain matching behavior (i -> col1, j -> col2) change
--   the query to the following:
Select …
From …
Where
    col1 = col2
or (col1 is null and col2 is null)
-- (Visual Basic 'Nothing'.)
```

<span data-ttu-id="e6389-166">Um problema semelhante ocorre com a suposição sobre resultados duas avaliados.</span><span class="sxs-lookup"><span data-stu-id="e6389-166">A similar problem occurs with the assumption about two-valued results.</span></span>

[!code-csharp[DLinqMismatch#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#3)]
[!code-vb[DLinqMismatch#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#3)]

```sql
-- Assume col1 and col2 are nullable columns.
-- Assume that ANSI null behavior has not been explicitly
--   turned off.
Select …
From …
Where
    col1 = col2
or col1 != col2
-- Visual Basic: col1 <> col2.

-- Excludes the case where the boolean expression evaluates
--   to null. Therefore the where clause does not always
--   evaluate to true.
```

<span data-ttu-id="e6389-167">Em casos anteriores, você pode obter o comportamento equivalente em gerar o SQL, mas a conversão não pode exatamente refletir sua intenção.</span><span class="sxs-lookup"><span data-stu-id="e6389-167">In the previous case, you can get equivalent behavior in generating SQL, but the translation might not accurately reflect your intention.</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e6389-168">não impõe C# `null` ou o Visual Basic `nothing` semântica de comparação no SQL.</span><span class="sxs-lookup"><span data-stu-id="e6389-168">does not impose C# `null` or Visual Basic `nothing` comparison semantics on SQL.</span></span> <span data-ttu-id="e6389-169">Os operadores de comparação são convertidos sintaticamente para seus equivalentes SQL.</span><span class="sxs-lookup"><span data-stu-id="e6389-169">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="e6389-170">Semânticas reflete a semântica do SQL como definida pelas configurações do servidor ou de conexão.</span><span class="sxs-lookup"><span data-stu-id="e6389-170">The semantics reflect SQL semantics as defined by server or connection settings.</span></span> <span data-ttu-id="e6389-171">Dois valores nulos são considerados configurações padrão inferiores desiguais SQL Server (embora você possa alterar as configurações para alterar a semântica).</span><span class="sxs-lookup"><span data-stu-id="e6389-171">Two null values are considered unequal under default SQL Server settings (although you can change the settings to change the semantics).</span></span> <span data-ttu-id="e6389-172">De qualquer forma, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não considera configurações de servidor para a tradução de consulta.</span><span class="sxs-lookup"><span data-stu-id="e6389-172">Regardless, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not consider server settings in query translation.</span></span>

<span data-ttu-id="e6389-173">Uma comparação com `null` literal (`nothing`) é convertido para a versão apropriada do SQL (`is null` ou `is not null`).</span><span class="sxs-lookup"><span data-stu-id="e6389-173">A comparison with the literal `null` (`nothing`) is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>

<span data-ttu-id="e6389-174">O valor de `null` (`nothing`) na ordenação é definido pelo SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não altera a ordenação.</span><span class="sxs-lookup"><span data-stu-id="e6389-174">The value of `null` (`nothing`) in collation is defined by SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not change the collation.</span></span>

### <a name="type-conversion-and-promotion"></a><span data-ttu-id="e6389-175">Conversão de tipos e promoção</span><span class="sxs-lookup"><span data-stu-id="e6389-175">Type Conversion and Promotion</span></span>

<span data-ttu-id="e6389-176">O SQL suporta um conjunto rico de conversões implícitas em expressões.</span><span class="sxs-lookup"><span data-stu-id="e6389-176">SQL supports a rich set of implicit conversions in expressions.</span></span> <span data-ttu-id="e6389-177">As expressões semelhantes em C# exigiriam uma conversão explícita.</span><span class="sxs-lookup"><span data-stu-id="e6389-177">Similar expressions in C# would require an explicit cast.</span></span> <span data-ttu-id="e6389-178">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e6389-178">For example:</span></span>

- <span data-ttu-id="e6389-179">`Nvarchar` e os tipos de `DateTime` podem ser comparadas em SQL sem nenhuma conversões explícitas; C# requer conversão explícita.</span><span class="sxs-lookup"><span data-stu-id="e6389-179">`Nvarchar` and `DateTime` types can be compared in SQL without any explicit casts; C# requires explicit conversion.</span></span>

- <span data-ttu-id="e6389-180">`Decimal` é convertido implicitamente a `DateTime` no SQL.</span><span class="sxs-lookup"><span data-stu-id="e6389-180">`Decimal` is implicitly converted to `DateTime` in SQL.</span></span> <span data-ttu-id="e6389-181">C# não permite uma conversão implícita.</span><span class="sxs-lookup"><span data-stu-id="e6389-181">C# does not allow for an implicit conversion.</span></span>

<span data-ttu-id="e6389-182">Também, a precedência de tipo em Transact-SQL difere de precedência de tipo em C# porque o conjunto sendo a base de tipos é diferente.</span><span class="sxs-lookup"><span data-stu-id="e6389-182">Likewise, type precedence in Transact-SQL differs from type precedence in C# because the underlying set of types is different.</span></span> <span data-ttu-id="e6389-183">De fato, não há nenhuma relação clara do subconjunto/superconjunto entre as listas de precedência.</span><span class="sxs-lookup"><span data-stu-id="e6389-183">In fact, there is no clear subset/superset relationship between the precedence lists.</span></span> <span data-ttu-id="e6389-184">Por exemplo, `nvarchar` comparar com `varchar` faz com que a conversão implícita da expressão de `varchar` a `nvarchar`.</span><span class="sxs-lookup"><span data-stu-id="e6389-184">For example, comparing an `nvarchar` with a `varchar` causes the implicit conversion of the `varchar` expression to `nvarchar`.</span></span> <span data-ttu-id="e6389-185">CLR não fornece nenhuma promoção equivalente.</span><span class="sxs-lookup"><span data-stu-id="e6389-185">The CLR provides no equivalent promotion.</span></span>

<span data-ttu-id="e6389-186">Em casos simples, essas diferenças fazem com que as expressões de CLR com conversões sejam redundantes para uma expressão correspondente SQL.</span><span class="sxs-lookup"><span data-stu-id="e6389-186">In simple cases, these differences cause CLR expressions with casts to be redundant for a corresponding SQL expression.</span></span> <span data-ttu-id="e6389-187">Mais importante, os resultados intermediários de uma expressão SQL podem ser implicitamente promovidos para um tipo que não tem contraparte exata em C#, e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="e6389-187">More importantly, the intermediate results of a SQL expression might be implicitly promoted to a type that has no accurate counterpart in C#, and vice versa.</span></span> <span data-ttu-id="e6389-188">Total, os testes, depuração, e a validação dessas expressões adiciona a carga significativa no usuário.</span><span class="sxs-lookup"><span data-stu-id="e6389-188">Overall, the testing, debugging, and validation of such expressions adds significant burden on the user.</span></span>

### <a name="collation"></a><span data-ttu-id="e6389-189">Ordenação</span><span class="sxs-lookup"><span data-stu-id="e6389-189">Collation</span></span>

<span data-ttu-id="e6389-190">Transact-SQL suporta ordenações explícitas como as anotações a cadeia de caracteres tipo.</span><span class="sxs-lookup"><span data-stu-id="e6389-190">Transact-SQL supports explicit collations as annotations to character string types.</span></span> <span data-ttu-id="e6389-191">Essas ordenações determinam a validade de determinadas comparações.</span><span class="sxs-lookup"><span data-stu-id="e6389-191">These collations determine the validity of certain comparisons.</span></span> <span data-ttu-id="e6389-192">Por exemplo, comparar duas colunas com diferentes ordenações explícitas é um erro.</span><span class="sxs-lookup"><span data-stu-id="e6389-192">For example, comparing two columns with different explicit collations is an error.</span></span> <span data-ttu-id="e6389-193">O uso do tipo muito mais simples de cadeia de caracteres de CTS não causa esses erros.</span><span class="sxs-lookup"><span data-stu-id="e6389-193">The use of much simplified CTS string type does not cause such errors.</span></span> <span data-ttu-id="e6389-194">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e6389-194">Consider the following example:</span></span>

```sql
create table T2 (
    Col1 nvarchar(10),
    Col2      nvarchar(10) collate Latin_general_ci_as
)
```

[!code-csharp[DLinqMismatch#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#4)]
[!code-vb[DLinqMismatch#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#4)]

```sql
Select …
From …
Where Col1 = Col2
-- Error, collation conflict.
```

<span data-ttu-id="e6389-195">Na verdade, o subclause de agrupamento cria uma *restritos de tipo* que não é substitutable.</span><span class="sxs-lookup"><span data-stu-id="e6389-195">In effect, the collation subclause creates a *restricted type* that is not substitutable.</span></span>

<span data-ttu-id="e6389-196">Da mesma forma, a ordem de classificação pode ser significativamente diferente entre sistemas de tipos.</span><span class="sxs-lookup"><span data-stu-id="e6389-196">Similarly, the sort order can be significantly different across the type systems.</span></span> <span data-ttu-id="e6389-197">Essa diferença afeta a classificação dos resultados.</span><span class="sxs-lookup"><span data-stu-id="e6389-197">This difference affects the sorting of results.</span></span> <span data-ttu-id="e6389-198"><xref:System.Guid> são classificadas em todos os 16 bytes pela ordem lexicographic (`IComparable()`), enquanto T-SQL compara GUIDs na seguinte ordem: (nó 10-15), relógio- segs. (8-9), Hora- alto (6-7), Hora- mid (4-5), Hora- baixo (0-3).</span><span class="sxs-lookup"><span data-stu-id="e6389-198"><xref:System.Guid> is sorted on all 16 bytes by lexicographic order (`IComparable()`), whereas T-SQL compares GUIDs in the following order: node(10-15), clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3).</span></span> <span data-ttu-id="e6389-199">Isso regras que foi feito no SQL 7.0 GUIDs gerado quando NT- tinha uma ordem de octeto.</span><span class="sxs-lookup"><span data-stu-id="e6389-199">This ordering was done in SQL 7.0 when NT-generated GUIDs had such an octet order.</span></span> <span data-ttu-id="e6389-200">A abordagem de assegurou-se que GUIDs gerado no mesmo conjunto de nó viesse juntos em ordem sequencial de acordo com o carimbo de data/hora.</span><span class="sxs-lookup"><span data-stu-id="e6389-200">The approach ensured that GUIDs generated at the same node cluster came together in sequential order according to timestamp.</span></span> <span data-ttu-id="e6389-201">A abordagem também é útil para compilar índices (inserções se tornam append em vez de IOs aleatório).</span><span class="sxs-lookup"><span data-stu-id="e6389-201">The approach was also useful for building indexes (inserts become appends instead of random IOs).</span></span> <span data-ttu-id="e6389-202">A ordem scrambled posteriormente no Windows devido a interesses privacidade, mas o SQL deve manter compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="e6389-202">The order was scrambled later in Windows because of privacy concerns, but SQL must maintain compatibility.</span></span> <span data-ttu-id="e6389-203">Uma solução alternativa é usar <xref:System.Data.SqlTypes.SqlGuid> em vez de <xref:System.Guid>.</span><span class="sxs-lookup"><span data-stu-id="e6389-203">A workaround is to use <xref:System.Data.SqlTypes.SqlGuid> instead of <xref:System.Guid>.</span></span>

### <a name="operator-and-function-differences"></a><span data-ttu-id="e6389-204">Operador e diferenças de função</span><span class="sxs-lookup"><span data-stu-id="e6389-204">Operator and Function Differences</span></span>

<span data-ttu-id="e6389-205">Os operadores e funções que são essencialmente comparáveis têm a semântica ligeiramente diferente.</span><span class="sxs-lookup"><span data-stu-id="e6389-205">Operators and functions that are essentially comparable have subtly different semantics.</span></span> <span data-ttu-id="e6389-206">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e6389-206">For example:</span></span>

- <span data-ttu-id="e6389-207">Especifica C# procura por um caminho menor a semântica com base na ordem lexicalmente de operandos para operadores lógicos `&&` e `||`.</span><span class="sxs-lookup"><span data-stu-id="e6389-207">C# specifies short circuit semantics based on lexical order of operands for logical operators `&&` and `||`.</span></span> <span data-ttu-id="e6389-208">O SQL por outro lado é definido para consultas definir - com base e portanto fornece mais liberdade de otimizador para decidir a ordem de execução.</span><span class="sxs-lookup"><span data-stu-id="e6389-208">SQL on the other hand is targeted for set-based queries and therefore provides more freedom for the optimizer to decide the order of execution.</span></span> <span data-ttu-id="e6389-209">Algumas implicações incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e6389-209">Some of the implications include the following:</span></span>

  - <span data-ttu-id="e6389-210">Conversão semanticamente equivalente exigiria "`CASE` ...</span><span class="sxs-lookup"><span data-stu-id="e6389-210">Semantically equivalent translation would require "`CASE` …</span></span> <span data-ttu-id="e6389-211">`WHEN` …</span><span class="sxs-lookup"><span data-stu-id="e6389-211">`WHEN` …</span></span> <span data-ttu-id="e6389-212">`THEN`"construir em SQL evitar reordenar de execução dos operandos.</span><span class="sxs-lookup"><span data-stu-id="e6389-212">`THEN`" construct in SQL to avoid reordering of operand execution.</span></span>

  - <span data-ttu-id="e6389-213">Uma conversão fraca a `AND` / `OR` pode causar erros inesperados se o C# expressão depende da avaliação o segundo operando sendo baseado no resultado da avaliação do primeiro operando.</span><span class="sxs-lookup"><span data-stu-id="e6389-213">A loose translation to `AND`/`OR` operators could cause unexpected errors if the C# expression relies on evaluation the second operand being based on the result of the evaluation of the first operand.</span></span>

- <span data-ttu-id="e6389-214">a função de`Round()` tem a semântica diferente em [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] e em T-SQL.</span><span class="sxs-lookup"><span data-stu-id="e6389-214">`Round()` function has different semantics in [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] and in T-SQL.</span></span>

- <span data-ttu-id="e6389-215">Iniciar o índice para cadeias de caracteres é 0 em CLR mas 1 no SQL.</span><span class="sxs-lookup"><span data-stu-id="e6389-215">Starting index for strings is 0 in the CLR but 1 in SQL.</span></span> <span data-ttu-id="e6389-216">Portanto, qualquer função que tem a conversão de índice das necessidades de índice.</span><span class="sxs-lookup"><span data-stu-id="e6389-216">Therefore, any function that has index needs index translation.</span></span>

- <span data-ttu-id="e6389-217">O módulo de suporte de CLR (“% ") o operador para números de ponto flutuante mas SQL não.</span><span class="sxs-lookup"><span data-stu-id="e6389-217">The CLR supports modulus (‘%’) operator for floating point numbers but SQL does not.</span></span>

- <span data-ttu-id="e6389-218">O operador de `Like` efetivamente chamando as sobrecargas automático com base em conversões implícitas.</span><span class="sxs-lookup"><span data-stu-id="e6389-218">The `Like` operator effectively acquires automatic overloads based on implicit conversions.</span></span> <span data-ttu-id="e6389-219">Embora o operador de `Like` é definido para operar em tipos de cadeia de caracteres, a conversão implícita de tipos numéricos ou de tipos de `DateTime` permite esses tipos não-cadeia de caracteres a ser usado assim como com `Like` .</span><span class="sxs-lookup"><span data-stu-id="e6389-219">Although the `Like` operator is defined to operate on character string types, implicit conversion from numeric types or `DateTime` types allows for those non-string types to be used with `Like` just as well.</span></span> <span data-ttu-id="e6389-220">Em CTS, as conversões implícitas comparáveis não existem.</span><span class="sxs-lookup"><span data-stu-id="e6389-220">In CTS, comparable implicit conversions do not exist.</span></span> <span data-ttu-id="e6389-221">Portanto, as sobrecargas adicionais são necessárias.</span><span class="sxs-lookup"><span data-stu-id="e6389-221">Therefore, additional overloads are needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e6389-222">Este comportamento do operador de `Like` se aplica a C# somente; a palavra-chave do Visual Basic `Like` é inalterado.</span><span class="sxs-lookup"><span data-stu-id="e6389-222">This `Like` operator behavior applies to C# only; the Visual Basic `Like` keyword is unchanged.</span></span>

- <span data-ttu-id="e6389-223">Estouro sempre é verificado no SQL, mas ele deve ser especificado explicitamente no C# (não no Visual Basic) para evitar o wraparound.</span><span class="sxs-lookup"><span data-stu-id="e6389-223">Overflow is always checked in SQL but it has to be explicitly specified in C# (not in Visual Basic) to avoid wraparound.</span></span> <span data-ttu-id="e6389-224">Colunas disponíveis C1, C2 e C3 inteiro, se C1+C2 é armazenado em C3 (atualização T ajustada C3 = C1 + C2).</span><span class="sxs-lookup"><span data-stu-id="e6389-224">Given integer columns C1, C2 and C3, if C1+C2 is stored in C3 (Update T Set C3 = C1 + C2).</span></span>

    ```sql
    create table T3 (
        Col1      integer,
        Col2      integer
    )
    insert into T3 (col1, col2) values (2147483647, 5)
    -- Valid values: max integer value and 5.
    select * from T3 where col1 + col2 < 0
    -- Produces arithmetic overflow error.
    ```

[!code-csharp[DLinqMismatch#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#5)]
[!code-vb[DLinqMismatch#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#5)]

- <span data-ttu-id="e6389-225">O SQL arredondamento executa aritmética simétrico quando usar [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] de arredondamento bancário.</span><span class="sxs-lookup"><span data-stu-id="e6389-225">SQL performs symmetric arithmetic rounding while [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] uses banker’s rounding.</span></span> <span data-ttu-id="e6389-226">Consulte o artigo 196652 da knowledgebase para obter detalhes adicionais.</span><span class="sxs-lookup"><span data-stu-id="e6389-226">See Knowledgebase article 196652 for additional details.</span></span>

- <span data-ttu-id="e6389-227">Por padrão, para localidades comuns, as comparações de cadeia de caracteres não diferenciam maiúsculas de minúsculas no SQL.</span><span class="sxs-lookup"><span data-stu-id="e6389-227">By default, for common locales, character-string comparisons are case-insensitive in SQL.</span></span> <span data-ttu-id="e6389-228">No Visual Basic e C#, diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="e6389-228">In Visual Basic and in C#, they are case-sensitive.</span></span> <span data-ttu-id="e6389-229">Por exemplo, `s == "Food"` (`s = "Food"` no Visual Basic) e `s == "Food"` pode produzir resultados diferentes se `s` é `food`.</span><span class="sxs-lookup"><span data-stu-id="e6389-229">For example, `s == "Food"` (`s = "Food"` in Visual Basic) and `s == "Food"` can yield different results if `s` is `food`.</span></span>

    ```sql
    -- Assume default US-English locale (case insensitive).
    create table T4 (
        Col1      nvarchar (256)
    )
    insert into T4 values (‘Food’)
    insert into T4 values (‘FOOD’)
    select * from T4 where Col1 = ‘food’
    -- Both the rows are returned because of case-insensitive matching.
    ```

[!code-csharp[DLinqMismatch#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#6)]
[!code-vb[DLinqMismatch#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#6)]

- <span data-ttu-id="e6389-230">Funções de operadores aplicadas a fixos argumentos de tipo de caracteres de comprimento em SQL têm a semântica significativamente diferente do que os mesmos operadores/funções aplicados a CLR <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6389-230">Operators/ functions applied to fixed length character type arguments in SQL have significantly different semantics than the same operators/functions applied to the CLR <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e6389-231">Isso pode também ser exibido como uma extensão do problema ausente de contrapartes discutido na seção sobre tipos.</span><span class="sxs-lookup"><span data-stu-id="e6389-231">This could also be viewed as an extension of the missing counterpart problem discussed in the section about types.</span></span>

    ```sql
    create table T4 (
        Col1      nchar(4)
    )
    Insert into T5(Col1) values ('21');
    Insert into T5(Col1) values ('1021');
    Select * from T5 where Col1 like '%1'
    -- Only the second row with Col1 = '1021' is returned.
    -- Not the first row!
    ```

     [!code-csharp[DLinqMismatch#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#7)]
     [!code-vb[DLinqMismatch#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#7)]

     <span data-ttu-id="e6389-232">Um problema semelhante ocorre com concatenação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e6389-232">A similar problem occurs with string concatenation.</span></span>

    ```sql
    create table T6 (
        Col1      nchar(4)
        Col2       nchar(4)
    )
    Insert into T6 values ('a', 'b');
    Select Col1+Col2 from T6
    -- Returns concatenation of padded strings "a   b   " and not "ab".
    ```

<span data-ttu-id="e6389-233">Em resumo, uma translação complicada pode ser necessária para expressões de CLR e os operadores/funções podem ser necessários para expor a funcionalidade SQL.</span><span class="sxs-lookup"><span data-stu-id="e6389-233">In summary, a convoluted translation might be required for CLR expressions and additional operators/functions may be necessary to expose SQL functionality.</span></span>

### <a name="type-casting"></a><span data-ttu-id="e6389-234">Conversão de tipo</span><span class="sxs-lookup"><span data-stu-id="e6389-234">Type Casting</span></span>

<span data-ttu-id="e6389-235">Em C# e no SQL, os usuários podem subtituir a semântica padrão de expressões usando conversões explícitas de tipos (`Cast` e `Convert`).</span><span class="sxs-lookup"><span data-stu-id="e6389-235">In C# and in SQL, users can override the default semantics of expressions by using explicit type casts (`Cast` and `Convert`).</span></span> <span data-ttu-id="e6389-236">No entanto, expor esse recurso até o limite do sistema de tipos gerencie um dilema.</span><span class="sxs-lookup"><span data-stu-id="e6389-236">However, exposing this capability across the type system boundary poses a dilemma.</span></span> <span data-ttu-id="e6389-237">Um SQL converte-se que fornecesse a semântica desejada não pode facilmente ser convertido para uma conversão correspondente C#.</span><span class="sxs-lookup"><span data-stu-id="e6389-237">A SQL cast that provides the desired semantics cannot be easily translated to a corresponding C# cast.</span></span> <span data-ttu-id="e6389-238">Por outro lado, uma conversão C# não pode diretamente ser convertida em um equivalente SQL convertido devido aos tipos incompatíveis, a contrapartes ausente, e para hierarquias diferentes de precedência de tipo.</span><span class="sxs-lookup"><span data-stu-id="e6389-238">On the other hand, a C# cast cannot be directly translated into an equivalent SQL cast because of type mismatches, missing counterparts, and different type precedence hierarchies.</span></span> <span data-ttu-id="e6389-239">Há uma escolha entre a exposição de incompatibilidade do sistema de tipos e poder significativa perdedora da expressão.</span><span class="sxs-lookup"><span data-stu-id="e6389-239">There is a trade-off between exposing the type system mismatch and losing significant power of expression.</span></span>

<span data-ttu-id="e6389-240">Em outros casos, a conversão de tipo não pode ser necessária em qualquer domínio para validação de uma expressão mas pode ser necessária para certificar-se de que um mapeamento padrão não é aplicado corretamente para a expressão.</span><span class="sxs-lookup"><span data-stu-id="e6389-240">In other cases, type casting might not be needed in either domain for validation of an expression but might be required to make sure that a non-default mapping is correctly applied to the expression.</span></span>

```sql
-- Example from "Non-default Mapping" section extended
create table T5 (
    Col1      nvarchar(10),
    Col2      nvarchar(10)
)
Insert into T5(col1, col2) values (‘3’, ‘2’);
```

[!code-csharp[DLinqMismatch#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#8)]
[!code-vb[DLinqMismatch#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#8)]

```sql
Select *
From T5
Where Col1 + Col2 > 4
-- "Col1 + Col2" expr evaluates to '32'
```

## <a name="performance-issues"></a><span data-ttu-id="e6389-241">Problemas de desempenho</span><span class="sxs-lookup"><span data-stu-id="e6389-241">Performance Issues</span></span>

<span data-ttu-id="e6389-242">Diferenças de tipo de contabilidade para algumas-CLR do SQL Server podem resultar em uma queda no desempenho ao cruzar-se entre CLR e SQL Server sistemas de tipos.</span><span class="sxs-lookup"><span data-stu-id="e6389-242">Accounting for some SQL Server-CLR type differences may result in a decrease in performance when crossing between the CLR and SQL Server type systems.</span></span> <span data-ttu-id="e6389-243">Exemplos de cenários que afetam o desempenho incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e6389-243">Examples of scenarios impacting performance include the following:</span></span>

- <span data-ttu-id="e6389-244">Forçado a ordem de classificação para lógico e/ou operadores</span><span class="sxs-lookup"><span data-stu-id="e6389-244">Forced order of evaluation for logical and/or operators</span></span>

- <span data-ttu-id="e6389-245">Gerar o SQL para aplicar a ordem de classificação de predicado restringe a capacidade de otimizador SQL.</span><span class="sxs-lookup"><span data-stu-id="e6389-245">Generating SQL to enforce order of predicate evaluation restricts the SQL optimizer’s ability.</span></span>

- <span data-ttu-id="e6389-246">Conversões de tipos, se introduzido por um compilador de CLR ou por uma implementação objeto relacional de consulta, podem reduzir o uso de índice.</span><span class="sxs-lookup"><span data-stu-id="e6389-246">Type conversions, whether introduced by a CLR compiler or by an Object-Relational query implementation, may curtail index usage.</span></span>

     <span data-ttu-id="e6389-247">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="e6389-247">For example,</span></span>

    ```sql
    -- Table DDL
    create table T5 (
        Col1      varchar(100)
    )
    ```

     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]

     <span data-ttu-id="e6389-248">Considere a conversão de expressão `(s = SOME_STRING_CONSTANT)`.</span><span class="sxs-lookup"><span data-stu-id="e6389-248">Consider the translation of expression `(s = SOME_STRING_CONSTANT)`.</span></span>

    ```sql
    -- Corresponding part of SQL where clause
    Where …
    Col1 = SOME_STRING_CONSTANT
    -- This expression is of the form <varchar> = <nvarchar>.
    -- Hence SQL introduces a conversion from varchar to nvarchar,
    --   resulting in
    Where …
    Convert(nvarchar(100), Col1) = SOME_STRING_CONSTANT
    -- Cannot use the index for column Col1 for some implementations.
    ```

<span data-ttu-id="e6389-249">Além de diferenças semânticas, é importante considerar impactos o desempenho ao cruzar-se entre o SQL Server e sistemas de tipos de CLR.</span><span class="sxs-lookup"><span data-stu-id="e6389-249">In addition to semantic differences, it is important to consider impacts to performance when crossing between the SQL Server and CLR type systems.</span></span> <span data-ttu-id="e6389-250">Para grandes conjuntos de dados, tais problemas de desempenho podem determinar se um aplicativo está deployable.</span><span class="sxs-lookup"><span data-stu-id="e6389-250">For large data sets, such performance issues can determine whether an application is deployable.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6389-251">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6389-251">See also</span></span>

- [<span data-ttu-id="e6389-252">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="e6389-252">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
