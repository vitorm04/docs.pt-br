---
title: Arquitetura e design
ms.date: 03/30/2017
ms.assetid: bd738d39-00e2-4bab-b387-90aac1a014bd
ms.openlocfilehash: c2e8ff5f21a2941d75b21915552e6935a1423978
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766862"
---
# <a name="architecture-and-design"></a><span data-ttu-id="8b967-102">Arquitetura e design</span><span class="sxs-lookup"><span data-stu-id="8b967-102">Architecture and Design</span></span>
<span data-ttu-id="8b967-103">O módulo de geração de SQL no [provedor exemplo](http://go.microsoft.com/fwlink/?LinkId=180616) é implementado como um visitante na árvore de expressão que representa a árvore de comandos.</span><span class="sxs-lookup"><span data-stu-id="8b967-103">The SQL generation module in the [Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) is implemented as a visitor on the expression tree that represents the command tree.</span></span> <span data-ttu-id="8b967-104">A geração é feita em uma única passada sobre a árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="8b967-104">The generation is done in a single pass over the expression tree.</span></span>  
  
 <span data-ttu-id="8b967-105">Os nós de árvore são processados a partir de baixo.</span><span class="sxs-lookup"><span data-stu-id="8b967-105">The nodes of the tree are processed from the bottom up.</span></span> <span data-ttu-id="8b967-106">Primeiro, uma estrutura intermediária é gerada: SqlSelectStatement ou SqlBuilder, ambos que implementam ISqlFragment.</span><span class="sxs-lookup"><span data-stu-id="8b967-106">First, an intermediate structure is produced: SqlSelectStatement or SqlBuilder, both implementing ISqlFragment.</span></span> <span data-ttu-id="8b967-107">Em seguida, a instrução SQL de cadeia de caracteres é gerado dessa estrutura.</span><span class="sxs-lookup"><span data-stu-id="8b967-107">Next, the string SQL statement is produced from that structure.</span></span> <span data-ttu-id="8b967-108">Há dois motivos para a estrutura intermediário:</span><span class="sxs-lookup"><span data-stu-id="8b967-108">There are two reasons for the intermediate structure:</span></span>  
  
-   <span data-ttu-id="8b967-109">Logicamente, uma instrução SQL SELECT está fora de serviço preenchido.</span><span class="sxs-lookup"><span data-stu-id="8b967-109">Logically, a SQL SELECT statement is populated out of order.</span></span> <span data-ttu-id="8b967-110">Os nós que participam na cláusula são visitados antes que os nós que participam em WHERE GRUPO, PERTO, e a cláusula ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="8b967-110">The nodes that participate in the FROM clause are visited before the nodes that participate in the WHERE, GROUP BY, and the ORDER BY clause.</span></span>  
  
-   <span data-ttu-id="8b967-111">Para renomear alias, você deve identificar todas as aliases usadas para evitar colisões em renomear.</span><span class="sxs-lookup"><span data-stu-id="8b967-111">To rename aliases, you must identify all used aliases to avoid collisions during renaming.</span></span> <span data-ttu-id="8b967-112">Para adiar as opções renomeando em SqlBuilder, o símbolo de uso objetos para representar as colunas que são candidatos para renomear.</span><span class="sxs-lookup"><span data-stu-id="8b967-112">To defer the renaming choices in SqlBuilder, use Symbol objects to represent the columns that are candidates for renaming.</span></span>  
  
 <span data-ttu-id="8b967-113">![Diagrama de](../../../../../docs/framework/data/adonet/ef/media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")</span><span class="sxs-lookup"><span data-stu-id="8b967-113">![Diagram](../../../../../docs/framework/data/adonet/ef/media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")</span></span>  
  
 <span data-ttu-id="8b967-114">Na primeira etapa, a visitar a árvore de expressão, as expressões são agrupadas em SqlSelectStatements, join são aplainadas, e ingressar em alias são aplainadas.</span><span class="sxs-lookup"><span data-stu-id="8b967-114">In the first phase, while visiting the expression tree, expressions are grouped into SqlSelectStatements, joins are flattened, and join aliases are flattened.</span></span> <span data-ttu-id="8b967-115">Durante esta etapa, os objetos do símbolo representam colunas ou alias de entrada que podem ser renomeados.</span><span class="sxs-lookup"><span data-stu-id="8b967-115">During this pass, Symbol objects represent columns or input aliases that may be renamed.</span></span>  
  
 <span data-ttu-id="8b967-116">Na segunda etapa, para gerar a cadeia de caracteres real, o alias são renomeados.</span><span class="sxs-lookup"><span data-stu-id="8b967-116">In the second phase, while producing the actual string, aliases are renamed.</span></span>  
  
## <a name="data-structures"></a><span data-ttu-id="8b967-117">Estruturas de dados</span><span class="sxs-lookup"><span data-stu-id="8b967-117">Data Structures</span></span>  
 <span data-ttu-id="8b967-118">Esta seção aborda os tipos usados no [provedor exemplo](http://go.microsoft.com/fwlink/?LinkId=180616) que você use para criar uma instrução SQL.</span><span class="sxs-lookup"><span data-stu-id="8b967-118">This section discusses the types used in the [Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) that you use to build a SQL statement.</span></span>  
  
### <a name="isqlfragment"></a><span data-ttu-id="8b967-119">ISqlFragment</span><span class="sxs-lookup"><span data-stu-id="8b967-119">ISqlFragment</span></span>  
 <span data-ttu-id="8b967-120">Esta seção aborda as classes que implementam a interface de ISqlFragment, que serve duas finalidades:</span><span class="sxs-lookup"><span data-stu-id="8b967-120">This section covers the classes that implement the ISqlFragment interface, which serves two purposes:</span></span>  
  
-   <span data-ttu-id="8b967-121">Um tipo de retorno comum para todos os métodos do visitante.</span><span class="sxs-lookup"><span data-stu-id="8b967-121">A common return type for all the visitor methods.</span></span>  
  
-   <span data-ttu-id="8b967-122">Fornece um método para gravar a cadeia de caracteres final SQL.</span><span class="sxs-lookup"><span data-stu-id="8b967-122">Gives a method to write the final SQL string.</span></span>  
  
```  
internal interface ISqlFragment {  
   void WriteSql(SqlWriter writer, SqlGenerator sqlGenerator);  
}  
```  
  
#### <a name="sqlbuilder"></a><span data-ttu-id="8b967-123">SqlBuilder</span><span class="sxs-lookup"><span data-stu-id="8b967-123">SqlBuilder</span></span>  
 <span data-ttu-id="8b967-124">SqlBuilder é um dispositivo de coletar para a cadeia de caracteres final SQL, semelhante a um StringBuilder.</span><span class="sxs-lookup"><span data-stu-id="8b967-124">SqlBuilder is a gathering device for the final SQL string, similar to StringBuilder.</span></span> <span data-ttu-id="8b967-125">Consiste em cadeias de caracteres que compõem o SQL final, juntamente com ISqlFragments que pode ser convertido em cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8b967-125">It consists of the strings that make up the final SQL, along with ISqlFragments that can be converted into strings.</span></span>  
  
```  
internal sealed class SqlBuilder : ISqlFragment {  
   public void Append(object s)  
   public void AppendLine()  
   public bool IsEmpty  
}  
```  
  
#### <a name="sqlselectstatement"></a><span data-ttu-id="8b967-126">SqlSelectStatement</span><span class="sxs-lookup"><span data-stu-id="8b967-126">SqlSelectStatement</span></span>  
 <span data-ttu-id="8b967-127">SqlSelectStatement representa uma instrução SQL SELECT canônica da forma "SELECT...</span><span class="sxs-lookup"><span data-stu-id="8b967-127">SqlSelectStatement represents a canonical SQL SELECT statement of the shape "SELECT …</span></span> <span data-ttu-id="8b967-128">DE..</span><span class="sxs-lookup"><span data-stu-id="8b967-128">FROM  ..</span></span> <span data-ttu-id="8b967-129">ONDE...</span><span class="sxs-lookup"><span data-stu-id="8b967-129">WHERE …</span></span> <span data-ttu-id="8b967-130">AGRUPE POR...</span><span class="sxs-lookup"><span data-stu-id="8b967-130">GROUP BY …</span></span> <span data-ttu-id="8b967-131">ORDENE POR".</span><span class="sxs-lookup"><span data-stu-id="8b967-131">ORDER BY".</span></span>  
  
 <span data-ttu-id="8b967-132">Cada uma das cláusulas SQL é representada por um StringBuilder.</span><span class="sxs-lookup"><span data-stu-id="8b967-132">Each of the SQL clauses is represented by a StringBuilder.</span></span> <span data-ttu-id="8b967-133">Além disso, controla se distinto foi especificado e se a instrução é o mais alto.</span><span class="sxs-lookup"><span data-stu-id="8b967-133">In addition, it tracks whether Distinct has been specified and whether the statement is topmost.</span></span> <span data-ttu-id="8b967-134">Se a declaração não é mais alto, a cláusula ORDER BY for omitido a menos que a declaração também tem uma cláusula TOP.</span><span class="sxs-lookup"><span data-stu-id="8b967-134">If the statement is not topmost, the ORDER BY clause is omitted unless the statement also has a TOP clause.</span></span>  
  
 <span data-ttu-id="8b967-135">FromExtents contém a lista de entradas para a instrução SELECT.</span><span class="sxs-lookup"><span data-stu-id="8b967-135">FromExtents contains the list of inputs for the SELECT statement.</span></span> <span data-ttu-id="8b967-136">Há geralmente apenas um elemento nesse.</span><span class="sxs-lookup"><span data-stu-id="8b967-136">There is usually just one element in this.</span></span> <span data-ttu-id="8b967-137">As instruções SELECT para ingressar temporariamente podem ter mais de um elemento.</span><span class="sxs-lookup"><span data-stu-id="8b967-137">SELECT statements for joins may temporarily have more than one element.</span></span>  
  
 <span data-ttu-id="8b967-138">Se a declaração SELECT é criada por um nó do join, SqlSelectStatement mantém uma lista de todas as extensões que foram aplainadas no join em AllJoinExtents.</span><span class="sxs-lookup"><span data-stu-id="8b967-138">If the SELECT statement is created by a Join node, SqlSelectStatement maintains a list of all the extents that have been flattened in the join in AllJoinExtents.</span></span> <span data-ttu-id="8b967-139">Representa OuterExtents referências externas de SqlSelectStatement e é usado para renomear alias de entrada.</span><span class="sxs-lookup"><span data-stu-id="8b967-139">OuterExtents represents outer references of the SqlSelectStatement and is used for input alias renaming.</span></span>  
  
```  
internal sealed class SqlSelectStatement : ISqlFragment {  
   internal bool IsDistinct { get, set };  
   internal bool IsTopMost  
  
   internal List<Symbol> AllJoinExtents { get, set };  
   internal List<Symbol> FromExtents { get};  
   internal Dictionary<Symbol, bool> OuterExtents { get};  
  
   internal TopClause Top { get, set };  
  
   internal SqlBuilder Select {get};  
   internal SqlBuilder From  
   internal SqlBuilder Where  
   internal SqlBuilder GroupBy  
   public SqlBuilder OrderBy  
}  
```  
  
#### <a name="topclause"></a><span data-ttu-id="8b967-140">TopClause</span><span class="sxs-lookup"><span data-stu-id="8b967-140">TopClause</span></span>  
 <span data-ttu-id="8b967-141">TopClause representa a expressão TOP em um SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="8b967-141">TopClause represents the TOP expression in a SqlSelectStatement.</span></span> <span data-ttu-id="8b967-142">A propriedade de TopCount indica quantas linhas SUPERIORES devem ser selecionadas.</span><span class="sxs-lookup"><span data-stu-id="8b967-142">The TopCount property indicates how many TOP rows should be selected.</span></span>  <span data-ttu-id="8b967-143">Quando WithTies é verdadeiro, a TopClause foi criado de um DbLimitExpession.</span><span class="sxs-lookup"><span data-stu-id="8b967-143">When WithTies is true, the TopClause was built from a DbLimitExpession.</span></span>  
  
```  
class TopClause : ISqlFragment {  
   internal bool WithTies {get}  
   internal ISqlFragment TopCount {get}  
   internal TopClause(ISqlFragment topCount, bool withTies)  
   internal TopClause(int topCount, bool withTies)  
}  
```  
  
### <a name="symbols"></a><span data-ttu-id="8b967-144">Símbolos</span><span class="sxs-lookup"><span data-stu-id="8b967-144">Symbols</span></span>  
 <span data-ttu-id="8b967-145">As classes Símbolo- relacionadas e a tabela de símbolo executam alias de entrada que renomiar, join para alias que aplainam, e a renomear alias de coluna.</span><span class="sxs-lookup"><span data-stu-id="8b967-145">The Symbol-related classes and the symbol table perform input alias renaming, join alias flattening, and column alias renaming.</span></span>  
  
 <span data-ttu-id="8b967-146">A classe do símbolo representa uma extensão, uma instrução SELECT aninhada, ou coluna.</span><span class="sxs-lookup"><span data-stu-id="8b967-146">The Symbol class represents an extent, a nested SELECT statement, or a column.</span></span> <span data-ttu-id="8b967-147">É usada em vez de um alias reais para permitir renomear depois que foi usada e também apresenta informações adicionais para o produto que representa (como o tipo).</span><span class="sxs-lookup"><span data-stu-id="8b967-147">It is used instead of an actual alias to allow for renaming after it has been used and it also carries additional information for the artifact it represents (like the type).</span></span>  
  
```  
class Symbol : ISqlFragment {  
   internal Dictionary<string, Symbol> Columns {get}  
   internal bool NeedsRenaming {get, set}  
   internal bool IsUnnest {get, set}   //not used  
  
   public string Name{get}  
   public string NewName {get,set}  
   internal TypeUsage Type {get, set}  
  
   public Symbol(string name, TypeUsage type)  
}  
```  
  
 <span data-ttu-id="8b967-148">O nome do alias originais para a extensão representada, a declaração SELECT aninhada, ou coluna.</span><span class="sxs-lookup"><span data-stu-id="8b967-148">Name stores the original alias for the represented extent, nested SELECT statement, or a column.</span></span>  
  
 <span data-ttu-id="8b967-149">NewName armazena alias que serão usadas na instrução SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="8b967-149">NewName stores the alias that will be used in the SQL SELECT statement.</span></span> <span data-ttu-id="8b967-150">É definida originalmente para nomear, e renomeada somente se necessário para gerar a consulta final da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8b967-150">It is originally set to Name, and only renamed if needed when generating the final string query.</span></span>  
  
 <span data-ttu-id="8b967-151">O tipo só é útil para os símbolos que representam extensões e instruções SELECT aninhadas.</span><span class="sxs-lookup"><span data-stu-id="8b967-151">Type is only useful for symbols representing extents and nested SELECT statements.</span></span>  
  
#### <a name="symbolpair"></a><span data-ttu-id="8b967-152">SymbolPair</span><span class="sxs-lookup"><span data-stu-id="8b967-152">SymbolPair</span></span>  
 <span data-ttu-id="8b967-153">Ajuste de registro de endereços da classe de SymbolPair.</span><span class="sxs-lookup"><span data-stu-id="8b967-153">The SymbolPair class addresses record flattening.</span></span>  
  
 <span data-ttu-id="8b967-154">Considere uma expressão Da propriedade (v, j3.j2.j1.a.x “”) onde v é um VarRef, j1, j2, j3 são join, a é uma extensão, e x é colunas.</span><span class="sxs-lookup"><span data-stu-id="8b967-154">Consider a property expression D(v, "j3.j2.j1.a.x") where v is a VarRef, j1, j2, j3 are joins, a is an extent, and x is a columns.</span></span>  
  
 <span data-ttu-id="8b967-155">Isso tem que ser convertido eventualmente em {} j. {} x.</span><span class="sxs-lookup"><span data-stu-id="8b967-155">This has to be translated eventually into {j'}.{x'}.</span></span> <span data-ttu-id="8b967-156">O campo de origem representa o SqlStatement mais externo, representando uma expressão de associação (digamos j2); este é sempre um símbolo do join.</span><span class="sxs-lookup"><span data-stu-id="8b967-156">The source field represents the outermost SqlStatement, representing a join expression (say j2); this is always a Join symbol.</span></span> <span data-ttu-id="8b967-157">Os movimentos do campo de coluna de um join para o símbolo a seguir até que parar em um símbolo de não join.</span><span class="sxs-lookup"><span data-stu-id="8b967-157">The column field moves from one join symbol to the next until it stops at a non-join symbol.</span></span> <span data-ttu-id="8b967-158">Isso é retornado para visitar um DbPropertyExpression mas nunca é adicionado a um SqlBuilder.</span><span class="sxs-lookup"><span data-stu-id="8b967-158">This is returned when visiting a DbPropertyExpression but is never added to a SqlBuilder.</span></span>  
  
```  
class SymbolPair : ISqlFragment {  
   public Symbol Source;  
   public Symbol Column;  
   public SymbolPair(Symbol source, Symbol column)  
}  
```  
  
#### <a name="joinsymbol"></a><span data-ttu-id="8b967-159">JoinSymbol</span><span class="sxs-lookup"><span data-stu-id="8b967-159">JoinSymbol</span></span>  
 <span data-ttu-id="8b967-160">Um símbolo de associação é um símbolo que representa uma instrução SELECT aninhada com uma união ou uma entrada de associação.</span><span class="sxs-lookup"><span data-stu-id="8b967-160">A Join symbol is a Symbol that represents a nested SELECT statement with a join or a join input.</span></span>  
  
```  
internal sealed class JoinSymbol : Symbol {  
   internal List<Symbol> ColumnList {get, set}  
   internal List<Symbol> ExtentList {get}  
   internal List<Symbol> FlattenedExtentList {get, set}  
   internal Dictionary<string, Symbol> NameToExtent {get}  
   internal bool IsNestedJoin {get, set}  
  
   public JoinSymbol(string name, TypeUsage type, List<Symbol> extents)  
}  
```  
  
 <span data-ttu-id="8b967-161">ColumnList representa a lista de colunas na cláusula SELECT se esse símbolo representa uma instrução SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="8b967-161">ColumnList represents the list of columns in the SELECT clause if this symbol represents a SQL SELECT statement.</span></span> <span data-ttu-id="8b967-162">ExtentList é a lista de extensões na cláusula SELECT.</span><span class="sxs-lookup"><span data-stu-id="8b967-162">ExtentList is the list of extents in the SELECT clause.</span></span> <span data-ttu-id="8b967-163">Se a associação possui várias extensões aplainadas a de nível superior, FlattenedExtentList controla as extensões para garantir que o alias de extensão são renomeados corretamente.</span><span class="sxs-lookup"><span data-stu-id="8b967-163">If the join has multiple extents flattened at the top level, FlattenedExtentList tracks the extents to ensure that extent aliases are renamed correctly.</span></span>  
  
 <span data-ttu-id="8b967-164">NameToExtent tem todas as extensões em ExtentList como um dicionário.</span><span class="sxs-lookup"><span data-stu-id="8b967-164">NameToExtent has all the extents in ExtentList as a dictionary.</span></span> <span data-ttu-id="8b967-165">IsNestedJoin é usado para determinar se um JoinSymbol é um comum se associa ao símbolo ou um que têm um SqlSelectStatement correspondente.</span><span class="sxs-lookup"><span data-stu-id="8b967-165">IsNestedJoin is used to determine whether a JoinSymbol is an ordinary join symbol or one that has a corresponding SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="8b967-166">Todas as listas são definidas exatamente uma vez e usadas para pesquisas ou enumeração.</span><span class="sxs-lookup"><span data-stu-id="8b967-166">All the lists are set exactly once and then used for lookups or enumeration.</span></span>  
  
#### <a name="symboltable"></a><span data-ttu-id="8b967-167">SymbolTable</span><span class="sxs-lookup"><span data-stu-id="8b967-167">SymbolTable</span></span>  
 <span data-ttu-id="8b967-168">SymbolTable é usado para resolver nomes de variável aos símbolos.</span><span class="sxs-lookup"><span data-stu-id="8b967-168">SymbolTable is used to resolve variable names to Symbols.</span></span> <span data-ttu-id="8b967-169">SymbolTable é implementado como uma pilha com uma nova entrada para cada escopo.</span><span class="sxs-lookup"><span data-stu-id="8b967-169">SymbolTable is implemented as a stack with a new entry for each scope.</span></span> <span data-ttu-id="8b967-170">As pesquisas pesquisam a parte superior da pilha para a parte inferior até que uma entrada seja encontrada.</span><span class="sxs-lookup"><span data-stu-id="8b967-170">Lookups search from the top of the stack to the bottom until an entry is found.</span></span>  
  
```  
internal sealed class SymbolTable {  
   internal void EnterScope()  
   internal void ExitScope()  
   internal void Add(string name, Symbol value)  
   internal Symbol Lookup(string name)  
}  
```  
  
 <span data-ttu-id="8b967-171">Há apenas um SymbolTable por uma instância do módulo de geração do SQL.</span><span class="sxs-lookup"><span data-stu-id="8b967-171">There is only one SymbolTable per one instance of the Sql Generation module.</span></span> <span data-ttu-id="8b967-172">Os escopos são inseridos e saídos para cada nó relacional.</span><span class="sxs-lookup"><span data-stu-id="8b967-172">Scopes are entered and exited for each relational node.</span></span> <span data-ttu-id="8b967-173">Todos os símbolos em um escopos anteriores são visíveis para um escopos posteriores a menos que oculto por outros símbolos com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="8b967-173">All symbols in earlier scopes are visible to later scopes unless hidden by other symbols with the same name.</span></span>  
  
### <a name="global-state-for-the-visitor"></a><span data-ttu-id="8b967-174">Estado global para o visitante</span><span class="sxs-lookup"><span data-stu-id="8b967-174">Global State for the Visitor</span></span>  
 <span data-ttu-id="8b967-175">Para ajudar em renomear alias e colunas, manter uma lista de todos os nomes de coluna (AllColumnNames) e do alias de extensão (AllExtentNames) que foram usados na primeira passagem sobre a árvore de consulta.</span><span class="sxs-lookup"><span data-stu-id="8b967-175">To assist in renaming of aliases and columns, maintain a list of all the column names (AllColumnNames) and extent aliases (AllExtentNames) that have been used in the first pass over the query tree.</span></span>  <span data-ttu-id="8b967-176">A tabela de símbolo resolver nomes de variável aos símbolos.</span><span class="sxs-lookup"><span data-stu-id="8b967-176">The symbol table resolves variable names to Symbols.</span></span> <span data-ttu-id="8b967-177">IsVarRefSingle é usado somente para efeitos de verificação, ele não é estritamente necessária.</span><span class="sxs-lookup"><span data-stu-id="8b967-177">IsVarRefSingle is only used for verification purposes, it is not strictly necessary.</span></span>  
  
 <span data-ttu-id="8b967-178">As duas pilhas usadas por meio de CurrentSelectStatement e de IsParentAJoin são usadas para passar parâmetros “” pai nós filho, desde que o padrão de visitante não permite que nós passem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="8b967-178">The two stacks used via CurrentSelectStatement and IsParentAJoin are used to pass "parameters" from parent to child nodes, since the visitor pattern does not allow us to pass parameters.</span></span>  
  
```  
internal Dictionary<string, int> AllExtentNames {get}  
internal Dictionary<string, int> AllColumnNames {get}  
SymbolTable symbolTable = new SymbolTable();  
bool isVarRefSingle = false;  
  
Stack<SqlSelectStatement> selectStatementStack;  
private SqlSelectStatement CurrentSelectStatement{get}  
  
Stack<bool> isParentAJoinStack;  
private bool IsParentAJoin{get}  
```  
  
## <a name="common-scenarios"></a><span data-ttu-id="8b967-179">Cenários comuns</span><span class="sxs-lookup"><span data-stu-id="8b967-179">Common Scenarios</span></span>  
 <span data-ttu-id="8b967-180">Esta seção descreve cenários comuns do provedor.</span><span class="sxs-lookup"><span data-stu-id="8b967-180">This section discusses common provider scenarios.</span></span>  
  
### <a name="grouping-expression-nodes-into-sql-statements"></a><span data-ttu-id="8b967-181">Nós de expressão de agrupamento em instruções SQL</span><span class="sxs-lookup"><span data-stu-id="8b967-181">Grouping Expression Nodes into SQL Statements</span></span>  
 <span data-ttu-id="8b967-182">Um SqlSelectStatement é criado quando o primeiro nó relacional é encontrado (normalmente uma extensão de DbScanExpression) para visitar a árvore a partir de baixo.</span><span class="sxs-lookup"><span data-stu-id="8b967-182">A SqlSelectStatement is created when the first relational node is encountered (typically a DbScanExpression extent) when visiting the tree from the bottom up.</span></span> <span data-ttu-id="8b967-183">Para gerar uma instrução SQL SELECT com poucas consultas aninhadas tão possíveis, agregar o tanto como seus nós pai como possível nesse SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="8b967-183">To produce a SQL SELECT statement with as few nested queries as possible, aggregate as many of its parent nodes as possible in that SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="8b967-184">A decisão de se um nó relacional () dado pode ser adicionado ao SqlSelectStatement atual (aquele retornado para o visitar a entrada) ou se uma nova declaração precisa ser iniciada é calculado pelo método IsCompatible e depende do que já estiver no SqlSelectStatement, que depende de nós que estavam abaixo do nó determinado.</span><span class="sxs-lookup"><span data-stu-id="8b967-184">The decision of whether a given (relational) node can be added to the current SqlSelectStatement (the one returned when visiting the input) or if a new statement needs to be started is computed by the method IsCompatible and depends on what is already in the SqlSelectStatement, which depends on what nodes were below the given node.</span></span>  
  
 <span data-ttu-id="8b967-185">Normalmente, se as cláusulas da instrução SQL são avaliadas após as cláusulas onde os nós que estão sendo considerados mesclando não estiverem vazias, o nó não pode ser adicionado à instrução atual.</span><span class="sxs-lookup"><span data-stu-id="8b967-185">Typically, if SQL statement clauses are evaluated after clauses where the nodes being considered for merging are not empty, the node cannot be added to the current statement.</span></span> <span data-ttu-id="8b967-186">Por exemplo, se o nó seguir é um filtro, o nó pode ser inserido em SqlSelectStatement atual somente se o seguinte é verdadeira:</span><span class="sxs-lookup"><span data-stu-id="8b967-186">For example, if the next node is a Filter, that node can be incorporated into the current SqlSelectStatement only if the following is true:</span></span>  
  
-   <span data-ttu-id="8b967-187">A lista SELECT está vazia.</span><span class="sxs-lookup"><span data-stu-id="8b967-187">The SELECT list is empty.</span></span> <span data-ttu-id="8b967-188">Se a lista SELECT é não vazio, a lista select foi gerada por um nó que precede o filtro e o predicado pode consultar as colunas geradas por essa lista SELECT.</span><span class="sxs-lookup"><span data-stu-id="8b967-188">If the SELECT list is not empty, the select list was produced by a node preceding the filter and the predicate may refer to columns produced by that SELECT list.</span></span>  
  
-   <span data-ttu-id="8b967-189">O GROUPBY está vazia.</span><span class="sxs-lookup"><span data-stu-id="8b967-189">The GROUPBY is empty.</span></span> <span data-ttu-id="8b967-190">Se o GROUPBY é não vazio, adicione o filtro significaria filtro antes de agrupamento, que não está correto.</span><span class="sxs-lookup"><span data-stu-id="8b967-190">If the GROUPBY is not empty, adding the filter would mean filtering before grouping, which is not correct.</span></span>  
  
-   <span data-ttu-id="8b967-191">A cláusula TOP está vazia.</span><span class="sxs-lookup"><span data-stu-id="8b967-191">The TOP clause is empty.</span></span> <span data-ttu-id="8b967-192">Se a cláusula TOP é não vazio, adicione o filtro significaria filtro antes de fazer a TOP, que não está correto.</span><span class="sxs-lookup"><span data-stu-id="8b967-192">If the TOP clause is not empty, adding the filter would mean filtering before doing TOP, which is not correct.</span></span>  
  
 <span data-ttu-id="8b967-193">Isso não se aplica a nós não-relacionais como DbConstantExpression ou expressões aritméticas, porque esses são sempre incluídos como parte de um SqlSelectStatement existente.</span><span class="sxs-lookup"><span data-stu-id="8b967-193">This does not apply to non-relational nodes like DbConstantExpression or arithmetic expressions, because these are always included as part of an existing SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="8b967-194">Além disso, para localizar a raiz da árvore join (um nó do join que não tenha um pai do join), um novo SqlSelectStatement é iniciado.</span><span class="sxs-lookup"><span data-stu-id="8b967-194">Also, when encountering the root of join tree (a join node that does not have a join parent), a new SqlSelectStatement is started.</span></span> <span data-ttu-id="8b967-195">Todas as suas espinha esquerda se associa ao filho é aggregate nesse SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="8b967-195">All of its left spine join children are aggregated into that SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="8b967-196">Sempre que um novo SqlSelectStatement é iniciado, e atual é adicionado à entrada, o SqlSelectStatement atual precise ser concluído adicionando colunas de projeção (uma cláusula SELECT) se não existir uma.</span><span class="sxs-lookup"><span data-stu-id="8b967-196">Whenever a new SqlSelectStatement is started, and the current one is added to the input, the current SqlSelectStatement may need to be completed by adding projection columns (a SELECT clause) if one does not exist.</span></span> <span data-ttu-id="8b967-197">Isso é feito com o método AddDefaultColumns, que tem o FromExtents de SqlSelectStatement e adiciona todas as colunas que a lista de extensões representadas por FromExtents traz no escopo à lista de colunas projetadas.</span><span class="sxs-lookup"><span data-stu-id="8b967-197">This is done with the method AddDefaultColumns, which looks at the FromExtents of the SqlSelectStatement and adds all the columns that the list of extents represented by FromExtents brings in scope to the list of projected columns.</span></span> <span data-ttu-id="8b967-198">Isso é feito, porque nesse ponto, é conhecido que as colunas são referenciadas por outros nós.</span><span class="sxs-lookup"><span data-stu-id="8b967-198">This is done, because at that point, it is unknown which columns are referenced by the other nodes.</span></span> <span data-ttu-id="8b967-199">Isso pode ser otimizada para projetar somente as colunas que podem ser usadas posteriormente.</span><span class="sxs-lookup"><span data-stu-id="8b967-199">This can be optimized to only project the columns that can later be used.</span></span>  
  
### <a name="join-flattening"></a><span data-ttu-id="8b967-200">Adição a ajuste</span><span class="sxs-lookup"><span data-stu-id="8b967-200">Join Flattening</span></span>  
 <span data-ttu-id="8b967-201">Ajuda da propriedade de IsParentAJoin determinar se um determinado joins pode ser aplainado.</span><span class="sxs-lookup"><span data-stu-id="8b967-201">The IsParentAJoin property helps determine whether a given join can be flattened.</span></span> <span data-ttu-id="8b967-202">Em particular, IsParentAJoin retorna `true` somente para o filho esquerdo de uma união e para cada DbScanExpression que é uma entrada imediata a uma união, nesse caso o nó filho reutiliza o mesmo SqlSelectStatement que o pai usaria posteriormente.</span><span class="sxs-lookup"><span data-stu-id="8b967-202">In particular, IsParentAJoin returns `true` only for the left child of a join and for each DbScanExpression that is an immediate input to a join, in which case that child node reuses the same SqlSelectStatement that the parent would later use.</span></span> <span data-ttu-id="8b967-203">Para obter mais informações, consulte “join a expressões”.</span><span class="sxs-lookup"><span data-stu-id="8b967-203">For more information, see "Join Expressions".</span></span>  
  
### <a name="input-alias-redirecting"></a><span data-ttu-id="8b967-204">Entre o redirecionamento alias</span><span class="sxs-lookup"><span data-stu-id="8b967-204">Input Alias Redirecting</span></span>  
 <span data-ttu-id="8b967-205">Alias de entrada que redirecionem são realizadas com a tabela de símbolo.</span><span class="sxs-lookup"><span data-stu-id="8b967-205">Input alias redirecting is accomplished with the symbol table.</span></span>  
  
 <span data-ttu-id="8b967-206">Para explicar redirecionando o alias de entrada, consulte o primeiro exemplo [gerando SQL das árvores de comando - práticas recomendadas](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="8b967-206">To explain input alias redirecting, refer to the first example in [Generating SQL from Command Trees - Best Practices](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md).</span></span>  <span data-ttu-id="8b967-207">Existem “a” não precisava ser redirecionado para “b” na projeção.</span><span class="sxs-lookup"><span data-stu-id="8b967-207">There "a" needed to be redirected to "b" in the projection.</span></span>  
  
 <span data-ttu-id="8b967-208">Quando um objeto de SqlSelectStatement é criado, a extensão é que a entrada ao nó é colocada na propriedade de SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="8b967-208">When a SqlSelectStatement object is created, the extent that is the input to the node is put in the From property of the SqlSelectStatement.</span></span> <span data-ttu-id="8b967-209">Um símbolo (<symbol_b>) é criado com base no nome de associação de entrada (“b”) para representar a extensão e “COMO” + <symbol_b> é acrescentado à cláusula.</span><span class="sxs-lookup"><span data-stu-id="8b967-209">A Symbol (<symbol_b>) is created based on the input binding name ("b") to represent that extent and "AS  " +  <symbol_b> is appended to the From Clause.</span></span>  <span data-ttu-id="8b967-210">O símbolo também é adicionado à propriedade de FromExtents.</span><span class="sxs-lookup"><span data-stu-id="8b967-210">The symbol is also added to the FromExtents property.</span></span>  
  
 <span data-ttu-id="8b967-211">O símbolo também é adicionado à tabela de símbolo para vincular o nome de associação de entrada (“b”, <symbol_b>).</span><span class="sxs-lookup"><span data-stu-id="8b967-211">The symbol is also added to the symbol table to link the input binding name to it ("b", <symbol_b>).</span></span>  
  
 <span data-ttu-id="8b967-212">Se reutilização subsequentes de um nó que SqlSelectStatement, ele adiciona uma entrada à tabela de símbolo para vincular o nome de associação de entrada ao símbolo.</span><span class="sxs-lookup"><span data-stu-id="8b967-212">If a subsequent node reuses that SqlSelectStatement, it adds an entry to the symbol table to link its input binding name to that symbol.</span></span> <span data-ttu-id="8b967-213">Em nosso exemplo, DbProjectExpression com o nome da associação de entrada de "a" seria reutilizar o SqlSelectStatement e adicionar ("a", \< symbol_b >) na tabela.</span><span class="sxs-lookup"><span data-stu-id="8b967-213">In our example, the DbProjectExpression with the input binding name of "a" would reuse the SqlSelectStatement and add ("a", \< symbol_b>) to the table.</span></span>  
  
 <span data-ttu-id="8b967-214">Quando as expressões no nome de associação de entrada do nó que estiver reutilizando o SqlSelectStatement, a referência é resolvida usando a tabela de símbolo redirecionado para o símbolo correto.</span><span class="sxs-lookup"><span data-stu-id="8b967-214">When expressions reference the input binding name of the node that is reusing the SqlSelectStatement, that reference is resolved using the symbol table to the correct redirected symbol.</span></span> <span data-ttu-id="8b967-215">Quando “a” de “a.x” é resolvido para visitar o DbVariableReferenceExpression que representa “a” resolvidos para o symbol_b <do símbolo.></span><span class="sxs-lookup"><span data-stu-id="8b967-215">When "a" from "a.x" is resolved while visiting the DbVariableReferenceExpression representing "a" it will resolve to the Symbol <symbol_b>.</span></span>  
  
### <a name="join-alias-flattening"></a><span data-ttu-id="8b967-216">Adição a ajuste alias</span><span class="sxs-lookup"><span data-stu-id="8b967-216">Join Alias Flattening</span></span>  
 <span data-ttu-id="8b967-217">Adição a ajuste alias é obtido quando visitar um DbPropertyExpression como descrito na seção intitulou DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="8b967-217">Join alias flattening is achieved when visiting a DbPropertyExpression as described in the section titled DbPropertyExpression.</span></span>  
  
### <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="8b967-218">Renomear alias o nome da coluna e de extensão</span><span class="sxs-lookup"><span data-stu-id="8b967-218">Column Name and Extent Alias Renaming</span></span>  
 <span data-ttu-id="8b967-219">A entrada de renomeação alias o nome da coluna e de extensão é abordada usando os símbolos que obtêm somente substituído com alias na segunda etapa de geração descrito na seção denominada segundo fase de geração SQL: Gerando o comando de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8b967-219">The issue of column name and extent alias renaming is addressed by using symbols that only get substituted with aliases in the second phase of the generation described in the section titled Second Phase of SQL Generation: Generating the String Command.</span></span>  
  
## <a name="first-phase-of-the-sql-generation-visiting-the-expression-tree"></a><span data-ttu-id="8b967-220">Primeiro estágio de geração SQL: Visitar a árvore de expressão</span><span class="sxs-lookup"><span data-stu-id="8b967-220">First Phase of the SQL Generation: Visiting the Expression Tree</span></span>  
 <span data-ttu-id="8b967-221">Esta seção descreve a primeira etapa de geração SQL, quando a expressão que representa a consulta é visitada e uma estrutura intermediária é gerada, um SqlSelectStatement ou um SqlBuilder.</span><span class="sxs-lookup"><span data-stu-id="8b967-221">This section describes the first phase of SQL generation, when the expression representing the query is visited and an intermediate structure is produced, either a SqlSelectStatement or a SqlBuilder.</span></span>  
  
 <span data-ttu-id="8b967-222">Esta seção descreve as noções básicas de visitar categorias diferentes de nó da expressão, e os detalhes de visitar a expressão específica tipo.</span><span class="sxs-lookup"><span data-stu-id="8b967-222">This section describes the principles of visiting different expression node categories, and details of visiting specific expression types.</span></span>  
  
### <a name="relational-non-join-nodes"></a><span data-ttu-id="8b967-223">(não se junte nós relacionais)</span><span class="sxs-lookup"><span data-stu-id="8b967-223">Relational (Non-Join) Nodes</span></span>  
 <span data-ttu-id="8b967-224">O seguinte suporte de expressão não associa a nós:</span><span class="sxs-lookup"><span data-stu-id="8b967-224">The following expression types support non-join nodes:</span></span>  
  
-   <span data-ttu-id="8b967-225">DbDistinctExpression</span><span class="sxs-lookup"><span data-stu-id="8b967-225">DbDistinctExpression</span></span>  
  
-   <span data-ttu-id="8b967-226">DbFilterExpression</span><span class="sxs-lookup"><span data-stu-id="8b967-226">DbFilterExpression</span></span>  
  
-   <span data-ttu-id="8b967-227">DbGroupByExpression</span><span class="sxs-lookup"><span data-stu-id="8b967-227">DbGroupByExpression</span></span>  
  
-   <span data-ttu-id="8b967-228">DbLimitExpession</span><span class="sxs-lookup"><span data-stu-id="8b967-228">DbLimitExpession</span></span>  
  
-   <span data-ttu-id="8b967-229">DbProjectExpression</span><span class="sxs-lookup"><span data-stu-id="8b967-229">DbProjectExpression</span></span>  
  
-   <span data-ttu-id="8b967-230">DbSkipExpression</span><span class="sxs-lookup"><span data-stu-id="8b967-230">DbSkipExpression</span></span>  
  
-   <span data-ttu-id="8b967-231">DbSortExpression</span><span class="sxs-lookup"><span data-stu-id="8b967-231">DbSortExpression</span></span>  
  
 <span data-ttu-id="8b967-232">Visitar esses nós segue o padrão a seguir:</span><span class="sxs-lookup"><span data-stu-id="8b967-232">Visiting these nodes follows the following pattern:</span></span>  
  
1.  <span data-ttu-id="8b967-233">Interativo entrada relacional e obter o SqlSelectStatement resultante.</span><span class="sxs-lookup"><span data-stu-id="8b967-233">Visit the relational input and get the resulting SqlSelectStatement.</span></span> <span data-ttu-id="8b967-234">A entrada a um nó relacional pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="8b967-234">The input to a relational node could be one of the following:</span></span>  
  
    -   <span data-ttu-id="8b967-235">Um nó relacional, incluindo uma extensão (um DbScanExpression, por exemplo).</span><span class="sxs-lookup"><span data-stu-id="8b967-235">A relational node, including an extent (a DbScanExpression, for example).</span></span> <span data-ttu-id="8b967-236">Visitar um nó retorna um SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="8b967-236">Visiting such a node returns a SqlSelectStatement.</span></span>  
  
    -   <span data-ttu-id="8b967-237">Uma expressão de operação relevante (UNION TODOS, por exemplo).</span><span class="sxs-lookup"><span data-stu-id="8b967-237">A set operation expression (UNION ALL, for example).</span></span> <span data-ttu-id="8b967-238">O resultado tem que ser empacotado entre colchetes e coloque na cláusula de um novo SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="8b967-238">The result has to be wrapped in brackets and put in the FROM clause of a new SqlSelectStatement.</span></span>  
  
2.  <span data-ttu-id="8b967-239">Verifique se o nó atual pode ser adicionado ao SqlSelectStatement gerado pela entrada.</span><span class="sxs-lookup"><span data-stu-id="8b967-239">Check whether the current node can be added to the SqlSelectStatement produced by the input.</span></span> <span data-ttu-id="8b967-240">A seção denominada agrupamento expressões em instruções SQL descreve esta.</span><span class="sxs-lookup"><span data-stu-id="8b967-240">The section titled Grouping Expressions into SQL Statements describes this.</span></span> <span data-ttu-id="8b967-241">Se não,</span><span class="sxs-lookup"><span data-stu-id="8b967-241">If not,</span></span>  
  
    -   <span data-ttu-id="8b967-242">Aparecer o objeto atual de SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="8b967-242">Pop the current SqlSelectStatement object.</span></span>  
  
    -   <span data-ttu-id="8b967-243">Crie um novo objeto de SqlSelectStatement e adicione o SqlSelectStatement aparecido como o novo objeto de SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="8b967-243">Create a new SqlSelectStatement object and add the popped SqlSelectStatement as the FROM of the new SqlSelectStatement object.</span></span>  
  
    -   <span data-ttu-id="8b967-244">Coloque o novo objeto sobre a pilha.</span><span class="sxs-lookup"><span data-stu-id="8b967-244">Put the new object on top of the stack.</span></span>  
  
3.  <span data-ttu-id="8b967-245">Redirecionando a expressão de entrada que associa o símbolo correto de entrada.</span><span class="sxs-lookup"><span data-stu-id="8b967-245">Redirect the input expression binding to the correct symbol from the input.</span></span> <span data-ttu-id="8b967-246">Essa informação é mantida no objeto de SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="8b967-246">This information is maintained in the SqlSelectStatement object.</span></span>  
  
4.  <span data-ttu-id="8b967-247">Adicione um novo escopo de SymbolTable.</span><span class="sxs-lookup"><span data-stu-id="8b967-247">Add a new SymbolTable scope.</span></span>  
  
5.  <span data-ttu-id="8b967-248">Interativo a parte das entrada de expressões (por exemplo, projeção e predicado).</span><span class="sxs-lookup"><span data-stu-id="8b967-248">Visit the non-input part of the expression (for example, Projection and Predicate).</span></span>  
  
6.  <span data-ttu-id="8b967-249">Aparecer todos os objetos adicionados às pilhas globais.</span><span class="sxs-lookup"><span data-stu-id="8b967-249">Pop all the objects added to the global stacks.</span></span>  
  
 <span data-ttu-id="8b967-250">DbSkipExpression para não ter um direto equivalente no SQL.</span><span class="sxs-lookup"><span data-stu-id="8b967-250">DbSkipExpression not have a direct equivalent in SQL.</span></span> <span data-ttu-id="8b967-251">Logicamente, é convertido em:</span><span class="sxs-lookup"><span data-stu-id="8b967-251">Logically, it is translated into:</span></span>  
  
```  
SELECT Y.x1, Y.x2, ..., Y.xn  
FROM (  
   SELECT X.x1, X.x2, ..., X.xn, row_number() OVER (ORDER BY sk1, sk2, ...) AS [row_number]   
   FROM input as X   
   ) as Y  
WHERE Y.[row_number] > count   
ORDER BY sk1, sk2, ...  
```  
  
### <a name="join-expressions"></a><span data-ttu-id="8b967-252">Adição às expressões</span><span class="sxs-lookup"><span data-stu-id="8b967-252">Join Expressions</span></span>  
 <span data-ttu-id="8b967-253">Os seguintes são considerados ingressar em expressões e são processados em uma maneira comum, pelo método de VisitJoinExpression:</span><span class="sxs-lookup"><span data-stu-id="8b967-253">The following are considered join expressions and they are processed in a common way, by the VisitJoinExpression method:</span></span>  
  
-   <span data-ttu-id="8b967-254">DbApplyExpression</span><span class="sxs-lookup"><span data-stu-id="8b967-254">DbApplyExpression</span></span>  
  
-   <span data-ttu-id="8b967-255">DbJoinExpression</span><span class="sxs-lookup"><span data-stu-id="8b967-255">DbJoinExpression</span></span>  
  
-   <span data-ttu-id="8b967-256">DbCrossJoinExpression</span><span class="sxs-lookup"><span data-stu-id="8b967-256">DbCrossJoinExpression</span></span>  
  
 <span data-ttu-id="8b967-257">A seguir estão as etapas de visita:</span><span class="sxs-lookup"><span data-stu-id="8b967-257">The following are the visit steps:</span></span>  
  
 <span data-ttu-id="8b967-258">Primeiro, antes de visitar filhos, IsParentAJoin é chamado para verificar se o nó do join é um filho de uma união ao longo de uma espinha esquerda.</span><span class="sxs-lookup"><span data-stu-id="8b967-258">First, before visiting the children, IsParentAJoin is invoked to check whether the join node is a child of a join along a left spine.</span></span> <span data-ttu-id="8b967-259">Se ele retornar false, um novo SqlSelectStatement é iniciado.</span><span class="sxs-lookup"><span data-stu-id="8b967-259">If it returns false, a new SqlSelectStatement is started.</span></span> <span data-ttu-id="8b967-260">Nesse sentido, join são visitados diferente do restante de nós, porque o pai (o nó do join) cria o SqlSelectStatement para que os filhos utilizarão possivelmente.</span><span class="sxs-lookup"><span data-stu-id="8b967-260">In that sense, joins are visited differently from the rest of the nodes, as the parent (the join node) creates the SqlSelectStatement for the children to possibly use.</span></span>  
  
 <span data-ttu-id="8b967-261">Segundo, processar entradas um de cada vez.</span><span class="sxs-lookup"><span data-stu-id="8b967-261">Second, process the inputs one at a time.</span></span> <span data-ttu-id="8b967-262">Para cada entrada:</span><span class="sxs-lookup"><span data-stu-id="8b967-262">For each input:</span></span>  
  
1.  <span data-ttu-id="8b967-263">Didático de entrada.</span><span class="sxs-lookup"><span data-stu-id="8b967-263">Visit the input.</span></span>  
  
2.  <span data-ttu-id="8b967-264">Enviar o processo visitar o resultado da entrada por ProcessJoinInputResult, que é responsável para manter a tabela de símbolo após visitado um filho de uma expressão de associação e possivelmente ter concluído o SqlSelectStatement gerado pelo filho.</span><span class="sxs-lookup"><span data-stu-id="8b967-264">Post process the result of visiting the input by invoking ProcessJoinInputResult, which is responsible for maintaining the symbol table after visiting a child of a join expression and possibly finishing the SqlSelectStatement produced by the child.</span></span> <span data-ttu-id="8b967-265">O resultado de filho pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="8b967-265">The child's result could be one of the following:</span></span>  
  
    -   <span data-ttu-id="8b967-266">Um SqlSelectStatement diferente de aquele que o pai será adicionado.</span><span class="sxs-lookup"><span data-stu-id="8b967-266">A SqlSelectStatement different from the one to which the parent will be added.</span></span> <span data-ttu-id="8b967-267">Em tais casos, talvez precisem ser concluído adicionando colunas padrão.</span><span class="sxs-lookup"><span data-stu-id="8b967-267">In such case, it may need to be completed by adding default columns.</span></span> <span data-ttu-id="8b967-268">Se a entrada foi uma associação, você precisa criar um novo join para o símbolo.</span><span class="sxs-lookup"><span data-stu-id="8b967-268">If the input was a Join, you need to create a new join symbol.</span></span> <span data-ttu-id="8b967-269">Caso contrário, crie um símbolo normal.</span><span class="sxs-lookup"><span data-stu-id="8b967-269">Otherwise, create a normal symbol.</span></span>  
  
    -   <span data-ttu-id="8b967-270">Uma extensão (um DbScanExpression, por exemplo), nesse caso é simplesmente adicionada à lista de entradas de SqlSelectStatement pai.</span><span class="sxs-lookup"><span data-stu-id="8b967-270">An extent (a DbScanExpression, for example), in which case it is simply added to the list of inputs of the parent’s SqlSelectStatement.</span></span>  
  
    -   <span data-ttu-id="8b967-271">Não um SqlSelectStatement, nesse caso é empacotado com colchetes.</span><span class="sxs-lookup"><span data-stu-id="8b967-271">Not a SqlSelectStatement, in which case it is wrapped with brackets.</span></span>  
  
    -   <span data-ttu-id="8b967-272">O mesmo SqlSelectStatement a que o pai é adicionado.</span><span class="sxs-lookup"><span data-stu-id="8b967-272">The same SqlSelectStatement to which the parent is added.</span></span> <span data-ttu-id="8b967-273">Em tais casos, os símbolos na lista de FromExtents precisam ser substituídos por um único novo JoinSymbol que representa todos os.</span><span class="sxs-lookup"><span data-stu-id="8b967-273">In such case, the symbols in the FromExtents list need to be replaced with a single new JoinSymbol representing them all.</span></span>  
  
    -   <span data-ttu-id="8b967-274">Para os primeiros três casos, AddFromSymbol é chamado para adicionar COMO a cláusula, e atualizar a tabela de símbolo.</span><span class="sxs-lookup"><span data-stu-id="8b967-274">For the first three cases, AddFromSymbol is called to add the AS clause, and update the symbol table.</span></span>  
  
 <span data-ttu-id="8b967-275">No lugar, a condição de adição (se houver) é visitada.</span><span class="sxs-lookup"><span data-stu-id="8b967-275">Third, the join condition (if any) is visited.</span></span>  
  
### <a name="set-operations"></a><span data-ttu-id="8b967-276">Operações de conjunto</span><span class="sxs-lookup"><span data-stu-id="8b967-276">Set Operations</span></span>  
 <span data-ttu-id="8b967-277">As operações de conjunto DbUnionAllExpression, DbExceptExpression, e DbIntersectExpression são processadas pelo método VisitSetOpExpression.</span><span class="sxs-lookup"><span data-stu-id="8b967-277">The set operations DbUnionAllExpression, DbExceptExpression, and DbIntersectExpression are processed by the method VisitSetOpExpression.</span></span> <span data-ttu-id="8b967-278">Cria um SqlBuilder de forma</span><span class="sxs-lookup"><span data-stu-id="8b967-278">It creates a SqlBuilder of the shape</span></span>  
  
```xml  
<leftSqlSelectStatement> <setOp> <rightSqlSelectStatement>  
```  
  
 <span data-ttu-id="8b967-279">Onde \<leftSqlSelectStatement > e \<rightSqlSelectStatement > são SqlSelectStatements obtido visitando cada uma das entradas, e \<setOp > é a operação correspondente (UNION ALL, por exemplo).</span><span class="sxs-lookup"><span data-stu-id="8b967-279">Where \<leftSqlSelectStatement> and \<rightSqlSelectStatement> are SqlSelectStatements obtained by visiting each of the inputs, and \<setOp> is the corresponding operation (UNION ALL for example).</span></span>  
  
### <a name="dbscanexpression"></a><span data-ttu-id="8b967-280">DbScanExpression</span><span class="sxs-lookup"><span data-stu-id="8b967-280">DbScanExpression</span></span>  
 <span data-ttu-id="8b967-281">Se visitado em um contexto do join (como uma entrada para uma associação que é um filho de outro esquerdo se junte), DbScanExpression retorna um SqlBuilder com o destino SQL para o destino correspondente, que é uma consulta de definição, a tabela, ou uma exibição.</span><span class="sxs-lookup"><span data-stu-id="8b967-281">If visited in a join context (as an input to a join that is a left child of another join), DbScanExpression returns a SqlBuilder with the target SQL for the corresponding target, which is either a defining query, table, or a view.</span></span> <span data-ttu-id="8b967-282">Se não, um novo SqlSelectStatement é criado com o conjunto de campo para corresponder ao destino correspondente.</span><span class="sxs-lookup"><span data-stu-id="8b967-282">Otherwise, a new SqlSelectStatement is created with the FROM field set to correspond to the corresponding target.</span></span>  
  
### <a name="dbvariablereferenceexpression"></a><span data-ttu-id="8b967-283">DbVariableReferenceExpression</span><span class="sxs-lookup"><span data-stu-id="8b967-283">DbVariableReferenceExpression</span></span>  
 <span data-ttu-id="8b967-284">A visitar de um DbVariableReferenceExpression retorna o símbolo que corresponde à expressão variável de referência com base na tabela de pesquisa símbolo.</span><span class="sxs-lookup"><span data-stu-id="8b967-284">The visit of a DbVariableReferenceExpression returns the Symbol corresponding to that variable reference expression based on a look up in the symbol table.</span></span>  
  
### <a name="dbpropertyexpression"></a><span data-ttu-id="8b967-285">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="8b967-285">DbPropertyExpression</span></span>  
 <span data-ttu-id="8b967-286">Adição a ajuste alias é identificado e processado para visitar um DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="8b967-286">Join alias flattening is identified and processed when visiting a DbPropertyExpression.</span></span>  
  
 <span data-ttu-id="8b967-287">A propriedade a instância é visitada primeiro e o resultado é um símbolo, um JoinSymbol, ou um SymbolPair.</span><span class="sxs-lookup"><span data-stu-id="8b967-287">The Instance property is first visited and the result is a Symbol, a JoinSymbol, or a SymbolPair.</span></span> <span data-ttu-id="8b967-288">É aqui como esses três ocorrências são tratados:</span><span class="sxs-lookup"><span data-stu-id="8b967-288">Here is how these three cases are handled:</span></span>  
  
-   <span data-ttu-id="8b967-289">Se um JoinSymbol é retornado, de sua propriedade de NameToExtent contém um símbolo para a propriedade necessário.</span><span class="sxs-lookup"><span data-stu-id="8b967-289">If a JoinSymbol is returned, than its NameToExtent property contains a symbol for the needed property.</span></span> <span data-ttu-id="8b967-290">Se o símbolo de associação verdadeira, aninhado representa um novo registro do símbolo é retornado com o símbolo do join para controlar o símbolo que seria usado como o alias de instância, e o símbolo que representa a propriedade real para resolver mais.</span><span class="sxs-lookup"><span data-stu-id="8b967-290">If the join symbol represents a nested join, a new Symbol pair is returned with the join symbol to track the symbol that would be used as the instance alias, and the symbol representing the actual property for further resolving.</span></span>  
  
-   <span data-ttu-id="8b967-291">Se um SymbolPair é retornado e parte da coluna é um símbolo de adição, um símbolo de associação é retornado novamente, mas a propriedade coluna é atualizada agora para apontar para a propriedade representada pela expressão atual da propriedade.</span><span class="sxs-lookup"><span data-stu-id="8b967-291">If a SymbolPair is returned and the Column part is a join symbol, a join symbol is again returned, but now the column property is updated to point to the property represented by the current property expression.</span></span> <span data-ttu-id="8b967-292">Se não um SqlBuilder é retornado com a fonte de SymbolPair como alias, e o símbolo para a propriedade atual como a coluna.</span><span class="sxs-lookup"><span data-stu-id="8b967-292">Otherwise a SqlBuilder is returned with the SymbolPair source as the alias, and the symbol for the current property as the column.</span></span>  
  
-   <span data-ttu-id="8b967-293">Se um símbolo é retornado, o método de visita retorna um método de SqlBuilder com essa instância como alias, e o nome da propriedade como o nome da coluna.</span><span class="sxs-lookup"><span data-stu-id="8b967-293">If a Symbol is returned, the Visit method returns a SqlBuilder method with that instance as the alias, and the property name as column name.</span></span>  
  
### <a name="dbnewinstanceexpression"></a><span data-ttu-id="8b967-294">DbNewInstanceExpression</span><span class="sxs-lookup"><span data-stu-id="8b967-294">DbNewInstanceExpression</span></span>  
 <span data-ttu-id="8b967-295">Quando usado como a propriedade de projeção de DbProjectExpression, DbNewInstanceExpression gerencia uma lista separada por vírgulas de argumentos para representar as colunas projetadas.</span><span class="sxs-lookup"><span data-stu-id="8b967-295">When used as the Projection property of DbProjectExpression, DbNewInstanceExpression produces a comma-separated list of the arguments to represent the projected columns.</span></span>  
  
 <span data-ttu-id="8b967-296">Quando DbNewInstanceExpression tem um tipo de retorno da coleção, e define uma nova coleção de expressões fornecidas como argumentos, os seguintes três ocorrências são tratados separada:</span><span class="sxs-lookup"><span data-stu-id="8b967-296">When DbNewInstanceExpression has a collection return type, and defines a new collection of the expressions provided as arguments, the following three cases are handled separately:</span></span>  
  
-   <span data-ttu-id="8b967-297">Se DbNewInstanceExpression tem DbElementExpression como o argumento único, ele é convertido como segue:</span><span class="sxs-lookup"><span data-stu-id="8b967-297">If DbNewInstanceExpression has DbElementExpression as the only argument, it is translated as follows:</span></span>  
  
    ```  
    NewInstance(Element(X)) =>  SELECT TOP 1 …FROM X  
    ```  
  
 <span data-ttu-id="8b967-298">Se DbNewInstanceExpression não tem nenhum argumento (representa uma tabela vazia), ele é convertido em DbNewInstanceExpression:</span><span class="sxs-lookup"><span data-stu-id="8b967-298">If DbNewInstanceExpression has no arguments (represents an empty table), DbNewInstanceExpression is translated into:</span></span>  
  
```  
SELECT CAST(NULL AS <primitiveType>) as X  
FROM (SELECT 1) AS Y WHERE 1=0  
```  
  
 <span data-ttu-id="8b967-299">Se não DbNewInstanceExpression compila UNION- qualquer escada dos argumentos:</span><span class="sxs-lookup"><span data-stu-id="8b967-299">Otherwise DbNewInstanceExpression builds a union-all ladder of the arguments:</span></span>  
  
```  
SELECT <visit-result-arg1> as X  
UNION ALL SELECT <visit-result-arg2> as X  
UNION ALL …  
UNION ALL SELECT <visit-result-argN> as X  
```  
  
### <a name="dbfunctionexpression"></a><span data-ttu-id="8b967-300">DbFunctionExpression</span><span class="sxs-lookup"><span data-stu-id="8b967-300">DbFunctionExpression</span></span>  
 <span data-ttu-id="8b967-301">Canônico e funções internas são processados da mesma maneira: se precisam tratamento especial (GUARNIÇÃO (cadeia de caracteres) a LTRIM (RTRIM (cadeia de caracteres), por exemplo), o manipulador adequado são chamados.</span><span class="sxs-lookup"><span data-stu-id="8b967-301">Canonical and built-in functions are processed the same way: if they need special handling (TRIM(string) to  LTRIM(RTRIM(string), for example), the appropriate handler is invoked.</span></span> <span data-ttu-id="8b967-302">Se não são traduzidas a Nomedafunção (arg1, arg2,…, argn).</span><span class="sxs-lookup"><span data-stu-id="8b967-302">Otherwise they are translated to FunctionName(arg1, arg2, ..., argn).</span></span>  
  
 <span data-ttu-id="8b967-303">Dicionários são usados para manter controle de quais papéis precisam tratamento especial e seus manipuladores apropriadas.</span><span class="sxs-lookup"><span data-stu-id="8b967-303">Dictionaries are used to keep track of which functions need special handling and their appropriate handlers.</span></span>  
  
 <span data-ttu-id="8b967-304">As funções definidas pelo usuário tanslated a NamespaceName.FunctionName (arg1, arg2,…, argn).</span><span class="sxs-lookup"><span data-stu-id="8b967-304">User-defined functions are tanslated to NamespaceName.FunctionName(arg1, arg2, ..., argn).</span></span>  
  
### <a name="dbelementexpression"></a><span data-ttu-id="8b967-305">DbElementExpression</span><span class="sxs-lookup"><span data-stu-id="8b967-305">DbElementExpression</span></span>  
 <span data-ttu-id="8b967-306">O método visita DbElementExpression que é chamado somente visitar um DbElementExpression quando usado para representar um subconsulta escalar.</span><span class="sxs-lookup"><span data-stu-id="8b967-306">The method that visits DbElementExpression is only invoked for visiting a DbElementExpression when used to represent a scalar subquery.</span></span> <span data-ttu-id="8b967-307">Portanto, DbElementExpression converte em um SqlSelectStatement completo e adiciona os colchetes redor deles.</span><span class="sxs-lookup"><span data-stu-id="8b967-307">Therefore, DbElementExpression translates into a complete SqlSelectStatement and adds brackets around it.</span></span>  
  
### <a name="dbquantifierexpression"></a><span data-ttu-id="8b967-308">DbQuantifierExpression</span><span class="sxs-lookup"><span data-stu-id="8b967-308">DbQuantifierExpression</span></span>  
 <span data-ttu-id="8b967-309">Dependendo do tipo da expressão (alguns ou todos), DbQuantifierExpression é convertido como:</span><span class="sxs-lookup"><span data-stu-id="8b967-309">Depending on the expression type (Any or All), DbQuantifierExpression is translated it as:</span></span>  
  
```  
Any(input, x) => Exists(Filter(input,x))  
All(input, x) => Not Exists(Filter(input, not(x))  
```  
  
### <a name="dbnotexpression"></a><span data-ttu-id="8b967-310">DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="8b967-310">DbNotExpression</span></span>  
 <span data-ttu-id="8b967-311">Em alguns casos é possível recolher a conversão de DbNotExpression com sua expressão de entrada.</span><span class="sxs-lookup"><span data-stu-id="8b967-311">In some cases it is possible to collapse the translation of DbNotExpression with its input expression.</span></span> <span data-ttu-id="8b967-312">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="8b967-312">For example:</span></span>  
  
```  
Not(IsNull(a)) =>  "a IS NOT NULL"  
Not(All(input, x) => Not (Not Exists(Filter(input, not(x))) => Exists(Filter(input, not(x))  
```  
  
 <span data-ttu-id="8b967-313">A razão que o segundo recolher é executado é porque as incapacidades foram introduzidas pelo provedor para converter DbQuantifierExpression de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="8b967-313">The reason the second collapse is performed is because inefficiencies were introduced by the provider when translating DbQuantifierExpression of type All.</span></span> <span data-ttu-id="8b967-314">Isso Entity Framework não pode ter feito a simplificação.</span><span class="sxs-lookup"><span data-stu-id="8b967-314">Thus the Entity Framework could not have done the simplification.</span></span>  
  
### <a name="dbisemptyexpression"></a><span data-ttu-id="8b967-315">DbIsEmptyExpression</span><span class="sxs-lookup"><span data-stu-id="8b967-315">DbIsEmptyExpression</span></span>  
 <span data-ttu-id="8b967-316">DbIsEmptyExpression é convertido como:</span><span class="sxs-lookup"><span data-stu-id="8b967-316">DbIsEmptyExpression is translated as:</span></span>  
  
```  
IsEmpty(inut) = Not Exists(input)  
```  
  
## <a name="second-phase-of-sql-generation-generating-the-string-command"></a><span data-ttu-id="8b967-317">Segundo fase de geração SQL: Gerando o comando de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8b967-317">Second Phase of SQL Generation: Generating the String Command</span></span>  
 <span data-ttu-id="8b967-318">Para gerar um comando SQL de cadeia de caracteres, o SqlSelectStatement gerencia alias reais dos símbolos, que tratam a introdução para renomear alias o nome da coluna e de extensão.</span><span class="sxs-lookup"><span data-stu-id="8b967-318">When generating a string SQL command, the SqlSelectStatement produces actual aliases for the symbols, which addresses the issue of column name and extent alias renaming.</span></span>  
  
 <span data-ttu-id="8b967-319">Renomear alias de extensão ocorre ao escrever o objeto de SqlSelectStatement em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8b967-319">Extent alias renaming occurs while writing the SqlSelectStatement object into a string.</span></span> <span data-ttu-id="8b967-320">Primeiro crie uma lista de todas as aliases usadas por extensões externos.</span><span class="sxs-lookup"><span data-stu-id="8b967-320">First create a list of all the aliases used by the outer extents.</span></span> <span data-ttu-id="8b967-321">Cada símbolo no FromExtents (ou em AllJoinExtents se é não-nulo), é renomeado se colidir com quaisquer das extensões externos.</span><span class="sxs-lookup"><span data-stu-id="8b967-321">Each symbol in the FromExtents (or AllJoinExtents if it is non-null), gets renamed if it collides with any of the outer extents.</span></span> <span data-ttu-id="8b967-322">Se renomear for necessário, não será em conflito com quaisquer das extensões coletadas em AllExtentNames.</span><span class="sxs-lookup"><span data-stu-id="8b967-322">If renaming is needed, it will not conflict with any of the extents collected in AllExtentNames.</span></span>  
  
 <span data-ttu-id="8b967-323">Renomear a coluna ocorre ao escrever um objeto do símbolo para uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8b967-323">Column renaming occurs while writing a Symbol object to a string.</span></span> <span data-ttu-id="8b967-324">AddDefaultColumns na primeira etapa determinar se um determinado símbolo da coluna tem que ser renomeado.</span><span class="sxs-lookup"><span data-stu-id="8b967-324">AddDefaultColumns in the first phase has determined if a certain column symbol has to be renamed.</span></span> <span data-ttu-id="8b967-325">Na segunda etapa somente renomear ocorre certificar-se de que o nome gerado não está em conflito com qualquer nome usado em AllColumnNames</span><span class="sxs-lookup"><span data-stu-id="8b967-325">In the second phase only the rename occurs making sure that the name produced does not conflict with any name used in AllColumnNames</span></span>  
  
 <span data-ttu-id="8b967-326">Para gerar nomes exclusivos para alias de extensão e para colunas, existing_name_n <>de uso onde n é o alias as menores que ainda não foram usadas.</span><span class="sxs-lookup"><span data-stu-id="8b967-326">To produce unique names both for extent aliases and for columns, use <existing_name>_n where n is the smallest alias that has not been used yet.</span></span> <span data-ttu-id="8b967-327">A lista global de todas as aliases aumenta a necessidade de se conectar renomear.</span><span class="sxs-lookup"><span data-stu-id="8b967-327">The global list of all aliases increases the need for cascading renames.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b967-328">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b967-328">See Also</span></span>  
 [<span data-ttu-id="8b967-329">Geração de SQL no provedor exemplo</span><span class="sxs-lookup"><span data-stu-id="8b967-329">SQL Generation in the Sample Provider</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
