---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198338"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a><span data-ttu-id="5bd03-101">Cache: Microsoft.Extensions.Caching.SqlServer usa novo pacote SqlClient</span><span class="sxs-lookup"><span data-stu-id="5bd03-101">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>

<span data-ttu-id="5bd03-102">O `Microsoft.Extensions.Caching.SqlServer` pacote usará `Microsoft.Data.SqlClient` o novo `System.Data.SqlClient` pacote em vez de pacote.</span><span class="sxs-lookup"><span data-stu-id="5bd03-102">The `Microsoft.Extensions.Caching.SqlServer` package will use the new `Microsoft.Data.SqlClient` package instead of `System.Data.SqlClient` package.</span></span> <span data-ttu-id="5bd03-103">Essa mudança pode causar pequenas mudanças comportamentais.</span><span class="sxs-lookup"><span data-stu-id="5bd03-103">This change could cause slight behavioral breaking changes.</span></span> <span data-ttu-id="5bd03-104">Para obter mais informações, consulte [Introduzindo o novo Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span><span class="sxs-lookup"><span data-stu-id="5bd03-104">For more information, see [Introducing the new Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5bd03-105">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="5bd03-105">Version introduced</span></span>

<span data-ttu-id="5bd03-106">3.0</span><span class="sxs-lookup"><span data-stu-id="5bd03-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5bd03-107">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="5bd03-107">Old behavior</span></span>

<span data-ttu-id="5bd03-108">O `Microsoft.Extensions.Caching.SqlServer` pacote `System.Data.SqlClient` usou o pacote.</span><span class="sxs-lookup"><span data-stu-id="5bd03-108">The `Microsoft.Extensions.Caching.SqlServer` package used the `System.Data.SqlClient` package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="5bd03-109">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="5bd03-109">New behavior</span></span>

<span data-ttu-id="5bd03-110">`Microsoft.Extensions.Caching.SqlServer`agora está `Microsoft.Data.SqlClient` usando o pacote.</span><span class="sxs-lookup"><span data-stu-id="5bd03-110">`Microsoft.Extensions.Caching.SqlServer` is now using the `Microsoft.Data.SqlClient` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5bd03-111">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="5bd03-111">Reason for change</span></span>

<span data-ttu-id="5bd03-112">`Microsoft.Data.SqlClient`é um novo pacote que `System.Data.SqlClient`é construído a partir de .</span><span class="sxs-lookup"><span data-stu-id="5bd03-112">`Microsoft.Data.SqlClient` is a new package that is built off of `System.Data.SqlClient`.</span></span> <span data-ttu-id="5bd03-113">É onde todos os novos trabalhos serão feitos a partir de agora.</span><span class="sxs-lookup"><span data-stu-id="5bd03-113">It's where all new feature work will be done from now on.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5bd03-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="5bd03-114">Recommended action</span></span>

<span data-ttu-id="5bd03-115">Os clientes não devem se preocupar com essa mudança de `Microsoft.Extensions.Caching.SqlServer` quebra, a `System.Data.SqlClient` menos que estejam usando tipos devolvidos pelo pacote e lançando-os para tipos.</span><span class="sxs-lookup"><span data-stu-id="5bd03-115">Customers shouldn't need to worry about this breaking change unless they were using types returned by the `Microsoft.Extensions.Caching.SqlServer` package and casting them to `System.Data.SqlClient` types.</span></span> <span data-ttu-id="5bd03-116">Por exemplo, se alguém `DbConnection` estivesse lançando um para o [antigo tipo SqlConnection,](xref:System.Data.SqlClient.SqlConnection)ele precisaria mudar o elenco para o novo `Microsoft.Data.SqlClient.SqlConnection` tipo.</span><span class="sxs-lookup"><span data-stu-id="5bd03-116">For example, if someone was casting a `DbConnection` to the [old SqlConnection type](xref:System.Data.SqlClient.SqlConnection), they would need to change the cast to the new `Microsoft.Data.SqlClient.SqlConnection` type.</span></span>

#### <a name="category"></a><span data-ttu-id="5bd03-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="5bd03-117">Category</span></span>

<span data-ttu-id="5bd03-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5bd03-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5bd03-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="5bd03-119">Affected APIs</span></span>

<span data-ttu-id="5bd03-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5bd03-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
