---
title: A forma das árvores de comando
ms.date: 03/30/2017
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
ms.openlocfilehash: 9084e2616ac4ea540bdf755afd011d67a5c991fa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766030"
---
# <a name="the-shape-of-the-command-trees"></a>A forma das árvores de comando
O módulo de geração SQL é responsável por gerar uma consulta SQL backend específica com base em uma entrada dada comando expressão de consulta de árvore. Esta seção descreve as características, propriedades, e a estrutura das árvores de comando de consulta.  
  
## <a name="query-command-trees-overview"></a>Visão geral das árvores de comando de consulta  
 Uma árvore de comando de consulta é uma representação do modelo de objeto de uma consulta. Árvores de comando de consulta servem duas finalidades:  
  
-   Para expressar uma entrada consulte que é especificada em [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
-   Para expressar uma saída consulte que são fornecidas para um provedor e descrevam uma consulta na parte posterior.  
  
 Consulte uma semântica mais rica de suporte das árvores de comando do SQL: consultas 1999 compatíveis, incluindo suporte para trabalhar com coleções e operações aninhadas de tipo, como verificar se uma entidade é de um tipo específico, ou filtragem definem baseado em um tipo.  
  
 A propriedade de DBQueryCommandTree.Query é a raiz da árvore de expressão que descreve a lógica de consulta. A propriedade de DBQueryCommandTree.Parameters contém uma lista de parâmetros que são usados na consulta. A árvore de expressão é composta de objetos de DbExpression.  
  
 Um objeto de DbExpression representa qualquer computação. Vários tipos de expressões são fornecidos por [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] composto expressões de consulta, incluindo constantes, variáveis, funções, construtores, e operadores relacionais padrões como filtro e join. Cada objeto de DbExpression tem uma propriedade ResultType que representa o tipo do resultado produzido por essa expressão. Esse tipo é expresso como um TypeUsage.  
  
## <a name="shapes-of-the-output-query-command-tree"></a>Formas da árvore de comando de consulta de saída  
 Árvores de comando de consulta de saída representam às consultas SQL () relacionais e aderem às regras muito mais rígidas do que aquelas que se aplicam para consulte árvores de comando. Normalmente contêm as compilações que são transmitidos facilmente para SQL.  
  
 Árvores de comando de entrada são expressas no modelo conceitual, que suporta propriedades de navegação, associações entre entidades, e herança. Árvores de comando de saída são expressas no modelo de armazenamento. Árvores de comando de entrada permitem que você projeta coleções aninhadas, mas as árvores de comando de saída não.  
  
 Árvores de comando de consulta de saída são criadas usando um subconjunto dos objetos disponíveis de DbExpression e mesmo algumas expressões nesse subconjunto restringiram uso.  
  
 Digite operações, como verificar se uma expressão fornecida seja de um tipo específico ou conjuntos de filtragem com base em um tipo, não estão atual em árvores de comando de saída.  
  
 Na saída comande árvores, somente as expressões que os valores Booleanos de retorno são usados para projeções e somente para predicados em expressões que exigem um predicado, como um filtro ou uma instrução case.  
  
 A raiz das árvores de um comando de consulta de saída é um objeto de DbProjectExpression.  
  
### <a name="expression-types-not-present-in-output-query-command-trees"></a>Tipos de expressão não presentes em árvores de comando de consulta de saída  
 Os seguintes tipos de expressão não são válidos em uma árvore de comando de consulta de saída e não precisam ser tratados por provedores:  
  
 DbDerefExpression  
  
 DbEntityRefExpression  
  
 DbRefKeyExpression  
  
 DbIsOfExpression  
  
 DbOfTypeExpression  
  
 DbRefExpression  
  
 DbRelationshipNavigationExpression  
  
 DbTreatExpression  
  
### <a name="expression-restrictions-and-notes"></a>Restrições e notas de expressão  
 Várias expressões podem ser utilizadas somente em uma maneira strict em árvores de comando de consulta de saída:  
  
#### <a name="dbfunctionexpression"></a>DbFunctionExpression  
 Os seguintes tipos de função podem ser passados:  
  
-   Funções canônicas que são reconhecidas pelo namespace de Edm.  
  
-   Funções internas (de armazenamento) que são reconhecidas pelo BuiltInAttribute.  
  
-   Funções definidas pelo usuário.  
  
 Funções canônicas (consulte [funções canônicas](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) para obter mais informações) são especificados como parte do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], e os provedores devem fornecer implementações para funções canônicas conforme as especificações. Funções de Store são baseados nas especificações no manifesto correspondente do provedor. As funções definidas pelo usuário são baseadas nas especificações em SSDL.  
  
 Além disso, as funções que têm o atributo de NiladicFunction não têm nenhum argumento e devem ser traduzidas sem o parêntese no final.  Ou seja, para  *\<functionName >* em vez de  *\<functionName > ()*.  
  
