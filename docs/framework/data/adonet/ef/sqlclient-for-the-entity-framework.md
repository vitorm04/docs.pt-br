---
title: SqlClient para Entity Framework
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: f7077cf9c9b8eb8a86b01e8b38431d1b9a87a80c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248369"
---
# <a name="sqlclient-for-the-entity-framework"></a><span data-ttu-id="cf621-102">SqlClient para Entity Framework</span><span class="sxs-lookup"><span data-stu-id="cf621-102">SqlClient for the Entity Framework</span></span>
<span data-ttu-id="cf621-103">Esta seção descreve o provedor de dados. NET Framework para SQL Server (SqlClient), que permite Entity Framework para trabalhar sobre o Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cf621-103">This section describes the .NET Framework Data Provider for SQL Server (SqlClient), which enables the Entity Framework to work over Microsoft SQL Server.</span></span>  
  
## <a name="provider-schema-attribute"></a><span data-ttu-id="cf621-104">Atributo do provedor</span><span class="sxs-lookup"><span data-stu-id="cf621-104">Provider Schema Attribute</span></span>  
 <span data-ttu-id="cf621-105">`Provider` é um atributo do elemento de `Schema` na linguagem de definição de esquema de armazenamento (SSDL).</span><span class="sxs-lookup"><span data-stu-id="cf621-105">`Provider` is an attribute of the `Schema` element in store schema definition language (SSDL).</span></span>  
  
 <span data-ttu-id="cf621-106">Para usar SqlClient, atribua a cadeia de caracteres “System.Data.SqlClient” ao atributo de `Provider` do elemento de `Schema` .</span><span class="sxs-lookup"><span data-stu-id="cf621-106">To use SqlClient, assign the string "System.Data.SqlClient" to the `Provider` attribute of the `Schema` element.</span></span>  
  
