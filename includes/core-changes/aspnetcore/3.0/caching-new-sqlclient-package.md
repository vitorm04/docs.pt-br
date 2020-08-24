---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198338"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a><span data-ttu-id="6599e-101">Caching: o Microsoft. Extensions. Caching. SqlServer usa o novo pacote SqlClient</span><span class="sxs-lookup"><span data-stu-id="6599e-101">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>

<span data-ttu-id="6599e-102">O `Microsoft.Extensions.Caching.SqlServer` pacote usará o novo `Microsoft.Data.SqlClient` pacote em vez do `System.Data.SqlClient` pacote.</span><span class="sxs-lookup"><span data-stu-id="6599e-102">The `Microsoft.Extensions.Caching.SqlServer` package will use the new `Microsoft.Data.SqlClient` package instead of `System.Data.SqlClient` package.</span></span> <span data-ttu-id="6599e-103">Essa alteração pode causar pequenas alterações significativas no comportamento.</span><span class="sxs-lookup"><span data-stu-id="6599e-103">This change could cause slight behavioral breaking changes.</span></span> <span data-ttu-id="6599e-104">Para obter mais informações, consulte [apresentando o novo Microsoft. Data. SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span><span class="sxs-lookup"><span data-stu-id="6599e-104">For more information, see [Introducing the new Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6599e-105">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="6599e-105">Version introduced</span></span>

<span data-ttu-id="6599e-106">3,0</span><span class="sxs-lookup"><span data-stu-id="6599e-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6599e-107">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="6599e-107">Old behavior</span></span>

<span data-ttu-id="6599e-108">O `Microsoft.Extensions.Caching.SqlServer` pacote usou o `System.Data.SqlClient` pacote.</span><span class="sxs-lookup"><span data-stu-id="6599e-108">The `Microsoft.Extensions.Caching.SqlServer` package used the `System.Data.SqlClient` package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6599e-109">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="6599e-109">New behavior</span></span>

<span data-ttu-id="6599e-110">`Microsoft.Extensions.Caching.SqlServer` Agora está usando o `Microsoft.Data.SqlClient` pacote.</span><span class="sxs-lookup"><span data-stu-id="6599e-110">`Microsoft.Extensions.Caching.SqlServer` is now using the `Microsoft.Data.SqlClient` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6599e-111">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="6599e-111">Reason for change</span></span>

<span data-ttu-id="6599e-112">`Microsoft.Data.SqlClient` é um novo pacote criado do `System.Data.SqlClient` .</span><span class="sxs-lookup"><span data-stu-id="6599e-112">`Microsoft.Data.SqlClient` is a new package that is built off of `System.Data.SqlClient`.</span></span> <span data-ttu-id="6599e-113">É aqui que todo o novo recurso funcionará a partir de agora.</span><span class="sxs-lookup"><span data-stu-id="6599e-113">It's where all new feature work will be done from now on.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6599e-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="6599e-114">Recommended action</span></span>

<span data-ttu-id="6599e-115">Os clientes não devem precisar se preocupar com essa alteração significativa, a menos que estejam usando tipos retornados pelo `Microsoft.Extensions.Caching.SqlServer` pacote e convertendo-os em `System.Data.SqlClient` tipos.</span><span class="sxs-lookup"><span data-stu-id="6599e-115">Customers shouldn't need to worry about this breaking change unless they were using types returned by the `Microsoft.Extensions.Caching.SqlServer` package and casting them to `System.Data.SqlClient` types.</span></span> <span data-ttu-id="6599e-116">Por exemplo, se alguém estivesse convertendo um `DbConnection` para o [tipo SqlConnection antigo](xref:System.Data.SqlClient.SqlConnection), ele precisaria alterar a conversão para o novo `Microsoft.Data.SqlClient.SqlConnection` tipo.</span><span class="sxs-lookup"><span data-stu-id="6599e-116">For example, if someone was casting a `DbConnection` to the [old SqlConnection type](xref:System.Data.SqlClient.SqlConnection), they would need to change the cast to the new `Microsoft.Data.SqlClient.SqlConnection` type.</span></span>

#### <a name="category"></a><span data-ttu-id="6599e-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="6599e-117">Category</span></span>

<span data-ttu-id="6599e-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6599e-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6599e-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="6599e-119">Affected APIs</span></span>

<span data-ttu-id="6599e-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="6599e-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
