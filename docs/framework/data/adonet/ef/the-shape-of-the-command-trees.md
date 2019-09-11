---
title: A forma das árvores de comando
ms.date: 03/30/2017
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
ms.openlocfilehash: 8368354049a77a56a5aa54ab500619576f41b0dc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854271"
---
# <a name="the-shape-of-the-command-trees"></a><span data-ttu-id="36883-102">A forma das árvores de comando</span><span class="sxs-lookup"><span data-stu-id="36883-102">The Shape of the Command Trees</span></span>

<span data-ttu-id="36883-103">O módulo de geração SQL é responsável por gerar uma consulta SQL backend específica com base em uma entrada dada comando expressão de consulta de árvore.</span><span class="sxs-lookup"><span data-stu-id="36883-103">The SQL generation module is responsible for generating a backend specific SQL query based on a given input query command tree expression.</span></span> <span data-ttu-id="36883-104">Esta seção descreve as características, propriedades, e a estrutura das árvores de comando de consulta.</span><span class="sxs-lookup"><span data-stu-id="36883-104">This section discusses the characteristics, properties, and structure of the query command trees.</span></span>

## <a name="query-command-trees-overview"></a><span data-ttu-id="36883-105">Visão geral das árvores de comando de consulta</span><span class="sxs-lookup"><span data-stu-id="36883-105">Query Command Trees Overview</span></span>

<span data-ttu-id="36883-106">Uma árvore de comando de consulta é uma representação do modelo de objeto de uma consulta.</span><span class="sxs-lookup"><span data-stu-id="36883-106">A query command tree is an object model representation of a query.</span></span> <span data-ttu-id="36883-107">Árvores de comando de consulta servem duas finalidades:</span><span class="sxs-lookup"><span data-stu-id="36883-107">Query command trees serve two purposes:</span></span>

- <span data-ttu-id="36883-108">Para expressar uma consulta de entrada que é especificada no Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="36883-108">To express an input query that is specified against the Entity Framework.</span></span>

- <span data-ttu-id="36883-109">Para expressar uma saída consulte que são fornecidas para um provedor e descrevam uma consulta na parte posterior.</span><span class="sxs-lookup"><span data-stu-id="36883-109">To express an output query that is given to a provider and describes a query against the backend.</span></span>

<span data-ttu-id="36883-110">Consulte uma semântica mais rica de suporte das árvores de comando do SQL: consultas 1999 compatíveis, incluindo suporte para trabalhar com coleções e operações aninhadas de tipo, como verificar se uma entidade é de um tipo específico, ou filtragem definem baseado em um tipo.</span><span class="sxs-lookup"><span data-stu-id="36883-110">Query command trees support richer semantics than SQL:1999 compliant queries, including support for working with nested collections and type operations, like checking whether an entity is of a particular type, or filtering sets based on a type.</span></span>

<span data-ttu-id="36883-111">A propriedade de DBQueryCommandTree.Query é a raiz da árvore de expressão que descreve a lógica de consulta.</span><span class="sxs-lookup"><span data-stu-id="36883-111">The DBQueryCommandTree.Query property is the root of the expression tree that describes the query logic.</span></span> <span data-ttu-id="36883-112">A propriedade de DBQueryCommandTree.Parameters contém uma lista de parâmetros que são usados na consulta.</span><span class="sxs-lookup"><span data-stu-id="36883-112">The DBQueryCommandTree.Parameters property contains a list of parameters that are used in the query.</span></span> <span data-ttu-id="36883-113">A árvore de expressão é composta de objetos de DbExpression.</span><span class="sxs-lookup"><span data-stu-id="36883-113">The expression tree is composed of DbExpression objects.</span></span>

<span data-ttu-id="36883-114">Um objeto de DbExpression representa qualquer computação.</span><span class="sxs-lookup"><span data-stu-id="36883-114">A DbExpression object represents some computation.</span></span> <span data-ttu-id="36883-115">Vários tipos de expressões são fornecidos pelo Entity Framework para compor expressões de consulta, incluindo constantes, variáveis, funções, construtores e operadores relacionais padrão como filtro e junção.</span><span class="sxs-lookup"><span data-stu-id="36883-115">Several kinds of expressions are provided by the Entity Framework for composing query expressions, including constants, variables, functions, constructors, and standard relational operators like filter and join.</span></span> <span data-ttu-id="36883-116">Cada objeto DbExpression tem uma propriedade ResultType que representa o tipo do resultado produzido por essa expressão.</span><span class="sxs-lookup"><span data-stu-id="36883-116">Every DbExpression object has a ResultType property that represents the type of the result produced by that expression.</span></span> <span data-ttu-id="36883-117">Esse tipo é expresso como um TypeUsage.</span><span class="sxs-lookup"><span data-stu-id="36883-117">This type is expressed as a TypeUsage.</span></span>

