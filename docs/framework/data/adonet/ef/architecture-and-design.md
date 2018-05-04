---
title: Arquitetura e design
ms.date: 03/30/2017
ms.assetid: bd738d39-00e2-4bab-b387-90aac1a014bd
ms.openlocfilehash: c2e8ff5f21a2941d75b21915552e6935a1423978
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="architecture-and-design"></a>Arquitetura e design
O módulo de geração de SQL no [provedor exemplo](http://go.microsoft.com/fwlink/?LinkId=180616) é implementado como um visitante na árvore de expressão que representa a árvore de comandos. A geração é feita em uma única passada sobre a árvore de expressão.  
  
 Os nós de árvore são processados a partir de baixo. Primeiro, uma estrutura intermediária é gerada: SqlSelectStatement ou SqlBuilder, ambos que implementam ISqlFragment. Em seguida, a instrução SQL de cadeia de caracteres é gerado dessa estrutura. Há dois motivos para a estrutura intermediário:  
  
-   Logicamente, uma instrução SQL SELECT está fora de serviço preenchido. Os nós que participam na cláusula são visitados antes que os nós que participam em WHERE GRUPO, PERTO, e a cláusula ORDER BY.  
  
-   Para renomear alias, você deve identificar todas as aliases usadas para evitar colisões em renomear. Para adiar as opções renomeando em SqlBuilder, o símbolo de uso objetos para representar as colunas que são candidatos para renomear.  
  
 ![Diagrama de](../../../../../docs/framework/data/adonet/ef/media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")  
  
 Na primeira etapa, a visitar a árvore de expressão, as expressões são agrupadas em SqlSelectStatements, join são aplainadas, e ingressar em alias são aplainadas. Durante esta etapa, os objetos do símbolo representam colunas ou alias de entrada que podem ser renomeados.  
  
 Na segunda etapa, para gerar a cadeia de caracteres real, o alias são renomeados.  
  
## <a name="data-structures"></a>Estruturas de dados  
 Esta seção aborda os tipos usados no [provedor exemplo](http://go.microsoft.com/fwlink/?LinkId=180616) que você use para criar uma instrução SQL.  
  
### <a name="isqlfragment"></a>ISqlFragment  
 Esta seção aborda as classes que implementam a interface de ISqlFragment, que serve duas finalidades:  
  
-   Um tipo de retorno comum para todos os métodos do visitante.  
  
-   Fornece um método para gravar a cadeia de caracteres final SQL.  
  
```  
internal interface ISqlFragment {  
   void WriteSql(SqlWriter writer, SqlGenerator sqlGenerator);  
}  
```  
  
#### <a name="sqlbuilder"></a>SqlBuilder  
 SqlBuilder é um dispositivo de coletar para a cadeia de caracteres final SQL, semelhante a um StringBuilder. Consiste em cadeias de caracteres que compõem o SQL final, juntamente com ISqlFragments que pode ser convertido em cadeias de caracteres.  
  
```  
internal sealed class SqlBuilder : ISqlFragment {  
   public void Append(object s)  
   public void AppendLine()  
   public bool IsEmpty  
}  
```  
  
#### <a name="sqlselectstatement"></a>SqlSelectStatement  
 SqlSelectStatement representa uma instrução SQL SELECT canônica da forma "SELECT... DE.. ONDE... AGRUPE POR... ORDENE POR".  
  
 Cada uma das cláusulas SQL é representada por um StringBuilder. Além disso, controla se distinto foi especificado e se a instrução é o mais alto. Se a declaração não é mais alto, a cláusula ORDER BY for omitido a menos que a declaração também tem uma cláusula TOP.  
  
 FromExtents contém a lista de entradas para a instrução SELECT. Há geralmente apenas um elemento nesse. As instruções SELECT para ingressar temporariamente podem ter mais de um elemento.  
  
 Se a declaração SELECT é criada por um nó do join, SqlSelectStatement mantém uma lista de todas as extensões que foram aplainadas no join em AllJoinExtents. Representa OuterExtents referências externas de SqlSelectStatement e é usado para renomear alias de entrada.  
  
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
  
#### <a name="topclause"></a>TopClause  
 TopClause representa a expressão TOP em um SqlSelectStatement. A propriedade de TopCount indica quantas linhas SUPERIORES devem ser selecionadas.  Quando WithTies é verdadeiro, a TopClause foi criado de um DbLimitExpession.  
  
```  
class TopClause : ISqlFragment {  
   internal bool WithTies {get}  
   internal ISqlFragment TopCount {get}  
   internal TopClause(ISqlFragment topCount, bool withTies)  
   internal TopClause(int topCount, bool withTies)  
}  
```  
  
### <a name="symbols"></a>Símbolos  
 As classes Símbolo- relacionadas e a tabela de símbolo executam alias de entrada que renomiar, join para alias que aplainam, e a renomear alias de coluna.  
  
 A classe do símbolo representa uma extensão, uma instrução SELECT aninhada, ou coluna. É usada em vez de um alias reais para permitir renomear depois que foi usada e também apresenta informações adicionais para o produto que representa (como o tipo).  
  
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
  
 O nome do alias originais para a extensão representada, a declaração SELECT aninhada, ou coluna.  
  
 NewName armazena alias que serão usadas na instrução SQL SELECT. É definida originalmente para nomear, e renomeada somente se necessário para gerar a consulta final da cadeia de caracteres.  
  
 O tipo só é útil para os símbolos que representam extensões e instruções SELECT aninhadas.  
  
#### <a name="symbolpair"></a>SymbolPair  
 Ajuste de registro de endereços da classe de SymbolPair.  
  
 Considere uma expressão Da propriedade (v, j3.j2.j1.a.x “”) onde v é um VarRef, j1, j2, j3 são join, a é uma extensão, e x é colunas.  
  
 Isso tem que ser convertido eventualmente em {} j. {} x. O campo de origem representa o SqlStatement mais externo, representando uma expressão de associação (digamos j2); este é sempre um símbolo do join. Os movimentos do campo de coluna de um join para o símbolo a seguir até que parar em um símbolo de não join. Isso é retornado para visitar um DbPropertyExpression mas nunca é adicionado a um SqlBuilder.  
  
```  
class SymbolPair : ISqlFragment {  
   public Symbol Source;  
   public Symbol Column;  
   public SymbolPair(Symbol source, Symbol column)  
}  
```  
  
#### <a name="joinsymbol"></a>JoinSymbol  
 Um símbolo de associação é um símbolo que representa uma instrução SELECT aninhada com uma união ou uma entrada de associação.  
  
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
  
 ColumnList representa a lista de colunas na cláusula SELECT se esse símbolo representa uma instrução SQL SELECT. ExtentList é a lista de extensões na cláusula SELECT. Se a associação possui várias extensões aplainadas a de nível superior, FlattenedExtentList controla as extensões para garantir que o alias de extensão são renomeados corretamente.  
  
 NameToExtent tem todas as extensões em ExtentList como um dicionário. IsNestedJoin é usado para determinar se um JoinSymbol é um comum se associa ao símbolo ou um que têm um SqlSelectStatement correspondente.  
  
 Todas as listas são definidas exatamente uma vez e usadas para pesquisas ou enumeração.  
  
#### <a name="symboltable"></a>SymbolTable  
 SymbolTable é usado para resolver nomes de variável aos símbolos. SymbolTable é implementado como uma pilha com uma nova entrada para cada escopo. As pesquisas pesquisam a parte superior da pilha para a parte inferior até que uma entrada seja encontrada.  
  
```  
internal sealed class SymbolTable {  
   internal void EnterScope()  
   internal void ExitScope()  
   internal void Add(string name, Symbol value)  
   internal Symbol Lookup(string name)  
}  
```  
  
 Há apenas um SymbolTable por uma instância do módulo de geração do SQL. Os escopos são inseridos e saídos para cada nó relacional. Todos os símbolos em um escopos anteriores são visíveis para um escopos posteriores a menos que oculto por outros símbolos com o mesmo nome.  
  
### <a name="global-state-for-the-visitor"></a>Estado global para o visitante  
 Para ajudar em renomear alias e colunas, manter uma lista de todos os nomes de coluna (AllColumnNames) e do alias de extensão (AllExtentNames) que foram usados na primeira passagem sobre a árvore de consulta.  A tabela de símbolo resolver nomes de variável aos símbolos. IsVarRefSingle é usado somente para efeitos de verificação, ele não é estritamente necessária.  
  
 As duas pilhas usadas por meio de CurrentSelectStatement e de IsParentAJoin são usadas para passar parâmetros “” pai nós filho, desde que o padrão de visitante não permite que nós passem parâmetros.  
  
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
  
## <a name="common-scenarios"></a>Cenários comuns  
 Esta seção descreve cenários comuns do provedor.  
  
### <a name="grouping-expression-nodes-into-sql-statements"></a>Nós de expressão de agrupamento em instruções SQL  
 Um SqlSelectStatement é criado quando o primeiro nó relacional é encontrado (normalmente uma extensão de DbScanExpression) para visitar a árvore a partir de baixo. Para gerar uma instrução SQL SELECT com poucas consultas aninhadas tão possíveis, agregar o tanto como seus nós pai como possível nesse SqlSelectStatement.  
  
 A decisão de se um nó relacional () dado pode ser adicionado ao SqlSelectStatement atual (aquele retornado para o visitar a entrada) ou se uma nova declaração precisa ser iniciada é calculado pelo método IsCompatible e depende do que já estiver no SqlSelectStatement, que depende de nós que estavam abaixo do nó determinado.  
  
 Normalmente, se as cláusulas da instrução SQL são avaliadas após as cláusulas onde os nós que estão sendo considerados mesclando não estiverem vazias, o nó não pode ser adicionado à instrução atual. Por exemplo, se o nó seguir é um filtro, o nó pode ser inserido em SqlSelectStatement atual somente se o seguinte é verdadeira:  
  
-   A lista SELECT está vazia. Se a lista SELECT é não vazio, a lista select foi gerada por um nó que precede o filtro e o predicado pode consultar as colunas geradas por essa lista SELECT.  
  
-   O GROUPBY está vazia. Se o GROUPBY é não vazio, adicione o filtro significaria filtro antes de agrupamento, que não está correto.  
  
-   A cláusula TOP está vazia. Se a cláusula TOP é não vazio, adicione o filtro significaria filtro antes de fazer a TOP, que não está correto.  
  
 Isso não se aplica a nós não-relacionais como DbConstantExpression ou expressões aritméticas, porque esses são sempre incluídos como parte de um SqlSelectStatement existente.  
  
 Além disso, para localizar a raiz da árvore join (um nó do join que não tenha um pai do join), um novo SqlSelectStatement é iniciado. Todas as suas espinha esquerda se associa ao filho é aggregate nesse SqlSelectStatement.  
  
 Sempre que um novo SqlSelectStatement é iniciado, e atual é adicionado à entrada, o SqlSelectStatement atual precise ser concluído adicionando colunas de projeção (uma cláusula SELECT) se não existir uma. Isso é feito com o método AddDefaultColumns, que tem o FromExtents de SqlSelectStatement e adiciona todas as colunas que a lista de extensões representadas por FromExtents traz no escopo à lista de colunas projetadas. Isso é feito, porque nesse ponto, é conhecido que as colunas são referenciadas por outros nós. Isso pode ser otimizada para projetar somente as colunas que podem ser usadas posteriormente.  
  
### <a name="join-flattening"></a>Adição a ajuste  
 Ajuda da propriedade de IsParentAJoin determinar se um determinado joins pode ser aplainado. Em particular, IsParentAJoin retorna `true` somente para o filho esquerdo de uma união e para cada DbScanExpression que é uma entrada imediata a uma união, nesse caso o nó filho reutiliza o mesmo SqlSelectStatement que o pai usaria posteriormente. Para obter mais informações, consulte “join a expressões”.  
  
### <a name="input-alias-redirecting"></a>Entre o redirecionamento alias  
 Alias de entrada que redirecionem são realizadas com a tabela de símbolo.  
  
 Para explicar redirecionando o alias de entrada, consulte o primeiro exemplo [gerando SQL das árvores de comando - práticas recomendadas](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md).  Existem “a” não precisava ser redirecionado para “b” na projeção.  
  
 Quando um objeto de SqlSelectStatement é criado, a extensão é que a entrada ao nó é colocada na propriedade de SqlSelectStatement. Um símbolo (<symbol_b>) é criado com base no nome de associação de entrada (“b”) para representar a extensão e “COMO” + <symbol_b> é acrescentado à cláusula.  O símbolo também é adicionado à propriedade de FromExtents.  
  
 O símbolo também é adicionado à tabela de símbolo para vincular o nome de associação de entrada (“b”, <symbol_b>).  
  
 Se reutilização subsequentes de um nó que SqlSelectStatement, ele adiciona uma entrada à tabela de símbolo para vincular o nome de associação de entrada ao símbolo. Em nosso exemplo, DbProjectExpression com o nome da associação de entrada de "a" seria reutilizar o SqlSelectStatement e adicionar ("a", \< symbol_b >) na tabela.  
  
 Quando as expressões no nome de associação de entrada do nó que estiver reutilizando o SqlSelectStatement, a referência é resolvida usando a tabela de símbolo redirecionado para o símbolo correto. Quando “a” de “a.x” é resolvido para visitar o DbVariableReferenceExpression que representa “a” resolvidos para o symbol_b <do símbolo.>  
  
### <a name="join-alias-flattening"></a>Adição a ajuste alias  
 Adição a ajuste alias é obtido quando visitar um DbPropertyExpression como descrito na seção intitulou DbPropertyExpression.  
  
### <a name="column-name-and-extent-alias-renaming"></a>Renomear alias o nome da coluna e de extensão  
 A entrada de renomeação alias o nome da coluna e de extensão é abordada usando os símbolos que obtêm somente substituído com alias na segunda etapa de geração descrito na seção denominada segundo fase de geração SQL: Gerando o comando de cadeia de caracteres.  
  
## <a name="first-phase-of-the-sql-generation-visiting-the-expression-tree"></a>Primeiro estágio de geração SQL: Visitar a árvore de expressão  
 Esta seção descreve a primeira etapa de geração SQL, quando a expressão que representa a consulta é visitada e uma estrutura intermediária é gerada, um SqlSelectStatement ou um SqlBuilder.  
  
 Esta seção descreve as noções básicas de visitar categorias diferentes de nó da expressão, e os detalhes de visitar a expressão específica tipo.  
  
### <a name="relational-non-join-nodes"></a>(não se junte nós relacionais)  
 O seguinte suporte de expressão não associa a nós:  
  
-   DbDistinctExpression  
  
-   DbFilterExpression  
  
-   DbGroupByExpression  
  
-   DbLimitExpession  
  
-   DbProjectExpression  
  
-   DbSkipExpression  
  
-   DbSortExpression  
  
 Visitar esses nós segue o padrão a seguir:  
  
1.  Interativo entrada relacional e obter o SqlSelectStatement resultante. A entrada a um nó relacional pode ser um dos seguintes:  
  
    -   Um nó relacional, incluindo uma extensão (um DbScanExpression, por exemplo). Visitar um nó retorna um SqlSelectStatement.  
  
    -   Uma expressão de operação relevante (UNION TODOS, por exemplo). O resultado tem que ser empacotado entre colchetes e coloque na cláusula de um novo SqlSelectStatement.  
  
2.  Verifique se o nó atual pode ser adicionado ao SqlSelectStatement gerado pela entrada. A seção denominada agrupamento expressões em instruções SQL descreve esta. Se não,  
  
    -   Aparecer o objeto atual de SqlSelectStatement.  
  
    -   Crie um novo objeto de SqlSelectStatement e adicione o SqlSelectStatement aparecido como o novo objeto de SqlSelectStatement.  
  
    -   Coloque o novo objeto sobre a pilha.  
  
3.  Redirecionando a expressão de entrada que associa o símbolo correto de entrada. Essa informação é mantida no objeto de SqlSelectStatement.  
  
4.  Adicione um novo escopo de SymbolTable.  
  
5.  Interativo a parte das entrada de expressões (por exemplo, projeção e predicado).  
  
6.  Aparecer todos os objetos adicionados às pilhas globais.  
  
 DbSkipExpression para não ter um direto equivalente no SQL. Logicamente, é convertido em:  
  
```  
SELECT Y.x1, Y.x2, ..., Y.xn  
FROM (  
   SELECT X.x1, X.x2, ..., X.xn, row_number() OVER (ORDER BY sk1, sk2, ...) AS [row_number]   
   FROM input as X   
   ) as Y  
WHERE Y.[row_number] > count   
ORDER BY sk1, sk2, ...  
```  
  
### <a name="join-expressions"></a>Adição às expressões  
 Os seguintes são considerados ingressar em expressões e são processados em uma maneira comum, pelo método de VisitJoinExpression:  
  
-   DbApplyExpression  
  
-   DbJoinExpression  
  
-   DbCrossJoinExpression  
  
 A seguir estão as etapas de visita:  
  
 Primeiro, antes de visitar filhos, IsParentAJoin é chamado para verificar se o nó do join é um filho de uma união ao longo de uma espinha esquerda. Se ele retornar false, um novo SqlSelectStatement é iniciado. Nesse sentido, join são visitados diferente do restante de nós, porque o pai (o nó do join) cria o SqlSelectStatement para que os filhos utilizarão possivelmente.  
  
 Segundo, processar entradas um de cada vez. Para cada entrada:  
  
1.  Didático de entrada.  
  
2.  Enviar o processo visitar o resultado da entrada por ProcessJoinInputResult, que é responsável para manter a tabela de símbolo após visitado um filho de uma expressão de associação e possivelmente ter concluído o SqlSelectStatement gerado pelo filho. O resultado de filho pode ser um dos seguintes:  
  
    -   Um SqlSelectStatement diferente de aquele que o pai será adicionado. Em tais casos, talvez precisem ser concluído adicionando colunas padrão. Se a entrada foi uma associação, você precisa criar um novo join para o símbolo. Caso contrário, crie um símbolo normal.  
  
    -   Uma extensão (um DbScanExpression, por exemplo), nesse caso é simplesmente adicionada à lista de entradas de SqlSelectStatement pai.  
  
    -   Não um SqlSelectStatement, nesse caso é empacotado com colchetes.  
  
    -   O mesmo SqlSelectStatement a que o pai é adicionado. Em tais casos, os símbolos na lista de FromExtents precisam ser substituídos por um único novo JoinSymbol que representa todos os.  
  
    -   Para os primeiros três casos, AddFromSymbol é chamado para adicionar COMO a cláusula, e atualizar a tabela de símbolo.  
  
 No lugar, a condição de adição (se houver) é visitada.  
  
### <a name="set-operations"></a>Operações de conjunto  
 As operações de conjunto DbUnionAllExpression, DbExceptExpression, e DbIntersectExpression são processadas pelo método VisitSetOpExpression. Cria um SqlBuilder de forma  
  
```xml  
<leftSqlSelectStatement> <setOp> <rightSqlSelectStatement>  
```  
  
 Onde \<leftSqlSelectStatement > e \<rightSqlSelectStatement > são SqlSelectStatements obtido visitando cada uma das entradas, e \<setOp > é a operação correspondente (UNION ALL, por exemplo).  
  
### <a name="dbscanexpression"></a>DbScanExpression  
 Se visitado em um contexto do join (como uma entrada para uma associação que é um filho de outro esquerdo se junte), DbScanExpression retorna um SqlBuilder com o destino SQL para o destino correspondente, que é uma consulta de definição, a tabela, ou uma exibição. Se não, um novo SqlSelectStatement é criado com o conjunto de campo para corresponder ao destino correspondente.  
  
### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression  
 A visitar de um DbVariableReferenceExpression retorna o símbolo que corresponde à expressão variável de referência com base na tabela de pesquisa símbolo.  
  
### <a name="dbpropertyexpression"></a>DbPropertyExpression  
 Adição a ajuste alias é identificado e processado para visitar um DbPropertyExpression.  
  
 A propriedade a instância é visitada primeiro e o resultado é um símbolo, um JoinSymbol, ou um SymbolPair. É aqui como esses três ocorrências são tratados:  
  
-   Se um JoinSymbol é retornado, de sua propriedade de NameToExtent contém um símbolo para a propriedade necessário. Se o símbolo de associação verdadeira, aninhado representa um novo registro do símbolo é retornado com o símbolo do join para controlar o símbolo que seria usado como o alias de instância, e o símbolo que representa a propriedade real para resolver mais.  
  
-   Se um SymbolPair é retornado e parte da coluna é um símbolo de adição, um símbolo de associação é retornado novamente, mas a propriedade coluna é atualizada agora para apontar para a propriedade representada pela expressão atual da propriedade. Se não um SqlBuilder é retornado com a fonte de SymbolPair como alias, e o símbolo para a propriedade atual como a coluna.  
  
-   Se um símbolo é retornado, o método de visita retorna um método de SqlBuilder com essa instância como alias, e o nome da propriedade como o nome da coluna.  
  
### <a name="dbnewinstanceexpression"></a>DbNewInstanceExpression  
 Quando usado como a propriedade de projeção de DbProjectExpression, DbNewInstanceExpression gerencia uma lista separada por vírgulas de argumentos para representar as colunas projetadas.  
  
 Quando DbNewInstanceExpression tem um tipo de retorno da coleção, e define uma nova coleção de expressões fornecidas como argumentos, os seguintes três ocorrências são tratados separada:  
  
-   Se DbNewInstanceExpression tem DbElementExpression como o argumento único, ele é convertido como segue:  
  
    ```  
    NewInstance(Element(X)) =>  SELECT TOP 1 …FROM X  
    ```  
  
 Se DbNewInstanceExpression não tem nenhum argumento (representa uma tabela vazia), ele é convertido em DbNewInstanceExpression:  
  
```  
SELECT CAST(NULL AS <primitiveType>) as X  
FROM (SELECT 1) AS Y WHERE 1=0  
```  
  
 Se não DbNewInstanceExpression compila UNION- qualquer escada dos argumentos:  
  
```  
SELECT <visit-result-arg1> as X  
UNION ALL SELECT <visit-result-arg2> as X  
UNION ALL …  
UNION ALL SELECT <visit-result-argN> as X  
```  
  
### <a name="dbfunctionexpression"></a>DbFunctionExpression  
 Canônico e funções internas são processados da mesma maneira: se precisam tratamento especial (GUARNIÇÃO (cadeia de caracteres) a LTRIM (RTRIM (cadeia de caracteres), por exemplo), o manipulador adequado são chamados. Se não são traduzidas a Nomedafunção (arg1, arg2,…, argn).  
  
 Dicionários são usados para manter controle de quais papéis precisam tratamento especial e seus manipuladores apropriadas.  
  
 As funções definidas pelo usuário tanslated a NamespaceName.FunctionName (arg1, arg2,…, argn).  
  
### <a name="dbelementexpression"></a>DbElementExpression  
 O método visita DbElementExpression que é chamado somente visitar um DbElementExpression quando usado para representar um subconsulta escalar. Portanto, DbElementExpression converte em um SqlSelectStatement completo e adiciona os colchetes redor deles.  
  
### <a name="dbquantifierexpression"></a>DbQuantifierExpression  
 Dependendo do tipo da expressão (alguns ou todos), DbQuantifierExpression é convertido como:  
  
```  
Any(input, x) => Exists(Filter(input,x))  
All(input, x) => Not Exists(Filter(input, not(x))  
```  
  
### <a name="dbnotexpression"></a>DbNotExpression  
 Em alguns casos é possível recolher a conversão de DbNotExpression com sua expressão de entrada. Por exemplo:  
  
```  
Not(IsNull(a)) =>  "a IS NOT NULL"  
Not(All(input, x) => Not (Not Exists(Filter(input, not(x))) => Exists(Filter(input, not(x))  
```  
  
 A razão que o segundo recolher é executado é porque as incapacidades foram introduzidas pelo provedor para converter DbQuantifierExpression de qualquer tipo. Isso Entity Framework não pode ter feito a simplificação.  
  
### <a name="dbisemptyexpression"></a>DbIsEmptyExpression  
 DbIsEmptyExpression é convertido como:  
  
```  
IsEmpty(inut) = Not Exists(input)  
```  
  
## <a name="second-phase-of-sql-generation-generating-the-string-command"></a>Segundo fase de geração SQL: Gerando o comando de cadeia de caracteres  
 Para gerar um comando SQL de cadeia de caracteres, o SqlSelectStatement gerencia alias reais dos símbolos, que tratam a introdução para renomear alias o nome da coluna e de extensão.  
  
 Renomear alias de extensão ocorre ao escrever o objeto de SqlSelectStatement em uma cadeia de caracteres. Primeiro crie uma lista de todas as aliases usadas por extensões externos. Cada símbolo no FromExtents (ou em AllJoinExtents se é não-nulo), é renomeado se colidir com quaisquer das extensões externos. Se renomear for necessário, não será em conflito com quaisquer das extensões coletadas em AllExtentNames.  
  
 Renomear a coluna ocorre ao escrever um objeto do símbolo para uma cadeia de caracteres. AddDefaultColumns na primeira etapa determinar se um determinado símbolo da coluna tem que ser renomeado. Na segunda etapa somente renomear ocorre certificar-se de que o nome gerado não está em conflito com qualquer nome usado em AllColumnNames  
  
 Para gerar nomes exclusivos para alias de extensão e para colunas, existing_name_n <>de uso onde n é o alias as menores que ainda não foram usadas. A lista global de todas as aliases aumenta a necessidade de se conectar renomear.  
  
## <a name="see-also"></a>Consulte também  
 [Geração de SQL no provedor exemplo](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
