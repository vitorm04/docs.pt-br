---
title: "Segurança em LINQ to SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 27e40221c22a91bb2a8c40ec4bcfd663eb05aaef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="security-in-linq-to-sql"></a><span data-ttu-id="d85be-102">Segurança em LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d85be-102">Security in LINQ to SQL</span></span>
<span data-ttu-id="d85be-103">Os riscos de segurança são sempre presentes em que você se conecta a um base de dados.</span><span class="sxs-lookup"><span data-stu-id="d85be-103">Security risks are always present when you connect to a database.</span></span> <span data-ttu-id="d85be-104">Embora LINQ to SQL pode incluir algumas novas maneiras de trabalhar com dados no SQL Server, não fornece os mecanismos de segurança adicionais.</span><span class="sxs-lookup"><span data-stu-id="d85be-104">Although LINQ to SQL may include some new ways to work with data in SQL Server, it does not provide any additional security mechanisms.</span></span>  
  
## <a name="access-control-and-authentication"></a><span data-ttu-id="d85be-105">Controle de acesso e autenticação</span><span class="sxs-lookup"><span data-stu-id="d85be-105">Access Control and Authentication</span></span>  
 <span data-ttu-id="d85be-106">LINQ to SQL não tem seu próprio mecanismos de modelo ou de autenticação de usuário.</span><span class="sxs-lookup"><span data-stu-id="d85be-106">LINQ to SQL does not have its own user model or authentication mechanisms.</span></span> <span data-ttu-id="d85be-107">Use a segurança do SQL Server para controlar o acesso a base de dados, para tabelas de base de dados, modos de exibição, e procedimentos armazenados que são mapeados para o seu modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="d85be-107">Use SQL Server Security to control access to the database, database tables, views, and stored procedures that are mapped to your object model.</span></span> <span data-ttu-id="d85be-108">Conceda acesso mìnima necessário aos usuários e requer senhas de alta segurança para autenticação de usuário.</span><span class="sxs-lookup"><span data-stu-id="d85be-108">Grant the minimally required access to users and require strong passwords for user authentication.</span></span>  
  
## <a name="mapping-and-schema-information"></a><span data-ttu-id="d85be-109">Mapeamento e informações de esquema</span><span class="sxs-lookup"><span data-stu-id="d85be-109">Mapping and Schema Information</span></span>  
 <span data-ttu-id="d85be-110">O mapeamento de tipo de SQL-CLR e informações do esquema de base de dados no seu modelo de objeto ou arquivos de mapeamento externo estão disponíveis para todos com acesso 2 esses arquivos no sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="d85be-110">SQL-CLR type mapping and database schema information in your object model or external mapping file is available for all with access to those files in the file system.</span></span> <span data-ttu-id="d85be-111">Suponha que as informações de esquema estará disponível para todos que pode acessar o modelo de objeto ou arquivo de mapeamento externo. Para evitar um acesso mais difusão a informações do esquema, use mecanismos de segurança do arquivo para proteger arquivos de origem e arquivos de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="d85be-111">Assume that schema information will be available to all who can access the object model or external mapping file.To prevent more widespread access to schema information, use file security mechanisms to secure source files and mapping files.</span></span>  
  
## <a name="connection-strings"></a><span data-ttu-id="d85be-112">Cadeias de caracteres de conexão</span><span class="sxs-lookup"><span data-stu-id="d85be-112">Connection Strings</span></span>  
 <span data-ttu-id="d85be-113">Usar senhas em cadeias de conexão deve ser impedida sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="d85be-113">Using passwords in connection strings should be avoided whenever possible.</span></span> <span data-ttu-id="d85be-114">Não é apenas uma cadeia de conexão um risco para a segurança em próprio, mas a cadeia de conexão também pode ser adicionada em texto não criptografado para o modelo de objeto ou arquivo de mapeamento externo ao usar a ferramenta de linha de comando Object Relational Designer ou de SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="d85be-114">Not only is a connection string a security risk in its own right, but the connection string may also be added in clear text to the object model or external mapping file when using the Object Relational Designer or SQLMetal command-line tool.</span></span> <span data-ttu-id="d85be-115">Qualquer pessoa com acesso ao modelo de objeto ou arquivo de mapeamento externo através do sistema de arquivos pode ver a senha de conexão (se é incluído na cadeia de conexão).</span><span class="sxs-lookup"><span data-stu-id="d85be-115">Anyone with access to the object model or external mapping file via the file system could see the connection password (if it is included in the connection string).</span></span>  
  
 <span data-ttu-id="d85be-116">Para minimizar como riscos, use segurança integrada para fazer uma conexão confiável com [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d85be-116">To minimize such risks, use integrated security to make a trusted connection with [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d85be-117">Usando essa abordagem, você não tiver que armazenar uma senha na cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="d85be-117">By using this approach, you do not have to store a password in the connection string.</span></span> <span data-ttu-id="d85be-118">Para obter mais informações, consulte [segurança do SQL Server](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md).</span><span class="sxs-lookup"><span data-stu-id="d85be-118">For more information, see [SQL Server Security](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md).</span></span>  
  
 <span data-ttu-id="d85be-119">Na ausência de segurança integrado, uma senha de texto não será necessária na cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="d85be-119">In the absence of integrated security, a clear-text password will be needed in the connection string.</span></span> <span data-ttu-id="d85be-120">A melhor maneira para ajudar a proteger a cadeia de conexão, na ordem crescente de risco, é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="d85be-120">The best way to help secure your connection string, in increasing order of risk, is as follows:</span></span>  
  
-   <span data-ttu-id="d85be-121">Use segurança integrada.</span><span class="sxs-lookup"><span data-stu-id="d85be-121">Use integrated security.</span></span>  
  
-   <span data-ttu-id="d85be-122">Proteger cadeias de conexão com senhas e minimizar passar ao redor de cadeias de conexão.</span><span class="sxs-lookup"><span data-stu-id="d85be-122">Secure connection strings with passwords and minimize passing around connection strings.</span></span>  
  
-   <span data-ttu-id="d85be-123">Use uma classe de <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> em vez de uma cadeia de conexão já que limita a duração de exibição.</span><span class="sxs-lookup"><span data-stu-id="d85be-123">Use a <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> class instead of a connection string since it limits the duration of exposure.</span></span> <span data-ttu-id="d85be-124">A classe LINQ to SQL <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> pode ser instanciada usando <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="d85be-124">The LINQ to SQL <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> class can be instantiated using a <xref:System.Data.SqlClient.SqlConnection>.</span></span>  
  
-   <span data-ttu-id="d85be-125">Minimize o tempo de vida e toque em pontos para todas as cadeias de conexão.</span><span class="sxs-lookup"><span data-stu-id="d85be-125">Minimize lifetimes and touch points for all connection strings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d85be-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d85be-126">See Also</span></span>  
 [<span data-ttu-id="d85be-127">Informações de plano de fundo</span><span class="sxs-lookup"><span data-stu-id="d85be-127">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="d85be-128">Perguntas frequentes</span><span class="sxs-lookup"><span data-stu-id="d85be-128">Frequently Asked Questions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
