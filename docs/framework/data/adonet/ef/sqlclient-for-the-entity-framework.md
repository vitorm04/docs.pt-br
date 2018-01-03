---
title: SqlClient para Entity Framework
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 590df03857805c43b6e9a60c030cadcad3501d3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sqlclient-for-the-entity-framework"></a><span data-ttu-id="3b279-102">SqlClient para Entity Framework</span><span class="sxs-lookup"><span data-stu-id="3b279-102">SqlClient for the Entity Framework</span></span>
<span data-ttu-id="3b279-103">Esta seção descreve o provedor de dados. NET Framework para SQL Server (SqlClient), que permite Entity Framework para trabalhar sobre o Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3b279-103">This section describes the .NET Framework Data Provider for SQL Server (SqlClient), which enables the Entity Framework to work over Microsoft SQL Server.</span></span>  
  
## <a name="provider-schema-attribute"></a><span data-ttu-id="3b279-104">Atributo do provedor</span><span class="sxs-lookup"><span data-stu-id="3b279-104">Provider Schema Attribute</span></span>  
 <span data-ttu-id="3b279-105">`Provider` é um atributo do elemento de `Schema` na linguagem de definição de esquema de armazenamento (SSDL).</span><span class="sxs-lookup"><span data-stu-id="3b279-105">`Provider` is an attribute of the `Schema` element in store schema definition language (SSDL).</span></span>  
  
 <span data-ttu-id="3b279-106">Para usar SqlClient, atribua a cadeia de caracteres “System.Data.SqlClient” ao atributo de `Provider` do elemento de `Schema` .</span><span class="sxs-lookup"><span data-stu-id="3b279-106">To use SqlClient, assign the string "System.Data.SqlClient" to the `Provider` attribute of the `Schema` element.</span></span>  
  
