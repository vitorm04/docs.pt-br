---
title: Gerando SQL das árvores de comando - práticas recomendadas
ms.date: 03/30/2017
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
ms.openlocfilehash: 0087c67b12b4b6ea36cabd5800b7be0a72fc4a90
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="generating-sql-from-command-trees---best-practices"></a><span data-ttu-id="4f86b-102">Gerando SQL das árvores de comando - práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="4f86b-102">Generating SQL from Command Trees - Best Practices</span></span>
<span data-ttu-id="4f86b-103">O modelo das árvores de comando de consulta de saída a consulta expressável no SQL.</span><span class="sxs-lookup"><span data-stu-id="4f86b-103">Output query command trees closely model queries expressible in SQL.</span></span> <span data-ttu-id="4f86b-104">No entanto, há determinados desafios comum para criadores de provedor para gerar o SQL de uma árvore de comando de saída.</span><span class="sxs-lookup"><span data-stu-id="4f86b-104">However, there are certain common challenges for provider writers when generating SQL from an output command tree.</span></span> <span data-ttu-id="4f86b-105">Este tópico discute esses desafios.</span><span class="sxs-lookup"><span data-stu-id="4f86b-105">This topic discusses these challenges.</span></span> <span data-ttu-id="4f86b-106">No próximo tópico, o provedor exemplo mostra como resolver esses desafios.</span><span class="sxs-lookup"><span data-stu-id="4f86b-106">In the next topic, the sample provider shows how to address these challenges.</span></span>  
  
## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a><span data-ttu-id="4f86b-107">Os nós de DbExpression do grupo em um SELECIONAM a instrução SQL</span><span class="sxs-lookup"><span data-stu-id="4f86b-107">Group DbExpression Nodes in a SQL SELECT Statement</span></span>  
 <span data-ttu-id="4f86b-108">Uma instrução SQL típica tem uma estrutura aninhada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="4f86b-108">A typical SQL statement has a nested structure of the following shape:</span></span>  
  
```  
SELECT …  
FROM …  
WHERE …  
GROUP BY …  
ORDER BY …  
```  
  
 <span data-ttu-id="4f86b-109">Uma ou mais cláusulas podem estar vazios.</span><span class="sxs-lookup"><span data-stu-id="4f86b-109">One or more clauses may be empty.</span></span>  <span data-ttu-id="4f86b-110">Uma instrução SELECT aninhada pode ocorrer em algumas linhas.</span><span class="sxs-lookup"><span data-stu-id="4f86b-110">A nested SELECT statement could occur in any of the lines.</span></span>  
  
 <span data-ttu-id="4f86b-111">Uma conversão possível de uma árvore de comando de consulta em uma instrução SQL SELECT de um subconsulta para cada operador relacional.</span><span class="sxs-lookup"><span data-stu-id="4f86b-111">A possible translation of a query command tree into a SQL SELECT statement would produce one subquery for every relational operator.</span></span> <span data-ttu-id="4f86b-112">No entanto, isso resultaria a subconsultas aninhados desnecessários que poderiam ser difíceis de ler.</span><span class="sxs-lookup"><span data-stu-id="4f86b-112">However, that would lead to unnecessary nested subqueries that would be difficult to read.</span></span>  <span data-ttu-id="4f86b-113">Em alguns armazenamentos de dados, a consulta pode executar de maneira distorcida.</span><span class="sxs-lookup"><span data-stu-id="4f86b-113">On some data stores, the query may perform poorly.</span></span>  
  
 <span data-ttu-id="4f86b-114">Como exemplo, considere a seguinte árvore de comando de consulta</span><span class="sxs-lookup"><span data-stu-id="4f86b-114">As an example, consider the following query command tree</span></span>  
  
```  
Project (  
a.x,  
   a = Filter(  
      b.y = 5,   
      b = Scan("TableA")  
   )  
)  
```  
  
 <span data-ttu-id="4f86b-115">Uma conversão não geraria:</span><span class="sxs-lookup"><span data-stu-id="4f86b-115">An inefficient translation would produce:</span></span>  
  
```  
SELECT a.x  
FROM (   SELECT *  
         FROM TableA as b  
         WHERE b.y = 5) as a  
```  
  
 <span data-ttu-id="4f86b-116">Observe que cada nó da expressão relacional se torna uma nova declaração SELECT SQL.</span><span class="sxs-lookup"><span data-stu-id="4f86b-116">Note that every relational expression node becomes a new SQL SELECT statement.</span></span>  
  
 <span data-ttu-id="4f86b-117">Portanto, é importante agregar muitas como nós de expressão como possível em uma única instrução SQL SELECT para preservar a exatidão.</span><span class="sxs-lookup"><span data-stu-id="4f86b-117">Therefore, it is important to aggregate as many expression nodes as possible into a single SQL SELECT statement while preserving correctness.</span></span>  
  
 <span data-ttu-id="4f86b-118">O resultado de uma agregação para o exemplo anterior apresentado seria:</span><span class="sxs-lookup"><span data-stu-id="4f86b-118">The result of such aggregation for the example presented above would be:</span></span>  
  
