---
ms.openlocfilehash: 32c7f4e9e4736145f9275b74f34c04404e7c770a
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394011"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a><span data-ttu-id="ed554-101">Caching: o Microsoft. Extensions. Caching. SqlServer usa o novo pacote SqlClient</span><span class="sxs-lookup"><span data-stu-id="ed554-101">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>

<span data-ttu-id="ed554-102">O pacote `Microsoft.Extensions.Caching.SqlServer` usará o novo pacote `Microsoft.Data.SqlClient` em vez do pacote `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="ed554-102">The `Microsoft.Extensions.Caching.SqlServer` package will use the new `Microsoft.Data.SqlClient` package instead of `System.Data.SqlClient` package.</span></span> <span data-ttu-id="ed554-103">Essa alteração pode causar pequenas alterações significativas no comportamento.</span><span class="sxs-lookup"><span data-stu-id="ed554-103">This change could cause slight behavioral breaking changes.</span></span> <span data-ttu-id="ed554-104">Para obter mais informações, consulte [apresentando o novo Microsoft. Data. SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span><span class="sxs-lookup"><span data-stu-id="ed554-104">For more information, see [Introducing the new Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ed554-105">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ed554-105">Version introduced</span></span>

<span data-ttu-id="ed554-106">3.0</span><span class="sxs-lookup"><span data-stu-id="ed554-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ed554-107">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="ed554-107">Old behavior</span></span>

<span data-ttu-id="ed554-108">O pacote `Microsoft.Extensions.Caching.SqlServer` usou o pacote `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="ed554-108">The `Microsoft.Extensions.Caching.SqlServer` package used the `System.Data.SqlClient` package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ed554-109">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="ed554-109">New behavior</span></span>

<span data-ttu-id="ed554-110">`Microsoft.Extensions.Caching.SqlServer` agora está usando o pacote `Microsoft.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="ed554-110">`Microsoft.Extensions.Caching.SqlServer` is now using the `Microsoft.Data.SqlClient` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ed554-111">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="ed554-111">Reason for change</span></span>

<span data-ttu-id="ed554-112">`Microsoft.Data.SqlClient` é um novo pacote criado de `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="ed554-112">`Microsoft.Data.SqlClient` is a new package that is built off of `System.Data.SqlClient`.</span></span> <span data-ttu-id="ed554-113">É aqui que todo o novo recurso funcionará a partir de agora.</span><span class="sxs-lookup"><span data-stu-id="ed554-113">It's where all new feature work will be done from now on.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ed554-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ed554-114">Recommended action</span></span>

<span data-ttu-id="ed554-115">Os clientes não devem precisar se preocupar com essa alteração significativa, a menos que estejam usando tipos retornados pelo pacote `Microsoft.Extensions.Caching.SqlServer` e convertendo-os em tipos `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="ed554-115">Customers shouldn't need to worry about this breaking change unless they were using types returned by the `Microsoft.Extensions.Caching.SqlServer` package and casting them to `System.Data.SqlClient` types.</span></span> <span data-ttu-id="ed554-116">Por exemplo, se alguém estivesse convertendo um `DbConnection` para o [tipo SqlConnection antigo](xref:System.Data.SqlClient.SqlConnection), ele precisaria alterar a conversão para o novo tipo de @no__t 2.</span><span class="sxs-lookup"><span data-stu-id="ed554-116">For example, if someone was casting a `DbConnection` to the [old SqlConnection type](xref:System.Data.SqlClient.SqlConnection), they would need to change the cast to the new `Microsoft.Data.SqlClient.SqlConnection` type.</span></span> 

#### <a name="category"></a><span data-ttu-id="ed554-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="ed554-117">Category</span></span>

<span data-ttu-id="ed554-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ed554-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ed554-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ed554-119">Affected APIs</span></span>

<span data-ttu-id="ed554-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ed554-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
