---
title: Linguagem Entity SQL
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: a2e4b7245dbfccf7864481b52a0e868a85efbca6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251013"
---
# <a name="entity-sql-language"></a>Linguagem Entity SQL
O Entity SQL é uma linguagem de consulta independente de armazenamento semelhante ao SQL. O Entity SQL permite que você consulte dados de entidade, como objetos ou em forma de tabela. Você deve considerar o uso do Entity SQL nos seguintes casos:  
  
- Quando uma consulta deve ser construída dinamicamente em tempo de execução. Nesse caso, você também deve considerar o uso dos métodos do construtor de consultas de <xref:System.Data.Objects.ObjectQuery%601>, em vez de construir uma cadeia de caracteres de consulta Entity SQL em tempo de execução.  
  
- Quando você deseja definir uma consulta como parte da definição do modelo. Somente o Entity SQL tem suporte em um modelo de dados. Para obter mais informações, consulte [elemento QueryView (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)  
  
- Ao usar EntityClient para retornar dados de entidade somente leitura como conjuntos de linhas usando <xref:System.Data.EntityClient.EntityDataReader>. Para obter mais informações, consulte [EntityClient Provider for the Entity Framework](../entityclient-provider-for-the-entity-framework.md).  
  
- Se você já for um especialista em linguagens de consulta baseadas em SQL, o Entity SQL poderá parecer a opção mais natural para você.  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a>Usando Entity SQL com o provedor EntityClient  
 Se você desejar usar o Entity SQL com o provedor EntityClient, consulte os seguintes tópicos para obter mais informações:  
  
 [Provedor EntityClient para Entity Framework](../entityclient-provider-for-the-entity-framework.md)  
  
 [Como: Criar uma cadeia de conexão de EntityConnection](../how-to-build-an-entityconnection-connection-string.md)  
  
 [Como: Executar uma consulta que retorna os resultados de Primitivatype](../how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Como: Executar uma consulta que retorna resultados de Estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Como: Executar uma consulta que retorna resultados de RefType](../how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Como: Executar uma consulta que retorna tipos complexos](../how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Como: Executar uma consulta que retorna coleções aninhadas](../how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Como: Executar uma consulta de Entity SQL parametrizada usando EntityCommand](../how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Como: Executar um procedimento armazenado com parâmetros usando EntityCommand](../how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Como: Executar uma consulta polimórfica](../how-to-execute-a-polymorphic-query.md)  
  
 [Como: Navegar pelas relações com o operador Navigate](../how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a>Usando o Entity SQL com consultas de objetos  
 Se você desejar usar o Entity SQL com consultas de objetos, consulte os seguintes tópicos para obter mais informações:  
  
 [Como: Executar uma consulta que retorna objetos de tipo de entidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))  
  
 [Como: Executar uma consulta parametrizada](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))  
  
 [Como: Navegar pelas relações usando as propriedades de navegação](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))  
  
 [Como: Chamar uma função definida pelo usuário](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))  
  
 [Como: Filtrar dados](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))  
  
 [Como: Classificar dados](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))  
  
 [Como: Agrupar dados](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))  
  
 [Como: Agregar dados](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))  
  
 [Como: Executar uma consulta que retorna objetos de tipo anônimo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))  
  
 [Como: Executar uma consulta que retorna uma coleção de tipos primitivos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))  
  
 [Como: Consultar objetos relacionados em uma EntityCollection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))  
  
 [Como: Ordenar a União de duas consultas](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))  
  
 [Como: Página por meio de resultados da consulta](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral do Entity SQL](entity-sql-overview.md)  
  
 [Referência de Entity SQL](entity-sql-reference.md)  
  
## <a name="see-also"></a>Consulte também

- [Entity Framework do ADO.NET](../index.md)
- [Referência de Linguagem](index.md)
