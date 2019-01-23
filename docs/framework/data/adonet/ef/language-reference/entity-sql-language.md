---
title: Linguagem Entity SQL
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: 0c698f04c3b95ffb204a20d41e91ef3f6210c5d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494089"
---
# <a name="entity-sql-language"></a>Linguagem Entity SQL
O Entity SQL é uma linguagem de consulta independente de armazenamento semelhante ao SQL. O Entity SQL permite que você consulte dados de entidade, como objetos ou em forma de tabela. Você deve considerar o uso do Entity SQL nos seguintes casos:  
  
-   Quando uma consulta deve ser construída dinamicamente em tempo de execução. Nesse caso, você também deve considerar o uso dos métodos do construtor de consultas de <xref:System.Data.Objects.ObjectQuery%601>, em vez de construir uma cadeia de caracteres de consulta Entity SQL em tempo de execução.  
  
-   Quando você deseja definir uma consulta como parte da definição do modelo. Somente o Entity SQL tem suporte em um modelo de dados. Para obter mais informações, consulte [QueryView elemento (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)  
  
-   Ao usar EntityClient para retornar dados de entidade somente leitura como conjuntos de linhas usando <xref:System.Data.EntityClient.EntityDataReader>. Para obter mais informações, consulte [provedor EntityClient para Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
-   Se você já for um especialista em linguagens de consulta baseadas em SQL, o Entity SQL poderá parecer a opção mais natural para você.  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a>Usando Entity SQL com o provedor EntityClient  
 Se você desejar usar o Entity SQL com o provedor EntityClient, consulte os seguintes tópicos para obter mais informações:  
  
 [Provedor EntityClient para Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [Como: Compilar uma cadeia de Conexão EntityConnection](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [Como: Executar uma consulta que retorna resultados PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Como: Executar uma consulta que retorna resultados RefType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Como: Executar uma consulta que retorna tipos complexos](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Como: Executar uma consulta que retorna coleções aninhadas](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Como: Executar uma consulta Entity SQL parametrizada usando EntityCommand](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Como: Executar um procedimento armazenado parametrizado usando EntityCommand](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Como: Executar uma consulta Polimorfo](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [Como: Navegar em relações com o operador navegar](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a>Usando o Entity SQL com consultas de objetos  
 Se você desejar usar o Entity SQL com consultas de objetos, consulte os seguintes tópicos para obter mais informações:  
  
 [Como: Executar uma consulta que retorna objetos do tipo de entidade](https://msdn.microsoft.com/library/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [Como: Executar uma consulta parametrizada](https://msdn.microsoft.com/library/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [Como: Navegar em relações usando as propriedades de navegação](https://msdn.microsoft.com/library/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [Como: Chamar uma função definida pelo usuário](https://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [Como: Filtrar dados](https://msdn.microsoft.com/library/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [Como: Classificar dados](https://msdn.microsoft.com/library/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [Como: Dados de grupo](https://msdn.microsoft.com/library/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [Como: Dados de agregação](https://msdn.microsoft.com/library/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [Como: Executar uma consulta que retorna objetos de tipo anônimo](https://msdn.microsoft.com/library/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [Como: Executar uma consulta que retorna uma coleção de tipos primitivos](https://msdn.microsoft.com/library/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [Como: Consultar objetos relacionados em uma EntityCollection](https://msdn.microsoft.com/library/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [Como: A união de duas consultas de ordem](https://msdn.microsoft.com/library/853c583a-eaba-4400-830d-be974e735313)  
  
 [Como: Paginar os resultados da consulta](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral do Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a>Consulte também
- [Entity Framework do ADO.NET](../../../../../../docs/framework/data/adonet/ef/index.md)
- [Referência de Linguagem](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
