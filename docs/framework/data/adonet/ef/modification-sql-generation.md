---
title: Geração de alteração SQL
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: b6c1b71effba17d33c035d0f1df386bf56d405b5
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039891"
---
# <a name="modification-sql-generation"></a><span data-ttu-id="f0e85-102">Geração de alteração SQL</span><span class="sxs-lookup"><span data-stu-id="f0e85-102">Modification SQL Generation</span></span>

<span data-ttu-id="f0e85-103">Esta seção discute como desenvolver um módulo de geração SQL de alteração para o seu (SQL: provedor de base de dados compliant 1999).</span><span class="sxs-lookup"><span data-stu-id="f0e85-103">This section discusses how to develop a modification SQL generation module for your (SQL:1999-compliant database) provider.</span></span> <span data-ttu-id="f0e85-104">Este módulo é responsável para converter uma árvore de comando de alteração apropriadas nas instruções SQL INSERT, UPDATE ou DELETE.</span><span class="sxs-lookup"><span data-stu-id="f0e85-104">This module is responsible for translating a modification command tree into the appropriate SQL INSERT, UPDATE or DELETE statements.</span></span>

<span data-ttu-id="f0e85-105">Para obter informações sobre a geração de SQL para instruções SELECT, consulte [geração de SQL](sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="f0e85-105">For information about SQL generation for select statements, see [SQL Generation](sql-generation.md).</span></span>

## <a name="overview-of-modification-command-trees"></a><span data-ttu-id="f0e85-106">Visão geral das árvores de alteração de comando</span><span class="sxs-lookup"><span data-stu-id="f0e85-106">Overview of Modification Command Trees</span></span>

<span data-ttu-id="f0e85-107">O módulo de geração SQL de alteração gerenciar as instruções SQL base de dados - específicas de alteração com base em uma entrada dada DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="f0e85-107">The modification SQL generation module generates database-specific modification SQL statements based on a given input DbModificationCommandTree.</span></span>

<span data-ttu-id="f0e85-108">Um DbModificationCommandTree é uma representação do modelo de objeto de uma operação de alteração DML (uma inserção, uma atualização, ou uma operação de exclusão), herdando de DbCommandTree.</span><span class="sxs-lookup"><span data-stu-id="f0e85-108">A DbModificationCommandTree is an object model representation of a modification DML operation (an insert, an update, or a delete operation), inheriting from DbCommandTree.</span></span> <span data-ttu-id="f0e85-109">Há três implementações de DbModificationCommandTree:</span><span class="sxs-lookup"><span data-stu-id="f0e85-109">There are three implementations of DbModificationCommandTree:</span></span>

- <span data-ttu-id="f0e85-110">DbInsertCommandTree</span><span class="sxs-lookup"><span data-stu-id="f0e85-110">DbInsertCommandTree</span></span>

- <span data-ttu-id="f0e85-111">DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="f0e85-111">DbUpdateCommandTree</span></span>

- <span data-ttu-id="f0e85-112">DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="f0e85-112">DbDeleteCommandTree</span></span>

<span data-ttu-id="f0e85-113">DbModificationCommandTree e suas implementações que são produzidas pelo Entity Framework sempre representam uma única operação de linha.</span><span class="sxs-lookup"><span data-stu-id="f0e85-113">DbModificationCommandTree and its implementations that are produced by the Entity Framework always represent a single row operation.</span></span> <span data-ttu-id="f0e85-114">Esta seção descreve esses tipos com as restrições no .NET Framework versão 3.5.</span><span class="sxs-lookup"><span data-stu-id="f0e85-114">This section describes these types with their constraints in the .NET Framework version 3.5.</span></span>

<span data-ttu-id="f0e85-115">![Organograma](./media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span><span class="sxs-lookup"><span data-stu-id="f0e85-115">![Diagram](./media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span></span>

<span data-ttu-id="f0e85-116">DbModificationCommandTree tem uma propriedade de destino que representa o destino definido para a operação de alteração.</span><span class="sxs-lookup"><span data-stu-id="f0e85-116">DbModificationCommandTree has a Target property that represents the target set for the modification operation.</span></span> <span data-ttu-id="f0e85-117">A propriedade da expressão de destino, que define o conjunto de entrada é sempre DbScanExpression.</span><span class="sxs-lookup"><span data-stu-id="f0e85-117">The Target’s Expression property, which defines the input set is always DbScanExpression.</span></span>  <span data-ttu-id="f0e85-118">Um DbScanExpression pode representar uma tabela ou uma exibição, ou um conjunto de dados definido com uma consulta se a propriedade de metadados "definindo consulta" de seu destino for não nula.</span><span class="sxs-lookup"><span data-stu-id="f0e85-118">A DbScanExpression can either represent a table or a view, or a set of data defined with a query if the metadata property "Defining Query" of its Target is non-null.</span></span>

<span data-ttu-id="f0e85-119">Um DbScanExpression que representa uma consulta somente poderia alcançar um provedor como um destino de alteração se o dataset foi definido usando uma consulta de definição no modelo mas em nenhuma função foi fornecido para a operação correspondente de alteração.</span><span class="sxs-lookup"><span data-stu-id="f0e85-119">A DbScanExpression that represents a query could only reach a provider as a target of modification if the set was defined by using a defining query in the model but no function was provided for the corresponding modification operation.</span></span> <span data-ttu-id="f0e85-120">Os provedores não podem ser capaz de suportar esse cenário (SqlClient, por exemplo, não faz).</span><span class="sxs-lookup"><span data-stu-id="f0e85-120">Providers may not be able to support such a scenario (SqlClient, for example, does not).</span></span>

<span data-ttu-id="f0e85-121">DbInsertCommandTree representa uma única operação de inserção de linha expressa como uma árvore de comando.</span><span class="sxs-lookup"><span data-stu-id="f0e85-121">DbInsertCommandTree represents a single row insert operation expressed as a command tree.</span></span>

```csharp
public sealed class DbInsertCommandTree : DbModificationCommandTree {
   public IList<DbModificationClause> SetClauses { get }
   public DbExpression Returning { get }
}
```

<span data-ttu-id="f0e85-122">DbUpdateCommandTree representa uma operação de atualização de única linha expressa como uma árvore de comando.</span><span class="sxs-lookup"><span data-stu-id="f0e85-122">DbUpdateCommandTree represents a single-row update operation expressed as a command tree.</span></span>

<span data-ttu-id="f0e85-123">DbDeleteCommandTree representa uma única operação de exclusão de linha expressa como uma árvore de comando.</span><span class="sxs-lookup"><span data-stu-id="f0e85-123">DbDeleteCommandTree represents a single row delete operation expressed as a command tree.</span></span>

### <a name="restrictions-on-modification-command-tree-properties"></a><span data-ttu-id="f0e85-124">Restrições em propriedades da árvore de comando de alteração</span><span class="sxs-lookup"><span data-stu-id="f0e85-124">Restrictions on Modification Command Tree Properties</span></span>

<span data-ttu-id="f0e85-125">As seguintes informações e limitações se aplicam às propriedades de árvore de comando de alteração.</span><span class="sxs-lookup"><span data-stu-id="f0e85-125">The following information and restrictions apply to the modification command tree properties.</span></span>

#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="f0e85-126">Retornar em DbInsertCommandTree e em DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="f0e85-126">Returning in DbInsertCommandTree and DbUpdateCommandTree</span></span>

<span data-ttu-id="f0e85-127">Quando não-nulo, retornar indica que o comando retorna um leitor.</span><span class="sxs-lookup"><span data-stu-id="f0e85-127">When non-null, Returning indicates that the command returns a reader.</span></span> <span data-ttu-id="f0e85-128">Caso contrário, o comando deve retornar um valor escalar indicando o número de linhas afetadas (inserido ou atualizado).</span><span class="sxs-lookup"><span data-stu-id="f0e85-128">Otherwise, the command should return a scalar value indicating the number of rows affected (inserted or updated).</span></span>

<span data-ttu-id="f0e85-129">O valor retornando especifica uma projeção de resultados sejam retornados com base na linha inserida ou atualizado.</span><span class="sxs-lookup"><span data-stu-id="f0e85-129">The Returning value specifies a projection of results to be returned based on the inserted or the updated row.</span></span> <span data-ttu-id="f0e85-130">Só pode ser do tipo DbNewInstanceExpression que representa uma linha, a cada um dos argumentos que são um DbPropertyExpression sobre um DbVariableReferenceExpression que representa uma referência ao destino de DbModificationCommandTree correspondente.</span><span class="sxs-lookup"><span data-stu-id="f0e85-130">It can only be of type DbNewInstanceExpression representing a row, with each of its arguments being a DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span> <span data-ttu-id="f0e85-131">As propriedades representadas pelo DbPropertyExpressions usado em retornar de propriedade são sempre valores gerados ou computados de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="f0e85-131">The properties represented by the DbPropertyExpressions used in the property Returning are always store generated or computed values.</span></span> <span data-ttu-id="f0e85-132">Em DbInsertCommandTree, retornar não é zero quando pelo menos uma propriedade de tabela na linha que está sendo inserido é especificado como o armazenamento gerou ou computou (marcado como StoreGeneratedPattern.Identity ou StoreGeneratedPattern.Computed no ssdl).</span><span class="sxs-lookup"><span data-stu-id="f0e85-132">In DbInsertCommandTree, Returning is not null when at least one property of the table in which the row is being inserted is specified as store generated or computed (marked as StoreGeneratedPattern.Identity or StoreGeneratedPattern.Computed in the ssdl).</span></span> <span data-ttu-id="f0e85-133">Em DbUpdateCommandTrees, retornar não é zero quando pelo menos uma propriedade de tabela na linha que está sendo atualizada é especificado como o armazenamento calculado (marcado como StoreGeneratedPattern.Computed no ssdl).</span><span class="sxs-lookup"><span data-stu-id="f0e85-133">In DbUpdateCommandTrees, Returning is not null when at least one property of the table in which the row is being updated is specified as store computed (marked as StoreGeneratedPattern.Computed in the ssdl).</span></span>

#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="f0e85-134">SetClauses em DbInsertCommandTree e em DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="f0e85-134">SetClauses in DbInsertCommandTree and DbUpdateCommandTree</span></span>

<span data-ttu-id="f0e85-135">SetClauses especifica a lista de cláusulas conjunto de inserção ou de atualização que definem a inserção ou a operação de atualização.</span><span class="sxs-lookup"><span data-stu-id="f0e85-135">SetClauses specifies the list of insert or update set clauses that define the insert or update operation.</span></span>

<span data-ttu-id="f0e85-136">Os elementos da lista são especificados como tipo DbModificationClause, que especifica uma única cláusula em uma operação INSERT ou Update modification.</span><span class="sxs-lookup"><span data-stu-id="f0e85-136">The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation.</span></span> <span data-ttu-id="f0e85-137">DbSetClause herda de DbModificationClause e especifica a cláusula em uma operação de modificação que define o valor de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="f0e85-137">DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property.</span></span> <span data-ttu-id="f0e85-138">A partir da versão 3,5 do .NET Framework, todos os elementos em setcláusulas são do tipo setcláusula.</span><span class="sxs-lookup"><span data-stu-id="f0e85-138">Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.</span></span>

<span data-ttu-id="f0e85-139">A propriedade especifica a propriedade que deve ser atualizada.</span><span class="sxs-lookup"><span data-stu-id="f0e85-139">Property specifies the property that should be updated.</span></span> <span data-ttu-id="f0e85-140">É sempre um DbPropertyExpression sobre um DbVariableReferenceExpression, que representa uma referência ao destino de DbModificationCommandTree correspondente.</span><span class="sxs-lookup"><span data-stu-id="f0e85-140">It is always a DbPropertyExpression over a DbVariableReferenceExpression, which represents a reference to the Target of the corresponding DbModificationCommandTree.</span></span>

<span data-ttu-id="f0e85-141">O valor especifica o novo valor com que para atualizar a propriedade.</span><span class="sxs-lookup"><span data-stu-id="f0e85-141">Value specifies the new value with which to update the property.</span></span> <span data-ttu-id="f0e85-142">É do tipo DbConstantExpression ou DbNullExpression.</span><span class="sxs-lookup"><span data-stu-id="f0e85-142">It is either of type DbConstantExpression or DbNullExpression.</span></span>

#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a><span data-ttu-id="f0e85-143">Predicado em DbUpdateCommandTree e em DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="f0e85-143">Predicate in DbUpdateCommandTree and DbDeleteCommandTree</span></span>

<span data-ttu-id="f0e85-144">O predicado especifica o predicado usado para determinar quais membros da coleção de destino devem ser atualizados ou excluídos.</span><span class="sxs-lookup"><span data-stu-id="f0e85-144">Predicate specifies the predicate used to determine which members of the target collection should be updated or deleted.</span></span> <span data-ttu-id="f0e85-145">É uma árvore de expressão compilada da seguir subconjunto de DbExpressions:</span><span class="sxs-lookup"><span data-stu-id="f0e85-145">It is an expression tree built of the following subset of DbExpressions:</span></span>

- <span data-ttu-id="f0e85-146">DbComparisonExpression de Kind é igual a, com o filho correto sendo um DbPropertyExpression como restrito abaixo e o filho esquerdo a DbConstantExpression.</span><span class="sxs-lookup"><span data-stu-id="f0e85-146">DbComparisonExpression of kind Equals, with the right child being a DbPropertyExpression as restricted below and the left child a DbConstantExpression.</span></span>

- <span data-ttu-id="f0e85-147">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="f0e85-147">DbConstantExpression</span></span>

- <span data-ttu-id="f0e85-148">DbIsNullExpression em um DbPropertyExpression como restrito abaixo</span><span class="sxs-lookup"><span data-stu-id="f0e85-148">DbIsNullExpression over a DbPropertyExpression as restricted below</span></span>

- <span data-ttu-id="f0e85-149">DbPropertyExpression sobre um DbVariableReferenceExpression que representa uma referência ao destino de DbModificationCommandTree correspondente.</span><span class="sxs-lookup"><span data-stu-id="f0e85-149">DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span>

- <span data-ttu-id="f0e85-150">DbAndExpression</span><span class="sxs-lookup"><span data-stu-id="f0e85-150">DbAndExpression</span></span>

- <span data-ttu-id="f0e85-151">DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="f0e85-151">DbNotExpression</span></span>

- <span data-ttu-id="f0e85-152">DbOrExpression</span><span class="sxs-lookup"><span data-stu-id="f0e85-152">DbOrExpression</span></span>

## <a name="modification-sql-generation-in-the-sample-provider"></a><span data-ttu-id="f0e85-153">Geração SQL alteração no provedor exemplo</span><span class="sxs-lookup"><span data-stu-id="f0e85-153">Modification SQL Generation in the Sample Provider</span></span>

<span data-ttu-id="f0e85-154">O [provedor de exemplo Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstra os componentes de provedores de dados ADO.NET que dão suporte ao Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="f0e85-154">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the components of ADO.NET Data Providers that support the Entity Framework.</span></span> <span data-ttu-id="f0e85-155">Tem como alvo um base de dados do SQL Server 2005 e é implementado como um wrapper sobre o provedor de dados do ADO.NET .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="f0e85-155">It targets a SQL Server 2005 database and is implemented as a wrapper on top of System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>

<span data-ttu-id="f0e85-156">O módulo de geração SQL de alteração do provedor de exemplo (localizado na geração SQL do arquivo DmlSqlGenerator.cs \) usa uma entrada DbModificationCommandTree e gerencia uma única instrução SQL de alteração seguida possivelmente por uma instrução select para retornar um leitor se especificado pelo DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="f0e85-156">The modification SQL generation module of the sample provider (located in the file SQL Generation\DmlSqlGenerator.cs) takes an input DbModificationCommandTree and produces a single modification SQL statement possibly followed by a select statement to return a reader if specified by the DbModificationCommandTree.</span></span> <span data-ttu-id="f0e85-157">Observe que a forma de comandos gerados é afetada por base de dados SQL Server de destino.</span><span class="sxs-lookup"><span data-stu-id="f0e85-157">Note that the shape of the commands generated is affected by the target SQL Server database.</span></span>

### <a name="helper-classes-expressiontranslator"></a><span data-ttu-id="f0e85-158">Classes auxiliar: ExpressionTranslator</span><span class="sxs-lookup"><span data-stu-id="f0e85-158">Helper Classes: ExpressionTranslator</span></span>

<span data-ttu-id="f0e85-159">Serve de ExpressionTranslator como um tradutor leve comum para todas as propriedades da árvore de comando de alteração de tipo DbExpression.</span><span class="sxs-lookup"><span data-stu-id="f0e85-159">ExpressionTranslator serves as a common lightweight translator for all modification command tree properties of type DbExpression.</span></span> <span data-ttu-id="f0e85-160">Oferece suporte à conversão de tipos somente da expressão às propriedades de árvore de comando de alteração são restritas e é compilado com as restrições específicos em mente.</span><span class="sxs-lookup"><span data-stu-id="f0e85-160">It supports translation of only the expression types to which the properties of the modification command tree are constrained and is built with the particular constraints in mind.</span></span>

<span data-ttu-id="f0e85-161">As informações a seguir descreve tipos específicos de visita de expressões (os nós com traduções triviais são omitidos.)</span><span class="sxs-lookup"><span data-stu-id="f0e85-161">The following information discusses visiting specific expression types (nodes with trivial translations are omitted).</span></span>

### <a name="dbcomparisonexpression"></a><span data-ttu-id="f0e85-162">DbComparisonExpression</span><span class="sxs-lookup"><span data-stu-id="f0e85-162">DbComparisonExpression</span></span>

<span data-ttu-id="f0e85-163">Quando o ExpressionTranslator é construído com preserveMemberValues = retifique, e quando a constante à direita é um DbConstantExpression (em vez de DbNullExpression), associa o operando esquerdo (um DbPropertyExpressions) com esse DbConstantExpression.</span><span class="sxs-lookup"><span data-stu-id="f0e85-163">When the ExpressionTranslator is constructed with preserveMemberValues = true, and when the constant to the right is a DbConstantExpression (instead of DbNullExpression), it associates the left operand (a DbPropertyExpressions) with that DbConstantExpression.</span></span> <span data-ttu-id="f0e85-164">Isso é usado se uma instrução SELECT de retorno precisa ser gerada para identificar a linha afetado.</span><span class="sxs-lookup"><span data-stu-id="f0e85-164">That is used if a return Select statement needs to be generated to identify the affected row.</span></span>

### <a name="dbconstantexpression"></a><span data-ttu-id="f0e85-165">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="f0e85-165">DbConstantExpression</span></span>

<span data-ttu-id="f0e85-166">Para cada constante visitada um parâmetro é criado.</span><span class="sxs-lookup"><span data-stu-id="f0e85-166">For each visited constant a parameter is created.</span></span>

### <a name="dbpropertyexpression"></a><span data-ttu-id="f0e85-167">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="f0e85-167">DbPropertyExpression</span></span>

<span data-ttu-id="f0e85-168">Dado que a instância de DbPropertyExpression sempre representa a tabela de entrada, a menos que a geração criar um apelido (que ocorrem apenas em cenários de atualização quando uma variável da tabela é usado), nenhum alias precisa ser especificada para a entrada; a conversão tem como padrão o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="f0e85-168">Given that the Instance of the DbPropertyExpression always represents the input table, unless the generation has created an alias (which only happens in update scenarios when a table variable is used), no alias needs to be specified for the input; the translation defaults to the property name.</span></span>

## <a name="generating-an-insert-sql-command"></a><span data-ttu-id="f0e85-169">Gerando um comando SQL de inserção</span><span class="sxs-lookup"><span data-stu-id="f0e85-169">Generating an Insert SQL Command</span></span>

<span data-ttu-id="f0e85-170">Para um DbInsertCommandTree determinado no provedor de exemplo, o comando gerado de inserção segue um dos dois modelos de inserção abaixo.</span><span class="sxs-lookup"><span data-stu-id="f0e85-170">For a given DbInsertCommandTree in the sample provider, the generated insert command follows one of the two insert templates below.</span></span>

<span data-ttu-id="f0e85-171">O primeiro modelo tem um comando executar a inserção dados os valores na lista de SetClauses, e uma instrução SELECT para retornar as propriedades especificadas na propriedade retornando para a linha inserida se a propriedade retornando não era nula.</span><span class="sxs-lookup"><span data-stu-id="f0e85-171">The first template has a command to perform the insert given the values in the list of SetClauses, and a SELECT statement to return the properties specified in the Returning property for the inserted row if the Returning property was not null.</span></span> <span data-ttu-id="f0e85-172">O elemento de predicado "\@@ROWCOUNT > 0" será true se uma linha tiver sido inserida.</span><span class="sxs-lookup"><span data-stu-id="f0e85-172">The predicate element "\@@ROWCOUNT > 0" is true if a row was inserted.</span></span> <span data-ttu-id="f0e85-173">O elemento predicado "keymemberi = &#124; SCOPE_IDENTITY ()" usa a forma "keymemberi = SCOPE_IDENTITY ()" somente se keymemberi for uma chave gerada pelo repositório, porque SCOPE_IDENTITY () retorna o último valor de identidade inserido em uma identidade ( coluna gerada pelo armazenamento).</span><span class="sxs-lookup"><span data-stu-id="f0e85-173">The predicate element "keyMemberI =  keyValueI &#124; scope_identity()" takes the shape  "keyMemberI =  scope_identity()" only if keyMemberI is a store-generated key, because scope_identity() returns the last identity value inserted into an identity (store-generated) column.</span></span>

```sql
-- first insert Template
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

<span data-ttu-id="f0e85-174">O segundo modelo é necessário se a inserção especifica inserir uma linha onde a chave primária é gerado Store- mas não é um tipo inteiro e portanto não pode ser usada com scope_identity()).</span><span class="sxs-lookup"><span data-stu-id="f0e85-174">The second template is needed if the insert specifies inserting a row where the primary key is store-generated but is not an integer type and therefore can't be used with scope_identity()).</span></span> <span data-ttu-id="f0e85-175">Também é usado se houver uma chave Store- gerado composta.</span><span class="sxs-lookup"><span data-stu-id="f0e85-175">It is also used if there is a compound store-generated key.</span></span>

```sql
-- second insert template
DECLARE @generated_keys TABLE [(keyMember0, … keyMemberN)

INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]
 OUTPUT inserted.KeyMember0, …, inserted.KeyMemberN INTO @generated_keys
 VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES

[SELECT <returning_over_t>
 FROM @generated_keys  AS g
JOIN <target> AS t ON g.KeyMember0 = t.KeyMember0 AND … g.KeyMemberN = t.KeyMemberN
 WHERE @@ROWCOUNT > 0
```

<span data-ttu-id="f0e85-176">A seguir está um exemplo que usa o modelo que está incluído com o provedor de exemplo.</span><span class="sxs-lookup"><span data-stu-id="f0e85-176">The following is an example that uses the model that is included with the sample provider.</span></span> <span data-ttu-id="f0e85-177">Gerencia um comando de inserção de um DbInsertCommandTree.</span><span class="sxs-lookup"><span data-stu-id="f0e85-177">It generates an insert command from a DbInsertCommandTree.</span></span>

<span data-ttu-id="f0e85-178">O código a seguir insere uma categoria:</span><span class="sxs-lookup"><span data-stu-id="f0e85-178">The following code inserts a Category:</span></span>

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = new Category();
   c.CategoryName = "Test Category";
   c.Description = "A new category for testing";
   northwindContext.AddObject("Categories", c);
   northwindContext.SaveChanges();
}
```

<span data-ttu-id="f0e85-179">Esse código gerencia a seguir árvore de comando, que é passada para o provedor:</span><span class="sxs-lookup"><span data-stu-id="f0e85-179">This code produces the following command tree, which is passed to the provider:</span></span>

```output
DbInsertCommandTree
|_Parameters
|_Target : 'target'
| |_Scan : dbo.Categories
|_SetClauses
| |_DbSetClause
| | |_Property
| | | |_Var(target).CategoryName
| | |_Value
| |   |_'Test Category'
| |_DbSetClause
| | |_Property
| | | |_Var(target).Description
| | |_Value
| |   |_'A new category for testing'
| |_DbSetClause
|   |_Property
|   | |_Var(target).Picture
|   |_Value
|     |_null
|_Returning
  |_NewInstance : Record['CategoryID'=Edm.Int32]
    |_Column : 'CategoryID'
      |_Var(target).CategoryID
```

<span data-ttu-id="f0e85-180">O comando de armazenamento que o provedor exemplo gerencia é a seguinte instrução SQL:</span><span class="sxs-lookup"><span data-stu-id="f0e85-180">The store command that the sample provider produces is the following SQL statement:</span></span>

```sql
insert [dbo].[Categories]([CategoryName], [Description], [Picture])
values (@p0, @p1, null)
select [CategoryID]
from [dbo].[Categories]
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()
```

## <a name="generating-an-update-sql-command"></a><span data-ttu-id="f0e85-181">Gerando um comando SQL de atualização</span><span class="sxs-lookup"><span data-stu-id="f0e85-181">Generating an Update SQL Command</span></span>

<span data-ttu-id="f0e85-182">Para um determinado DbUpdateCommandTree, o comando gerado de atualização é baseado no modelo seguir:</span><span class="sxs-lookup"><span data-stu-id="f0e85-182">For a given DbUpdateCommandTree, the generated update command is based on the following template:</span></span>

```sql
-- UPDATE Template
UPDATE <target>
SET setClauseProperty0 = setClauseValue0, .. setClausePropertyN = setClauseValueN  | @i = 0
WHERE <predicate>

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

<span data-ttu-id="f0e85-183">A cláusula SET tem a cláusula SET falsa ("@i = 0") somente se nenhuma cláusula SET for especificada.</span><span class="sxs-lookup"><span data-stu-id="f0e85-183">The set clause has the fake set clause ("@i = 0") only if no set clauses are specified.</span></span> <span data-ttu-id="f0e85-184">Este é garantir que todas as colunas Store- computadas recalculados.</span><span class="sxs-lookup"><span data-stu-id="f0e85-184">This is to ensure that any store-computed columns are recomputed.</span></span>

<span data-ttu-id="f0e85-185">Somente se a propriedade retornando não é nulo, uma instrução SELECT é gerada para retornar as propriedades especificadas na propriedade retornando.</span><span class="sxs-lookup"><span data-stu-id="f0e85-185">Only if the Returning property is not null, a select statement is generated to return the properties specified in the Returning property.</span></span>

<span data-ttu-id="f0e85-186">O exemplo a seguir usa o modelo que está incluído com o provedor de exemplo para gerar um comando de atualização.</span><span class="sxs-lookup"><span data-stu-id="f0e85-186">The following example uses the model that is included with the sample provider to generate an update command.</span></span>

<span data-ttu-id="f0e85-187">O seguinte código do usuário atualiza uma categoria:</span><span class="sxs-lookup"><span data-stu-id="f0e85-187">The following user code updates a Category:</span></span>

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();
   c.CategoryName = "New test name";
   northwindContext.SaveChanges();
}
```

<span data-ttu-id="f0e85-188">Esse código do usuário gerencia a seguir árvore de comando, que é passada para o provedor:</span><span class="sxs-lookup"><span data-stu-id="f0e85-188">This user code produces the following command tree, which is passed to the provider:</span></span>

```output
DbUpdateCommandTree
|_Parameters
|_Target : 'target'
| |_Scan : dbo.Categories
|_SetClauses
| |_DbSetClause
|   |_Property
|   | |_Var(target).CategoryName
|   |_Value
|     |_'New test name'
|_Predicate
| |_
|   |_Var(target).CategoryID
|   |_=
|   |_10
|_Returning
```

<span data-ttu-id="f0e85-189">O exemplo de provedor para gerenciar o seguinte comando de armazenamento:</span><span class="sxs-lookup"><span data-stu-id="f0e85-189">The sample provider produces the following store command:</span></span>

```sql
update [dbo].[Categories]
set [CategoryName] = @p0
where ([CategoryID] = @p1)
```

### <a name="generating-a-delete-sql-command"></a><span data-ttu-id="f0e85-190">Gerando um comando SQL delete</span><span class="sxs-lookup"><span data-stu-id="f0e85-190">Generating a Delete SQL Command</span></span>

<span data-ttu-id="f0e85-191">Para um determinado DbDeleteCommandTree, o comando DELETE gerado é baseado no modelo seguir:</span><span class="sxs-lookup"><span data-stu-id="f0e85-191">For a given DbDeleteCommandTree, the generated DELETE command is based on the following template:</span></span>

```sql
-- DELETE Template
DELETE <target>
WHERE <predicate>
```

<span data-ttu-id="f0e85-192">O exemplo a seguir usa o modelo que está incluído com o provedor de exemplo para gerar um comando delete.</span><span class="sxs-lookup"><span data-stu-id="f0e85-192">The following example uses the model that is included with the sample provider to generate a delete command.</span></span>

<span data-ttu-id="f0e85-193">O seguinte código do usuário exclui uma categoria:</span><span class="sxs-lookup"><span data-stu-id="f0e85-193">The following user code deletes a Category:</span></span>

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();
   northwindContext.DeleteObject(c);
   northwindContext.SaveChanges();
}
```

<span data-ttu-id="f0e85-194">Esse código do usuário gerencia a seguir árvore de comando, que é passada para o provedor.</span><span class="sxs-lookup"><span data-stu-id="f0e85-194">This user code produces the following command tree, which is passed to the provider.</span></span>

```output
DbDeleteCommandTree
|_Parameters
|_Target : 'target'
| |_Scan : dbo.Categories
|_Predicate
  |_
    |_Var(target).CategoryID
    |_=
    |_10
```

<span data-ttu-id="f0e85-195">O seguinte comando de armazenamento é gerado pelo provedor exemplo:</span><span class="sxs-lookup"><span data-stu-id="f0e85-195">The following store command is produced by the sample provider:</span></span>

```sql
delete [dbo].[Categories]
where ([CategoryID] = @p0)
```

## <a name="see-also"></a><span data-ttu-id="f0e85-196">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0e85-196">See also</span></span>

- [<span data-ttu-id="f0e85-197">Escrevendo um Provedor de Dados do Entity Framework</span><span class="sxs-lookup"><span data-stu-id="f0e85-197">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
