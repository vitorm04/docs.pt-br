---
title: Geração de alteração SQL
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: 8e0568e32094b6cc27137409f3d908928d82cebb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43560750"
---
# <a name="modification-sql-generation"></a><span data-ttu-id="8cdba-102">Geração de alteração SQL</span><span class="sxs-lookup"><span data-stu-id="8cdba-102">Modification SQL Generation</span></span>
<span data-ttu-id="8cdba-103">Esta seção discute como desenvolver um módulo de geração SQL de alteração para o seu (SQL: provedor de base de dados compliant 1999).</span><span class="sxs-lookup"><span data-stu-id="8cdba-103">This section discusses how to develop a modification SQL generation module for your (SQL:1999-compliant database) provider.</span></span> <span data-ttu-id="8cdba-104">Este módulo é responsável para converter uma árvore de comando de alteração apropriadas nas instruções SQL INSERT, UPDATE ou DELETE.</span><span class="sxs-lookup"><span data-stu-id="8cdba-104">This module is responsible for translating a modification command tree into the appropriate SQL INSERT, UPDATE or DELETE statements.</span></span>  
  
 <span data-ttu-id="8cdba-105">Para obter informações sobre a geração de SQL para instruções select, consulte [geração SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="8cdba-105">For information about SQL generation for select statements, see [SQL Generation](../../../../../docs/framework/data/adonet/ef/sql-generation.md).</span></span>  
  
## <a name="overview-of-modification-command-trees"></a><span data-ttu-id="8cdba-106">Visão geral das árvores de alteração de comando</span><span class="sxs-lookup"><span data-stu-id="8cdba-106">Overview of Modification Command Trees</span></span>  
 <span data-ttu-id="8cdba-107">O módulo de geração SQL de alteração gerenciar as instruções SQL base de dados - específicas de alteração com base em uma entrada dada DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="8cdba-107">The modification SQL generation module generates database-specific modification SQL statements based on a given input DbModificationCommandTree.</span></span>  
  
 <span data-ttu-id="8cdba-108">Um DbModificationCommandTree é uma representação do modelo de objeto de uma operação de alteração DML (uma inserção, uma atualização, ou uma operação de exclusão), herdando de DbCommandTree.</span><span class="sxs-lookup"><span data-stu-id="8cdba-108">A DbModificationCommandTree is an object model representation of a modification DML operation (an insert, an update, or a delete operation), inheriting from DbCommandTree.</span></span> <span data-ttu-id="8cdba-109">Há três implementações de DbModificationCommandTree:</span><span class="sxs-lookup"><span data-stu-id="8cdba-109">There are three implementations of DbModificationCommandTree:</span></span>  
  
-   <span data-ttu-id="8cdba-110">DbInsertCommandTree</span><span class="sxs-lookup"><span data-stu-id="8cdba-110">DbInsertCommandTree</span></span>  
  
-   <span data-ttu-id="8cdba-111">DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="8cdba-111">DbUpdateCommandTree</span></span>  
  
-   <span data-ttu-id="8cdba-112">DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="8cdba-112">DbDeleteCommandTree</span></span>  
  
 <span data-ttu-id="8cdba-113">DbModificationCommandTree e suas implementações que são produzidas pelo [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sempre representam uma operação única linha.</span><span class="sxs-lookup"><span data-stu-id="8cdba-113">DbModificationCommandTree and its implementations that are produced by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] always represent a single row operation.</span></span> <span data-ttu-id="8cdba-114">Esta seção descreve esses tipos com as restrições no .NET Framework versão 3.5.</span><span class="sxs-lookup"><span data-stu-id="8cdba-114">This section describes these types with their constraints in the .NET Framework version 3.5.</span></span>  
  
 <span data-ttu-id="8cdba-115">![Diagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span><span class="sxs-lookup"><span data-stu-id="8cdba-115">![Diagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span></span>  
  
 <span data-ttu-id="8cdba-116">DbModificationCommandTree tem uma propriedade de destino que representa o destino definido para a operação de alteração.</span><span class="sxs-lookup"><span data-stu-id="8cdba-116">DbModificationCommandTree has a Target property that represents the target set for the modification operation.</span></span> <span data-ttu-id="8cdba-117">A propriedade da expressão de destino, que define o conjunto de entrada é sempre DbScanExpression.</span><span class="sxs-lookup"><span data-stu-id="8cdba-117">The Target’s Expression property, which defines the input set is always DbScanExpression.</span></span>  <span data-ttu-id="8cdba-118">Um DbScanExpression pode representar uma tabela ou exibição, ou um conjunto de dados definidos com uma consulta se a propriedade de metadados "Que define a consulta" do seu destino for não nulo.</span><span class="sxs-lookup"><span data-stu-id="8cdba-118">A DbScanExpression can either represent a table or a view, or a set of data defined with a query if the metadata property "Defining Query" of its Target is non-null.</span></span>  
  
 <span data-ttu-id="8cdba-119">Um DbScanExpression que representa uma consulta somente poderia alcançar um provedor como um destino de alteração se o dataset foi definido usando uma consulta de definição no modelo mas em nenhuma função foi fornecido para a operação correspondente de alteração.</span><span class="sxs-lookup"><span data-stu-id="8cdba-119">A DbScanExpression that represents a query could only reach a provider as a target of modification if the set was defined by using a defining query in the model but no function was provided for the corresponding modification operation.</span></span> <span data-ttu-id="8cdba-120">Os provedores não podem ser capaz de suportar esse cenário (SqlClient, por exemplo, não faz).</span><span class="sxs-lookup"><span data-stu-id="8cdba-120">Providers may not be able to support such a scenario (SqlClient, for example, does not).</span></span>  
  
 <span data-ttu-id="8cdba-121">DbInsertCommandTree representa uma única operação de inserção de linha expressa como uma árvore de comando.</span><span class="sxs-lookup"><span data-stu-id="8cdba-121">DbInsertCommandTree represents a single row insert operation expressed as a command tree.</span></span>  
  
```  
public sealed class DbInsertCommandTree : DbModificationCommandTree {  
   public IList<DbModificationClause> SetClauses { get }  
   public DbExpression Returning { get }  
}  
```  
  
 <span data-ttu-id="8cdba-122">DbUpdateCommandTree representa uma operação de atualização de única linha expressa como uma árvore de comando.</span><span class="sxs-lookup"><span data-stu-id="8cdba-122">DbUpdateCommandTree represents a single-row update operation expressed as a command tree.</span></span>  
  
 <span data-ttu-id="8cdba-123">DbDeleteCommandTree representa uma única operação de exclusão de linha expressa como uma árvore de comando.</span><span class="sxs-lookup"><span data-stu-id="8cdba-123">DbDeleteCommandTree represents a single row delete operation expressed as a command tree.</span></span>  
  
### <a name="restrictions-on-modification-command-tree-properties"></a><span data-ttu-id="8cdba-124">Restrições em propriedades da árvore de comando de alteração</span><span class="sxs-lookup"><span data-stu-id="8cdba-124">Restrictions on Modification Command Tree Properties</span></span>  
 <span data-ttu-id="8cdba-125">As seguintes informações e limitações se aplicam às propriedades de árvore de comando de alteração.</span><span class="sxs-lookup"><span data-stu-id="8cdba-125">The following information and restrictions apply to the modification command tree properties.</span></span>  
  
#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="8cdba-126">Retornar em DbInsertCommandTree e em DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="8cdba-126">Returning in DbInsertCommandTree and DbUpdateCommandTree</span></span>  
 <span data-ttu-id="8cdba-127">Quando não-nulo, retornar indica que o comando retorna um leitor.</span><span class="sxs-lookup"><span data-stu-id="8cdba-127">When non-null, Returning indicates that the command returns a reader.</span></span> <span data-ttu-id="8cdba-128">Caso contrário, o comando deve retornar um valor escalar indicando o número de linhas afetadas (inserido ou atualizado).</span><span class="sxs-lookup"><span data-stu-id="8cdba-128">Otherwise, the command should return a scalar value indicating the number of rows affected (inserted or updated).</span></span>  
  
 <span data-ttu-id="8cdba-129">O valor retornando especifica uma projeção de resultados sejam retornados com base na linha inserida ou atualizado.</span><span class="sxs-lookup"><span data-stu-id="8cdba-129">The Returning value specifies a projection of results to be returned based on the inserted or the updated row.</span></span> <span data-ttu-id="8cdba-130">Só pode ser do tipo DbNewInstanceExpression que representa uma linha, a cada um dos argumentos que são um DbPropertyExpression sobre um DbVariableReferenceExpression que representa uma referência ao destino de DbModificationCommandTree correspondente.</span><span class="sxs-lookup"><span data-stu-id="8cdba-130">It can only be of type DbNewInstanceExpression representing a row, with each of its arguments being a DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span> <span data-ttu-id="8cdba-131">As propriedades representadas pelo DbPropertyExpressions usado em retornar de propriedade são sempre valores gerados ou computados de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="8cdba-131">The properties represented by the DbPropertyExpressions used in the property Returning are always store generated or computed values.</span></span> <span data-ttu-id="8cdba-132">Em DbInsertCommandTree, retornar não é zero quando pelo menos uma propriedade de tabela na linha que está sendo inserido é especificado como o armazenamento gerou ou computou (marcado como StoreGeneratedPattern.Identity ou StoreGeneratedPattern.Computed no ssdl).</span><span class="sxs-lookup"><span data-stu-id="8cdba-132">In DbInsertCommandTree, Returning is not null when at least one property of the table in which the row is being inserted is specified as store generated or computed (marked as StoreGeneratedPattern.Identity or StoreGeneratedPattern.Computed in the ssdl).</span></span> <span data-ttu-id="8cdba-133">Em DbUpdateCommandTrees, retornar não é zero quando pelo menos uma propriedade de tabela na linha que está sendo atualizada é especificado como o armazenamento calculado (marcado como StoreGeneratedPattern.Computed no ssdl).</span><span class="sxs-lookup"><span data-stu-id="8cdba-133">In DbUpdateCommandTrees, Returning is not null when at least one property of the table in which the row is being updated is specified as store computed (marked as StoreGeneratedPattern.Computed in the ssdl).</span></span>  
  
#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="8cdba-134">SetClauses em DbInsertCommandTree e em DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="8cdba-134">SetClauses in DbInsertCommandTree and DbUpdateCommandTree</span></span>  
 <span data-ttu-id="8cdba-135">SetClauses especifica a lista de cláusulas conjunto de inserção ou de atualização que definem a inserção ou a operação de atualização.</span><span class="sxs-lookup"><span data-stu-id="8cdba-135">SetClauses specifies the list of insert or update set clauses that define the insert or update operation.</span></span>  
  
```  
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.   
```  
  
 <span data-ttu-id="8cdba-136">A propriedade especifica a propriedade que deve ser atualizada.</span><span class="sxs-lookup"><span data-stu-id="8cdba-136">Property specifies the property that should be updated.</span></span> <span data-ttu-id="8cdba-137">É sempre um DbPropertyExpression sobre um DbVariableReferenceExpression, que representa uma referência ao destino de DbModificationCommandTree correspondente.</span><span class="sxs-lookup"><span data-stu-id="8cdba-137">It is always a DbPropertyExpression over a DbVariableReferenceExpression, which represents a reference to the Target of the corresponding DbModificationCommandTree.</span></span>  
  
 <span data-ttu-id="8cdba-138">O valor especifica o novo valor com que para atualizar a propriedade.</span><span class="sxs-lookup"><span data-stu-id="8cdba-138">Value specifies the new value with which to update the property.</span></span> <span data-ttu-id="8cdba-139">É do tipo DbConstantExpression ou DbNullExpression.</span><span class="sxs-lookup"><span data-stu-id="8cdba-139">It is either of type DbConstantExpression or DbNullExpression.</span></span>  
  
#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a><span data-ttu-id="8cdba-140">Predicado em DbUpdateCommandTree e em DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="8cdba-140">Predicate in DbUpdateCommandTree and DbDeleteCommandTree</span></span>  
 <span data-ttu-id="8cdba-141">O predicado especifica o predicado usado para determinar quais membros da coleção de destino devem ser atualizados ou excluídos.</span><span class="sxs-lookup"><span data-stu-id="8cdba-141">Predicate specifies the predicate used to determine which members of the target collection should be updated or deleted.</span></span> <span data-ttu-id="8cdba-142">É uma árvore de expressão compilada da seguir subconjunto de DbExpressions:</span><span class="sxs-lookup"><span data-stu-id="8cdba-142">It is an expression tree built of the following subset of DbExpressions:</span></span>  
  
-   <span data-ttu-id="8cdba-143">DbComparisonExpression de semelhantes amáveis, com o filho adequado que são um DbPropertyExression como restrito abaixo e o filho esquerdo um DbConstantExpression.</span><span class="sxs-lookup"><span data-stu-id="8cdba-143">DbComparisonExpression of kind Equals, with the right child being a DbPropertyExression as restricted below and the left child a DbConstantExpression.</span></span>  
  
-   <span data-ttu-id="8cdba-144">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="8cdba-144">DbConstantExpression</span></span>  
  
-   <span data-ttu-id="8cdba-145">DbIsNullExpression sobre um DbPropertyExpresison como restrito abaixo</span><span class="sxs-lookup"><span data-stu-id="8cdba-145">DbIsNullExpression over a DbPropertyExpresison as restricted below</span></span>  
  
-   <span data-ttu-id="8cdba-146">DbPropertyExpression sobre um DbVariableReferenceExpression que representa uma referência ao destino de DbModificationCommandTree correspondente.</span><span class="sxs-lookup"><span data-stu-id="8cdba-146">DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span>  
  
-   <span data-ttu-id="8cdba-147">DbAndExpression</span><span class="sxs-lookup"><span data-stu-id="8cdba-147">DbAndExpression</span></span>  
  
-   <span data-ttu-id="8cdba-148">DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="8cdba-148">DbNotExpression</span></span>  
  
-   <span data-ttu-id="8cdba-149">DbOrExpression</span><span class="sxs-lookup"><span data-stu-id="8cdba-149">DbOrExpression</span></span>  
  
## <a name="modification-sql-generation-in-the-sample-provider"></a><span data-ttu-id="8cdba-150">Geração SQL alteração no provedor exemplo</span><span class="sxs-lookup"><span data-stu-id="8cdba-150">Modification SQL Generation in the Sample Provider</span></span>  
 <span data-ttu-id="8cdba-151">O [provedor de exemplo do Entity Framework](https://go.microsoft.com/fwlink/?LinkId=180616) demonstra os componentes de provedores de dados ADO.NET que dão suporte a [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8cdba-151">The [Entity Framework Sample Provider](https://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="8cdba-152">Tem como alvo um base de dados do SQL Server 2005 e é implementado como um wrapper sobre o provedor de dados do ADO.NET .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="8cdba-152">It targets a SQL Server 2005 database and is implemented as a wrapper on top of System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="8cdba-153">O módulo de geração SQL de alteração do provedor de exemplo (localizado na geração SQL do arquivo DmlSqlGenerator.cs \) usa uma entrada DbModificationCommandTree e gerencia uma única instrução SQL de alteração seguida possivelmente por uma instrução select para retornar um leitor se especificado pelo DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="8cdba-153">The modification SQL generation module of the sample provider (located in the file SQL Generation\DmlSqlGenerator.cs) takes an input DbModificationCommandTree and produces a single modification SQL statement possibly followed by a select statement to return a reader if specified by the DbModificationCommandTree.</span></span> <span data-ttu-id="8cdba-154">Observe que a forma de comandos gerados é afetada por base de dados SQL Server de destino.</span><span class="sxs-lookup"><span data-stu-id="8cdba-154">Note that the shape of the commands generated is affected by the target SQL Server database.</span></span>  
  
### <a name="helper-classes-expressiontranslator"></a><span data-ttu-id="8cdba-155">Classes auxiliar: ExpressionTranslator</span><span class="sxs-lookup"><span data-stu-id="8cdba-155">Helper Classes: ExpressionTranslator</span></span>  
 <span data-ttu-id="8cdba-156">Serve de ExpressionTranslator como um tradutor leve comum para todas as propriedades da árvore de comando de alteração de tipo DbExpression.</span><span class="sxs-lookup"><span data-stu-id="8cdba-156">ExpressionTranslator serves as a common lightweight translator for all modification command tree properties of type DbExpression.</span></span> <span data-ttu-id="8cdba-157">Oferece suporte à conversão de tipos somente da expressão às propriedades de árvore de comando de alteração são restritas e é compilado com as restrições específicos em mente.</span><span class="sxs-lookup"><span data-stu-id="8cdba-157">It supports translation of only the expression types to which the properties of the modification command tree are constrained and is built with the particular constraints in mind.</span></span>  
  
 <span data-ttu-id="8cdba-158">As informações a seguir descreve tipos específicos de visita de expressões (os nós com traduções triviais são omitidos.)</span><span class="sxs-lookup"><span data-stu-id="8cdba-158">The following information discusses visiting specific expression types (nodes with trivial translations are omitted).</span></span>  
  
### <a name="dbcomparisonexpression"></a><span data-ttu-id="8cdba-159">DbComparisonExpression</span><span class="sxs-lookup"><span data-stu-id="8cdba-159">DbComparisonExpression</span></span>  
 <span data-ttu-id="8cdba-160">Quando o ExpressionTranslator é construído com preserveMemberValues = retifique, e quando a constante à direita é um DbConstantExpression (em vez de DbNullExpression), associa o operando esquerdo (um DbPropertyExpressions) com esse DbConstantExpression.</span><span class="sxs-lookup"><span data-stu-id="8cdba-160">When the ExpressionTranslator is constructed with preserveMemberValues = true, and when the constant to the right is a DbConstantExpression (instead of DbNullExpression), it associates the left operand (a DbPropertyExpressions) with that DbConstantExpression.</span></span> <span data-ttu-id="8cdba-161">Isso é usado se uma instrução SELECT de retorno precisa ser gerada para identificar a linha afetado.</span><span class="sxs-lookup"><span data-stu-id="8cdba-161">That is used if a return Select statement needs to be generated to identify the affected row.</span></span>  
  
### <a name="dbconstantexpression"></a><span data-ttu-id="8cdba-162">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="8cdba-162">DbConstantExpression</span></span>  
 <span data-ttu-id="8cdba-163">Para cada constante visitada um parâmetro é criado.</span><span class="sxs-lookup"><span data-stu-id="8cdba-163">For each visited constant a parameter is created.</span></span>  
  
### <a name="dbpropertyexpression"></a><span data-ttu-id="8cdba-164">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="8cdba-164">DbPropertyExpression</span></span>  
 <span data-ttu-id="8cdba-165">Dado que a instância de DbPropertyExpression sempre representa a tabela de entrada, a menos que a geração criar um apelido (que ocorrem apenas em cenários de atualização quando uma variável da tabela é usado), nenhum alias precisa ser especificada para a entrada; a conversão tem como padrão o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="8cdba-165">Given that the Instance of the DbPropertyExpression always represents the input table, unless the generation has created an alias (which only happens in update scenarios when a table variable is used), no alias needs to be specified for the input; the translation defaults to the property name.</span></span>  
  
## <a name="generating-an-insert-sql-command"></a><span data-ttu-id="8cdba-166">Gerando um comando SQL de inserção</span><span class="sxs-lookup"><span data-stu-id="8cdba-166">Generating an Insert SQL Command</span></span>  
 <span data-ttu-id="8cdba-167">Para um DbInsertCommandTree determinado no provedor de exemplo, o comando gerado de inserção segue um dos dois modelos de inserção abaixo.</span><span class="sxs-lookup"><span data-stu-id="8cdba-167">For a given DbInsertCommandTree in the sample provider, the generated insert command follows one of the two insert templates below.</span></span>  
  
 <span data-ttu-id="8cdba-168">O primeiro modelo tem um comando executar a inserção dados os valores na lista de SetClauses, e uma instrução SELECT para retornar as propriedades especificadas na propriedade retornando para a linha inserida se a propriedade retornando não era nula.</span><span class="sxs-lookup"><span data-stu-id="8cdba-168">The first template has a command to perform the insert given the values in the list of SetClauses, and a SELECT statement to return the properties specified in the Returning property for the inserted row if the Returning property was not null.</span></span> <span data-ttu-id="8cdba-169">O elemento de predicado "\@ @ROWCOUNT > 0" é verdadeiro se uma linha foi inserida.</span><span class="sxs-lookup"><span data-stu-id="8cdba-169">The predicate element "\@@ROWCOUNT > 0" is true if a row was inserted.</span></span> <span data-ttu-id="8cdba-170">O elemento de predicado "keyMemberI = keyValueI &#124; SCOPE_IDENTITY ()" leva a forma "keyMemberI = SCOPE_IDENTITY ()" apenas se o keyMemeberI é uma chave store-gerado, porque SCOPE_IDENTITY () retorna o último valor de identidade inserido em uma identidade ( coluna Store-gerado).</span><span class="sxs-lookup"><span data-stu-id="8cdba-170">The predicate element "keyMemberI =  keyValueI &#124; scope_identity()" takes the shape  "keyMemberI =  scope_identity()" only if keyMemeberI is a store-generated key, because scope_identity() returns the last identity value inserted into an identity (store-generated) column.</span></span>  
  
```  
-- first insert Template  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES   
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 <span data-ttu-id="8cdba-171">O segundo modelo é necessário se a inserção especifica inserir uma linha onde a chave primária é gerado Store- mas não é um tipo inteiro e portanto não pode ser usada com scope_identity()).</span><span class="sxs-lookup"><span data-stu-id="8cdba-171">The second template is needed if the insert specifies inserting a row where the primary key is store-generated but is not an integer type and therefore can't be used with scope_identity()).</span></span> <span data-ttu-id="8cdba-172">Também é usado se houver uma chave Store- gerado composta.</span><span class="sxs-lookup"><span data-stu-id="8cdba-172">It is also used if there is a compound store-generated key.</span></span>  
  
```  
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
  
 <span data-ttu-id="8cdba-173">A seguir está um exemplo que usa o modelo que está incluído com o provedor de exemplo.</span><span class="sxs-lookup"><span data-stu-id="8cdba-173">The following is an example that uses the model that is included with the sample provider.</span></span> <span data-ttu-id="8cdba-174">Gerencia um comando de inserção de um DbInsertCommandTree.</span><span class="sxs-lookup"><span data-stu-id="8cdba-174">It generates an insert command from a DbInsertCommandTree.</span></span>  
  
 <span data-ttu-id="8cdba-175">O código a seguir insere uma categoria:</span><span class="sxs-lookup"><span data-stu-id="8cdba-175">The following code inserts a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = new Category();  
   c.CategoryName = "Test Category";  
   c.Description = "A new category for testing";  
   northwindContext.AddObject("Categories", c);  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="8cdba-176">Esse código gerencia a seguir árvore de comando, que é passada para o provedor:</span><span class="sxs-lookup"><span data-stu-id="8cdba-176">This code produces the following command tree, which is passed to the provider:</span></span>  
  
```  
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
  
 <span data-ttu-id="8cdba-177">O comando de armazenamento que o provedor exemplo gerencia é a seguinte instrução SQL:</span><span class="sxs-lookup"><span data-stu-id="8cdba-177">The store command that the sample provider produces is the following SQL statement:</span></span>  
  
```  
insert [dbo].[Categories]([CategoryName], [Description], [Picture])  
values (@p0, @p1, null)  
select [CategoryID]  
from [dbo].[Categories]  
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()  
```  
  
## <a name="generating-an-update-sql-command"></a><span data-ttu-id="8cdba-178">Gerando um comando SQL de atualização</span><span class="sxs-lookup"><span data-stu-id="8cdba-178">Generating an Update SQL Command</span></span>  
 <span data-ttu-id="8cdba-179">Para um determinado DbUpdateCommandTree, o comando gerado de atualização é baseado no modelo seguir:</span><span class="sxs-lookup"><span data-stu-id="8cdba-179">For a given DbUpdateCommandTree, the generated update command is based on the following template:</span></span>  
  
```  
-- UPDATE Template   
UPDATE <target>   
SET setClauseProprerty0 = setClauseValue0,  .. setClauseProprertyN = setClauseValueN  | @i = 0  
WHERE <predicate>  
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 <span data-ttu-id="8cdba-180">A cláusula set tem a cláusula set falso ("@i = 0") somente se nenhum conjunto de cláusulas forem especificado.</span><span class="sxs-lookup"><span data-stu-id="8cdba-180">The set clause has the fake set clause ("@i = 0") only if no set clauses are specified.</span></span> <span data-ttu-id="8cdba-181">Este é garantir que todas as colunas Store- computadas recalculados.</span><span class="sxs-lookup"><span data-stu-id="8cdba-181">This is to ensure that any store-computed columns are recomputed.</span></span>  
  
 <span data-ttu-id="8cdba-182">Somente se a propriedade retornando não é nulo, uma instrução SELECT é gerada para retornar as propriedades especificadas na propriedade retornando.</span><span class="sxs-lookup"><span data-stu-id="8cdba-182">Only if the Returning property is not null, a select statement is generated to return the properties specified in the Returning property.</span></span>  
  
 <span data-ttu-id="8cdba-183">O exemplo a seguir usa o modelo que está incluído com o provedor de exemplo para gerar um comando de atualização.</span><span class="sxs-lookup"><span data-stu-id="8cdba-183">The following example uses the model that is included with the sample provider to generate an update command.</span></span>  
  
 <span data-ttu-id="8cdba-184">O seguinte código do usuário atualiza uma categoria:</span><span class="sxs-lookup"><span data-stu-id="8cdba-184">The following user code updates a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();  
   c.CategoryName = "New test name";  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="8cdba-185">Esse código do usuário gerencia a seguir árvore de comando, que é passada para o provedor:</span><span class="sxs-lookup"><span data-stu-id="8cdba-185">This user code produces the following command tree, which is passed to the provider:</span></span>  
  
```  
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
  
 <span data-ttu-id="8cdba-186">O exemplo de provedor para gerenciar o seguinte comando de armazenamento:</span><span class="sxs-lookup"><span data-stu-id="8cdba-186">The sample provider produces the following store command:</span></span>  
  
```  
update [dbo].[Categories]  
set [CategoryName] = @p0  
where ([CategoryID] = @p1)   
```  
  
### <a name="generating-a-delete-sql-command"></a><span data-ttu-id="8cdba-187">Gerando um comando SQL delete</span><span class="sxs-lookup"><span data-stu-id="8cdba-187">Generating a Delete SQL Command</span></span>  
 <span data-ttu-id="8cdba-188">Para um determinado DbDeleteCommandTree, o comando DELETE gerado é baseado no modelo seguir:</span><span class="sxs-lookup"><span data-stu-id="8cdba-188">For a given DbDeleteCommandTree, the generated DELETE command is based on the following template:</span></span>  
  
```  
-- DELETE Template   
DELETE <target>   
WHERE <predicate>  
```  
  
 <span data-ttu-id="8cdba-189">O exemplo a seguir usa o modelo que está incluído com o provedor de exemplo para gerar um comando delete.</span><span class="sxs-lookup"><span data-stu-id="8cdba-189">The following example uses the model that is included with the sample provider to generate a delete command.</span></span>  
  
 <span data-ttu-id="8cdba-190">O seguinte código do usuário exclui uma categoria:</span><span class="sxs-lookup"><span data-stu-id="8cdba-190">The following user code deletes a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();  
   northwindContext.DeleteObject(c);  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="8cdba-191">Esse código do usuário gerencia a seguir árvore de comando, que é passada para o provedor.</span><span class="sxs-lookup"><span data-stu-id="8cdba-191">This user code produces the following command tree, which is passed to the provider.</span></span>  
  
```  
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
  
 <span data-ttu-id="8cdba-192">O seguinte comando de armazenamento é gerado pelo provedor exemplo:</span><span class="sxs-lookup"><span data-stu-id="8cdba-192">The following store command is produced by the sample provider:</span></span>  
  
```  
delete [dbo].[Categories]  
where ([CategoryID] = @p0)  
```  
  
## <a name="see-also"></a><span data-ttu-id="8cdba-193">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8cdba-193">See Also</span></span>  
 [<span data-ttu-id="8cdba-194">Escrevendo um Provedor de Dados do Entity Framework</span><span class="sxs-lookup"><span data-stu-id="8cdba-194">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
