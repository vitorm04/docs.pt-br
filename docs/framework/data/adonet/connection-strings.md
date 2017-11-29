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
ms.openlocfilehash: bd787373b869c31727cfc0d027b6b98774b0d630
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="8e25d-102">Cadeias de caracteres de conexão no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8e25d-102">Connection Strings in ADO.NET</span></span>
<span data-ttu-id="8e25d-103">O .NET Framework 2.0 apresentou novas funcionalidades para trabalhar com cadeias de conexão, incluindo a introdução de novas palavras-chave nas classes de construtores de cadeias de conexão, que permitem criar mais facilmente cadeias de conexão válidas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8e25d-103">The .NET Framework 2.0 introduced new capabilities for working with connection strings, including the introduction of new keywords to the connection string builder classes, which facilitate creating valid connection strings at run time.</span></span>  
  
 <span data-ttu-id="8e25d-104">Uma cadeia de conexão contém informações de inicialização que são passadas como parâmetros de um provedor de dados para uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8e25d-104">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="8e25d-105">A sintaxe depende do provedor de dados, e a cadeia de conexão é analisada durante a tentativa de abrir uma conexão.</span><span class="sxs-lookup"><span data-stu-id="8e25d-105">The syntax depends on the data provider, and the connection string is parsed during the attempt to open a connection.</span></span> <span data-ttu-id="8e25d-106">Erros de sintaxe geram uma exceção em tempo de execução, mas outros erros ocorrem somente após a fonte de dados receber informações de conexão.</span><span class="sxs-lookup"><span data-stu-id="8e25d-106">Syntax errors generate a run-time exception, but other errors occur only after the data source receives connection information.</span></span> <span data-ttu-id="8e25d-107">Uma vez validada, a fonte de dados aplica as opções especificadas na cadeia de conexão e abre a conexão.</span><span class="sxs-lookup"><span data-stu-id="8e25d-107">Once validated, the data source applies the options specified in the connection string and opens the connection.</span></span>  
  
 <span data-ttu-id="8e25d-108">O formato de uma cadeia de conexão é uma lista de pares chave-valor de parâmetros separados por ponto e vírgula:</span><span class="sxs-lookup"><span data-stu-id="8e25d-108">The format of a connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>  
  
 `keyword1=value; keyword2=value;`  
  
 <span data-ttu-id="8e25d-109">As palavras-chave não diferenciam maiúsculas de minúsculas, e os espaços entre os pares chave-valor são ignorados.</span><span class="sxs-lookup"><span data-stu-id="8e25d-109">Keywords are not case sensitive, and spaces between key/value pairs are ignored.</span></span> <span data-ttu-id="8e25d-110">Entretanto, os valores podem diferenciar maiúsculas de minúsculas, dependendo da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8e25d-110">However, values may be case sensitive, depending on the data source.</span></span> <span data-ttu-id="8e25d-111">Todo valor que contenha ponto e vírgula, aspas simples ou aspas duplas deve ficar entre aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="8e25d-111">Any values containing a semicolon, single quotation marks, or double quotation marks must be enclosed in double quotation marks.</span></span>  
  
 <span data-ttu-id="8e25d-112">A sintaxe válida de cadeia de conexão depende do provedor e evoluiu ao longo dos anos desde as primeiras APIs, como ODBC.</span><span class="sxs-lookup"><span data-stu-id="8e25d-112">Valid connection string syntax depends on the provider, and has evolved over the years from earlier APIs like ODBC.</span></span> <span data-ttu-id="8e25d-113">O Provedor de Dados .NET Framework para SQL Server (SqlClient) incorpora muitos elementos de uma sintaxe mais antiga e é geralmente mais flexível com a sintaxe comum de cadeias de conexão.</span><span class="sxs-lookup"><span data-stu-id="8e25d-113">The .NET Framework Data Provider for SQL Server (SqlClient) incorporates many elements from older syntax and is generally more flexible with common connection string syntax.</span></span> <span data-ttu-id="8e25d-114">Existem, frequentemente, sinônimos igualmente válidos para elementos de sintaxe de cadeia de conexão, mas alguns erros de sintaxe e de ortografia podem causar problemas.</span><span class="sxs-lookup"><span data-stu-id="8e25d-114">There are frequently equally valid synonyms for connection string syntax elements, but some syntax and spelling errors can cause problems.</span></span> <span data-ttu-id="8e25d-115">Por exemplo, "`Integrated Security=true`" é válido, enquanto "`IntegratedSecurity=true`" gera um erro.</span><span class="sxs-lookup"><span data-stu-id="8e25d-115">For example, "`Integrated Security=true`" is valid, whereas "`IntegratedSecurity=true`" causes an error.</span></span> <span data-ttu-id="8e25d-116">Além disso, as cadeias de conexão construídas em tempo de execução a partir de entrada de usuário não validada podem resultar em ataques de injeção de cadeia de caracteres, colocando em risco a segurança da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8e25d-116">In addition, connection strings constructed at run time from unvalidated user input can lead to string injection attacks, jeopardizing security at the data source.</span></span>  
  
 <span data-ttu-id="8e25d-117">Para resolver esses problemas, o ADO.NET 2.0 introduziu novos construtores de cadeias de conexão para cada provedor de dados .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8e25d-117">To address these problems, ADO.NET 2.0 introduced new connection string builders for each .NET Framework data provider.</span></span> <span data-ttu-id="8e25d-118">As palavras-chave são expostas como propriedades, permitindo que a sintaxe da cadeia de conexão seja validada antes de ser enviada à fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8e25d-118">Keywords are exposed as properties, enabling connection string syntax to be validated before submission to the data source.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8e25d-119">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8e25d-119">In This Section</span></span>  
 [<span data-ttu-id="8e25d-120">Construtores de cadeia de Conexão</span><span class="sxs-lookup"><span data-stu-id="8e25d-120">Connection String Builders</span></span>](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 <span data-ttu-id="8e25d-121">Demonstra como usar as classes `ConnectionStringBuilder` para construir cadeias de conexão válidas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8e25d-121">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>  
  
 [<span data-ttu-id="8e25d-122">Cadeias de caracteres de Conexão e arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="8e25d-122">Connection Strings and Configuration Files</span></span>](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 <span data-ttu-id="8e25d-123">Demonstra como armazenar e recuperar cadeias de conexão em arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="8e25d-123">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>  
  
 [<span data-ttu-id="8e25d-124">Sintaxe de cadeia de caracteres de Conexão</span><span class="sxs-lookup"><span data-stu-id="8e25d-124">Connection String Syntax</span></span>](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 <span data-ttu-id="8e25d-125">Descreve como configurar cadeias de conexão específicas do provedor para `SqlClient`, `OracleClient`, `OleDb` e `Odbc`.</span><span class="sxs-lookup"><span data-stu-id="8e25d-125">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>  
  
 [<span data-ttu-id="8e25d-126">Protegendo informações de conexão</span><span class="sxs-lookup"><span data-stu-id="8e25d-126">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 <span data-ttu-id="8e25d-127">Demonstra técnicas para proteger informações usadas para se conectar a uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8e25d-127">Demonstrates techniques for protecting information used to connect to a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e25d-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e25d-128">See Also</span></span>  
 [<span data-ttu-id="8e25d-129">Conectando a uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="8e25d-129">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)  
 <span data-ttu-id="8e25d-130">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8e25d-130">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