#### <a name="dbnewinstanceexpression"></a>DbNewInstanceExpression  
 DbNewInstanceExpression pode ocorrer somente nos dois seguintes casos:  
  
-   Como a propriedade de projeção de DbProjectExpression.  Quando usadas como esta'n as seguintes limitações se aplicam:  
  
    -   O tipo do resultado deve ser um tipo de linha.  
  
    -   Cada um dos argumentos é uma expressão que gerencia um resultado com um tipo primitivo. Normalmente, cada argumento é uma expressão escalar, como um PropertyExpression sobre um DbVariableReferenceExpression, uma chamada de função, ou uma computação aritmética de DbPropertyExpression sobre um DbVariableReferenceExpression ou uma chamada de função. No entanto, uma expressão que representa um subconsulta escalar também pode ocorrer na lista de argumentos para um DbNewInstanceExpression. Uma expressão que representa um subconsulta escalar é uma árvore de expressão que representa um subconsulta que retorna exatamente uma linha e uma coluna de um tipo primitivo com uma raiz do objeto de DbElementExperession  
  
-   Com um tipo de retorno da coleção, nesse caso define uma nova coleção de expressões fornecidas como argumentos.  
  
#### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression  
 Um DbVariableReferenceExpression tem que ser um filho do nó de DbPropertyExpression.  
  
#### <a name="dbgroupbyexpression"></a>DbGroupByExpression  
 A propriedade as agregações de um DbGroupByExpression pode ter apenas elementos do tipo DbFunctionAggregate. Não há nenhum outro tipo agregado.  
  
#### <a name="dblimitexpression"></a>DbLimitExpression  
 O limite de propriedade só pode ser um DbConstantExpression ou um DbParameterReferenceExpression. Também a propriedade WithTies é sempre false até a data do .NET Framework versão 3,5.  
  
#### <a name="dbscanexpression"></a>DbScanExpression  
 Quando usado em árvores de comando de saída, o DbScanExpression efetivamente representa uma verificação em uma tabela, uma exibição, ou uma consulta de armazenamento, representado por EnitySetBase::Target.  
  
 Se a propriedade de metadados "Definição de consulta" do destino for não nulo, ele representa uma consulta, o texto da consulta para o qual é fornecido nessa propriedade de metadados no idioma específico do provedor (ou dialeto) conforme especificado na definição de esquema do repositório.  
  
 Caso contrário, o destino representa uma tabela ou uma exibição. O prefixo de esquema está na propriedade de metadados de "Esquema", se não nulo, caso contrário, é o nome do contêiner de entidade.  O nome de tabela ou exibição é tanto de propriedade de metadados de "Tabela", se não for null, caso contrário, a propriedade de nome da entidade definida base.  
  
 Todas essas propriedades são originados de definição de EntitySet correspondente no arquivo de definição do esquema de armazenamento (SSDL).  
  
### <a name="using-primitive-types"></a>Usando tipos primitivos  
 Quando os tipos primitivos são referenciados em árvores de comando de saída, normalmente são referenciados em tipos primitivos de modelo conceitual. No entanto, certos expressões, provedores precisam o tipo primitivo correspondente do armazenamento. Os exemplos de como expressões incluem DbCastExpression e possivelmente DbNullExpression, se o provedor precisa converter o zero para o tipo correspondente. Nesses casos, os provedores devem fazer o mapeamento para o tipo de provedor com base no tipo primitivo tipo e em suas facetas.  
  
## <a name="see-also"></a>Consulte também  
 [Geração de SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
