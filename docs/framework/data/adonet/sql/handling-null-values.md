---
title: Manipulando valores nulos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8467d1748cec216c01756049d889ea29f02c3c7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="handling-null-values"></a><span data-ttu-id="26668-102">Manipulando valores nulos</span><span class="sxs-lookup"><span data-stu-id="26668-102">Handling Null Values</span></span>
<span data-ttu-id="26668-103">Um valor nulo em um banco de dados relacional é usado quando o valor em uma coluna é desconhecido ou ausente.</span><span class="sxs-lookup"><span data-stu-id="26668-103">A null value in a relational database is used when the value in a column is unknown or missing.</span></span> <span data-ttu-id="26668-104">Um nulo não é uma cadeia de caracteres vazia (para os tipos de dados character ou datetime) nem um valor zero (para tipos de dados numéricos).</span><span class="sxs-lookup"><span data-stu-id="26668-104">A null is neither an empty string (for character or datetime data types) nor a zero value (for numeric data types).</span></span> <span data-ttu-id="26668-105">A especificação ANSI SQL-92 indica que um valor nulo deve ser o mesmo para todos os tipos de dados, para que todos os nulos sejam tratados consistentemente.</span><span class="sxs-lookup"><span data-stu-id="26668-105">The ANSI SQL-92 specification states that a null must be the same for all data types, so that all nulls are handled consistently.</span></span> <span data-ttu-id="26668-106">O namespace <xref:System.Data.SqlTypes> fornece uma semântica nula implementando a interface <xref:System.Data.SqlTypes.INullable>.</span><span class="sxs-lookup"><span data-stu-id="26668-106">The <xref:System.Data.SqlTypes> namespace provides null semantics by implementing the <xref:System.Data.SqlTypes.INullable> interface.</span></span> <span data-ttu-id="26668-107">Cada um dos tipos de dados no <xref:System.Data.SqlTypes> tem sua própria propriedade `IsNull` e um valor `Null` que pode ser atribuído a uma instância desse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="26668-107">Each of the data types in <xref:System.Data.SqlTypes> has its own `IsNull` property and a `Null` value that can be assigned to an instance of that data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26668-108">O .NET Framework versão 2.0 incorporou o suporte a tipos que permitem valores nulos, proporcionando aos programadores meios de estender um tipo de valor para representar todos os valores do tipo subjacente.</span><span class="sxs-lookup"><span data-stu-id="26668-108">The .NET Framework version 2.0 introduced support for nullable types, which allow programmers to extend a value type to represent all values of the underlying type.</span></span> <span data-ttu-id="26668-109">Esses tipos CLR que permitem valores nulos representam uma instância da estrutura <xref:System.Nullable>.</span><span class="sxs-lookup"><span data-stu-id="26668-109">These CLR nullable types represent an instance of the <xref:System.Nullable> structure.</span></span> <span data-ttu-id="26668-110">Esse recurso é especialmente útil quando os tipos de valor são boxed e unboxed, fornecendo uma compatibilidade aprimorada com os tipos de objeto.</span><span class="sxs-lookup"><span data-stu-id="26668-110">This capability is especially useful when value types are boxed and unboxed, providing enhanced compatibility with object types.</span></span> <span data-ttu-id="26668-111">Os tipos CLR que permitem valores nulos não se destinam ao armazenamento dos valores nulos do banco de dados, pois um valor nulo ANSI SQL não se comporta da mesma maneira que uma referência `null` (ou `Nothing` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="26668-111">CLR nullable types are not intended for storage of database nulls because an ANSI SQL null does not behave the same way as a `null` reference (or `Nothing` in Visual Basic).</span></span> <span data-ttu-id="26668-112">Para trabalhar com valores nulos ANSI SQL do banco de dados, use os valores nulos <xref:System.Data.SqlTypes>, em vez de <xref:System.Nullable>.</span><span class="sxs-lookup"><span data-stu-id="26668-112">For working with database ANSI SQL null values, use <xref:System.Data.SqlTypes> nulls rather than <xref:System.Nullable>.</span></span> <span data-ttu-id="26668-113">Para obter mais informações sobre como trabalhar com CLR tipos anuláveis no Visual Basic consulte [tipos de valor anuláveis](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)e para c#, consulte [usando tipos anuláveis](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md).</span><span class="sxs-lookup"><span data-stu-id="26668-113">For more information on working with CLR nullable types in Visual Basic see [Nullable Value Types](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md), and for C# see [Using Nullable Types](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md).</span></span>  
  