## <a name="providermanifesttoken-schema-attribute"></a><span data-ttu-id="3b279-107">Atributo do esquema de ProviderManifestToken</span><span class="sxs-lookup"><span data-stu-id="3b279-107">ProviderManifestToken Schema Attribute</span></span>  
 <span data-ttu-id="3b279-108">`ProviderManifestToken` é necessário um atributo do elemento de `Schema` em SSDL.</span><span class="sxs-lookup"><span data-stu-id="3b279-108">`ProviderManifestToken` is a required attribute of the `Schema` element in SSDL.</span></span> <span data-ttu-id="3b279-109">Este token é usado para carregar o manifesto do provedor para cenários off-line.</span><span class="sxs-lookup"><span data-stu-id="3b279-109">This token is used to load the provider manifest for offline scenarios.</span></span> <span data-ttu-id="3b279-110">Para obter mais informações sobre `ProviderManifestToken` de atributo, consulte [elemento de esquema (SSDL)](http://msdn.microsoft.com/en-us/fec75ae4-7f16-4421-9265-9dac61509222).</span><span class="sxs-lookup"><span data-stu-id="3b279-110">For more information about `ProviderManifestToken` attribute, see [Schema Element (SSDL)](http://msdn.microsoft.com/en-us/fec75ae4-7f16-4421-9265-9dac61509222).</span></span>  
  
 <span data-ttu-id="3b279-111">SqlClient pode ser usado como um provedor de dados para versões diferentes de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3b279-111">SqlClient can be used as a data provider for different versions of [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3b279-112">Essas versões têm recursos diferentes.</span><span class="sxs-lookup"><span data-stu-id="3b279-112">These versions have different capabilities.</span></span> <span data-ttu-id="3b279-113">Por exemplo, [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] não oferece suporte `varchar(max)` e os tipos de `nvarchar(max)` que foram introduzidos com [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3b279-113">For example, [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] does not support `varchar(max)` and `nvarchar(max)` types that were introduced with [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="3b279-114">SqlClient gerencia e aceita os seguintes tokens de manifesto de provedor para versões diferentes do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3b279-114">SqlClient produces and accepts the following provider manifest tokens for different versions of SQL Server.</span></span>  
  
|<span data-ttu-id="3b279-115">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="3b279-115">SQL Server 2000</span></span>|<span data-ttu-id="3b279-116">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="3b279-116">SQL Server 2005</span></span>|<span data-ttu-id="3b279-117">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="3b279-117">SQL Server 2008</span></span>|  
|-|-|-|  
|<span data-ttu-id="3b279-118">2000</span><span class="sxs-lookup"><span data-stu-id="3b279-118">2000</span></span>|<span data-ttu-id="3b279-119">2005</span><span class="sxs-lookup"><span data-stu-id="3b279-119">2005</span></span>|<span data-ttu-id="3b279-120">2008</span><span class="sxs-lookup"><span data-stu-id="3b279-120">2008</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="3b279-121">Começando com [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] 2010, o [ferramentas de modelo de dados de entidade ADO.NET](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527) não oferecem suporte a SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="3b279-121">Starting with [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] 2010, the [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527) do not support SQL Server 2000.</span></span>  
  
## <a name="provider-namespace-name"></a><span data-ttu-id="3b279-122">Nome do namespace do provedor</span><span class="sxs-lookup"><span data-stu-id="3b279-122">Provider Namespace Name</span></span>  
 <span data-ttu-id="3b279-123">Todos os provedores devem especificar um namespace.</span><span class="sxs-lookup"><span data-stu-id="3b279-123">All providers must specify a namespace.</span></span> <span data-ttu-id="3b279-124">Essa propriedade informa a Entity Framework que prefixo é usado pelo provedor para compilações específicas, como tipos e funções.</span><span class="sxs-lookup"><span data-stu-id="3b279-124">This property tells the Entity Framework which prefix is used by the provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="3b279-125">O namespace para manifestos de provedor SqlClient é `SqlServer`.</span><span class="sxs-lookup"><span data-stu-id="3b279-125">The namespace for SqlClient provider manifests is `SqlServer`.</span></span> <span data-ttu-id="3b279-126">Para obter mais informações sobre namespaces, consulte [Namespaces](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3b279-126">For more information about namespaces, see [Namespaces](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).</span></span>  
  
## <a name="types"></a><span data-ttu-id="3b279-127">Tipos</span><span class="sxs-lookup"><span data-stu-id="3b279-127">Types</span></span>  
 <span data-ttu-id="3b279-128">O provedor SqlClient para Entity Framework fornece informações de mapeamento entre tipos de modelo conceitual e tipos SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3b279-128">The SqlClient provider for the Entity Framework provides mapping information between conceptual model types and SQL Server types.</span></span> <span data-ttu-id="3b279-129">Para obter mais informações, consulte [SqlClient para Entity FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).</span><span class="sxs-lookup"><span data-stu-id="3b279-129">For more information, see [SqlClient for Entity FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).</span></span>  
  
## <a name="functions"></a><span data-ttu-id="3b279-130">Funções</span><span class="sxs-lookup"><span data-stu-id="3b279-130">Functions</span></span>  
 <span data-ttu-id="3b279-131">O provedor SqlClient para Entity Framework define a lista de funções suportadas pelo provedor.</span><span class="sxs-lookup"><span data-stu-id="3b279-131">The SqlClient provider for the Entity Framework defines the list of functions supported by the provider.</span></span> <span data-ttu-id="3b279-132">Para obter uma lista das funções com suporte, consulte [SqlClient para funções de Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="3b279-132">For a list of the supported functions, see [SqlClient for Entity Framework Functions](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3b279-133">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="3b279-133">In This Section</span></span>  
 [<span data-ttu-id="3b279-134">SqlClient para funções de Entity Framework</span><span class="sxs-lookup"><span data-stu-id="3b279-134">SqlClient for Entity Framework Functions</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [<span data-ttu-id="3b279-135">SqlClient para Entity FrameworkTypes</span><span class="sxs-lookup"><span data-stu-id="3b279-135">SqlClient for Entity FrameworkTypes</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [<span data-ttu-id="3b279-136">Problemas conhecidos em SqlClient para Entity Framework</span><span class="sxs-lookup"><span data-stu-id="3b279-136">Known Issues in SqlClient for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="3b279-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b279-137">See Also</span></span>  
 <span data-ttu-id="3b279-138">[Entity SQL Language](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) (Linguagem SQL de entidade)</span><span class="sxs-lookup"><span data-stu-id="3b279-138">[Entity SQL Language](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)</span></span>  
 [<span data-ttu-id="3b279-139">Referência de Linguagem</span><span class="sxs-lookup"><span data-stu-id="3b279-139">Language Reference</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)  
 [<span data-ttu-id="3b279-140">Problemas conhecidos no provedor SqlClient para Entity Framework</span><span class="sxs-lookup"><span data-stu-id="3b279-140">Known Issues in SqlClient Provider for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