```  
SELECT b.x   
FROM TableA as b  
WHERE b.y = 5  
```  
  
## <a name="flatten-joins-in-a-sql-select-statement"></a><span data-ttu-id="4f86b-119">Aplaine join em uma instrução SQL SELECT</span><span class="sxs-lookup"><span data-stu-id="4f86b-119">Flatten Joins in a SQL SELECT Statement</span></span>  
 <span data-ttu-id="4f86b-120">Um caso de agregar vários nós em uma única instrução SQL SELECT é agregar várias condições a expressões em uma única instrução SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="4f86b-120">One case of aggregating multiple nodes into a single SQL SELECT statement is aggregating multiple join expressions into a single SQL SELECT statement.</span></span> <span data-ttu-id="4f86b-121">DbJoinExpression representa um único join entre duas entradas.</span><span class="sxs-lookup"><span data-stu-id="4f86b-121">DbJoinExpression represents a single join between two inputs.</span></span> <span data-ttu-id="4f86b-122">No entanto, como parte de uma única instrução SQL SELECT, mais de uma join pode ser especificado.</span><span class="sxs-lookup"><span data-stu-id="4f86b-122">However, as part of a single SQL SELECT statement, more than one join can be specified.</span></span> <span data-ttu-id="4f86b-123">Em que os casos join são executados na ordem especificada.</span><span class="sxs-lookup"><span data-stu-id="4f86b-123">In that case the joins are performed in the order specified.</span></span>  
  
 <span data-ttu-id="4f86b-124">A espinha esquerda, join (joins que aparece como um filho de outro esquerdo joins) pode ser mais facilmente aplainada em uma única instrução SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="4f86b-124">Left spine joins, (joins that appear as a left child of another join) can be more easily flattened into a single SQL SELECT statement.</span></span> <span data-ttu-id="4f86b-125">Por exemplo, considere a seguinte árvore de comando de consulta:</span><span class="sxs-lookup"><span data-stu-id="4f86b-125">For example, consider the following query command tree:</span></span>  
  
```  
InnerJoin(  
   a = LeftOuterJoin(  
   b = Extent("TableA")  
   c = Extent("TableB")  
   ON b.y = c.x ),  
   d = Extent("TableC")   
   ON a.b.y = d.z  
)  
```  
  
 <span data-ttu-id="4f86b-126">Isso pode ser convertido em corretamente:</span><span class="sxs-lookup"><span data-stu-id="4f86b-126">This can be correctly translated into:</span></span>  
  
```  
SELECT *  
FROM TableA as b  
LEFT OUTER JOIN TableB as c ON b.y = c.x  
INNER JOIN TableC as d ON b.y = d.z  
```  
  
 <span data-ttu-id="4f86b-127">No entanto, a espinha não esquerda join não pode ser facilmente aplainada, e você não deve tentar aplainá-los.</span><span class="sxs-lookup"><span data-stu-id="4f86b-127">However, non-left spine joins cannot easily be flattened, and you should not try to flatten them.</span></span> <span data-ttu-id="4f86b-128">Por exemplo, join na árvore de comando de consulta:</span><span class="sxs-lookup"><span data-stu-id="4f86b-128">For example, the joins in the following query command tree:</span></span>  
  
```  
InnerJoin(  
   a = Extent("TableA")   
   b = LeftOuterJoin(  
   c = Extent("TableB")  
   d = Extent("TableC")  
   ON c.y = d.x),  
   ON a.z = b.c.y  
)  
```  
  
 <span data-ttu-id="4f86b-129">É convertido para uma instrução SQL SELECT com subpropriedades uma consulta.</span><span class="sxs-lookup"><span data-stu-id="4f86b-129">Would be translated to a SQL SELECT statement with a sub-query.</span></span>  
  
```  
SELECT *  
FROM TableA as a  
INNER JOIN (SELECT *   
   FROM TableB as c   
   LEFT OUTER JOIN TableC as d  
   ON c.y = d.x) as b  
ON b.y = d.z  
```  
  