## <a name="nulls-and-three-valued-logic"></a><span data-ttu-id="26668-114">Valores nulos e lógica de três valores</span><span class="sxs-lookup"><span data-stu-id="26668-114">Nulls and Three-Valued Logic</span></span>  
 <span data-ttu-id="26668-115">A permissão de valores nulos em definições de coluna incorpora a lógica de três valores no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26668-115">Allowing null values in column definitions introduces three-valued logic into your application.</span></span> <span data-ttu-id="26668-116">Uma comparação pode ser avaliada como uma das três condições:</span><span class="sxs-lookup"><span data-stu-id="26668-116">A comparison can evaluate to one of three conditions:</span></span>  
  
-   <span data-ttu-id="26668-117">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="26668-117">True</span></span>  
  
-   <span data-ttu-id="26668-118">False</span><span class="sxs-lookup"><span data-stu-id="26668-118">False</span></span>  
  
-   <span data-ttu-id="26668-119">Unknown</span><span class="sxs-lookup"><span data-stu-id="26668-119">Unknown</span></span>  
  
 <span data-ttu-id="26668-120">Como o valor número é considerado desconhecido, dois valores nulos comparados entre si não são considerados iguais.</span><span class="sxs-lookup"><span data-stu-id="26668-120">Because null is considered to be unknown, two null values compared to each other are not considered to be equal.</span></span> <span data-ttu-id="26668-121">Nas expressões que usam operadores aritméticos, se qualquer um dos operandos for nulo, o resultado também será nulo.</span><span class="sxs-lookup"><span data-stu-id="26668-121">In expressions using arithmetic operators, if any of the operands is null, the result is null as well.</span></span>  
  