## <a name="providermanifesttoken-schema-attribute"></a><span data-ttu-id="cf621-107">Atributo do esquema de ProviderManifestToken</span><span class="sxs-lookup"><span data-stu-id="cf621-107">ProviderManifestToken Schema Attribute</span></span>  
 <span data-ttu-id="cf621-108">`ProviderManifestToken` é necessário um atributo do elemento de `Schema` em SSDL.</span><span class="sxs-lookup"><span data-stu-id="cf621-108">`ProviderManifestToken` is a required attribute of the `Schema` element in SSDL.</span></span> <span data-ttu-id="cf621-109">Este token é usado para carregar o manifesto do provedor para cenários off-line.</span><span class="sxs-lookup"><span data-stu-id="cf621-109">This token is used to load the provider manifest for offline scenarios.</span></span> <span data-ttu-id="cf621-110">Para obter mais informações `ProviderManifestToken` sobre o atributo, consulte [elemento de esquema (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="cf621-110">For more information about `ProviderManifestToken` attribute, see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span></span>  
  
 <span data-ttu-id="cf621-111">O SqlClient pode ser usado como um provedor de dados para diferentes versões do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cf621-111">SqlClient can be used as a data provider for different versions of SQL Server.</span></span> <span data-ttu-id="cf621-112">Essas versões têm recursos diferentes.</span><span class="sxs-lookup"><span data-stu-id="cf621-112">These versions have different capabilities.</span></span> <span data-ttu-id="cf621-113">Por exemplo, SQL Server 2000 não oferece suporte `varchar(max)` a `nvarchar(max)` tipos e que foram introduzidos com SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="cf621-113">For example, SQL Server 2000 does not support `varchar(max)` and `nvarchar(max)` types that were introduced with SQL Server 2005.</span></span>  
  
 <span data-ttu-id="cf621-114">SqlClient gerencia e aceita os seguintes tokens de manifesto de provedor para versões diferentes do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cf621-114">SqlClient produces and accepts the following provider manifest tokens for different versions of SQL Server.</span></span>  
  
|<span data-ttu-id="cf621-115">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="cf621-115">SQL Server 2000</span></span>|<span data-ttu-id="cf621-116">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="cf621-116">SQL Server 2005</span></span>|<span data-ttu-id="cf621-117">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="cf621-117">SQL Server 2008</span></span>|  
|-|-|-|  
|<span data-ttu-id="cf621-118">2000</span><span class="sxs-lookup"><span data-stu-id="cf621-118">2000</span></span>|<span data-ttu-id="cf621-119">2005</span><span class="sxs-lookup"><span data-stu-id="cf621-119">2005</span></span>|<span data-ttu-id="cf621-120">2008</span><span class="sxs-lookup"><span data-stu-id="cf621-120">2008</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="cf621-121">A partir do Visual Studio 2010, as [ferramentas de Modelo de Dados de Entidade ADO.net](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) não dão suporte a SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="cf621-121">Starting with Visual Studio 2010, the [ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) do not support SQL Server 2000.</span></span>  
  
## <a name="provider-namespace-name"></a><span data-ttu-id="cf621-122">Nome do namespace do provedor</span><span class="sxs-lookup"><span data-stu-id="cf621-122">Provider Namespace Name</span></span>  
 <span data-ttu-id="cf621-123">Todos os provedores devem especificar um namespace.</span><span class="sxs-lookup"><span data-stu-id="cf621-123">All providers must specify a namespace.</span></span> <span data-ttu-id="cf621-124">Essa propriedade informa a Entity Framework que prefixo é usado pelo provedor para compilações específicas, como tipos e funções.</span><span class="sxs-lookup"><span data-stu-id="cf621-124">This property tells the Entity Framework which prefix is used by the provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="cf621-125">O namespace para manifestos de provedor SqlClient é `SqlServer`.</span><span class="sxs-lookup"><span data-stu-id="cf621-125">The namespace for SqlClient provider manifests is `SqlServer`.</span></span> <span data-ttu-id="cf621-126">Para obter mais informações sobre namespaces, consulte [namespaces](./language-reference/namespaces-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="cf621-126">For more information about namespaces, see [Namespaces](./language-reference/namespaces-entity-sql.md).</span></span>  
  
## <a name="types"></a><span data-ttu-id="cf621-127">Tipos</span><span class="sxs-lookup"><span data-stu-id="cf621-127">Types</span></span>  
 <span data-ttu-id="cf621-128">O provedor SqlClient para Entity Framework fornece informações de mapeamento entre tipos de modelo conceitual e tipos SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cf621-128">The SqlClient provider for the Entity Framework provides mapping information between conceptual model types and SQL Server types.</span></span> <span data-ttu-id="cf621-129">Para obter mais informações, consulte [SqlClient para Entity FrameworkTypes](sqlclient-for-ef-types.md).</span><span class="sxs-lookup"><span data-stu-id="cf621-129">For more information, see [SqlClient for Entity FrameworkTypes](sqlclient-for-ef-types.md).</span></span>  
  
## <a name="functions"></a><span data-ttu-id="cf621-130">Funções</span><span class="sxs-lookup"><span data-stu-id="cf621-130">Functions</span></span>  
 <span data-ttu-id="cf621-131">O provedor SqlClient para Entity Framework define a lista de funções suportadas pelo provedor.</span><span class="sxs-lookup"><span data-stu-id="cf621-131">The SqlClient provider for the Entity Framework defines the list of functions supported by the provider.</span></span> <span data-ttu-id="cf621-132">Para obter uma lista das funções com suporte, consulte [SqlClient para funções de Entity Framework](sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="cf621-132">For a list of the supported functions, see [SqlClient for Entity Framework Functions](sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cf621-133">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="cf621-133">In This Section</span></span>  
 [<span data-ttu-id="cf621-134">SqlClient para funções de Entity Framework</span><span class="sxs-lookup"><span data-stu-id="cf621-134">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)  
  
 [<span data-ttu-id="cf621-135">SqlClient para Entity FrameworkTypes</span><span class="sxs-lookup"><span data-stu-id="cf621-135">SqlClient for Entity FrameworkTypes</span></span>](sqlclient-for-ef-types.md)  
  
 [<span data-ttu-id="cf621-136">Problemas conhecidos em SqlClient para Entity Framework</span><span class="sxs-lookup"><span data-stu-id="cf621-136">Known Issues in SqlClient for Entity Framework</span></span>](known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="cf621-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf621-137">See also</span></span>

- <span data-ttu-id="cf621-138">[Entity SQL Language](./language-reference/entity-sql-language.md) (Linguagem SQL de entidade)</span><span class="sxs-lookup"><span data-stu-id="cf621-138">[Entity SQL Language](./language-reference/entity-sql-language.md)</span></span>
- [<span data-ttu-id="cf621-139">Referência de Linguagem</span><span class="sxs-lookup"><span data-stu-id="cf621-139">Language Reference</span></span>](./language-reference/index.md)
- [<span data-ttu-id="cf621-140">Problemas conhecidos no provedor SqlClient para Entity Framework</span><span class="sxs-lookup"><span data-stu-id="cf621-140">Known Issues in SqlClient Provider for Entity Framework</span></span>](sqlclient-for-the-entity-framework.md)