## <a name="input-alias-redirecting"></a><span data-ttu-id="4f86b-130">Entre o redirecionamento alias</span><span class="sxs-lookup"><span data-stu-id="4f86b-130">Input Alias Redirecting</span></span>  
 <span data-ttu-id="4f86b-131">Para explicar o alias de entrada que redirecionem, considere a estrutura das expressões relacionais, como DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression, e DbSkipExpression.</span><span class="sxs-lookup"><span data-stu-id="4f86b-131">To explain input alias redirecting, consider the structure of the relational expressions, such as DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression, and DbSkipExpression.</span></span>  
  
 <span data-ttu-id="4f86b-132">Cada um desses tipos tem uma ou mais propriedades de entrada que descrevem uma coleção de entrada, e corresponder a variável de associação para cada entrada é usado para representar cada elemento da entrada durante uma passagem de coleção.</span><span class="sxs-lookup"><span data-stu-id="4f86b-132">Each of these types has one or more Input properties that describe an input collection, and a binding variable corresponding to each input is used to represent each element of that input during a collection traversal.</span></span> <span data-ttu-id="4f86b-133">A variável de associação é usado para se referir ao elemento de entrada, por exemplo na propriedade de predicado de um DbFilterExpression ou propriedade de projeção de um DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="4f86b-133">The binding variable is used when referring to the input element, for example in the Predicate property of a DbFilterExpression or the Projection property of a DbProjectExpression.</span></span>  
  
 <span data-ttu-id="4f86b-134">Para agregar uma expressão mais relacional nós em um único SELECIONAM a instrução SQL, e avaliar uma expressão que é parte de uma expressão relacional (por exemplo parte da projeção de um DbProjectExpression) a variável de associação que usa não pode ser o mesmo que o alias de entrada, porque várias associações de expressão precisariam ser redirecionada para uma única extensão.</span><span class="sxs-lookup"><span data-stu-id="4f86b-134">When aggregating more relational expression nodes into a single SQL SELECT statement, and evaluating an expression that is part of a relational expression (for example part of the Projection property of a DbProjectExpression) the binding variable that it uses may not be the same as the alias of the input, as multiple expression bindings would have to be redirected to a single extent.</span></span>  <span data-ttu-id="4f86b-135">Esse problema é chamado renomear alias.</span><span class="sxs-lookup"><span data-stu-id="4f86b-135">This problem is called alias renaming.</span></span>  
  
 <span data-ttu-id="4f86b-136">Considere o primeiro exemplo deste tópico.</span><span class="sxs-lookup"><span data-stu-id="4f86b-136">Consider the first example in this topic.</span></span> <span data-ttu-id="4f86b-137">Se fazendo a conversão de naïve e traduzir a projeção a.x (DbPropertyExpression (a, x)), está correto para converter em `a.x` porque nós com a entrada como “a” para corresponder a variável de associação.</span><span class="sxs-lookup"><span data-stu-id="4f86b-137">If doing the naïve translation and translating the Projection a.x (DbPropertyExpression(a, x)), it is correct to translate it into `a.x` because we have aliased the input as "a" to match the binding variable.</span></span>  <span data-ttu-id="4f86b-138">No entanto, para agregar ambos os nós em um único SELECIONAM a instrução SQL, você precisará converter o mesmo DbPropertyExpression em `b.x`, porque a entrada com com “b”.</span><span class="sxs-lookup"><span data-stu-id="4f86b-138">However, when aggregating both the nodes into a single SQL SELECT statement, you need to translate the same DbPropertyExpression into `b.x`, as the input has been aliased with "b".</span></span>  
  
## <a name="join-alias-flattening"></a><span data-ttu-id="4f86b-139">Adição a ajuste alias</span><span class="sxs-lookup"><span data-stu-id="4f86b-139">Join Alias Flattening</span></span>  
 <span data-ttu-id="4f86b-140">Ao contrário de alguma outra expressão relacional em uma árvore de comando de saída, a saída de DbJoinExpression um tipo de resultado que é uma linha que consiste em duas colunas, cada um deless corresponde a uma das entradas.</span><span class="sxs-lookup"><span data-stu-id="4f86b-140">Unlike any other relational expression in an output command tree, the DbJoinExpression outputs a result type that is a row consisting of two columns, each of which corresponds to one of the inputs.</span></span> <span data-ttu-id="4f86b-141">Quando um DbPropertyExpresssion é compilado para acessar uma propriedade escalar que se origina de uma união, está sobre um outro DbPropertyExpresssion.</span><span class="sxs-lookup"><span data-stu-id="4f86b-141">When a DbPropertyExpresssion is built to access a scalar property originating from a join, it is over another DbPropertyExpresssion.</span></span>  
  
 <span data-ttu-id="4f86b-142">Os exemplos incluem “no exemplo a.b.y” 2 “e” no exemplo b.c.y 3.</span><span class="sxs-lookup"><span data-stu-id="4f86b-142">Examples include "a.b.y" in example 2 and "b.c.y" in example 3.</span></span> <span data-ttu-id="4f86b-143">No entanto nas instruções SQL correspondentes esses são referidos como “b.y”.</span><span class="sxs-lookup"><span data-stu-id="4f86b-143">However in the corresponding SQL statements these are referred as "b.y".</span></span> <span data-ttu-id="4f86b-144">Esta novamente serrilha é chamada join a ajuste alias.</span><span class="sxs-lookup"><span data-stu-id="4f86b-144">This re-aliasing is called join alias flattening.</span></span>  
  
