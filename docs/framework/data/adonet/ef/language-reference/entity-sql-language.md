---
title: Linguagem Entity SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 08e366e8bbd9df31f367496ca5e106b876921896
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="entity-sql-language"></a>Linguagem Entity SQL
O Entity SQL é uma linguagem de consulta independente de armazenamento semelhante ao SQL. O Entity SQL permite que você consulte dados de entidade, como objetos ou em forma de tabela. Você deve considerar o uso do Entity SQL nos seguintes casos:  
  
-   Quando uma consulta deve ser construída dinamicamente em tempo de execução. Nesse caso, você também deve considerar o uso dos métodos do construtor de consultas de <xref:System.Data.Objects.ObjectQuery%601>, em vez de construir uma cadeia de caracteres de consulta Entity SQL em tempo de execução.  
  
-   Quando você deseja definir uma consulta como parte da definição do modelo. Somente o Entity SQL tem suporte em um modelo de dados. Para obter mais informações, consulte [QueryView elemento (MSL)](http://msdn.microsoft.com/en-us/f0426b34-45cb-4fd7-9777-e0570c5e0e80)  
  
-   Ao usar EntityClient para retornar dados de entidade somente leitura como conjuntos de linhas usando <xref:System.Data.EntityClient.EntityDataReader>. Para obter mais informações, consulte [provedor EntityClient para Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
-   Se você já for um especialista em linguagens de consulta baseadas em SQL, o Entity SQL poderá parecer a opção mais natural para você.  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a>Usando Entity SQL com o provedor EntityClient  
 Se você desejar usar o Entity SQL com o provedor EntityClient, consulte os seguintes tópicos para obter mais informações:  
  
 [Provedor EntityClient para Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [Como: criar uma cadeia de caracteres de Conexão EntityConnection](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [Como: executar uma consulta que retorna resultados de PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Como: executar uma consulta que retorna resultados de RefType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Como: executar uma consulta que retorna tipos complexos](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Como: executar uma consulta que retorna aninhados coleções](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Como: executar uma consulta Entity SQL parametrizada usando EntityCommand](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Como: executar um procedimento armazenado parametrizado usando EntityCommand](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Como: executar uma consulta Polimorfo](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [Como: navegar em relações com o operador navegar](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a>Usando o Entity SQL com consultas de objetos  
 Se você desejar usar o Entity SQL com consultas de objetos, consulte os seguintes tópicos para obter mais informações:  
  
 [Como: executar uma consulta que retorna os objetos de tipo de entidade](http://msdn.microsoft.com/en-us/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [Como: executar uma consulta parametrizada](http://msdn.microsoft.com/en-us/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [Como: navegar em relações usando propriedades de navegação](http://msdn.microsoft.com/en-us/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [Como: chamar uma função definida pelo usuário](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [Como: filtrar dados](http://msdn.microsoft.com/en-us/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [Como: classificar dados](http://msdn.microsoft.com/en-us/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [Como: agrupar dados](http://msdn.microsoft.com/en-us/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [Como: dados de agregação](http://msdn.microsoft.com/en-us/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [Como: executar uma consulta que retorna objetos de tipo anônimo](http://msdn.microsoft.com/en-us/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [Como: executar uma consulta que retorna uma coleção de tipos primitivos](http://msdn.microsoft.com/en-us/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [Como: consultar objetos relacionados em uma EntityCollection](http://msdn.microsoft.com/en-us/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [Como: ordenar a união de duas consultas](http://msdn.microsoft.com/en-us/853c583a-eaba-4400-830d-be974e735313)  
  
 [Como: resultados da página por meio de consulta](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral do Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [Referência de Linguagem](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
