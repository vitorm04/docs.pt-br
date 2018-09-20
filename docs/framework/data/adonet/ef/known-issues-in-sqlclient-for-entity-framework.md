---
title: Problemas conhecidos em SqlClient para Entity Framework
ms.date: 03/30/2017
ms.assetid: 48fe4912-4d0f-46b6-be96-3a42c54780f6
ms.openlocfilehash: c1353444415ddd2305a73d14bacf1bb33a931929
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46477860"
---
# <a name="known-issues-in-sqlclient-for-entity-framework"></a>Problemas conhecidos em SqlClient para Entity Framework
Esta seção descreve os problemas conhecidos relacionados ao provedor de dados. NET Framework para SQL Server (SqlClient).  
  
## <a name="trailing-spaces-in-string-functions"></a>Espaço à direita em funções de cadeia de caracteres  
 O SQL Server ignora os espaços à direita em valores de cadeia de caracteres. Portanto, passe espaço à direita na cadeia de caracteres pode levar a resultados imprevisíveis, mesmo falhas.  
  
 Se você precisa ter espaços à direita em sua cadeia de caracteres, você deve considerar acrescentar um caractere de espaço em branco no final, para que o SQL Server não apare a cadeia de caracteres. Se o espaço à direita não são necessários, devem ser quebrados antes de serem passados abaixo do pipeline de consulta.  
  
## <a name="right-function"></a>Função DIREITA  
 Se um valor de`null` não é passado como um argumento e primeiros 0 são passados como um segundo argumento para `RIGHT(nvarchar(max)`, 0`)` ou `RIGHT(varchar(max)`, 0`)`, um valor de `NULL` serão retornados em vez de uma cadeia de caracteres de `empty` .  
  
## <a name="cross-and-outer-apply-operators"></a>A CRUZ e EXTERIORES APLICAM operadores  
 A CRUZ e EXTERIORES APLICAM operadores foram introduzidos em [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)]. Em alguns casos o pipeline de consulta pode gerar uma instrução Transact-SQL que contém operadores CROSS APPLY e/ou OUTER APPLY. Porque alguns provedores de back-end, incluindo versões do SQL Server anteriores ao [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)], não dão suporte a esses operadores, essas consultas não podem ser executadas nesses provedores backend.  
  
 A seguir estão alguns cenários típicos que podem resultar na presença de CRUZ SE APLICAM e/ou OUTER APPLY operadores na consulta de saída:  
  
-   Um subconsulta correlacionado com paginação.  
  
-   `AnyElement` sobre subpropriedades uma consulta correlacionada, ou sobre uma coleção gerada por navegação.  
  
-   LINQ consulta que uso que agrupa os métodos que aceitam um seletor do elemento.  
  
-   Uma consulta em que uma CRUZ SE APLICA ou OUTER APPLY são especificados explicitamente  
  
-   Uma consulta que tenha uma compilação de DEREF sobre uma compilação de referência.  
  
## <a name="skip-operator"></a>Operador SKIP  
 Se você estiver usando [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)], usar a SKIP com cláusula ORDER BY em colunas não chave pode retornar resultados incorretos. Mais do que o número de linhas especificado podem ser ignoradas se a coluna de chave não tem dados duplicados nele. Isso é devido a como SKIP é convertido para [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]. Por exemplo, a consulta a seguir, mais de cinco linhas podem ser ignoradas se `E.NonKeyColumn` tem valores duplicados:  
  
```  
SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L  
```  
  
## <a name="targeting-the-correct-sql-server-version"></a>Direcionamento a versão correta do SQL Server  
 O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] destinos a [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] consulta com base na versão do SQL Server que é especificado no `ProviderManifestToken` atributo do elemento do esquema no arquivo de modelo (. SSDL) de armazenamento. Esta versão pode diferir de versão do SQL Server que você real é conectada. Por exemplo, se você estiver usando o SQL Server 2005, mas seu `ProviderManifestToken` atributo é definido como 2008, gerado [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] consulta não pode executar no servidor. Por exemplo, uma consulta que usa os tipos de tempo de nova data que foram introduzidos no SQL Server 2008 não será executado em versões anteriores do SQL Server. Se você estiver usando o SQL Server 2005, mas seu `ProviderManifestToken` atributo é definido como 2000, gerado [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] consulta pode ser menor otimizada, ou você pode receber uma exceção informando que a consulta não é suportada. Para obter mais informações, consulte a seção de operadores de aplicar a CRUZ e EXTERIORES, neste tópico.  
  
 Determinados comportamentos de base de dados depende de nível de compatibilidade definido para base de dados. Se o atributo de `ProviderManifestToken` é definido como 2005 e sua versão do SQL Server é 2005, mas a compatibilidade em nível de uma base de dados é definida como “80 " (SQL Server 2000), [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] será gerado como alvo o SQL Server 2005, mas pode não ser executadas como esperado devido à configuração de nível de compatibilidade. Por exemplo, você pode perder ordenação informações se um nome de coluna na cláusula ORDER a lista corresponde a um nome de coluna no seletor.  
  
## <a name="nested-queries-in-projection"></a>Consultas aninhadas na projeção  
 Consultas aninhadas em uma cláusula de projeção podem obter convertido em consultas de produto cartesiano no servidor. Em alguns servidores de back-end, incluindo o servidor de SLQ, isso pode causar a tabela de TempDB a Obtenha muito grande. Isso pode diminuir o desempenho do servidor.  
  
 Este é um exemplo de uma consulta aninhada em uma cláusula de projeção:  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="server-generated-guid-identity-values"></a>Valores gerados a identidade do GUID de servidor  
 Valores gerados o a identidade do tipo de GUID de suporte de [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] , mas o provedor devem oferecer suporte ao retornar o valor gerado de identidade depois que uma linha foi inserida. Começando com o SQL Server 2005, você pode retornar o tipo GUID gerado pelo servidor em um banco de dados do SQL Server por meio de [cláusula OUTPUT](https://go.microsoft.com/fwlink/?LinkId=169400) .  
  
## <a name="see-also"></a>Consulte também  
 [SqlClient para Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)  
 [Problemas conhecidos e considerações no LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)