## <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="4f86b-145">Renomear alias o nome da coluna e de extensão</span><span class="sxs-lookup"><span data-stu-id="4f86b-145">Column Name and Extent Alias Renaming</span></span>  
 <span data-ttu-id="4f86b-146">Se uma consulta SQL SELECT que tenha uma união tem que ser concluída com uma projeção, para enumerar todas as colunas de participação de entradas, uma colisão de nome pode ocorrer, desde que mais de uma entrada pode ter o mesmo nome de coluna.</span><span class="sxs-lookup"><span data-stu-id="4f86b-146">If a SQL SELECT query that has a join has to be completed with a projection, when enumerating all the participating columns from the inputs, a name collision may occur, as more than one input may have the same column name.</span></span> <span data-ttu-id="4f86b-147">Use um nome diferente para que a coluna evite a colisão.</span><span class="sxs-lookup"><span data-stu-id="4f86b-147">Use a different name for the column to avoid the collision.</span></span>  
  
 <span data-ttu-id="4f86b-148">Além disso, quando ajuste joins, as tabelas de participação (ou os subconsultas) podem ter alias de colisão nesse caso essas precisam ser renomeados.</span><span class="sxs-lookup"><span data-stu-id="4f86b-148">Also, when flattening joins, participating tables (or subqueries) may have colliding aliases in which case these need to be renamed.</span></span>  
  
## <a name="avoid-select-"></a><span data-ttu-id="4f86b-149">Evite SELECT \*</span><span class="sxs-lookup"><span data-stu-id="4f86b-149">Avoid SELECT \*</span></span>  
 <span data-ttu-id="4f86b-150">Não use `SELECT *` para selecionar as tabelas de base.</span><span class="sxs-lookup"><span data-stu-id="4f86b-150">Do not use `SELECT *` to select from base tables.</span></span> <span data-ttu-id="4f86b-151">O modelo de armazenamento em um [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplicativo pode incluir somente um subconjunto das colunas que estão na tabela de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="4f86b-151">The storage model in an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application may only include a subset of the columns that are in the database table.</span></span> <span data-ttu-id="4f86b-152">Nesse caso, `SELECT *` pode produzir um resultado incorreto.</span><span class="sxs-lookup"><span data-stu-id="4f86b-152">In this case, `SELECT *` may produce an incorrect result.</span></span> <span data-ttu-id="4f86b-153">Em vez disso, você deve especificar todas as colunas de participação usando os nomes de coluna tipo do resultado das expressões de participação.</span><span class="sxs-lookup"><span data-stu-id="4f86b-153">Instead, you should specify all participating columns by using the column names from the result type of the participating expressions.</span></span>  
  
## <a name="reuse-of-expressions"></a><span data-ttu-id="4f86b-154">Reutilização de expressões</span><span class="sxs-lookup"><span data-stu-id="4f86b-154">Reuse of Expressions</span></span>  
 <span data-ttu-id="4f86b-155">Expressões podem ser reutilizadas na árvore de comando de consulta passado pelo [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4f86b-155">Expressions may be reused in the query command tree passed by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="4f86b-156">Não suponha que cada expressão aparece apenas uma vez na árvore de comando de consulta.</span><span class="sxs-lookup"><span data-stu-id="4f86b-156">Do not assume that each expression appears only once in the query command tree.</span></span>  
  
## <a name="mapping-primitive-types"></a><span data-ttu-id="4f86b-157">Tipos primitivos de mapeamento</span><span class="sxs-lookup"><span data-stu-id="4f86b-157">Mapping Primitive Types</span></span>  
 <span data-ttu-id="4f86b-158">Quando mapear conceitual (EDM) tipos para tipos de provedor, você deve mapear para o tipo o maior (Int32) para que todos os possíveis valores caber.</span><span class="sxs-lookup"><span data-stu-id="4f86b-158">When mapping conceptual (EDM) types to provider types, you should map to the widest type (Int32) so that all possible values fit.</span></span> <span data-ttu-id="4f86b-159">Além disso, evite o mapeamento para tipos que não pode ser usado para várias operações, como tipos BLOB (por exemplo, `ntext` no SQL Server).</span><span class="sxs-lookup"><span data-stu-id="4f86b-159">Also, avoid mapping to types that cannot be used for many operations, like BLOB types (for example, `ntext` in SQL Server).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f86b-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f86b-160">See Also</span></span>  
 [<span data-ttu-id="4f86b-161">Geração de SQL</span><span class="sxs-lookup"><span data-stu-id="4f86b-161">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
