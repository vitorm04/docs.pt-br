---
title: Geração de alteração SQL
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: 8e0568e32094b6cc27137409f3d908928d82cebb
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45989950"
---
# <a name="modification-sql-generation"></a>Geração de alteração SQL
Esta seção discute como desenvolver um módulo de geração SQL de alteração para o seu (SQL: provedor de base de dados compliant 1999). Este módulo é responsável para converter uma árvore de comando de alteração apropriadas nas instruções SQL INSERT, UPDATE ou DELETE.  
  
 Para obter informações sobre a geração de SQL para instruções select, consulte [geração SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md).  
  
## <a name="overview-of-modification-command-trees"></a>Visão geral das árvores de alteração de comando  
 O módulo de geração SQL de alteração gerenciar as instruções SQL base de dados - específicas de alteração com base em uma entrada dada DbModificationCommandTree.  
  
 Um DbModificationCommandTree é uma representação do modelo de objeto de uma operação de alteração DML (uma inserção, uma atualização, ou uma operação de exclusão), herdando de DbCommandTree. Há três implementações de DbModificationCommandTree:  
  
-   DbInsertCommandTree  
  
-   DbUpdateCommandTree  
  
-   DbDeleteCommandTree  
  
 DbModificationCommandTree e suas implementações que são produzidas pelo [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sempre representam uma operação única linha. Esta seção descreve esses tipos com as restrições no .NET Framework versão 3.5.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")  
  
 DbModificationCommandTree tem uma propriedade de destino que representa o destino definido para a operação de alteração. A propriedade da expressão de destino, que define o conjunto de entrada é sempre DbScanExpression.  Um DbScanExpression pode representar uma tabela ou exibição, ou um conjunto de dados definidos com uma consulta se a propriedade de metadados "Que define a consulta" do seu destino for não nulo.  
  
 Um DbScanExpression que representa uma consulta somente poderia alcançar um provedor como um destino de alteração se o dataset foi definido usando uma consulta de definição no modelo mas em nenhuma função foi fornecido para a operação correspondente de alteração. Os provedores não podem ser capaz de suportar esse cenário (SqlClient, por exemplo, não faz).  
  
 DbInsertCommandTree representa uma única operação de inserção de linha expressa como uma árvore de comando.  
  
```  
public sealed class DbInsertCommandTree : DbModificationCommandTree {  
   public IList<DbModificationClause> SetClauses { get }  
   public DbExpression Returning { get }  
}  
```  
  
 DbUpdateCommandTree representa uma operação de atualização de única linha expressa como uma árvore de comando.  
  
 DbDeleteCommandTree representa uma única operação de exclusão de linha expressa como uma árvore de comando.  
  
### <a name="restrictions-on-modification-command-tree-properties"></a>Restrições em propriedades da árvore de comando de alteração  
 As seguintes informações e limitações se aplicam às propriedades de árvore de comando de alteração.  
  
#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>Retornar em DbInsertCommandTree e em DbUpdateCommandTree  
 Quando não-nulo, retornar indica que o comando retorna um leitor. Caso contrário, o comando deve retornar um valor escalar indicando o número de linhas afetadas (inserido ou atualizado).  
  
 O valor retornando especifica uma projeção de resultados sejam retornados com base na linha inserida ou atualizado. Só pode ser do tipo DbNewInstanceExpression que representa uma linha, a cada um dos argumentos que são um DbPropertyExpression sobre um DbVariableReferenceExpression que representa uma referência ao destino de DbModificationCommandTree correspondente. As propriedades representadas pelo DbPropertyExpressions usado em retornar de propriedade são sempre valores gerados ou computados de armazenamento. Em DbInsertCommandTree, retornar não é zero quando pelo menos uma propriedade de tabela na linha que está sendo inserido é especificado como o armazenamento gerou ou computou (marcado como StoreGeneratedPattern.Identity ou StoreGeneratedPattern.Computed no ssdl). Em DbUpdateCommandTrees, retornar não é zero quando pelo menos uma propriedade de tabela na linha que está sendo atualizada é especificado como o armazenamento calculado (marcado como StoreGeneratedPattern.Computed no ssdl).  
  
#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>SetClauses em DbInsertCommandTree e em DbUpdateCommandTree  
 SetClauses especifica a lista de cláusulas conjunto de inserção ou de atualização que definem a inserção ou a operação de atualização.  
  
```  
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.   
```  
  
 A propriedade especifica a propriedade que deve ser atualizada. É sempre um DbPropertyExpression sobre um DbVariableReferenceExpression, que representa uma referência ao destino de DbModificationCommandTree correspondente.  
  
 O valor especifica o novo valor com que para atualizar a propriedade. É do tipo DbConstantExpression ou DbNullExpression.  
  
#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a>Predicado em DbUpdateCommandTree e em DbDeleteCommandTree  
 O predicado especifica o predicado usado para determinar quais membros da coleção de destino devem ser atualizados ou excluídos. É uma árvore de expressão compilada da seguir subconjunto de DbExpressions:  
  
-   DbComparisonExpression de semelhantes amáveis, com o filho adequado que são um DbPropertyExression como restrito abaixo e o filho esquerdo um DbConstantExpression.  
  
-   DbConstantExpression  
  
-   DbIsNullExpression sobre um DbPropertyExpresison como restrito abaixo  
  
-   DbPropertyExpression sobre um DbVariableReferenceExpression que representa uma referência ao destino de DbModificationCommandTree correspondente.  
  
-   DbAndExpression  
  
-   DbNotExpression  
  
-   DbOrExpression  
  
## <a name="modification-sql-generation-in-the-sample-provider"></a>Geração SQL alteração no provedor exemplo  
 O [provedor de exemplo do Entity Framework](https://go.microsoft.com/fwlink/?LinkId=180616) demonstra os componentes de provedores de dados ADO.NET que dão suporte a [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Tem como alvo um base de dados do SQL Server 2005 e é implementado como um wrapper sobre o provedor de dados do ADO.NET .NET 2.0.  
  
 O módulo de geração SQL de alteração do provedor de exemplo (localizado na geração SQL do arquivo DmlSqlGenerator.cs \) usa uma entrada DbModificationCommandTree e gerencia uma única instrução SQL de alteração seguida possivelmente por uma instrução select para retornar um leitor se especificado pelo DbModificationCommandTree. Observe que a forma de comandos gerados é afetada por base de dados SQL Server de destino.  
  
### <a name="helper-classes-expressiontranslator"></a>Classes auxiliar: ExpressionTranslator  
 Serve de ExpressionTranslator como um tradutor leve comum para todas as propriedades da árvore de comando de alteração de tipo DbExpression. Oferece suporte à conversão de tipos somente da expressão às propriedades de árvore de comando de alteração são restritas e é compilado com as restrições específicos em mente.  
  
 As informações a seguir descreve tipos específicos de visita de expressões (os nós com traduções triviais são omitidos.)  
  
### <a name="dbcomparisonexpression"></a>DbComparisonExpression  
 Quando o ExpressionTranslator é construído com preserveMemberValues = retifique, e quando a constante à direita é um DbConstantExpression (em vez de DbNullExpression), associa o operando esquerdo (um DbPropertyExpressions) com esse DbConstantExpression. Isso é usado se uma instrução SELECT de retorno precisa ser gerada para identificar a linha afetado.  
  
### <a name="dbconstantexpression"></a>DbConstantExpression  
 Para cada constante visitada um parâmetro é criado.  
  
### <a name="dbpropertyexpression"></a>DbPropertyExpression  
 Dado que a instância de DbPropertyExpression sempre representa a tabela de entrada, a menos que a geração criar um apelido (que ocorrem apenas em cenários de atualização quando uma variável da tabela é usado), nenhum alias precisa ser especificada para a entrada; a conversão tem como padrão o nome da propriedade.  
  
## <a name="generating-an-insert-sql-command"></a>Gerando um comando SQL de inserção  
 Para um DbInsertCommandTree determinado no provedor de exemplo, o comando gerado de inserção segue um dos dois modelos de inserção abaixo.  
  
 O primeiro modelo tem um comando executar a inserção dados os valores na lista de SetClauses, e uma instrução SELECT para retornar as propriedades especificadas na propriedade retornando para a linha inserida se a propriedade retornando não era nula. O elemento de predicado "\@ @ROWCOUNT > 0" é verdadeiro se uma linha foi inserida. O elemento de predicado "keyMemberI = keyValueI &#124; SCOPE_IDENTITY ()" leva a forma "keyMemberI = SCOPE_IDENTITY ()" apenas se o keyMemeberI é uma chave store-gerado, porque SCOPE_IDENTITY () retorna o último valor de identidade inserido em uma identidade ( coluna Store-gerado).  
  
```  
-- first insert Template  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES   
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 O segundo modelo é necessário se a inserção especifica inserir uma linha onde a chave primária é gerado Store- mas não é um tipo inteiro e portanto não pode ser usada com scope_identity()). Também é usado se houver uma chave Store- gerado composta.  
  
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
  
 A seguir está um exemplo que usa o modelo que está incluído com o provedor de exemplo. Gerencia um comando de inserção de um DbInsertCommandTree.  
  
 O código a seguir insere uma categoria:  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = new Category();  
   c.CategoryName = "Test Category";  
   c.Description = "A new category for testing";  
   northwindContext.AddObject("Categories", c);  
   northwindContext.SaveChanges();  
}  
```  
  
 Esse código gerencia a seguir árvore de comando, que é passada para o provedor:  
  
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
  
 O comando de armazenamento que o provedor exemplo gerencia é a seguinte instrução SQL:  
  
```  
insert [dbo].[Categories]([CategoryName], [Description], [Picture])  
values (@p0, @p1, null)  
select [CategoryID]  
from [dbo].[Categories]  
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()  
```  
  
## <a name="generating-an-update-sql-command"></a>Gerando um comando SQL de atualização  
 Para um determinado DbUpdateCommandTree, o comando gerado de atualização é baseado no modelo seguir:  
  
```  
-- UPDATE Template   
UPDATE <target>   
SET setClauseProprerty0 = setClauseValue0,  .. setClauseProprertyN = setClauseValueN  | @i = 0  
WHERE <predicate>  
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 A cláusula set tem a cláusula set falso ("@i = 0") somente se nenhum conjunto de cláusulas forem especificado. Este é garantir que todas as colunas Store- computadas recalculados.  
  
 Somente se a propriedade retornando não é nulo, uma instrução SELECT é gerada para retornar as propriedades especificadas na propriedade retornando.  
  
 O exemplo a seguir usa o modelo que está incluído com o provedor de exemplo para gerar um comando de atualização.  
  
 O seguinte código do usuário atualiza uma categoria:  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();  
   c.CategoryName = "New test name";  
   northwindContext.SaveChanges();  
}  
```  
  
 Esse código do usuário gerencia a seguir árvore de comando, que é passada para o provedor:  
  
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
  
 O exemplo de provedor para gerenciar o seguinte comando de armazenamento:  
  
```  
update [dbo].[Categories]  
set [CategoryName] = @p0  
where ([CategoryID] = @p1)   
```  
  
### <a name="generating-a-delete-sql-command"></a>Gerando um comando SQL delete  
 Para um determinado DbDeleteCommandTree, o comando DELETE gerado é baseado no modelo seguir:  
  
```  
-- DELETE Template   
DELETE <target>   
WHERE <predicate>  
```  
  
 O exemplo a seguir usa o modelo que está incluído com o provedor de exemplo para gerar um comando delete.  
  
 O seguinte código do usuário exclui uma categoria:  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();  
   northwindContext.DeleteObject(c);  
   northwindContext.SaveChanges();  
}  
```  
  
 Esse código do usuário gerencia a seguir árvore de comando, que é passada para o provedor.  
  
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
  
 O seguinte comando de armazenamento é gerado pelo provedor exemplo:  
  
```  
delete [dbo].[Categories]  
where ([CategoryID] = @p0)  
```  
  
## <a name="see-also"></a>Consulte também  
 [Escrevendo um Provedor de Dados do Entity Framework](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