## <a name="shapes-of-the-output-query-command-tree"></a><span data-ttu-id="36883-118">Formas da árvore de comando de consulta de saída</span><span class="sxs-lookup"><span data-stu-id="36883-118">Shapes of the Output Query Command Tree</span></span>

<span data-ttu-id="36883-119">Árvores de comando de consulta de saída representam às consultas SQL () relacionais e aderem às regras muito mais rígidas do que aquelas que se aplicam para consulte árvores de comando.</span><span class="sxs-lookup"><span data-stu-id="36883-119">Output query command trees closely represent relational (SQL) queries and adhere to much stricter rules than those that apply to query command trees.</span></span> <span data-ttu-id="36883-120">Normalmente contêm as compilações que são transmitidos facilmente para SQL.</span><span class="sxs-lookup"><span data-stu-id="36883-120">They typically contain constructs that are easily translated to SQL.</span></span>

<span data-ttu-id="36883-121">Árvores de comando de entrada são expressas no modelo conceitual, que suporta propriedades de navegação, associações entre entidades, e herança.</span><span class="sxs-lookup"><span data-stu-id="36883-121">Input command trees are expressed against the conceptual model, which supports navigation properties, associations among entities, and inheritance.</span></span> <span data-ttu-id="36883-122">Árvores de comando de saída são expressas no modelo de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="36883-122">Output command trees are expressed against the storage model.</span></span> <span data-ttu-id="36883-123">Árvores de comando de entrada permitem que você projeta coleções aninhadas, mas as árvores de comando de saída não.</span><span class="sxs-lookup"><span data-stu-id="36883-123">Input command trees allow you to project nested collections, but output command trees do not.</span></span>

<span data-ttu-id="36883-124">Árvores de comando de consulta de saída são criadas usando um subconjunto dos objetos disponíveis de DbExpression e mesmo algumas expressões nesse subconjunto restringiram uso.</span><span class="sxs-lookup"><span data-stu-id="36883-124">Output query command trees are built using a subset of the available DbExpression objects and even some expressions in that subset have restricted usage.</span></span>

<span data-ttu-id="36883-125">Digite operações, como verificar se uma expressão fornecida seja de um tipo específico ou conjuntos de filtragem com base em um tipo, não estão atual em árvores de comando de saída.</span><span class="sxs-lookup"><span data-stu-id="36883-125">Type operations, like checking whether a given expression is of a particular type or filtering sets based on a type, are not present in output command trees.</span></span>

<span data-ttu-id="36883-126">Na saída comande árvores, somente as expressões que os valores Booleanos de retorno são usados para projeções e somente para predicados em expressões que exigem um predicado, como um filtro ou uma instrução case.</span><span class="sxs-lookup"><span data-stu-id="36883-126">In output command trees, only expressions that return Boolean values are used for projections and only for predicates in expressions requiring a predicate, like a filter or a case statement.</span></span>

<span data-ttu-id="36883-127">A raiz das árvores de um comando de consulta de saída é um objeto de DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="36883-127">The root of an output query command trees is a DbProjectExpression object.</span></span>

### <a name="expression-types-not-present-in-output-query-command-trees"></a><span data-ttu-id="36883-128">Tipos de expressão não presentes em árvores de comando de consulta de saída</span><span class="sxs-lookup"><span data-stu-id="36883-128">Expression Types Not Present in Output Query Command Trees</span></span>

<span data-ttu-id="36883-129">Os seguintes tipos de expressão não são válidos em uma árvore de comando de consulta de saída e não precisam ser tratados por provedores:</span><span class="sxs-lookup"><span data-stu-id="36883-129">The following expression types are not valid in an output query command tree and do not need to be handled by providers:</span></span>

- <span data-ttu-id="36883-130">DbDerefExpression</span><span class="sxs-lookup"><span data-stu-id="36883-130">DbDerefExpression</span></span>

- <span data-ttu-id="36883-131">DbEntityRefExpression</span><span class="sxs-lookup"><span data-stu-id="36883-131">DbEntityRefExpression</span></span>

