---
ms.openlocfilehash: 687118157020ede200f97a0125c4740a06bf4b5e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619795"
---
### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a><span data-ttu-id="60458-101">Tratamento de exceção diferente para os métodos ObjectContext.CreateDatabase e DbProviderServices.CreateDatabase</span><span class="sxs-lookup"><span data-stu-id="60458-101">Different exception handling for ObjectContext.CreateDatabase and DbProviderServices.CreateDatabase methods</span></span>

#### <a name="details"></a><span data-ttu-id="60458-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="60458-102">Details</span></span>

<span data-ttu-id="60458-103">Começando com o .NET Framework 4.5, se houver falha na criação do banco de dados, os métodos <code>CreateDatabase</code> tentarão remover o banco de dados vazio.</span><span class="sxs-lookup"><span data-stu-id="60458-103">Beginning in .NET Framework 4.5, if database creation fails, <code>CreateDatabase</code> methods will attempt to drop the empty database.</span></span> <span data-ttu-id="60458-104">Se essa operação for bem-sucedida, a <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> original será propagada (em vez da <xref:System.InvalidOperationException?displayProperty=fullName> que sempre era gerada no .NET Framework 4.0)</span><span class="sxs-lookup"><span data-stu-id="60458-104">If that operation succeeds, the original <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> will be propagated (instead of the <xref:System.InvalidOperationException?displayProperty=fullName> that was always thrown in .NET Framework 4.0)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="60458-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="60458-105">Suggestion</span></span>

<span data-ttu-id="60458-106">Ao capturar um <xref:System.InvalidOperationException?displayProperty=fullName> durante a execução de <xref:System.Data.Objects.ObjectContext.CreateDatabase> ou <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, agora, SQLExceptions também devem ser capturadas.</span><span class="sxs-lookup"><span data-stu-id="60458-106">When catching an <xref:System.InvalidOperationException?displayProperty=fullName> while executing <xref:System.Data.Objects.ObjectContext.CreateDatabase> or <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, SQLExceptions should now also be caught.</span></span>

| <span data-ttu-id="60458-107">Name</span><span class="sxs-lookup"><span data-stu-id="60458-107">Name</span></span>    | <span data-ttu-id="60458-108">Valor</span><span class="sxs-lookup"><span data-stu-id="60458-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="60458-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="60458-109">Scope</span></span>   |<span data-ttu-id="60458-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="60458-110">Minor</span></span>|
|<span data-ttu-id="60458-111">Versão</span><span class="sxs-lookup"><span data-stu-id="60458-111">Version</span></span>|<span data-ttu-id="60458-112">4.5</span><span class="sxs-lookup"><span data-stu-id="60458-112">4.5</span></span>|
|<span data-ttu-id="60458-113">Type</span><span class="sxs-lookup"><span data-stu-id="60458-113">Type</span></span>|<span data-ttu-id="60458-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="60458-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="60458-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="60458-115">Affected APIs</span></span>

-<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType></li></ul>|
