---
title: "Cadeias de caracteres de conexão no ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a20061c551f5cb1a19c64a2f92b8180465f58eb2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="connection-strings-in-adonet"></a>Cadeias de caracteres de conexão no ADO.NET
O .NET Framework 2.0 apresentou novas funcionalidades para trabalhar com cadeias de conexão, incluindo a introdução de novas palavras-chave nas classes de construtores de cadeias de conexão, que permitem criar mais facilmente cadeias de conexão válidas em tempo de execução.  
  
 Uma cadeia de conexão contém informações de inicialização que são passadas como parâmetros de um provedor de dados para uma fonte de dados. A sintaxe depende do provedor de dados, e a cadeia de conexão é analisada durante a tentativa de abrir uma conexão. Erros de sintaxe geram uma exceção em tempo de execução, mas outros erros ocorrem somente após a fonte de dados receber informações de conexão. Uma vez validada, a fonte de dados aplica as opções especificadas na cadeia de conexão e abre a conexão.  
  
 O formato de uma cadeia de conexão é uma lista de pares chave-valor de parâmetros separados por ponto e vírgula:  
  
 `keyword1=value; keyword2=value;`  
  
 As palavras-chave não diferenciam maiúsculas de minúsculas, e os espaços entre os pares chave-valor são ignorados. Entretanto, os valores podem diferenciar maiúsculas de minúsculas, dependendo da fonte de dados. Todo valor que contenha ponto e vírgula, aspas simples ou aspas duplas deve ficar entre aspas duplas.  
  
 A sintaxe válida de cadeia de conexão depende do provedor e evoluiu ao longo dos anos desde as primeiras APIs, como ODBC. O Provedor de Dados .NET Framework para SQL Server (SqlClient) incorpora muitos elementos de uma sintaxe mais antiga e é geralmente mais flexível com a sintaxe comum de cadeias de conexão. Existem, frequentemente, sinônimos igualmente válidos para elementos de sintaxe de cadeia de conexão, mas alguns erros de sintaxe e de ortografia podem causar problemas. Por exemplo, "`Integrated Security=true`" é válido, enquanto "`IntegratedSecurity=true`" gera um erro. Além disso, as cadeias de conexão construídas em tempo de execução a partir de entrada de usuário não validada podem resultar em ataques de injeção de cadeia de caracteres, colocando em risco a segurança da fonte de dados.  
  
 Para resolver esses problemas, o ADO.NET 2.0 introduziu novos construtores de cadeias de conexão para cada provedor de dados .NET Framework. As palavras-chave são expostas como propriedades, permitindo que a sintaxe da cadeia de conexão seja validada antes de ser enviada à fonte de dados.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Construtores de cadeia de Conexão](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 Demonstra como usar as classes `ConnectionStringBuilder` para construir cadeias de conexão válidas em tempo de execução.  
  
 [Cadeias de conexão e arquivos de configuração](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 Demonstra como armazenar e recuperar cadeias de conexão em arquivos de configuração.  
  
 [Sintaxe de cadeia de conexão](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 Descreve como configurar cadeias de conexão específicas do provedor para `SqlClient`, `OracleClient`, `OleDb` e `Odbc`.  
  
 [Protegendo informações de conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 Demonstra técnicas para proteger informações usadas para se conectar a uma fonte de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Conectando a uma fonte de dados](/cpp/data/odbc/connecting-to-a-data-source)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