- <span data-ttu-id="36883-132">DbRefKeyExpression</span><span class="sxs-lookup"><span data-stu-id="36883-132">DbRefKeyExpression</span></span>

- <span data-ttu-id="36883-133">DbIsOfExpression</span><span class="sxs-lookup"><span data-stu-id="36883-133">DbIsOfExpression</span></span>

- <span data-ttu-id="36883-134">DbOfTypeExpression</span><span class="sxs-lookup"><span data-stu-id="36883-134">DbOfTypeExpression</span></span>

- <span data-ttu-id="36883-135">DbRefExpression</span><span class="sxs-lookup"><span data-stu-id="36883-135">DbRefExpression</span></span>

- <span data-ttu-id="36883-136">DbRelationshipNavigationExpression</span><span class="sxs-lookup"><span data-stu-id="36883-136">DbRelationshipNavigationExpression</span></span>

- <span data-ttu-id="36883-137">DbTreatExpression</span><span class="sxs-lookup"><span data-stu-id="36883-137">DbTreatExpression</span></span>

### <a name="expression-restrictions-and-notes"></a><span data-ttu-id="36883-138">Restrições e notas de expressão</span><span class="sxs-lookup"><span data-stu-id="36883-138">Expression Restrictions and Notes</span></span>

<span data-ttu-id="36883-139">Várias expressões podem ser utilizadas somente em uma maneira strict em árvores de comando de consulta de saída:</span><span class="sxs-lookup"><span data-stu-id="36883-139">Many expressions can only be used in a restricted manner in output query command trees:</span></span>

#### <a name="dbfunctionexpression"></a><span data-ttu-id="36883-140">DbFunctionExpression</span><span class="sxs-lookup"><span data-stu-id="36883-140">DbFunctionExpression</span></span>

<span data-ttu-id="36883-141">Os seguintes tipos de função podem ser passados:</span><span class="sxs-lookup"><span data-stu-id="36883-141">The following function types can be passed:</span></span>

- <span data-ttu-id="36883-142">Funções canônicas que são reconhecidas pelo namespace de Edm.</span><span class="sxs-lookup"><span data-stu-id="36883-142">Canonical functions that are recognized by the Edm namespace.</span></span>

- <span data-ttu-id="36883-143">Funções internas (de armazenamento) que são reconhecidas pelo BuiltInAttribute.</span><span class="sxs-lookup"><span data-stu-id="36883-143">Built-in (store) functions that are recognized by the BuiltInAttribute.</span></span>

- <span data-ttu-id="36883-144">Funções definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="36883-144">User-defined functions.</span></span>

<span data-ttu-id="36883-145">Funções canônicas (consulte [funções canônicas](./language-reference/canonical-functions.md) para obter mais informações) são especificadas como parte do Entity Framework, e os provedores devem fornecer implementações para funções canônicas com base nessas especificações.</span><span class="sxs-lookup"><span data-stu-id="36883-145">Canonical functions (see [Canonical Functions](./language-reference/canonical-functions.md) for more information) are specified as part of the Entity Framework, and providers should supply implementations for canonical functions based on those specifications.</span></span> <span data-ttu-id="36883-146">Funções de Store são baseados nas especificações no manifesto correspondente do provedor.</span><span class="sxs-lookup"><span data-stu-id="36883-146">Store functions are based on the specifications in the corresponding provider manifest.</span></span> <span data-ttu-id="36883-147">As funções definidas pelo usuário são baseadas nas especificações em SSDL.</span><span class="sxs-lookup"><span data-stu-id="36883-147">User defined functions are based on specifications in the SSDL.</span></span>

<span data-ttu-id="36883-148">Além disso, as funções que têm o atributo de NiladicFunction não têm nenhum argumento e devem ser traduzidas sem o parêntese no final.</span><span class="sxs-lookup"><span data-stu-id="36883-148">Also, functions having the NiladicFunction attribute have no arguments and should be translated without the parenthesis at the end.</span></span>  <span data-ttu-id="36883-149">Ou seja, para  *\<FunctionName >* em vez de  *\<FunctionName > ()* .</span><span class="sxs-lookup"><span data-stu-id="36883-149">That is, to *\<functionName>* instead of *\<functionName>()*.</span></span>

#### <a name="dbnewinstanceexpression"></a><span data-ttu-id="36883-150">DbNewInstanceExpression</span><span class="sxs-lookup"><span data-stu-id="36883-150">DbNewInstanceExpression</span></span>