## <a name="nulls-and-sqlboolean"></a><span data-ttu-id="26668-122">Valores nulos e SqlBoolean</span><span class="sxs-lookup"><span data-stu-id="26668-122">Nulls and SqlBoolean</span></span>  
 <span data-ttu-id="26668-123">A comparação entre qualquer <xref:System.Data.SqlTypes> retornará <xref:System.Data.SqlTypes.SqlBoolean>.</span><span class="sxs-lookup"><span data-stu-id="26668-123">Comparison between any <xref:System.Data.SqlTypes> will return a <xref:System.Data.SqlTypes.SqlBoolean>.</span></span> <span data-ttu-id="26668-124">A função `IsNull` de cada `SqlType` retornará <xref:System.Data.SqlTypes.SqlBoolean> e poderá ser usada para verificar valores nulos.</span><span class="sxs-lookup"><span data-stu-id="26668-124">The `IsNull` function for each `SqlType` returns a <xref:System.Data.SqlTypes.SqlBoolean> and can be used to check for null values.</span></span> <span data-ttu-id="26668-125">As seguintes tabelas da verdade mostram como os operadores AND, OR e NO funcionam na presença de um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="26668-125">The following truth tables show how the AND, OR, and NOT operators function in the presence of a null value.</span></span> <span data-ttu-id="26668-126">(T=verdadeiro, F=falso e U=desconhecido ou nulo.)</span><span class="sxs-lookup"><span data-stu-id="26668-126">(T=true, F=false, and U=unknown, or null.)</span></span>  
  
 <span data-ttu-id="26668-127">![Tabela verdade](../../../../../docs/framework/data/adonet/sql/media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span><span class="sxs-lookup"><span data-stu-id="26668-127">![Truth Table](../../../../../docs/framework/data/adonet/sql/media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span></span>  
  
### <a name="understanding-the-ansinulls-option"></a><span data-ttu-id="26668-128">Noções básicas sobre a opção ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="26668-128">Understanding the ANSI_NULLS Option</span></span>  
 <span data-ttu-id="26668-129"><xref:System.Data.SqlTypes> fornece a mesma semântica do que a proporcionada quando a opção ANSI_NULLS é definida no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="26668-129"><xref:System.Data.SqlTypes> provides the same semantics as when the ANSI_NULLS option is set on in SQL Server.</span></span> <span data-ttu-id="26668-130">Todos os operadores aritméticos (+, -, *, /, %), operadores bit a bit (~, &, &#124;), e a maioria das funções de retorno nulo se qualquer um dos operandos ou argumentos for null, exceto para a propriedade `IsNull`.</span><span class="sxs-lookup"><span data-stu-id="26668-130">All arithmetic operators (+, -, *, /, %), bitwise operators (~, &, &#124;), and most functions return null if any of the operands or arguments is null, except for the property `IsNull`.</span></span>  
  
 <span data-ttu-id="26668-131">O padrão ANSI SQL-92 não suporta *columnName* = NULL em uma cláusula WHERE.</span><span class="sxs-lookup"><span data-stu-id="26668-131">The ANSI SQL-92 standard does not support *columnName* = NULL in a WHERE clause.</span></span> <span data-ttu-id="26668-132">No SQL Server, a opção ANSI_NULLS controla a nulidade padrão no banco de dados e a avaliação das comparações com valores nulos.</span><span class="sxs-lookup"><span data-stu-id="26668-132">In SQL Server, the ANSI_NULLS option controls both default nullability in the database and evaluation of comparisons against null values.</span></span> <span data-ttu-id="26668-133">Se ANSI_NULLS for ativado (o padrão), o operador IS NULL deverá ser usado nas expressões durante o teste de valores nulos.</span><span class="sxs-lookup"><span data-stu-id="26668-133">If ANSI_NULLS is turned on (the default), the IS NULL operator must be used in expressions when testing for null values.</span></span> <span data-ttu-id="26668-134">Por exemplo, a comparação a seguir sempre produzirá unknown quando ANSI_NULLS for ativado:</span><span class="sxs-lookup"><span data-stu-id="26668-134">For example, the following comparison always yields unknown when ANSI_NULLS is on:</span></span>  
  
```  
colname > NULL  
```  
  
 <span data-ttu-id="26668-135">A comparação com uma variável contendo um valor nulo também produz unknown:</span><span class="sxs-lookup"><span data-stu-id="26668-135">Comparison to a variable containing a null value also yields unknown:</span></span>  
  
```  
colname > @MyVariable  
```  
  
 <span data-ttu-id="26668-136">Use o predicado IS NULL ou IS NOT NULL para testar um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="26668-136">Use the IS NULL or IS NOT NULL predicate to test for a null value.</span></span> <span data-ttu-id="26668-137">Isso pode adicionar complexidade à cláusula WHERE.</span><span class="sxs-lookup"><span data-stu-id="26668-137">This can add complexity to the WHERE clause.</span></span> <span data-ttu-id="26668-138">Por exemplo, a coluna TerritoryID na tabela Customer do AdventureWorks permite valores nulos.</span><span class="sxs-lookup"><span data-stu-id="26668-138">For example, the TerritoryID column in the AdventureWorks Customer table allows null values.</span></span> <span data-ttu-id="26668-139">Se uma instrução SELECT for destinada a testar valores nulos além de outros, ela deverá incluir um predicado IS NULL:</span><span class="sxs-lookup"><span data-stu-id="26668-139">If a SELECT statement is to test for null values in addition to others, it must include an IS NULL predicate:</span></span>  
  
```  
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 <span data-ttu-id="26668-140">Se você desativar ANSI_NULLS no SQL Server, poderá criar expressões que usam o operador de igualdade para comparar com o valor nulo.</span><span class="sxs-lookup"><span data-stu-id="26668-140">If you set ANSI_NULLS off in SQL Server, you can create expressions that use the equality operator to compare to null.</span></span> <span data-ttu-id="26668-141">No entanto, você não pode impedir que as diferentes conexões definam opções nulas para essa conexão.</span><span class="sxs-lookup"><span data-stu-id="26668-141">However, you can't prevent different connections from setting null options for that connection.</span></span> <span data-ttu-id="26668-142">O uso de IS NULL para testar valores nulos sempre funciona, independentemente das configurações de ANSI_NULLS para uma conexão.</span><span class="sxs-lookup"><span data-stu-id="26668-142">Using IS NULL to test for null values always works, regardless of the ANSI_NULLS settings for a connection.</span></span>  
  
 <span data-ttu-id="26668-143">Não há suporte para a desativação de ANSI_NULLS em um `DataSet`, que sempre segue o padrão ANSI SQL-92 para manipular valores nulos no <xref:System.Data.SqlTypes>.</span><span class="sxs-lookup"><span data-stu-id="26668-143">Setting ANSI_NULLS off is not supported in a `DataSet`, which always follows the ANSI SQL-92 standard for handling null values in <xref:System.Data.SqlTypes>.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="26668-144">Atribuindo valores nulos</span><span class="sxs-lookup"><span data-stu-id="26668-144">Assigning Null Values</span></span>  
 <span data-ttu-id="26668-145">Os valores nulos são especiais, e as semânticas de armazenamento e de atribuição diferem entre sistemas de tipo e sistemas de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="26668-145">Null values are special, and their storage and assignment semantics differ across different type systems and storage systems.</span></span> <span data-ttu-id="26668-146">Um `Dataset` foi projetado para ser usado com diferentes sistemas de tipo e de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="26668-146">A `Dataset` is designed to be used with different type and storage systems.</span></span>  
  
 <span data-ttu-id="26668-147">Esta seção descreve as semânticas nulas para atribuir valores nulos a <xref:System.Data.DataColumn> em um <xref:System.Data.DataRow> entre diferentes sistemas de tipo.</span><span class="sxs-lookup"><span data-stu-id="26668-147">This section describes the null semantics for assigning null values to a <xref:System.Data.DataColumn> in a <xref:System.Data.DataRow> across the different type systems.</span></span>  
  
 `DBNull.Value`  
 <span data-ttu-id="26668-148">Esta atribuição é válida para uma `DataColumn` de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="26668-148">This assignment is valid for a `DataColumn` of any type.</span></span> <span data-ttu-id="26668-149">Se o tipo implementar `INullable`, `DBNull.Value` será forçado no valor nulo fortemente tipado apropriado.</span><span class="sxs-lookup"><span data-stu-id="26668-149">If the type implements `INullable`, `DBNull.Value` is coerced into the appropriate strongly typed Null value.</span></span>  
  
 `SqlType.Null`  
 <span data-ttu-id="26668-150">Todos os tipos de dados <xref:System.Data.SqlTypes> implementam `INullable`.</span><span class="sxs-lookup"><span data-stu-id="26668-150">All <xref:System.Data.SqlTypes> data types implement `INullable`.</span></span> <span data-ttu-id="26668-151">Se o valor nulo fortemente tipado puder ser convertido no tipo de dados da coluna usando operadores de conversão implícitos, a atribuição deverá ser feita.</span><span class="sxs-lookup"><span data-stu-id="26668-151">If the strongly typed null value can be converted into the column's data type using implicit cast operators, the assignment should go through.</span></span> <span data-ttu-id="26668-152">Caso contrário, uma exceção de conversão inválida será lançada.</span><span class="sxs-lookup"><span data-stu-id="26668-152">Otherwise an invalid cast exception is thrown.</span></span>  
  
 `null`  
 <span data-ttu-id="26668-153">Se 'null' for um valor válido para o tipo de dado de dados `DataColumn`, ele será forçado no `DbNull.Value` ou `Null` associado ao tipo `INullable` (`SqlType.Null`)</span><span class="sxs-lookup"><span data-stu-id="26668-153">If 'null' is a legal value for the given `DataColumn` data type, it is coerced into the appropriate `DbNull.Value` or `Null` associated with the `INullable` type (`SqlType.Null`)</span></span>  
  
 `derivedUdt.Null`  
 <span data-ttu-id="26668-154">Para colunas UDT, os valores nulos sempre são armazenados com base no tipo associado à `DataColumn`.</span><span class="sxs-lookup"><span data-stu-id="26668-154">For UDT columns, nulls are always stored based on the type associated with the `DataColumn`.</span></span> <span data-ttu-id="26668-155">Considere o caso de um UDT associado a uma `DataColumn` que não implementa `INullable` quando sua subclasse o faz.</span><span class="sxs-lookup"><span data-stu-id="26668-155">Consider the case of a UDT associated with a `DataColumn` that does not implement `INullable` while its sub-class does.</span></span> <span data-ttu-id="26668-156">Nesse caso, se um valor nulo fortemente tipado associado à classe derivada for atribuído, ele será armazenado como um `DbNull.Value` não tipado, porque o armazenamento nulo é sempre consistente com o tipo de dados de DataColumn.</span><span class="sxs-lookup"><span data-stu-id="26668-156">In this case, if a strongly typed null value associated with the derived class is assigned, it is stored as an untyped `DbNull.Value`, because null storage is always consistent with the DataColumn's data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26668-157">Não há suporte no momento para a estrutura `Nullable<T>` ou <xref:System.Nullable> no `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="26668-157">The `Nullable<T>` or <xref:System.Nullable> structure is not currently supported in the `DataSet`.</span></span>  
  
### <a name="multiple-column-row-assignment"></a><span data-ttu-id="26668-158">Atribuição de várias colunas (linha)</span><span class="sxs-lookup"><span data-stu-id="26668-158">Multiple Column (Row) Assignment</span></span>  
 <span data-ttu-id="26668-159">`DataTable.Add`, `DataTable.LoadDataRow` ou outras APIs que aceitam um <xref:System.Data.DataRow.ItemArray%2A> que é mapeado para uma linha mapeiam 'null' para o valor padrão de DataColumn.</span><span class="sxs-lookup"><span data-stu-id="26668-159">`DataTable.Add`, `DataTable.LoadDataRow`, or other APIs that accept an <xref:System.Data.DataRow.ItemArray%2A> that gets mapped to a row, map 'null' to the DataColumn's default value.</span></span> <span data-ttu-id="26668-160">Se um objeto na matriz contiver `DbNull.Value` ou seu equivalente fortemente tipado, as mesmas regras serão aplicadas conforme descrito acima.</span><span class="sxs-lookup"><span data-stu-id="26668-160">If an object in the array contains `DbNull.Value` or its strongly typed counterpart, the same rules as described above are applied.</span></span>  
  
 <span data-ttu-id="26668-161">Além disso, as seguintes regras se aplicam a uma instância de atribuições nulas de `DataRow.["columnName"]`:</span><span class="sxs-lookup"><span data-stu-id="26668-161">In addition, the following rules apply for an instance of `DataRow.["columnName"]` null assignments:</span></span>  
  
1.  <span data-ttu-id="26668-162">O padrão *padrão* valor é `DbNull.Value` para todos exceto as colunas nulas fortemente tipadas onde é apropriado fortemente tipado valor nulo.</span><span class="sxs-lookup"><span data-stu-id="26668-162">The default *default* value is `DbNull.Value` for all except the strongly typed null columns where it is the appropriate strongly typed null value.</span></span>  
  
2.  <span data-ttu-id="26668-163">Os valores nulos nunca são gravados durante a serialização para arquivos XML (como em “xsi:nil").</span><span class="sxs-lookup"><span data-stu-id="26668-163">Null values are never written out during serialization to XML files (as in "xsi:nil").</span></span>  
  
3.  <span data-ttu-id="26668-164">Todos os valores não nulos, incluindo os valores padrão, sempre são gravados durante a serialização para XML.</span><span class="sxs-lookup"><span data-stu-id="26668-164">All non-null values, including defaults, are always written out while serializing to XML.</span></span> <span data-ttu-id="26668-165">Esta é a semântica XSD/XML improvável, em que um valor nulo (xsi:nil) é explícito e o valor padrão é implícito (caso não esteja presente no XML, um analisador de validação poderá obtê-lo em um esquema XSD associado).</span><span class="sxs-lookup"><span data-stu-id="26668-165">This is unlike XSD/XML semantics where a null value (xsi:nil) is explicit and the default value is implicit (if not present in XML, a validating parser can get it from an associated XSD schema).</span></span> <span data-ttu-id="26668-166">O oposto é verdadeiro para `DataTable`: um valor nulo é implícito e o valor padrão é explícito.</span><span class="sxs-lookup"><span data-stu-id="26668-166">The opposite is true for a `DataTable`: a null value is implicit and the default value is explicit.</span></span>  
  
4.  <span data-ttu-id="26668-167">Todos os valores de coluna ausentes para as linhas lidas na entrada XML recebem NULL.</span><span class="sxs-lookup"><span data-stu-id="26668-167">All missing column values for rows read from XML input are assigned NULL.</span></span> <span data-ttu-id="26668-168">As linhas criadas por meio de <xref:System.Data.DataTable.NewRow%2A> ou de métodos similares recebem o valor padrão de DataColumn.</span><span class="sxs-lookup"><span data-stu-id="26668-168">Rows created using <xref:System.Data.DataTable.NewRow%2A> or similar methods are assigned the DataColumn's default value.</span></span>  
  
5.  <span data-ttu-id="26668-169">O método <xref:System.Data.DataRow.IsNull%2A> retorna `true` para `DbNull.Value` e `INullable.Null`.</span><span class="sxs-lookup"><span data-stu-id="26668-169">The <xref:System.Data.DataRow.IsNull%2A> method returns `true` for both `DbNull.Value` and `INullable.Null`.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="26668-170">Atribuindo valores nulos</span><span class="sxs-lookup"><span data-stu-id="26668-170">Assigning Null Values</span></span>  
 <span data-ttu-id="26668-171">O valor padrão para qualquer instância de <xref:System.Data.SqlTypes> é nulo.</span><span class="sxs-lookup"><span data-stu-id="26668-171">The default value for any <xref:System.Data.SqlTypes> instance is null.</span></span>  
  
 <span data-ttu-id="26668-172">Os valores nulos em <xref:System.Data.SqlTypes> são específicos de tipo e não podem ser representado por um único valor, como `DbNull`.</span><span class="sxs-lookup"><span data-stu-id="26668-172">Nulls in <xref:System.Data.SqlTypes> are type-specific and cannot be represented by a single value, such as `DbNull`.</span></span> <span data-ttu-id="26668-173">Use a propriedade `IsNull` para verificar valores nulos.</span><span class="sxs-lookup"><span data-stu-id="26668-173">Use the `IsNull` property to check for nulls.</span></span>  
  
 <span data-ttu-id="26668-174">Os valores nulos podem ser atribuídos a <xref:System.Data.DataColumn> conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="26668-174">Null values can be assigned to a <xref:System.Data.DataColumn> as shown in the following code example.</span></span> <span data-ttu-id="26668-175">Você pode atribuir diretamente valores nulos a variáveis `SqlTypes` sem disparar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="26668-175">You can directly assign null values to `SqlTypes` variables without triggering an exception.</span></span>  
  
### <a name="example"></a><span data-ttu-id="26668-176">Exemplo</span><span class="sxs-lookup"><span data-stu-id="26668-176">Example</span></span>  
 <span data-ttu-id="26668-177">O exemplo de código a seguir cria <xref:System.Data.DataTable> com duas colunas definidas como <xref:System.Data.SqlTypes.SqlInt32> e <xref:System.Data.SqlTypes.SqlString>.</span><span class="sxs-lookup"><span data-stu-id="26668-177">The following code example creates a <xref:System.Data.DataTable> with two columns defined as <xref:System.Data.SqlTypes.SqlInt32> and <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="26668-178">O código adiciona uma linha de valores conhecidos, uma linha de valores nulos e faz a iteração por <xref:System.Data.DataTable>, atribuindo os valores às variáveis e exibindo a saída na janela do console.</span><span class="sxs-lookup"><span data-stu-id="26668-178">The code adds one row of known values, one row of null values and then iterates through the <xref:System.Data.DataTable>, assigning the values to variables and displaying the output in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 <span data-ttu-id="26668-179">Esse exemplo exibe os seguintes resultados:</span><span class="sxs-lookup"><span data-stu-id="26668-179">This example displays the following results:</span></span>  
  
```  
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a><span data-ttu-id="26668-180">Comparando valores nulos com SqlTypes e os tipos CLR</span><span class="sxs-lookup"><span data-stu-id="26668-180">Comparing Null Values with SqlTypes and CLR Types</span></span>  
 <span data-ttu-id="26668-181">Durante a comparação dos valores nulos, é importante compreender a diferença entre a maneira como o método `Equals` avalia os valores nulos no <xref:System.Data.SqlTypes> e a maneira como ele funciona nos tipos CLR.</span><span class="sxs-lookup"><span data-stu-id="26668-181">When comparing null values, it is important to understand the difference between the way the `Equals` method evaluates null values in <xref:System.Data.SqlTypes> as compared with the way it works with CLR types.</span></span> <span data-ttu-id="26668-182">Todos os métodos <xref:System.Data.SqlTypes>`Equals` usam a semântica de banco de dados para avaliar valores nulos: se qualquer um ou ambos os valores forem nulos, a comparação produzirá um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="26668-182">All of the <xref:System.Data.SqlTypes>`Equals` methods use database semantics for evaluating null values: if either or both of the values is null, the comparison yields null.</span></span> <span data-ttu-id="26668-183">Por outro lado, o uso do método CLR `Equals` em dois <xref:System.Data.SqlTypes> produzirá verdadeiro se ambos forem nulos.</span><span class="sxs-lookup"><span data-stu-id="26668-183">On the other hand, using the CLR `Equals` method on two <xref:System.Data.SqlTypes> will yield true if both are null.</span></span> <span data-ttu-id="26668-184">Isso refletirá a diferença entre o uso de um método de instância, como o método CLR `String.Equals`, e o uso do método estático/compartilhado, `SqlString.Equals`.</span><span class="sxs-lookup"><span data-stu-id="26668-184">This reflects the difference between using an instance method such as the CLR `String.Equals` method, and using the static/shared method, `SqlString.Equals`.</span></span>  
  
 <span data-ttu-id="26668-185">O exemplo a seguir mostra a diferença nos resultados entre os métodos `SqlString.Equals` e `String.Equals` quando cada um recebe um par de valores nulos e, em seguida, um par de cadeias de caracteres vazias.</span><span class="sxs-lookup"><span data-stu-id="26668-185">The following example demonstrates the difference in results between the `SqlString.Equals` method and the `String.Equals` method when each is passed a pair of null values and then a pair of empty strings.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 <span data-ttu-id="26668-186">O código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="26668-186">The code produces the following output:</span></span>  
  
```  
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True   
```  
  
## <a name="see-also"></a><span data-ttu-id="26668-187">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26668-187">See Also</span></span>  
 <span data-ttu-id="26668-188">[SQL Server Data Types and ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md) (Tipos de dados do SQL Server e o ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="26668-188">[SQL Server Data Types and ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)</span></span>  
 <span data-ttu-id="26668-189">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="26668-189">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
