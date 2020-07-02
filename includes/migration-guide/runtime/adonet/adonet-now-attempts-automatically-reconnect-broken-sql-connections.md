---
ms.openlocfilehash: 23ba6064a283b47312a66f3636c2834a7d58106e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619772"
---
### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a><span data-ttu-id="181fb-101">Agora, ADO.NET tentará reconectar automaticamente conexões SQL interrompidas</span><span class="sxs-lookup"><span data-stu-id="181fb-101">ADO.NET now attempts to automatically reconnect broken SQL connections</span></span>

#### <a name="details"></a><span data-ttu-id="181fb-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="181fb-102">Details</span></span>

<span data-ttu-id="181fb-103">A partir do .NET Framework 4.5.1, o .NET Framework tentará reconectar automaticamente conexões SQL interrompidas.</span><span class="sxs-lookup"><span data-stu-id="181fb-103">Beginning in the .NET Framework 4.5.1, the .NET Framework will attempt to automatically reconnect broken SQL connections.</span></span> <span data-ttu-id="181fb-104">Embora, normalmente, isso torne os aplicativos mais confiáveis, há casos de borda em que um aplicativo precisa saber que a conexão foi perdida para tomar medidas sobre a reconexão.</span><span class="sxs-lookup"><span data-stu-id="181fb-104">Although this will typically make apps more reliable, there are edge cases in which an app needs to know that the connection was lost so that it can take some action upon reconnection.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="181fb-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="181fb-105">Suggestion</span></span>

<span data-ttu-id="181fb-106">Se esse recurso for indesejável devido a preocupações de compatibilidade, ele poderá ser desabilitado por meio da configuração da propriedade <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> de uma cadeia de conexão (ou <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>) para 0.</span><span class="sxs-lookup"><span data-stu-id="181fb-106">If this feature is undesirable due to compatibility concerns, it can be disabled by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> property of a connection string (or <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>) to 0.</span></span>

| <span data-ttu-id="181fb-107">Name</span><span class="sxs-lookup"><span data-stu-id="181fb-107">Name</span></span>    | <span data-ttu-id="181fb-108">Valor</span><span class="sxs-lookup"><span data-stu-id="181fb-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="181fb-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="181fb-109">Scope</span></span>   |<span data-ttu-id="181fb-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="181fb-110">Edge</span></span>|
|<span data-ttu-id="181fb-111">Versão</span><span class="sxs-lookup"><span data-stu-id="181fb-111">Version</span></span>|<span data-ttu-id="181fb-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="181fb-112">4.5.1</span></span>|
|<span data-ttu-id="181fb-113">Type</span><span class="sxs-lookup"><span data-stu-id="181fb-113">Type</span></span>|<span data-ttu-id="181fb-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="181fb-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="181fb-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="181fb-115">Affected APIs</span></span>

-<xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)></li></ul>|