<span data-ttu-id="36883-151">DbNewInstanceExpression pode ocorrer somente nos dois seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="36883-151">DbNewInstanceExpression can only occur in the following two cases:</span></span>

- <span data-ttu-id="36883-152">Como a propriedade de projeção de DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="36883-152">As the Projection property of DbProjectExpression.</span></span>  <span data-ttu-id="36883-153">Quando usadas como esta'n as seguintes limitações se aplicam:</span><span class="sxs-lookup"><span data-stu-id="36883-153">When used as such the following restrictions apply:</span></span>

  - <span data-ttu-id="36883-154">O tipo do resultado deve ser um tipo de linha.</span><span class="sxs-lookup"><span data-stu-id="36883-154">The result type must be a row type.</span></span>

  - <span data-ttu-id="36883-155">Cada um dos argumentos é uma expressão que gerencia um resultado com um tipo primitivo.</span><span class="sxs-lookup"><span data-stu-id="36883-155">Each of its arguments is an expression that produces a result with a primitive type.</span></span> <span data-ttu-id="36883-156">Normalmente, cada argumento é uma expressão escalar, como um PropertyExpression sobre um DbVariableReferenceExpression, uma chamada de função, ou uma computação aritmética de DbPropertyExpression sobre um DbVariableReferenceExpression ou uma chamada de função.</span><span class="sxs-lookup"><span data-stu-id="36883-156">Typically, each argument is a scalar expression, like a PropertyExpression over a DbVariableReferenceExpression, a function invocation, or an arithmetic computation of the DbPropertyExpression over a DbVariableReferenceExpression or a function invocation.</span></span> <span data-ttu-id="36883-157">No entanto, uma expressão que representa um subconsulta escalar também pode ocorrer na lista de argumentos para um DbNewInstanceExpression.</span><span class="sxs-lookup"><span data-stu-id="36883-157">However, an expression representing a scalar subquery can also occur in the list of arguments for a DbNewInstanceExpression.</span></span> <span data-ttu-id="36883-158">Uma expressão que representa uma subconsulta escalar é uma árvore de expressão que representa uma subconsulta que retorna exatamente uma linha e uma coluna de um tipo primitivo com uma raiz de objeto DbElementExpression</span><span class="sxs-lookup"><span data-stu-id="36883-158">An expression that represents a scalar subquery is an expression tree that represents a subquery that returns exactly one row and one column of a primitive type with a DbElementExpression object root</span></span>

- <span data-ttu-id="36883-159">Com um tipo de retorno da coleção, nesse caso define uma nova coleção de expressões fornecidas como argumentos.</span><span class="sxs-lookup"><span data-stu-id="36883-159">With a collection return type, in which case it defines a new collection of the expressions provided as arguments.</span></span>

#### <a name="dbvariablereferenceexpression"></a><span data-ttu-id="36883-160">DbVariableReferenceExpression</span><span class="sxs-lookup"><span data-stu-id="36883-160">DbVariableReferenceExpression</span></span>

<span data-ttu-id="36883-161">Um DbVariableReferenceExpression tem que ser um filho do nó de DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="36883-161">A DbVariableReferenceExpression has to be a child of DbPropertyExpression node.</span></span>

#### <a name="dbgroupbyexpression"></a><span data-ttu-id="36883-162">DbGroupByExpression</span><span class="sxs-lookup"><span data-stu-id="36883-162">DbGroupByExpression</span></span>

<span data-ttu-id="36883-163">A propriedade as agregações de um DbGroupByExpression pode ter apenas elementos do tipo DbFunctionAggregate.</span><span class="sxs-lookup"><span data-stu-id="36883-163">The Aggregates property of a DbGroupByExpression can only have elements of type DbFunctionAggregate.</span></span> <span data-ttu-id="36883-164">Não há nenhum outro tipo agregado.</span><span class="sxs-lookup"><span data-stu-id="36883-164">There are no other aggregate types.</span></span>

#### <a name="dblimitexpression"></a><span data-ttu-id="36883-165">DbLimitExpression</span><span class="sxs-lookup"><span data-stu-id="36883-165">DbLimitExpression</span></span>

<span data-ttu-id="36883-166">O limite de propriedade só pode ser um DbConstantExpression ou um DbParameterReferenceExpression.</span><span class="sxs-lookup"><span data-stu-id="36883-166">The property Limit can only be a DbConstantExpression or a DbParameterReferenceExpression.</span></span> <span data-ttu-id="36883-167">Também a propriedade WithTies é sempre false até a data do .NET Framework versão 3,5.</span><span class="sxs-lookup"><span data-stu-id="36883-167">Also property WithTies is always false as of version 3.5 of the .NET Framework.</span></span>

#### <a name="dbscanexpression"></a><span data-ttu-id="36883-168">DbScanExpression</span><span class="sxs-lookup"><span data-stu-id="36883-168">DbScanExpression</span></span>

<span data-ttu-id="36883-169">Quando usado em árvores de comando de saída, o DbScanExpression representa efetivamente uma verificação em uma tabela, uma exibição ou uma consulta de repositório, representada por EntitySetBase:: Target.</span><span class="sxs-lookup"><span data-stu-id="36883-169">When used in output command trees, the DbScanExpression effectively represents a scan over a table, a view, or a store query, represented by EntitySetBase::Target.</span></span>

<span data-ttu-id="36883-170">Se a propriedade de metadados "definindo a consulta" do destino for não nula, ela representará uma consulta, o texto de consulta para o qual é fornecido na propriedade de metadados na linguagem específica do provedor (ou dialeto) conforme especificado na definição do esquema de repositório.</span><span class="sxs-lookup"><span data-stu-id="36883-170">If the metadata property "Defining Query" of the target is non-null, then it represents a query, the query text for which is provided in that metadata property in the provider’s specific language (or dialect) as specified in the store schema definition.</span></span>

<span data-ttu-id="36883-171">Caso contrário, o destino representa uma tabela ou uma exibição.</span><span class="sxs-lookup"><span data-stu-id="36883-171">Otherwise, the target represents a table or a view.</span></span> <span data-ttu-id="36883-172">Seu prefixo de esquema está na propriedade de metadados "Schema", se não for NULL, caso contrário, é o nome do contêiner da entidade.</span><span class="sxs-lookup"><span data-stu-id="36883-172">Its schema prefix is either in the "Schema" metadata property, if not null, otherwise is the entity container name.</span></span>  <span data-ttu-id="36883-173">O nome da tabela ou exibição é a propriedade de metadados "Table", se não for NULL, caso contrário, a propriedade Name da base do conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="36883-173">The table or view name is either the "Table" metadata property, if not null, otherwise the Name property of the entity set base.</span></span>

<span data-ttu-id="36883-174">Todas essas propriedades são originados de definição de EntitySet correspondente no arquivo de definição do esquema de armazenamento (SSDL).</span><span class="sxs-lookup"><span data-stu-id="36883-174">All these properties originate from the definition of the corresponding EntitySet in the store schema definition file (the SSDL).</span></span>

### <a name="using-primitive-types"></a><span data-ttu-id="36883-175">Usando tipos primitivos</span><span class="sxs-lookup"><span data-stu-id="36883-175">Using Primitive Types</span></span>

<span data-ttu-id="36883-176">Quando os tipos primitivos são referenciados em árvores de comando de saída, normalmente são referenciados em tipos primitivos de modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="36883-176">When primitive types are referenced in output command trees, they are typically referenced in the conceptual model's primitive types.</span></span> <span data-ttu-id="36883-177">No entanto, certos expressões, provedores precisam o tipo primitivo correspondente do armazenamento.</span><span class="sxs-lookup"><span data-stu-id="36883-177">However, for certain expressions, providers need the corresponding store primitive type.</span></span> <span data-ttu-id="36883-178">Os exemplos de como expressões incluem DbCastExpression e possivelmente DbNullExpression, se o provedor precisa converter o zero para o tipo correspondente.</span><span class="sxs-lookup"><span data-stu-id="36883-178">Examples of such expressions include DbCastExpression and possibly DbNullExpression, if the provider needs to cast the null to the corresponding type.</span></span> <span data-ttu-id="36883-179">Nesses casos, os provedores devem fazer o mapeamento para o tipo de provedor com base no tipo primitivo tipo e em suas facetas.</span><span class="sxs-lookup"><span data-stu-id="36883-179">In these cases, providers should do the mapping to the provider type based on the primitive type kind and its facets.</span></span>

## <a name="see-also"></a><span data-ttu-id="36883-180">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36883-180">See also</span></span>

- [<span data-ttu-id="36883-181">Geração de SQL</span><span class="sxs-lookup"><span data-stu-id="36883-181">SQL Generation</span></span>](sql-generation.md)
